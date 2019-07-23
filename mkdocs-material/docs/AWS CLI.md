---
layout: default
title: AWS CLI
parent: Home
---

# AWS CLI Cheatsheet

## Basic actions

Enable autocompletion:

```bash
echo "complete -C '$(which aws_completer)' aws" >> ~/.bashrc
```

Create profil config:

```bash
aws configure --profile $PROFILE_NAME
```
