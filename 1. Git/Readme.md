# change directory to codebase
$ cd /file/path/to/code

#change disk in windows
 cd /D

# make directory a git repository
$ git init

# add git file or directory
git add <file or directory name>

#add all
git add .

# Commit changes to head (but not yet to the remote repository):
git commit -m "Commit message"

# Commit any files you've added with git add, and also commit any files you've changed since then:
git commit -a

#verify new remote
git remote -v

#add new remote
git remote add origin ssh://git@example.com:1234/myRepo.git

#if you're updating to use HTTPS, your URL might look like:
#https://github.com/USERNAME/REPOSITORY.git
#If you're updating to use SSH, your URL might look like:
#git@github.com:USERNAME/REPOSITORY.git

#Switching remote URLs from SSH to HTTPS
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git

#Switching remote URLs from HTTPS to SSH
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git

# Send changes to the master branch of your remote repository:	
git push origin master

#login github
ssh -T git@github.com

#keygen SSH keys
ssh-keygen -t rsa -b 4096 -C "mail@mail.com"

#difference
git diff

#create a new repository on the command line example
echo "# gittest" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:"login"/"repository name".git
git push -u origin main

#or push an existing repository from the command line
git remote add origin git@github.com:"login"/"repository name".git
git branch -M main
git push -u origin main