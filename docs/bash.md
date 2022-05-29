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

Rerun your last command, but with sudo this time:

```bash
sudo !!
```

Print the PATH in a readable manner:

```bash
echo $PATH | tr ':' '\n'
```

## Manage Environment variables

Set environment variable listed as key-value pair in a `.env` file:

```bash
export $(grep -v '^#' .env | xargs)
```

Unset environment variable listed as key-value pair in a `.env` file:

```bash
unset $(grep -v '^#' .env | sed -E 's/(.*)=.*/\1/' | xargs)
```

Preserving environments variables when elevating privileges:

```bash
sudo -E printenv
```

## Network stuff

Send a UDP Packet:

```bash
echo -n "blah:36|c" | nc -w 1 -u -4 $REMOTE_IP $REMOTE_PORT
```

Listen on UDP packet recieved by an host:

```bash
sudo tcpdump udp port $PORT_TO_LISTEN_ON -vv -X
```

## Volume management

List the block devices:

```bash
lsblk -a
```

List the partitions:

```bash
sudo pvdisplay 
```

Resize a partition:

```bash
sudo pvresize $PARTITION_PATH
```

List the Logical Volume

```bash
sudo lvdisplay
```

Extend the size of the Logical Volume to the use all the free space:

```bash
sudo lvextend -l +100%FREE $LV_PATH
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

## Archiving files 

Create a tar:

```bash
tar -cvzf $ARCHIVE_NAME.tar $DIRECTORY_TO_COMPRESS
```

Extract a tar:

```bash
tar -xvzf $ARCHIVE_NAME.tar
```

## Pimping the prompt

Add the following to your `~/.bashrc` file:

```bash
# Bash prompt
git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}

FMT_BOLD="\e[1m"
FMT_RESET="\e[0m"
FMT_UNBOLD="\e[21m"
FG_BLACK="\e[30m"
FG_BLUE="\e[34m"
FG_CYAN="\e[36m"
FG_GREEN="\e[32m"
FG_MAGENTA="\e[35m"
FG_RED="\e[31m"
FG_WHITE="\e[97m"
BG_BLUE="\e[44m"
BG_GREEN="\e[42m"
BG_MAGENTA="\e[45m"

export GIT_PS1_SHOWDIRTYSTATE=1
export GIT_PS1_SHOWCOLORHINTS=1

export PS1=\
"\n\[${BG_GREEN}\] \[${FG_RED}\] \[${FG_BLACK}\]\u \[${FG_GREEN}${BG_BLUE}\] "\
"\[${FG_BLACK}\]\w \[${FMT_RESET}${FG_GREEN}\]"\
'$(git_branch "\[${BG_MAGENTA}\] \[${FG_WHITE}\] %s \[${FMT_RESET}${FG_MAGENTA}\]")'\
"\n \[${FG_GREEN}\]╰ \[${FG_CYAN}\]\$ \[${FMT_RESET}\]"
```
