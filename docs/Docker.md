# Docker

## Basic actions

Push multiple docker images:

```bash
for t in $(docker images --format "{{.Repository}}:{{.Tag}} " | grep "$IMAGE_NAME"); do docker push "${t}"; done
```

