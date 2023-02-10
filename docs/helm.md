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
