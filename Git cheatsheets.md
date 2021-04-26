# Git codecademy


## Codecademy cheatsheet
### Checking the Status of a Git Repository

The `git status` command is used within a Git repository to its current status including the current commit, any modified files, and any new files not being tracked by Git.

The output of `git status` can vary widely, and it often includes helpful messages to direct the user to manage their repository. For example, `git status` will show the user the files they would commit by running `git commit` and the files they could commit by running `git add` before running `git commit`.

### Initializing a Git Repository

The `git init` command creates or initializes a new Git project, or _repository_. It creates a **.git** folder with all the tools and data necessary to maintain versions. This command only needs to be used once per project to complete the initial setup. For instance, the code block sets up the **home** folder as a new git repository.

```
$ cd /home$ git init
```

### Displaying Differences with Git Diff

The `git diff filename` command will display the differences between the working directory and the staging area in one specific file. Use `git diff filename` before adding new content to ensure that you are making the changes you expect.

```
$ git diff hello.txtdiff --git a/hello.txt b/hello.txtindex 557db03..980a0d5 100644--- a/hello.txt+++ b/hello.txt@@ -1 +1 @@-Hello World+Hello World!
```

### Showing Git Commit Logs

In Git, the `git log` command shows all of the commit logs for a project. The following is displayed for each commit:

