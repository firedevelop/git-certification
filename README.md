# git gitHub certification

# Cheat Sheet
https://education.github.com/git-cheat-sheet-education.pdf
#  Installation
https://gist.github.com/Klerith/90a612344dc2d4e4455ea810fdacbe69

# Update/upgrade git on mac
brew install git
brew upgrade git


## Free eBook
https://git-scm.com/book/en/v2 

# Commands
git version
git --version

git help

- / abreviation
-- // full words
### create local repository
1º create the folder .git
2º inicializate repository
```
git init
```

### in color red the files peding to commint
```
git status
```

![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/1.png?raw=true)


git log

### add: send files to stage
git add .

### exclude the file exclude.txt
git reset exclude.txt
// Now is missing the file

```html
git status
```

### comit: like snapshot
git commit -m "first commit"

### restore file
git checkout -- .

### U
means unt rack, when git no le da seguimiento a ese archivo  

### brach status
status:
```git status  ```
show actual branch
```git status --short --branch```
or
```git status -s -b```
or
```git branch```


### rename branch
-m means modify, branch with the name master to main
```git branch -m master main ```

### reset (don't upload changes of one file)
1º track the files 
``` git add . ```
2º after track, untrack only one file
``` git reset 1.txt ```
3º git commit -m "."
4ª git push
5º the file 1.txt doesn't change on github


### commit by extension (path needed)
git add js/*.js

### .gitkeep (keep folder tracking when is empty)
myUploads/.gitkeep

### add whole folder
``` git add css/ ```

#### create folder and file one line
mkdir myFolder && myFolder/myFile.txt

### resume status
``` git status --short ```

# ALIAS
## Method 1 (direct command)
```git config --global alias.s status --short --branch```

## CREATE ALIAS ELEGANTH LOG
install extension like Github Lab or write the next command:
```bash
git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
```

### i.e for short using the key 's'
``` git config --global alias.s status --short ```

### EDIT alias
git config --global -e
## CREATE ALIAS SHORTS
in [alias] area write the next to see the actual branch info
```s = status --short --branch```

## DIFF
git diff myFile.txt

### see stages files
git diff --staged

### COMMIT: change last commit name
```git commit --amend -m "." ```
### COMMIT: FULL EDITION
```git commit --amend```

### All tree
 This flag stages all of the tracked changes in the working tree.
```git commit -A```

### COMMIT: Add new changes to the last commit
HEAD  last commit hash
HEAD^  last commit
HEAD^2 past last commit
soft keep changes, is not destructive
``` git reset --soft HEAD^ ```
using hash
``` git reset --soft 111222 ```


### FIX WARNING CRLF
git config core.autocrlf true

### TIME MACHINE - ALL history
1º Find your hash
``` git reflog ```

2º restore
``` git reset --hard 111222 ```

### .gitignore
1º git add .gitignore
2º add folders like dist/ or *.log


### BRANCH - MERGE
create branch
```git branch rama-villanos```

access to branch and start to work on branch
``` git checkout rama-villanos```

#### commands to play
git add .
git commit -m "villanos.md: added"
git commit -m "villanos.md: added flash"

#### go back to master branch
git branch
git checkout master

#### go back to branch
git branch
git checkout rama-villanos

#### merge rama-villanos with maste
go to master branch
```git checkout master```
``` git merge rama-villanos ```
Fast-forward means the merge works well.
Now remove old branch if you wish. -f force fully deletion and some possible commits don't finished.
```git branch -d rama-villanos -f```

### BRANCH
create branch and go to the branch in one line
```git checkout -b rama-villanos```

# REBASE
## Normal
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/2.png?raw=true)
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/3.png?raw=true)
## Interactive
```git rebase -i HEAD~3```
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/4.png?raw=true)
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/5.png?raw=true)
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/6.png?raw=true)
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/7.png?raw=true)

## rebase example
```git branch```
```git rebase master```

# REBASE - SQUASH - merge commits
the number 4 indicate how many commits will be merged
```git rebase -i HEAD~4```
replace the last 2 hash by s and p like this:
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/9.png?raw=true)

save data in vi with :wq

# REBASE - How restore only one file after commit 2 files
start
```git add .```
add some text changes to files a.txt and b.txt
After commit:
```git commit -am "updates"```
now restore only one file
```git checkout -- a.txt```

change pickup to edit
```git rebase -i HEAD~```
```git rebase --continue```


# GITHUB - config pull method
```git config pull.rebase false ```   # merge(the default strategy)
```git config pull.rebase true```     # rebase
```git config pull.ff only```         # fast-forward only

We use fast-foward. And this method abort the pull when there are conflicts.
You can change the method usgin:
````git config --global -e````

# GITHUB - clone
git clone https://github.com/firedevelop/git-02.git


# GITHUB
know your repository remote:
```git remote -v```
```git push -u origin master```
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/10.png?raw=true)


first time, we need to indicate the origin
```git push -u origin main```
or
```git push -u origin master```
nest times:
```git push```

# GITHUB - conflicts LOCAL V.S. REMOTE
QUICK SOLUTION: 
```git config --global pull.rebase true```
or edit:
```git config --global -e```

Actualy we have our local github configured like:
```git config pull.ff only```
config to see the conflicts in visual studio
```git config pull.rebase true```
now push
```git push```

if doesn't work, try to commit your pending unstaged changes:
```git add .```
```git commit -am "updates"```
now try again
```git push```

finally you need to see:
```git log```
your local master branch and the remote origin/master on the same hash:
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/11.png?raw=true)

Finally we change the method to rebase, in order to fix the conflicts on Visual Studio UI. Setup rebase pull globally:
```git config --global pull.rebase true```
Rebase locally before push
```git rebase --continue```
```git push```


# GITHUB - PULL REQUEST
like a merge, but our branch with master and check conflicts with details.
Pull request allow you verify the changes before merge to main

# MARKDOWN
https://www.markdowntutorial.com/
🖥

# FETCH 
see changes before pull:
```git fetch```

Now you can see you local branch is HEAD -> master:
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/12.png?raw=true)

and the remote is origin/master.
Read the commits comments and if you happy with then try to pull:
```git pull```

After that, your local will be update with remote:
![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/13.png?raw=true)


# TAG
create tag
```git tag -a v0.0.1 -m "version Alpha"```
push tag to your repository
```git push --tags```

# exercise 09
create new branch on local
```git checkout -b rama-villanos```

create new branch on github
git push --set-upstream origin rama-villanos



