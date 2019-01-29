---
layout: default
title: Kubernetes
parent: Home
---

# Kubernetes Cheatsheet

Get everything:

```bash
kubectl get all --all-namespaces
```

Connect to a pod from your local workstation:

```bash
kubectl port-forward --namespace $POD_NAMESPACE $POD_NAME $LOCAL_PORT:$POD_PORT
```

Install autocompletion:

```bash
echo "source <(kubectl completion bash)" >> ~/.bashrc
```