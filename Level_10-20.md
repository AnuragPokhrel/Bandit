# Solutions for level 1 to 5 (2025-11-10)
## ⚠️ The methods I used aren't always the best or the most efficient or the only option. and there will be spoilers for the game. And sorry for typo mistakes

## Level 10 -> 11
Process : The password is in the file ~/data.txt and is encoded in base64 and can be easily seen by either ``base6d -d data.txt`` or ``cat data.txt | base64 -d``
## Level 11 -> 12
Process : The password is in ~/data.txt but has been encoded by ROT13 and to simply decode it, I used ``cat data.txt | tr "A-MN-Za-mn-z" "N-ZA-Mn-za-m"`` . Maybe there is a simpler command but this is what I used.
## Level 12 -> 13
Process : This was stupid, kinda interesting, so it starts with a hexdump and I after coping it to /tmp/randomfolder reversed it using ``xxd -r data.txt > file.txt`` and then after checking the file by just ``file file.txt`` it was a gzip compressed data and then to speed things up I did ``mv data.txt data.gz && gunzip data.gz && file data`` and then it was bzip2 compressed then gzip again then tar archived and again tar archived and bzip2 then tar then gzip and finally txt. I guess that was the correct sequence but it's easy to check file type by using ``file filename`` .
## Level 13 -> 14
Process : For this level you get sshkey.private in the ~/ folder. Which you can copy using scp and I changed permission to 600 later. Then you can use the key to go to the next level by using ``ssh -i ssh.key bandit14@bandit.labs.overthewire.org -p 2220`` . Note: ssh.key is the filename of the file I copied the key to.
## Level 14 -> 15
Process : For this level you read the password that is in ``/etc/bandit_pass/bandit14`` . And then sending the password to port 30000 on localhost by ``echo "actualpassword" | nc localhost 30000`` and then it returns the password for next level. 
## Level 15 -> 16
Process : For this level you simply have to send the password of current level to localhost 30001 using ssl/tls encryption. Using ``openssl s_client -connect localhost:30001`` and then enter the password of current level. 
## Level 16 -> 17
Process : This was quite interesting, I opened all the ports using ``nmap -p 31000-32000 localhost`` and it did print 5 open ports and there could have been better options to check which one is correct but I made a small script in /tmp which is this:
```                         
for i in 31046 31518 31691 31790 31960; do
openssl s_client -connect localhost:$i -quiet
done
```
Anyways it did work so it counts. and it gave a ssh key. 
## Level 17 -> 18
Process : It was quite easy, and simply using ``diff passwords.new passwords.old`` gives the password.
## Level 18 -> 19
Process : In this level the ``.bashrc`` file is modified to kick you out when you login. So all you have to do is do disable pseudo-terminal allocation and hint is the password is in readme file in ~ folder, so simply adding ``-T cat readme`` in the ssh command will print password. 
## Level 19 -> 20
Process : There is a setuid file in home directory which runs file as owner. after poking around for a bit and rereading hints, I figured out that running command with that file runs commands as the user bandit20 . so running ``bandit20-do cat /etc/bandit_pass/bandit20`` prints the password.