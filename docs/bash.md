# Bash

## Basic actions

One line `for` loop:

```bash
for t in {1..5}; do echo "${t}"; done
```

One line `for` infinite loop:

```bash
for (( t=1; ; t++ )); do echo "${t}"; done
```

Find a file by it's name:

```bash
find / -name find.txt  # case sensitive
find / -iname find.txt # case insensitive
```

## Dev workflow

Set environment variable listed as key-value pair in a `.env` file:

```bash
export $(grep -v '^#' .env | xargs)
```

Unset environment variable listed as key-value pair in a `.env` file:

```bash
unset $(grep -v '^#' .env | sed -E 's/(.*)=.*/\1/' | xargs)
```

## Setup a personal folder to store binaries

Create a `bin` folder in your home folder:

```bash
mkdir -p $HOME/bin
```

Add the `bin` folder to your PATH:

```bash
if [ -d $HOME/bin ]; then
  export PATH="$HOME/bin:$PATH"
fi
```

From now, all the binaries that you will put in your `bin` folders will be accessible from anywhere in your system.

## Tips

Preserving environments variables when elevating privileges:

```bash
sudo -E printenv
```