-   A 40-character code, called a [SHA](https://en.wikipedia.org/wiki/Secure_Hash_Algorithms), that uniquely identifies the commit.
-   The commit author
-   The date and time of the commit
-   The commit message

This command is particularly useful when you need to refer back to an old version of your project. The unique SHA code allows you to identify a point in your program’s history that you would like to revert to.

```
$ git logcommit 9d63f80111447544c303e9f1776fa08593a87310Author: codecademy <exampleuser@codecademy.com>Date:   Wed Jan 13 18:55:53 2021 +0000     Added updates to the file commit 3ba6efbeece6ed530d85de5e313e52123fdf8cb4Author: codecademy <exampleuser@codecademy.com>Date:   Wed Jan 6 10:11:13 2021 -0400     Completed first line of dialogue
```

### Committing Your Code

The `git commit -m "log message here"` command creates a new commit containing:

-   The current contents of the staging area
-   A log message describing the changes to the repository

A commit is the last step in our Git workflow. A commit permanently stores changes from the staging area inside the repository. This command is almost always used in conjunction with the `git add` command as `git add` is used to add files to the staging area.

```
$ git commit -m "Added About section to README"[master 9d63f80] Added About section to README1 file changed, 10 insertions(+), 1 deletion(-)
```

### Git

Git is a command line software that keeps track of changes made to a project over time. Git works by recording the changes made to a project, storing those changes, then allowing a programmer to reference them as needed.

All Git commands follow the pattern `git <action>` and, in order to use Git for a project, a project must first be initialized using the `git init` command in the project’s root directory.

### Adding Changes to the Staging Area

The `git add filename` command is used to add the `filename` file to the staging area. After your changes have been staged, you can use the `git commit` command to permanently store your changes.

![After running git add scene-1.txt, the file is staged and ready to be committed.](https://static-assets.codecademy.com/Courses/Learn-Git/Review-Cards/git-diff.png)

### Git Project Workflow

A Git project has three parts:

-   A Working Directory: where files are created, edited, deleted, and organized
-   A Staging Area: where changes that are made to the working directory are listed
-   A Repository: where Git permanently stores changes as different versions of the project

The Git workflow consists of editing files in the working directory, adding files to the staging area, and saving changes to a Git repository.

## Codecademy backtracking

### Showing Latest Commit Log

In Git, the commit you are currently on is known as the `HEAD` commit.

The output of the `git show HEAD` command will display everything the `git log` command displays for the `HEAD` commit, plus all the file changes that were committed.

```
$ git show HEADcommit 735359632f3ca3fe572484a4ec3e0d7b0d9c8f2dAuthor: codecademy <exampleuser@codecademy.com>Date:   Wed Jul 6 10:20:58 2016 -0400     scene-5.txt diff --git a/scene-5.txt b/scene-5.txtindex b12dd97..5dd5d4e 100644--- a/scene-5.txt+++ b/scene-5.txt@@ -12,3 +12,7 @@ Hamlet:I will.  +Ghost:+My hour is almost come,+When I to sulphurous and tormenting flames+Must render up myself.\ No newline at end of file
```

### Git Reset Using SHA

In Git, the `git reset commit_SHA` command can be used to set `HEAD` to the `commit_SHA` commit. The `commit_SHA` argument is the first seven digits of a previous commit’s [SHA](https://en.wikipedia.org/wiki/Secure_Hash_Algorithms). In this example, the `HEAD` was reset to the commit made on `Wed Jan 6`.

You can use `git log` to see a record of previous commits and their SHA values.

```
$ git logcommit 9d63f80111447544c303e9f1776fa08593a87310Author: codecademy <exampleuser@codecademy.com>Date:   Wed Jan 13 18:55:53 2021 +0000     Added updates to the file commit 3ba6efbeece6ed530d85de5e313e52123fdf8cb4Author: codecademy <exampleuser@codecademy.com>Date:   Wed Jan 6 10:11:13 2021 -0400     Completed first line of dialogue $ git reset 3ba6efb
```

### Staging Multiple Files

In Git, the `git add filename_1 filename_2` command is used to add multiple files to the staging area at once.

You can use `git status` to check if you properly added your files to the staging area.

```
$ git add scene-5.txt scene-7.txt$ git statusOn branch masterChanges to be committed:  (use ""git reset HEAD <file>..."" to unstage)         modified:   scene-5.txt        modified:   scene-7.txt
```

### Remove File from Staging

In Git, the `git reset HEAD filename` command will remove `filename` from the staging area. Note that this command does _not_ discard file changes from the working directory. You might use this command if you’ve added a file to the staging area, but the file includes incorrect edits.

You can use the `git status` command to make sure your file was properly removed from the staging area.

```
$ git reset HEAD scene-3.txtUnstaged changes after reset:M       scene-3.txt
```

### Rolling Back to Last Commit

In Git, the `git checkout HEAD filename` command rolls back all changes that have been made to `filename` since the last commit. In other words, this command will change your working directory to look exactly as it did when you last made a commit.

You can use the `git diff` command to see if the rollback was successful. If `git diff` doesn’t output anything, this means your working directory matches your last commit.

```
$ git checkout HEAD scene-5.txt$ git diff$
```

## Codecademy branching
### The Master Branch

In Git, the main project is completed on the `master` branch. Making your first commit in a new git repository will automatically create a `master`branch. Create new branches from the `master` branch to develop new features for a project. These branches can be merged into `master` at a later time to incorporate the new features. You can use `git branch` to check what branch you’re on.

```
$ git initInitialized empty Git repository in /home/ccuser/new-project/.git/$ echo "Hello World!" >> hello.txt$ git add hello.txt $ git commit -m 'initial commit'[master (root-commit) bb0e565] initial commit 1 file changed, 1 insertion(+) create mode 100644 hello.txt$ git branch* master
```

### Creating a New Branch

In Git, the `git branch branch-name` command is used to create a new branch called `branch-name`. Branches should be named something that describes the purpose of the branch.

Note that branch names can’t contain whitespace: `new-feature` and `new_feature` are valid branch names, but `new feature` is not.

![Run git branch new-feature to make a new branch called new-feature](https://static-assets.codecademy.com/Courses/Learn-Git/Review-Cards/learn-git-create-branch.png)

### Viewing the Current Branch

In Git, the `git branch` command will display all of the branches. The current branch will display `*` before its name.

![git branch displays the two branches "fencing" and "master".  "master" is preceded by an asterisk.](https://static-assets.codecademy.com/Courses/Learn-Git/Review-Cards/learn-git-branch.png)

### Merge Conflicts

In Git, a merge conflict occurs when the same file is changed on the current branch and the branch that is being merged. An error will appear displaying: `CONFLICT (content): Merge conflict in [filename]`.

Git will automatically edit the file with the conflict to show where the conflict is. The current branch’s text will be between `<<<<<<< HEAD` and `=======`. The text from the branch that is being merged into the current branch will be between `=======` and `>>>>>>> branch-name`

To resolve a merge conflict, edit the file with the conflict, decide which parts of each branch’s edits should be kept, then add and commit the file.

```
PETE PAN<<<<<<< HEADAddress: No 31 Kensington Hill Park, London, England=======Address: 113 Gloucester Rd Patchway, Bristol, England>>>>>>> resume-edits-------------------
```

### Deleting a Branch

In Git, the `git branch -d branch_name` command is used to delete the `branch_name` branch. It’s good practice to delete a branch after it has been merged into the `master` branch.

![git branch -d new-feature will delete the branch with the name "new-feature"](https://static-assets.codecademy.com/Courses/Learn-Git/Review-Cards/learn-git-remove-branch.png)

### Merging Branches

In Git, the `git merge branch-name` command will add the changes from `branch-name` into the current branch. Use this command when you have finished building a feature in a separate branch and want to bring those changes into your current branch.

![git merge resume-edits brings the changes from resume.txt into the master branch](https://static-assets.codecademy.com/Courses/Learn-Git/Review-Cards/learn-git-merge.png)

## Codecademy Teamwork
### List the Git Remotes

In Git, the `git-remote -v` command returns a list of remote repositories that the current project is tied to.

-   Git lists the name of the remote repository as well as its locations.
-   Git automatically names this remote `origin`, because it refers to the remote repository of origin. However, it is possible to safely change its name.
-   The remote is listed twice: once for `(fetch)` and once for `(push)`.

```
$ git remote -vorigin  /home/ccuser/workspace/curriculum/science-quizzes/ (fetch)origin  /home/ccuser/workspace/curriculum/science-quizzes/ (push)
```

### Git Collaboration Workflow

A common Git collaboration workflow is:

1.  Fetch and merge changes from the remote
2.  Create a branch to work on a new project feature
3.  Develop the feature on a branch and commit the work
4.  Fetch and merge from the remote again (in case new commits were made)
5.  Push branch up to the remote for review

Steps 1 and 4 are a safeguard against merge conflicts, which occur when two branches contain file changes that cannot be merged with the git merge command.

### Pushing Branch Changes

In Git, the `git push origin branch-name` command pushes the branch, and all committed changes, to the remote. This branch can now be reviewed by collaborators.

In the example, the current branch containing the committed changes is called `bio-questions`.

```
$ git push origin bio-questionsCounting objects: 3, done.Delta compression using up to 16 threads.Compressing objects: 100% (3/3), done.Writing objects: 100% (3/3), 392 bytes | 0 bytes/s, done.Total 3 (delta 1), reused 0 (delta 0)To /home/ccuser/workspace/curriculum-a/science-quizzes * [new branch]      bio-questions -> bio-questions
```

### Cloning a Remote Repository

In Git, the `git clone remote_location clone_name` command creates a local copy of a remote repository.

-   `remote_location` tells Git where to find the remote repository and can be a filepath or web address.
-   `clone_name` is the name of the directory where the remote repository’s contents will be copied.

In the example, `my-quizzes` is a new directory created as a local copy of the `science-quizzes` Git project. Committing changes to `my-quizzes` will not impact `science-quizzes`.

```
$ lsscience-quizzes $ git clone science-quizzes/ my-quizzesCloning into 'my-quizzes'...done. $ lsmy-quizzes  science-quizzes
```

### Fetching Remote Origin Changes

In Git, the `git fetch` command downloads objects from the `origin` remote repository. The changes, however, are not merged into the current `branch-name` branch. Instead, they are stored in the `origin/branch-name` branch, waiting to be merged.

In the provided example, using the [`git branch -a` command](https://git-scm.com/docs/git-branch#Documentation/git-branch.txt--a) to see the existing branches, we can see that fetched data has been stored in a new `origin/master` branch.

```
$ git branch -a* master $ git fetchremote: Counting objects: 5, done.remote: Compressing objects: 100% (5/5), done.remote: Total 5 (delta 1), reused 0 (delta 0)Unpacking objects: 100% (5/5), done.From /home/ccuser/workspace/curriculum-a/science-quizzes * [new branch]      master     -> origin/master $ git branch -a* master  remotes/origin/master
```

### Merging Fetched Changes

In Git, the `git merge origin/branch-name` command will merge fetched changes, stored in `origin/branch-name` to the current `branch-name` branch.

In the example, `master` is the name of the branch being merged.

```
$ git merge origin/masterUpdating 2fd7d9b..3a29454Fast-forward biology.txt | 4 ++++ 1 file changed, 4 insertions(+) create mode 100644 biology.txt
```

### Git Remote

A _remote_ is a shared Git repository that allows multiple collaborators to work on the same Git project from different locations. Collaborators work on the project independently and merge changes together when they are ready to do so.