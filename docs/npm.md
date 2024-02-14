# npm

## Basic actions

Install a package at user level:

```bash
npm install -u $PACKAGE_NAME
```

Install a package globaly:

```bash
npm install -g $PACKAGE_NAME
```

Check the version of a package:

```bash
npm show $PACKAGE_NAME version
```

Check the version of a package and all it depedencies:

```bash
npm list $PACKAGE_NAME
```

Set a private repo:

```bash
npm config set registry $REGISTRY_URL
```
