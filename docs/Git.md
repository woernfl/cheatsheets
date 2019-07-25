# Git Cheatsheet

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

## More advance actions

Check commit history:

```bash
git log --oneline --graph --color
```

Add file change to the last commit:

```bash
git commit --am -s -m "$COMMIT_MESSAGE"
```

Rebase a base branch in current branch:

```bash
git rebase $BASE_BRANCH
```

## Branch managment

Rename a branch:

```bash
git branch -m $BRANCH_OLD_NAME $BRANCH_NEW_NAME
git push origin :$BRANCH_OLD_NAME $BRANCH_NEW_NAME
git push origin -u $BRANCH_NEW_NAME
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
