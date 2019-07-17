---
layout: default
title: Docker
parent: Home
---

# Docker Cheatsheet

## Basic actions

Push multiple docker images:

```bash
for t in $(docker images --format "&#91;&#91;.Repository&#93;&#93;:&#91;&#91;.Tag&#93;&#93;" | grep "$IMAGE_NAME"); do docker push "${t}"; done
```
