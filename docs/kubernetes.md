# Kubernetes

## Basic actions

Get more info about pods:

```bash
kubectl get po -o wide
```

Get all main ressources:

```bash
kubectl get all --all-namespaces
```

Get main ressources for a specific namespace:

```bash
kubectl get all -n $NAMESPACE
```

Get really all the ressources of a specific namespace:

```bash
kubectl api-resources --verbs=list --namespaced -o name | xargs -n 1 kubectl get --show-kind --ignore-not-found -l app=myapp -n $NAMESPACE
```

## Deployment managment

Restart a rollout:

```bash
kubectl rollout restart
```

Get the rollout status:

```bash
kubectl rollout status -w
```

Get the rollouts history:

```bash
kubectl rollout history
```

Rollback a change:

```bash
kubectl rollout undo
```

## Secret managment

Create a secret from literal:

```bash
kubectl create secret generic $SECRET_NAME --from-literal=$KEY=$SECRET
```

Create a secret from a file:

```bash
kubectl create secret generic $SECRET_NAME --from-file=$KEY=$PATH_TO_FILE
```

Copy a secret froma namespace to an other:

```bash
kubectl get secrets -o json --namespace $NAMESPACE_OLD | jq '.items[].metadata.namespace = "$NAMESPACE_NEW"' | kubectl create-f  -
```

## Pod managment

```bash
kubectl get pods --watch --output-watch-events
```

Get the list of pod with their CPU consumpsion:

```bash
kubectl top pods -A | sort --reverse --key 3 --numeric
```

Get the list of pod with their memory consumpsion:

```bash
kubectl top pods -A | sort --reverse --key 4 --numeric
```

Sorting the list of pod by the number of restarts:

```bash
kubectl get pods --sort-by=.status.containerStatuses[0].restartCount
```

Print limits and requests of each pod:

```bash
kubectl get pods -n $NAMESPACE -o=custom-columns='NAME:spec.containers[*].name,MEMREQ:spec.containers[*].resources.requests.memory,MEMLIM:spec.containers[*].resources.limits.memory,CPUREQ:spec.containers[*].resources.requests.cpu,CPULIM:spec.containers[*].resources.limits.cpu'
```

Delete all the pods of a given namespace:

```bash
kubectl -n $NAMESPACE delete --all pods
```

## Node managment

Get the list of nodes and their memory size:

```bash
kubectl get no -o json | jq -r '.items | sort_by(.status.capacity.memory)[]|[.metadata.name,.status.capacity.memory]| @tsv'
```

Getting the list of nodes and the number of pods running on them

```bash
kubectl get po -o json --all-namespaces | jq '.items | group_by(.spec.nodeName) | map({"nodeName": .[0].spec.nodeName, "count": length}) | sort_by(.count)'
```

List the node taints:

```bash
kubectl get nodes -o custom-columns=NAME:.metadata.name,TAINTS:.spec.taints
```

List the nodes with there labels:

```bash
kubectl get nodes --show-labels
```

## Job managment

Create a job from a cronjob

```bash
kubectl create job --from=cronjobs.batch/$CRONJOB_NAME $JOB_NAME 
```

## Kustomize

To generate the manifest before applying it:

```bash
kubectl apply -k . --dry-run=client -o yaml > tmp.yaml
```

## To debug

Follow logs of multiple pods:

```bash
kubectl logs -f -n $NAMESPACE -l app=myapp --timestamps
```

Getting logs of the “previous” container:

```bash
kubectl -n $NAMESPACE logs $POD_NAME --previous
```

Get all events of what happened:

```bash
kubectl -n $NAMESPACE get events --sort-by='{.lastTimestamp}' | tail
```

Connect to a pod from your local workstation:

```bash
kubectl port-forward -n $NAMESPACE $POD_NAME $LOCAL_PORT:$POD_PORT
```

Connect to a service from your local workstation:

