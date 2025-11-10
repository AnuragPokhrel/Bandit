# Solutions for level 1 to 5 (2025-11-10)
## ⚠️ The methods I used aren't always the best or the most efficient or the only option. and there will be spoilers for the game. And sorry for typo mistakes
## Level 20 -> 21
Process : In this level you have to setup two terminals and connect to save level and in one terminal send the password of this level to any port above 1024 and pass the password using ``echo "password" | nc -l 55555`` and in another terminal run ``./suconnect 55555`` and if the password matches it will give password.
## Level 21 -> 22
Process : For this level the hint was cron a program to automate tasks and file ``cronjob_bandit22`` is in there and running cat command in this file gives another file ``/usr/bin/cronjob_bandit22.sh`` and running cat in this file gives the password like file but you have to cat that file to get password.
## Level 22 -> 23
Process : For this level same as before when I went to the cron.d and saw the job it was running the script, the script was storing password in a file inside /tmp and filename was the md5 hash and to get the filename I ran ``echo "I am user bandit23" | md5sum" and cat the file it gave.
## Level 23 -> 24
Process : In this level you have to ake your own script that will copy bandit24 password from file ``/etc/bandit_pass/bandit24`` to somewhere where you can read it. and you have to put the script in ``/var/spool/bandit24/foo/`` and cron will run it as bandit24 user and later you can read the password from the file. I used this simple script:
```
#!/bin/bash
cp /etc/bandit_pass/bandit24 /tmp/bandit24
```
## Level 24 -> 25
Process : For this you have to pass the bandit24 password and 4 digit pin and for that I used this script to brute force
```
( for i in {0000..9999}; do printf "%s %s\n" "bandit24password" "$i"; done ) | nc localhost 30002
```
## Level 25 -> 26
Process : The key for lvl 26 is in the home directory which can easily be copied.
## Level 26 -> 27
Process : Process : I had no idea what is happening and after some research it was found that making terminal size smaller will make it open in more and by pressing v it takes to vim text editor and in which we can easily run command and by ``set shell=/bin/bash`` and then run ``bandit27-do cat /etc/bandit_pass/bandit27`` we cam get password for lvl 27.
## Level 27 -> 28
Process : For lvl 28 password just copy the repo url and do ``git clone`` on port 2220 and then cat README that is inside repo.
## Level 28 -> 29
Process : For this level simply clone the given repo but the data is censored and so check the log using ``git log``. And checkout to the previous versions where the password hasn't been censored yet.
## Level 29 -> 30
Process : For this level similarly clone the repo and check the branches ny using ``git branch -a``. The password is in remotes/origin/dev branch and you can switch easily using ``git checkout remotes/origin/dev`` . 
