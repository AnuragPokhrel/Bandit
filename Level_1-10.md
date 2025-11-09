# Solutions for level 1 to 5 (2025-11-09)
## ⚠️ The methods I used aren't always the best or the most efficient or the only option. and there will be spoilers for the game.

## Level 0 -> 1
Process : The password is in the file /home/bandit0/readme and can be seen by ``cat`` command.
##  Level 1 -> 2
process : The password is in the ./- file. (. means current directory, and in here it represents the directory in which we get logged into)  
``-`` is a special character, used to provide flag, and to escape it just write ``./-`` which makes it a file location.

## Level 2 -> 3
process : The password is in the ``~/--spaces in the filename--`` file. The file has - in it's name , same as before, and for the spaces in filename, cat reads that as multiple files, and to solve that, use filename inside ``""`` which makes it a single string.

## Level 3 -> 4
Process : The password is in the ~/inhere/...Hiding-From-You file.  To see hidden files use ``ls -a`` and then use ``cat`` to see the file contents.  
## Level 4 -> 5
Process : The password is in the one of the file in the inhere directory. There are multiple files and to get only human readable string I used ``strings ./-file{00..09}`` which prints all strigs in the file -file00 to -file09 that are in current directory.
## Level 5 -> 6
Process : The password is in the one of the files inside inhere directory, and I used ``find . -size 1033c -exec cat {} \;`` which finds the file with exact size of 1033 bytes and executes cat command on that file. Luckily there was only one file that had size of 1033 bytes, otherwise additional flags had to be used.
## Level 6 -> 7
Process : This time the file was somewhere in the system instead of a exact directory. and hints were owned by bandit7 griup bandit6 and 33 bytes in size, this time there were many files , so I had to use all three flags and the command used was ``find / -user bandit7 -group bandit6 -size 33c -exec cat {} \; 2>/dev/null`` . and 2>/dev/null is to redirect all standard errors like permission denied to void.

## Level 7 -> 8
Process : The password was simply in the ~/data.txt file next to the word millionth and to obtain this I used ``grep "millionth" data.txt`` . Alternatively ``cat data.txt | grep "millionth`` could be used.
 
## Level 8 -> 9
Process : The password is in the ~/data.txt file and is the only unique line. So I used ``sort`` command to sort and uniq command to filter diplicate lines, and the command I used was ``cat data.txt | sort | uniq -u`` . Or you can simply use ``cat data.txt | sort | uniq -c| sort -n | head -n 1`` for fun.
## Level 9 -> 10
Process : Again the password is in data.txt but this time preceded by many =. but when I tried ``strings data.txt | grep "="`` it said binary file matches and I had no idea what that means, but with ``-a`` flag, it forced grep to print it anyways and the password was revealed.
