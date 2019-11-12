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

## To debug

Follow logs of multiple pods:

```bash
kubectl logs -f -n $NAMESPACE -l app=myapp
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
kubectl port-forward --namespace $NAMESPACE --address 0.0.0.0 service/SERVICE_NAME $LOCAL_PORT:$POD_PORT
```

Boot a centos pod in Kubernetes:

```bash
kubectl run tmp-shell --rm -i --tty --image centos -- /bin/bash
```

## Bonus

Install autocompletion:

```bash
echo "source <(kubectl completion bash)" >> ~/.bashrc
```
