---
layout: default
title: SSH Key Generation
parent: Home
---

# SSH Key Generation

## Basic actions

Generate new SSH Keys:

```bash
ssh-keygen -t rsa -C "hello@onmyown.io"
```

Press `Enter` to accept default location and then type your paraphrase twice.

2 new files were created in the `~/.ssh` folder, the `id_rsa` and `id_rsa.pub` ones.
