# Git Commits
## Basics
1. Initialize git
``` git init ```
2. Add files 
``` git add . ```
3. Commit Changes 
``` git commit -m "message" ```
4. Push Changes 
``` git push -u origin main```
5. Status of changes 
```git status```

## File movement 
1. Remove File 
``` git rm file.txt ```
``` git rm --cached file.txt ``` for deleting only on local
``` git rm *.txt ```
2. Move File 
``` git mv file.txt Data/Text_Files```

## Branches
1. Create New Branch 
``` git branch new-branch-name```
2. Go to New Branch
``` git checkout new-branch-name```
3. Push to branch
``` git push -u origin new-branch-name```
4. Switch branches
``` git checkout current-branch ```
	```git checkout new-branch	```
	or
	```git switch new-branch```
	
5. Clone specific branch to local
```git clone -b branch-name --single-branch repo-name```

6. List local branches ```git branch```
7. List remote branches ```git branch -r```
8. List all branches ```git branch -a```
	
## Merging
1. Merging specific file from one branch to another
```git checkout source-branch <path>```

	
	