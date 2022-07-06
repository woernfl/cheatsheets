# Bash aliases

## Setup

Create the file storing your aliases

```bash
touch ~/.bash_aliases
```

Include this file in your `~/.bashrc` file

```bash
if [ -e $HOME/.bash_aliases ]; then
    source $HOME/.bash_aliases
fi
```

## `.bash_aliases` file

```bash
alias hg='echo "Use !\$CMD_HISTORY_NUM to run the specific cmd" && history|grep'
alias ll='ls -la'
alias gitcred='git config credential.helper store'
alias update='sudo apt-get update && sudo apt-get upgrade -y'
alias gitbrclean='git remote prune
```
