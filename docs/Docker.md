---
layout: default
title: Docker
parent: Home
---

# Docker Cheatsheet

## Basic actions

Push multiple docker images:

```bash
{% raw %}
  for t in $(docker images --format "{{.Repository}}:{{{.Tag}}} " | grep "$IMAGE_NAME"); do docker push "${t}"; done
{% endraw %}
```
