# Bash scripting Cheatsheet

## Basic actions

First line of the bash script:

```bash
#!/usr/bin/env bash
```

## Conditional

### If

Check if a user exist:

```bash
if ! id -u $USER_NAME > /dev/null 2>&1; then
  echo 'Add $USER_NAME user'
  adduser --ingroup $GROUP_NAME --home /home/$USER_NAME --gecos "" --shell /bin/bash --disabled-password $USER_NAME 
fi
```

Check if a group exist:

```bash
if ! id -g $GROUP_NAME > /dev/null 2>&1; then
  echo 'Add $GROUP_NAME group'
  addgroup $GROUP_NAME
fi
```

Check if a folder exist:

```bash
if [ ! -d "$FOLDER_PATH"; then
  echo 'Create $FOLDER_PATH folder'
  mkdir -p $FOLDER_PATH
fi
```

### For

Basic `for` loop:

```bash
for i in {1..5}; do
  echo "Welcome $i times"
done
```

Infinity `for` loop:

```bash
for (( ; ; )); do
  echo "Infinite loop [hit CTRL+C to stop]"
done
```
