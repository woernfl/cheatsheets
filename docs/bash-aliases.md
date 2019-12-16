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
alias hg='history|grep'
```
