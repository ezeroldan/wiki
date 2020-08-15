# Git & Github

## Instalar
```BASH
sudo apt update -y && sudo apt upgrade -y
sudo apt install -y git
```

```BASH
git config --global user.name "Ezequiel Roldan"
git config --global user.email "ezeroldan@gmail.com"
git config --global color.ui auto
```

## Comandos

`git commit -m "[descriptive message]"`
Records file snapshots permanently in version history  

`git pull`
Downloads bookmark history and incorporates changes  

`git push[alias] [branch]`
Uploads all local branch commits to GitHub  

`git init[project-name]`
Creates a new local repository with the specified name

`git clone[url]`
Downloads a project and its entire version history

`git status` 
Lists all new or modified files to be commited

`git diff`
Shows file differences not yet staged

`git add . / *.php`
Snapshots the file in preparation for versioning

`git diff--staged`  
Shows file differences between staging and the last file version

`git reset[file]`
Unstages the file, but preserve its contents

`git branch`
Lists all local branches in the current repository

`git branch[branch-name]`
Creates a new branch  

`git checkout[branch-name] master`
Switches to the specified branch and updates the working directory  

`git merge[branch]`
Combines the specified branch’s history into the current branch  

`git branch-d [branch-name]`
Deletes the specified branch  

`git rm[file]`
Deletes the file from the working directory and stages the deletion  

`git rm--cached [file]`
Removes the file from version control but preserves the file locally  

`git mv[file-original] [file-renamed]`
Changes the file name and prepares it for commit  

`git stash`
Temporarily stores all modified tracked files  

`git stash pop`
Restores the most recently stashed files  

`git stash list`
Lists all stashed changesets  

`git stash drop`
Discards the most recently stashed changeset  

`git log`
Lists version history for the current branch  

`git log--follow [file]`
Lists version history for a file, including renames  

`git diff[first-branch]...[second-branch]`
Shows content differences between two branches  

`git show[commit]`
Outputs metadata and content changes of the specified commit  

`git reset[commit]`
Undoes all commits afer [commit], preserving changes locally  

`git reset--hard [commit]`
Discards all history and changes back to the specified commit

`git fetch[bookmark]`
Downloads all history from the repository bookmark

`git merge[bookmark]/[branch]`
Combines bookmark’s branch into current local branch  

`git remote -v`

