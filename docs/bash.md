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

Check the difference between 2 files:

```bash
diff $FILE1 $FILE2
```

## Text processing

### `awk`

Search for a specific keyword:

```bash
awk '/$KEYWORD/' $FILENAME
```

Show specific a column only:

```bash
awk '{print $COLUMN_NUMBER}' $FILENAME
```

Show multiple columns:

```bash
awk '{print $COLUMN_NUMBER,$COLUMN_NUMBER}' $FILENAME
```

Show multiple columns without the whitespace between them:

```bash
awk '{print $COLUMN_NUMBER$COLUMN_NUMBER}' $FILENAME
```

Customize results using different characters as separators:

```bash
awk '{print $COLUMN_NUMBER "$SEPARATOR" $COLUMN_NUMBER}' $FILENAME
```

Combine search and column filtering:

```bash
awk '/$KEYWORD/ {print $COLUMN_NUMBER}' $FILENAME
```

Use a simple conditional statement:

```bash
awk '{if ($COLUMN_NUMBER expression $NUMBER) print $COLUMN_NUMBER}' $FILENAME
```

Use a different field separator. By default, AWK separates columns via white spaces:

```bash
awk -F '$SEPARATOR' '$STATEMENT' $FILENAME
```

Show results that should have all the specified keywords by using "and":

```bash
awk '/$KEYWORD/ && /$KEYWORD/' $FILENAME
```

Show results that should have any of the specified keywords by using “or”:

```bash
awk '/$KEYWORD/ || /$KEYWORD/' $FILENAME
```

Show everything except for the specified keyword using “not”:

```bash
awk '!/$KEYWORD/' $FILENAME
```

Thanks to Arc Sosangyo for his great blog post about `awk`. All the `awk` on this page come from [here](https://betterprogramming.pub/10-practical-use-of-awk-command-in-linux-unix-26fbd92f1112).

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

Check disk usage:

```bash
df -h
```

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

## Archiving files

Create a tar:

```bash
tar -cvzf $ARCHIVE_NAME.tar $DIRECTORY_TO_COMPRESS
```

Extract a tar:

```bash
tar -xvzf $ARCHIVE_NAME.tar
```

## Miscellaneous

Find out the top most used commands:

```bash
cat ~/.bash_history | tr "\|\;" "\n" | sed -e "s/^ //g" | cut -d " " -f 1 | sort | uniq -c | sort -n | tail -n 10
```

## Exit Codes

Check the exist code of the last command runned:

```bash
echo $?
```

`0` All good

`1` Catchall for general errors

`2` Misuse of shell builtins

`126` Command invoked cannot execute

`127` "command not found"

`128` Invalid argument to exit

`128+n` Fatal error signal “n”

`130` Script terminated by Control-C

`255\*` Exit status out of range

## Bash scripting

First line of the bash script:

```bash
#!/usr/bin/env bash
```

### Conditional

#### If

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

### Loop

#### While

Basic `while` loop:

```bash
COUNTER=0
while (( $COUNTER < 10 )); do
  echo The counter is $COUNTER
  let COUNTER=COUNTER+1
done
```

#### For

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
