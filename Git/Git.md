# Git
### Make directory a git repository
```
$ git init
```
### Commit any files you've added with git add, and also commit any files you've changed since then:
```
git commit -a
```
### Verify new remote
```
git remote -v
```
### Add new remote
```
git remote add origin ssh://git@example.com:1234/myRepo.git
if you're updating to use HTTPS, your URL might look like:
https[]()://github.com/USERNAME/REPOSITORY.git  
If you're updating to use SSH, your URL might look like:
git[]()@github.com:USERNAME/REPOSITORY.git
```
### Switching remote URLs from SSH to HTTPS
```
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
```
### Switching remote URLs from HTTPS to SSH
```
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```
### Send changes to the master branch of your remote repository:	
```
git push origin master
```
### login github
```
ssh -T git@github.com
```
### difference
```
git diff
```

### create a new repository on the command line example
```
echo "# gittest" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:"login"/"repository name".git
git push -u origin main
```

### or push an existing repository from the command line
```
git remote add origin git@github.com:"login"/"repository name".git
git branch -M main
git push -u origin main
```

### remove file (-r recursive for folders)
```
git rm <file>
```