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

## To debug

Connect to a pod from your local workstation:

```bash
kubectl port-forward --namespace $POD_NAMESPACE $POD_NAME $LOCAL_PORT:$POD_PORT
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
