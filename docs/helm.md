# Helm

## Basic actions

List versions of a chart:

```bash
helm search -l stable/$CHART_NAME
```

List all releases installed:

```bash
helm ls --all -d
```

Get all the informations available on a release:

```bash
helm get all $RELEASE_NAME
```

Get the status of a release:

```bash
helm status $RELEASE_NAME
```

Get the status of a release:

```bash
helm upgrade --install --namespace=$NAMESPACE_NAME --values=values.yaml $RELEASE_NAME $CHART_NAME
```

Delete a release:

```bash
helm uninstall --namespace=$NAMESPACE_NAME $RELEASE_NAME
```
