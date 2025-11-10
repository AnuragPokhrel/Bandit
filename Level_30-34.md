# Solutions for level 1 to 5 (2025-11-09)
## ⚠️ The methods I used aren't always the best or the most efficient or the only option. and there will be spoilers for the game. And sorry for typo mistakes

## Level 30 -> 31
Process : For this level clone the repo like before and check for branches but there's not any useful info. But we can check tags by ``git tag`` and it gives secret tag and using ``git show tag`` we can obtain the password.
## Level 31 -> 32
Process : For this we have to push file key.txt that contains the line ``May I come in?" . simply make a file with that content but .gitignore file will stop any text files from being pushed so delete it and add it to git and commit. And then push it to Master branch and you get the password.
## Level 32 -> 33
Process : In this level you're spawned in a weird shell that turns every character into uppercase, but by simply running ``$0`` you spawn a new shell and now you can cat the password for 33 level.
## Level 33 -> 34
Process : And as of now this doesn't exist yet so