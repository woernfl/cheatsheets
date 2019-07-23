---
layout: default
title: Kubernetes
parent: Home
---

# Kubernetes Cheatsheet

## Basic actions

Get everything:

```bash
kubectl get all --all-namespaces
```

Get more info about pods:

```bash
kubectl get po -o wide
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

Boot a centos pod in Kubernetes:

```bash
kubectl run tmp-shell --rm -i --tty --image centos -- /bin/bash
```

## Bonus

Install autocompletion:

```bash
echo "source <(kubectl completion bash)" >> ~/.bashrc
```
