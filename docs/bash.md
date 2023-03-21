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

Get the absolute path of a file:

```bash
readink -f $FILE
```

Become root:

```bash
sudo su –
```

Become any user without typing a password:

```bash
sudo su $USER_NAME
```

## Text processing

### find

Find a file by it's name:

```bash
find / -name $FILE_NAME # case sensitive
find / -iname $FILE_NAME # case insensitive
```

Find files containing an expression recursively:

```bash
find . -type f -exec grep -l "$SEARCH_EXPRESSION" {} \;
```

Find duplicate files based on the MD5 hash:

```bash
find -type f -exec  md5sum '{}' ';' |  sort |  uniq --all-repeated=separate -w 33 |  cut -c 35-
```

Delete file older that a certain number of days:

```bash
find . -type f -mtime +$NUMBER_OF_DAYS -exec rm {} \;
```

### grep

Search for a specific keyword (is case sensitive):

```bash
grep $KEYWORD $FILE_PATH
```

Search for a specific keyword (is note case sensitive):

```bash
grep -i $KEYWORD $FILE_PATH
```

Search for a specific keyword (returns the exact matches):

```bash
grep -w $KEYWORD $FILE_PATH
```

Display the count of number of matches:

```bash
grep -c $KEYWORD $FILE_PATH
```

Display only the matched pattern :

```bash
grep -o $KEYWORD $FILE_PATH
```

Show line number while displaying the output:

```bash
grep -n $KEYWORD $FILE_PATH
```

Display the lines that are not matched:

```bash
grep -v $KEYWORD $FILE_PATH
```

### sed

Replace a string by an other one:

```bash
sed 's/$SEARCH_STRING/$REPLACEMENT_STRING/g' $FILE_PATH
```

Replace a string by an other one in a particular line:

```bash
sed '$LINE_NUMBER s/$SEARCH_STRING/$REPLACEMENT_STRING/g' $FILE_PATH
```

Display replaced lines only:

```bash
sed -n 's/$SEARCH_STRING/$REPLACEMENT_STRING/p' $FILE_PATH
```

Delete lines:

```bash
sed '/^$/d' $FILE_PATH
```

Delete blank lines:

```bash
sed '/$SEARCH_STRING/d' $FILE_PATH
```

### awk

Search for a specific keyword:

```bash
awk '/$KEYWORD/' $FILE_PATH
```

Show specific a column only:

```bash
awk '{print $COLUMN_NUMBER}' $FILE_PATH
```

Show multiple columns:

```bash
awk '{print $COLUMN_NUMBER,$COLUMN_NUMBER}' $FILE_PATH
```

Show multiple columns without the whitespace between them:

```bash
awk '{print $COLUMN_NUMBER$COLUMN_NUMBER}' $FILE_PATH
```

Customize results using different characters as separators:

```bash
awk '{print $COLUMN_NUMBER "$SEPARATOR" $COLUMN_NUMBER}' $FILE_PATH
```

Combine search and column filtering:

```bash
awk '/$KEYWORD/ {print $COLUMN_NUMBER}' $FILE_PATH
```

Use a simple conditional statement:

```bash
awk '{if ($COLUMN_NUMBER expression $NUMBER) print $COLUMN_NUMBER}' $FILE_PATH
```

Use a different field separator. By default, AWK separates columns via white spaces:

```bash
awk -F '$SEPARATOR' '$STATEMENT' $FILE_PATH
```

Show results that should have all the specified keywords by using "and":

```bash
awk '/$KEYWORD/ && /$KEYWORD/' $FILE_PATH
```

Show results that should have any of the specified keywords by using “or”:

```bash
awk '/$KEYWORD/ || /$KEYWORD/' $FILE_PATH
```

Show everything except for the specified keyword using “not”:

```bash
awk '!/$KEYWORD/' $FILE_PATH
```

Thanks to Arc Sosangyo for his great blog post about `awk`. All the `awk` on this page come from [here](https://betterprogramming.pub/10-practical-use-of-awk-command-in-linux-unix-26fbd92f1112).

### head

Print the first X lines:

```bash
head -n $NUMBER_OF_LINES_TO_PRINT $FILE_PATH
```

Print all except the last X lines:

```bash
head -n -$NUMBER_OF_LINES_NOT_TO_PRINT $FILE_PATH
```

Print the X first bytes:

```bash
head -c $NUMBER_OF_BYTES_TO_PRINT $FILE_PATH
```

Print all except the last X bytes:

```bash
head -c -$NUMBER_OF_BYTES_NOT_TO_PRINT $FILE_PATH
```

## Check logs

Follow logs that are appended to a file:

```bash
tail -f $FILE_PATH
```

Retry to follow logs (useful when the file has not yet been created):

```bash
tail -f $FILE_PATH --retry
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

List all programs listing on a port:

```bash
# On a specific port
lsof -i:$PORT

# For all ports
lsof -i
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

Resize the size of file system to the use all the free space:

```bash
sudo resize2fs $LV_PATH
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

### Default script options

```bash
set -euxo pipefail
```

`-u`: fail on non-existing variable

`-x`: print the command before running it

`-e`: fail the script on command fail

`-o pipefail`: fail the script on a command fail in a pipeline 

Thanks to this [article](https://link.medium.com/RNKDFHuOisb) for clearly explaining all this options.

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

Print the time it took for some code to be executed:

```bash
#!/bin/bash

start_time=$(date +%s)

# some code here

end_time=$(date +%s)

echo "Took $(($end_time - $start_time)) seconds to complete"
```

### Create strucutured logs

You will need to have `jq` installed.

The function to use:

```bash
__timestamp(){
  date "+%Y%m%dT%H%M%S"
}
__log(){
  log_level="$1"
  message="$2"
  echo '{}' | \
  jq  --monochrome-output \
      --compact-output \
      --raw-output \
      --arg timestamp "$(__timestamp)" \
      --arg log_level "$log_level" \
      --arg message "$message" \
      '.timestamp=$timestamp|.log_level=$log_level|.message=$message'
}
````

Usage example:

```bash
# Line to put in your script
__log "INFO" "Hello, World!"

# Expected output
{"timestamp":"20210812T191730","log_level":"INFO","message":"Hello, World!"}
```

Thanks to Jesse Riddle for sharing this awsome pice of shell script. All the info's of this section come from [here](https://medium.com/@jesse.riddle/structured-logging-in-a-shell-script-with-jq-f7542a94a1f6).
