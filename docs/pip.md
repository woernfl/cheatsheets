# pip

## Basic actions

### Search for packages

```bash
pip search $PACKAGE_NAME
```

### Install some packages

```bash
pip install $PACKAGE_NAME
```

### Install some package in user space

```bash
pip install --user $PACKAGE_NAME
```

### Upgrade some package

```bash
pip install --upgrade $PACKAGE_NAME
```

### Install packages from file

```bash
pip install -r requirements.txt
```

## Bonus

### List outdated packages

```bash
pip list --outdated
```

### Install specific version of a package

```bash
pip install -I $PACKAGE_NAME==1.1.0
```
