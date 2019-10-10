# Bash scripting

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

## Loop

### While

Basic `while` loop:

```bash
COUNTER=0
while (( $COUNTER < 10 )); do
  echo The counter is $COUNTER
  let COUNTER=COUNTER+1
done
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

## Exit Codes

`0`

:   All good

`1`

:   Catchall for general errors

`2`

:   Misuse of shell builtins

`126`

:   Command invoked cannot execute

`127`

:   "command not found"

`128`

:   Invalid argument to exit

`128+n`

:   Fatal error signal “n”

`130`

:   Script terminated by Control-C

`255\*`

:   Exit status out of range
