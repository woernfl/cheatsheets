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

List all the labels of an images:

```bash
docker inspect $DOCKER_IMAGE_NAME | jq -r '.[0].Config.Labels'
```

### Get docker image informations

Check if an image already exist in a registry (will be 0 if the image exist or 1 if the image doesn't exist):

```bash
docker manifest inspect $IMAGE_NAME:$IMAGE_TAG > /dev/null ; echo $?
```

Get the sha of an image:

```bash
docker images --no-trunc --quiet $IMAGE_NAME:$IMAGE_TAG
```

List the ENTRYPOINT and CMD of an image:

```bash
docker inspect $IMAGE_NAME | jq '.[].Config.Entrypoint,.[].Config.Cmd'
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

### Clean up

Remove all unused images, containers, networks and volumes:

```bash
docker system prune -af --volumes
```

### Debug

Run a bash command without getting in the container:

```bash
docker run -it -u root --entrypoint /bin/bash $IMAGE_NAME -c "$BASH_COMMAND"
```

## ContainerD

### Basic actions

Pull an image:

```bash
ctr image pull $IMAGE_NAME
```
