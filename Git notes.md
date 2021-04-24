# Git 
## Workflow
> Working directory - where all changes are made 
> Staging area- where files are kept after "git add", before commit
> Repository- where commits are stored, final porduct

- git init -- initializes git project and enables all of the tool
```git init filename```
- git status -- shows any changed files, can be modified
```git status```
git add -- adds file to the staging area before committing the file
```git add filename```
git diff -- detects the differences between the working directory and the staging area
```git diff filename```
git commit -- stores file in the repository. Have to include message of 50 characters or less as a description.
```git commit -m "Some message" ```
git log -- View a history of commits, displays using a unique 40 character code called a SHA
```git log```
``` $ git commit -m "Added lines"
[master (root-commit) 4d154a5] Added lines
 1 file changed, 3 insertions(+)
 create mode 100644 scene-1.txt
$ ^C
$ git log
commit 4d154a5c8e0ef73cdb83138c9512087990963df7
Author: codecademy <ccuser@codecademy.com>
Date:   Sat Apr 24 02:45:13 2021 +0000 ```