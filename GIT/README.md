Practice with Git

```
sudo yum update
sudo yum install git
```

Check git version 

``` 
git version

```
git commit used to start new repo

```
git init

git config --global user.name "Your Github Name"
git config --global user.email "i@example.com"

```

Create file and make some changes

```
git stash
git stash pop
git stash list
git stash drop
```
Use for save the changes without committing them
This command restores the most recently stashed files.
This command lists all stashed changesets.
This command discards the most recently stashed changeset.

```
git diff
```
This command shows the file differences which are not yet staged.

```
git diff --staged
```
This command shows the differences between the files in the staging area and the latest version present.

```
git reset [file]
git reset [commit]
git reset -hard [commit]
```

Unstages the file, but it preserves the file contents.
This command undoes all the commits after the specified commit and preserves the changes locally.
This command discards all history and goes back to the specified commit.

```
git status
```

This command lists all the files that have to be committed.


```
git rm [file]
```

This command deletes the file from your working directory and stages the deletion.

```
git log
git log -follow [file]

```
This command is used to list the version history for the current branch.
This command lists version history for a file, including the renaming of files also.


```
git show

```

This command shows the metadata and content changes of the specified commit.


```
git tag [commitID]

```
This command is used to give tags to the specified commit.

```
git branch
git branch [branch name]
git branch -d [branch name]

```
This command lists all the local branches in the current repository.
This command creates a new branch.
This command deletes the feature branch.


```
git checkout [branch name]
git checkout -b [branch name]

```

This command is used to switch from one branch to another.
This command creates a new branch and also switches to it.

```
git merge
git merge [branch name]

```

This command merges the specified branch’s history into the current branch.

```
git remote

```

Usage: git remote add [variable name] [Remote Server Link]

This command is used to connect your local repository to the remote server.

```
git push
git push [variable name] [[branch name]
git push -all [variable name]
git push [variable name] :[branch name]

```

This command sends the committed changes of master branch to your remote repository.
This command sends the branch commits to your remote repository.
This command pushes all branches to your remote repository.
This command deletes a branch on your remote repository.

