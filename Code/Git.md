# Git Commits
## Basics
1. Initialize git
``` 
	git init 
``` 
2. Add files 
``` 
	git add .
```
3. Commit Changes 
``` 
	git commit -m "message" 
```
4. Push Changes 
``` 
	git push -u origin main
```
5. Status of changes 
```
	git status
```

## File movement 
1. Remove File 
``` 
	git rm file.txt 
```
``` 
	git rm --cached file.txt 
``` 
for deleting only on local
``` 
	git rm *.txt 
```
2. Move File 
``` 
	git mv file.txt Data/Text_Files
```

## Branches
1. Create New Branch 
``` 
	git branch new-branch-name
```
2. Go to New Branch
``` 
	git checkout new-branch-name
```
3. Push to branch
``` 
	git push -u origin new-branch-name
```
4. Switch branches
``` 
	git checkout current-branch 
```

```
	git checkout new-branch
```
```
	git switch new-branch
```
	
	
5. Clone specific branch to local
```
	git clone -b branch-name --single-branch repo-name
```

6. List local branches
 ```
	 git branch
 ```
8. List remote branches
 ```
	 git branch -r
 ```
10. List all branches 
```
	git branch -a
```
	
## Merging
1. Merging specific file from one branch to another
```
	git checkout source-branch <path>
```

## Setting up [[SSH]]
1. Generate SSH key
``` 
	cd ~
	ssh-keygen -t rsa 
```
2. Associate ssh key with remote repo : go to settings, click add ssh key, copy contents of `~/.ssh/id_rsa.pub` into 'Key'
3. Set remote url to a form that supports SSH
```git+ssh://git@github.com/username/reponame.git```

__To see repo URL__
```
git remote show origin
```
__To change current URL__
```
git remote set-url origin git+ssh://git@github.com/username/reponame.git
```

## Deleting Branch
1. Deleting local branch
```
git branch -d <branch-name
```

2. Deleting remote branch 
```
git push origin --delete <branch-name>
```git remote 
