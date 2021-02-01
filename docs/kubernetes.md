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

## Node managment

Get the list of nodes and their memory size:

```bash
kubectl get no -o json | jq -r '.items | sort_by(.status.capacity.memory)[]|[.metadata.name,.status.capacity.memory]| @tsv'
```

Getting the list of nodes and the number of pods running on them

```bash
kubectl get po -o json --all-namespaces | jq '.items | group_by(.spec.nodeName) | map({"nodeName": .[0].spec.nodeName, "count": length}) | sort_by(.count)'
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
kubectl get events -n $NAMESPACE
```

Connect to a pod from your local workstation:

```bash
kubectl port-forward --namespace $NAMESPACE $POD_NAME $LOCAL_PORT:$POD_PORT
```

Connect to a service from your local workstation:

```bash
kubectl port-forward --namespace $NAMESPACE --address 0.0.0.0 service/$SERVICE_NAME $LOCAL_PORT:$POD_PORT
```

Boot a centos pod in Kubernetes:

```bash
kubectl run centos --stdin --tty --image=centos:7
kubectl run tmp-shell --rm -i --tty --image centos -- /bin/bash
```

Start shell in a running container:

```bash
kubectl -n $NAMESPACE exec -it $POD_NAME -- /bin/bash
```

Get the value of a Kubernetes secret:

```bash
kubectl -n $NAMESPACE get secret $SECRET_NAME -o jsonpath="{.data.$SECRET_PATH}" | base64 --decode
```

## Bonus

Install autocompletion:

```bash
echo "source <(kubectl completion bash)" >> ~/.bashrc
```
