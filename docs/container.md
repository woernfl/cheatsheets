# Container

## Docker

### Basic actions

Log in to a Docker registry:

```bash
docker login $REGISTRY_URL
```

Exec into a container:

```bash
docker exec -it $CONTAINER_NAME /bin/bash
```

Push multiple docker images:

```bash
for t in $(docker images --format "{{.Repository}}:{{.Tag}} " | grep "$IMAGE_NAME"); do docker push "${t}"; done
```
### Build specific

Change the build log output:

```bash
export BUILDKIT_PROGRESS=plain
```

Automatically add some git lables:

```bash
export BUILDX_GIT_LABELS=full
```

## ContainerD

### Basic actions

Pull an image:

```bash
ctr image pull $IMAGE_NAME
```
