---
layout: default
title: Git
parent: Home
---

# Git Cheatsheet

## Basic actions

Get the status of your repo:

```bash
git status
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