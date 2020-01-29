# Docker

## Basic actions

Log in to a Docker registry:

```bash
docker login $REGISTRY_URL
```

Push multiple docker images:

```bash
for t in $(docker images --format "{{.Repository}}:{{.Tag}} " | grep "$IMAGE_NAME"); do docker push "${t}"; done
```

