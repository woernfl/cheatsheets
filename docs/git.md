# Git

## Basic actions

Clone a remote repo:

```bash
git clone $REMOTE_REPO_URL
```

Get the status of your repo:

```bash
git status
```

Get the status of your repo listing all the files:

```bash
git status -u
```

Stage a change:

```bash
git add $FILE_PATH
```

Commit a change and sign it:

```bash
git commit -s -m "$COMMIT_MESSAGE"
```

Push your change to a remote repo:

```bash
git push -u origin $BRANCH_NAME
```

Create a branch:

```bash
git checkout -b $BRANCH_NAME
```

## Check differences

Check all changes since last commit:

```bash
git diff --color-words
```

Check changes since last commit for a specific file:

```bash
git diff --color-words HEAD $PATH_TO_FILE
```

Check changes between two commits:

```bash
git diff --color-words $COMMIT_NUMBER $COMMIT_NUMBER
```

Check changes between two commits for a specific file:

```bash
git diff --color-words $COMMIT_NUMBER $COMMIT_NUMBER $PATH_TO_FILE
```

Check changes between two branches:

```bash
git diff --color-words $BRANCH_NAME $BRANCH_NAME
```

Check changes between two branches for a specific file:

```bash
git diff --color-words $BRANCH_NAME $BRANCH_NAME $PATH_TO_FILE
```

Check stages changes:

```bash
git diff --staged
```

## Commit history managment

Check commit history:

```bash
git log --oneline --graph --color
```

Add file change to the last commit:

```bash
git commit --am -s -m "$COMMIT_MESSAGE"
```

## Branch managment

Delete local branche:

```bash
git branch -d $BRANCH_NAME
```

Rebase a base branch in current branch:

```bash
git rebase $BASE_BRANCH
```

Rename a branch:

```bash
git branch -m $BRANCH_OLD_NAME $BRANCH_NEW_NAME
git push origin :$BRANCH_OLD_NAME $BRANCH_NEW_NAME
git push origin -u $BRANCH_NEW_NAME
```

Copy a file from a branch to the current one:

```bash
git checkout $BRANCH_TO_COPY_FROM $PATH_OF_THE_FILE_TO_COPY
```

## Config managment

Set username for the repo:

```bash
git config user.name "$NAME"
```

Set username globally:

```bash
git config --global user.name "$NAME"
```

Set email for the repo:

```bash
git config user.email "$EMAIL"
```

Set email globally:

```bash
git config --global user.email "$EMAIL"
```

Enable credential helper to not have to retype your password each time you want to do something:

```
git config credential.helper store 
```

## Tips and tricks

I committed and immediately realized I need to make one small change:

```bash
# make your change
git add . # or add individual files
git commit --amend --no-edit
```

I accidentally committed something to master that should have been on a new branch:

```bash
# create a new branch from the current state of master
git branch some-new-branch-name
# remove the last commit from the master branch
git reset HEAD~ --hard
git checkout some-new-branch-name
# your commit lives in this branch now
```

I accidentally committed to the wrong branch:

```bash
# undo the last commit, but leave the changes available
git reset HEAD~ --soft
git stash
# move to the correct branch
git checkout name-of-the-correct-branch
git stash pop
git add . # or add individual files
git commit -m "your message here";
# now your changes are on the correct branch
```

I need to undo a commit from like 5 commits ago:

```bash
# find the commit you need to undo
git log
# use the arrow keys to scroll up and down in history
# once you've found your commit, save the hash
git revert [saved hash]
# git will create a new commit that undoes that commit
# follow prompts to edit the commit message
# or just save and commit
```

I need to undo my changes to a file:

```bash
# find a hash for a commit before the file was changed
git log
# use the arrow keys to scroll up and down in history
# once you've found your commit, save the hash
git checkout [saved hash] -- path/to/file
# the old version of the file will be in your index
git commit -m "Wow, you don't have to copy-paste to undo"
```

Thanks to Frumusanu Razvan for this [tricks](https://medium.com/faun/stop-headaches-from-git-3829210d2a31)
