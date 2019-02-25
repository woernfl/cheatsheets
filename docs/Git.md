---
layout: default
title: Git
parent: Home
---

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

Check commit history:

```bash
git log --oneline --graph --color
```

Add file change to the last commit:

```bash
git commit --am -s -m "$COMMIT_MESSAGE"
```

## Bonus

Enable credential helper to not have to retype your password each time you want to do something:

```
git config credential.helper store 
```