```bash
kubectl port-forward -n $NAMESPACE --address 0.0.0.0 service/$SERVICE_NAME $LOCAL_PORT:$POD_PORT
```

Boot a centos pod in Kubernetes:

```bash
kubectl -n $NAMESPACE run tmp-shell --rm -i --tty --image centos -- /bin/bash
```

Start shell in a running container:

```bash
kubectl -n $NAMESPACE exec -it $POD_NAME -- /bin/bash
```

Get the value of a Kubernetes secret:

```bash
kubectl -n $NAMESPACE get secret $SECRET_NAME -o jsonpath="{.data.$SECRET_PATH}" | base64 --decode
kubectl -n $NAMESPACE get secret $SECRET_NAME -o 'go-template={{index .data "$SECRET_PATH"}}' | base64 --decode
```

Force delete a namespace:

```bash
kubectl get ns $NAMESPACE -o json | jq '.spec.finalizers = []'| kubectl replace --raw "/api/v1/namespaces/$NAMESPACE/finalize" -f -
```

## kubectl plugins

### krew

krew is available [here](https://krew.sigs.k8s.io/docs/user-guide/setup/install/).

It will need to be updated a first time before you can use it.

```bash
kubectl krew update
```

### deprecations

Install `deprecations`:

```bash
kubectl krew install deprecations
```

Use `deprecations`:

```bash
kubectl deprecations
```

### ktop

Install `ktop`:

```bash
kubectl krew install ktop
```

Use `ktop`:

```bash
kubectl ktop
```

### lineage

Install `lineage`:

```bash
kubectl krew install lineage
```

List dependent resources:

```bash
kubectl lineage $RESSOURCE_TYPE $RESSOURCE_NAME -o=wide
```

List dependencies resource:

```bash
kubectl lineage $RESSOURCE_TYPE $RESSOURCE_NAME -D -o=wide
```

Display Helm release resources:

```bash
kubectl lineage helm $HELM_RELEASE_NAME
```

### ns

Install `ns`:

```bash
kubectl krew install ns
```

Use `ns`:

```bash
kubectl ns $NAMESPACE
```

It is recommended to add [fzf](https://github.com/junegunn/fzf)

### outdated

Install `outdated`:

```bash
kubectl krew install outdated
```

Use `outdated`:

```bash
kubectl outdated
```

### pod-inspect

Install `pod-inspect`:

```bash
kubectl krew install pod-inspect
```

Use `pod-inspect`:

```bash
kubectl pod-inspect $POD_NAME
```

### resource-capacity

Install `resource-capacity`:

```bash
kubectl krew install resource-capacity
```

List node request and limits:

```bash
kubectl resource-capacity
```

List node request, limits and usage (require the metrics-server):

```bash
kubectl resource-capacity --util
```

List pod request and limits:

```bash
kubectl resource-capacity --pods
```

List node and pods request, limits and usage (require the metrics-server):

```bash
kubectl resource-capacity --pods --util
```

List node available resources:

```bash
kubectl resource-capacity --available
```

### sick-pods

Install `sick-pods`:

```bash
kubectl krew install sick-pods
```

Use `sick-pods`:

```bash
kubectl sick-pods $POD_NAME
```

### topology

Install `topology`:

```bash
kubectl krew install topology
```

Get the topology for the nodes:

```bash
kubectl topology node
```

Get the topology for the pods:

```bash
kubectl topology pod
```

### unused-volumes

Install `unused-volumes`:

```bash
kubectl krew install unused-volumes
```

Use `unused-volumes`:

```bash
kubectl unused-volumes
```

### Quick install

```bash
kubectl krew install deprecations
kubectl krew install ktop
kubectl krew install lineage
kubectl krew install ns
kubectl krew install outdated
kubectl krew install pod-inspect
kubectl krew install resource-capacity
kubectl krew install sick-pods
kubectl krew install topology
kubectl krew install unused-volumes
```

## Bonus

Install autocompletion:

```bash
echo "source <(kubectl completion bash)" >> ~/.bashrc
```
