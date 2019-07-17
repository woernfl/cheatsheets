---
layout: default
title: Docker
parent: Home
---

# Docker Cheatsheet

## Basic actions

Push multiple docker images:

```bash
for t in $(docker images --format "{{&#46;Repository}}:{{&#46;Tag}}" | grep "$IMAGE_NAME"); do docker push "${t}"; done
```
