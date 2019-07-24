# Bash Cheatsheet

## Basic actions

One line for loop:

```bash
for t in {1..5}; do echo "${t}"; done
```

Add an alias:

```bash
vim ~/.bashrc
# Go to the end of the file
alias aliascommand='commands'
```

## Tips

Preserving environments variables when elevating privileges:

```bash
sudo -E printenv
```
