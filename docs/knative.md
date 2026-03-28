# Knative

## Basic actions

List services:

```bash
kubectl -n $NAMESPACE get ksvc
```

Relaunche an initialisation of a service:

```bash
kubectl -n $NAMESPACE patch ksvc $SERVICE_NAME --type=merge -p '{"spec": {"template": {"metadata": {"annotations": {"force-redeploy": "'$(date +%s)'"}}}}}'
```
