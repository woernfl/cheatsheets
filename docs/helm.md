# Helm

## Basic actions

List versions of a chart:

```bash
helm search repo $CHART_NAME
```

List all releases installed:

```bash
helm list --all-namespaces
```

Get all the informations available on a release:

```bash
helm get all $RELEASE_NAME
```

Get the status of a release:

```bash
helm status $RELEASE_NAME
```

Install or upgrade a release:

```bash
helm upgrade --install --namespace=$NAMESPACE_NAME --values=values.yaml $RELEASE_NAME $CHART_NAME
```

Delete a release:

```bash
helm uninstall --namespace=$NAMESPACE_NAME $RELEASE_NAME
```

Template a chart:

```bash
helm template $RELEASE_NAME $CHART_NAME
```

Lint a chart:

```bash
helm lint $CHART_NAME
```

Update chart dependencies:

```bash
helm dependency update
```
