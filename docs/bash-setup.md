# BAsh setup

## Bash aliases

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

### `.bash_aliases` file

```bash
alias hg='echo "Use !\$CMD_HISTORY_NUM to run the specific cmd" && history|grep'
alias ll='ls -la'
alias gitcred='git config credential.helper store'
alias update='sudo apt-get update && sudo apt-get upgrade -y'
alias gitbrclean='git remote prune
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

## Bash autocompletion

A list of commande to enable autocompletion for things I use everyday:

```bash
echo "complete -C '$(which aws_completer)' aws" >> ~/.bashrc
echo "source <(kubectl completion bash)" >> ~/.bashrc
echo "source <(helm completion bash)" >> ~/.bashrc
echo "source <(minikube completion bash)" >> ~/.bashrc
echo "source <(skaffold completion bash)" >> ~/.bashrc
terraform -install-autocomplete
vault -autocomplete-install
```

## Choosing which bash

Check which shells are installed:

```bash
cat /etc/shells
```

Switch to bash:

```bash
chsh -s /bin/bash
```

## Pimping the prompt

Add the following to your `~/.bashrc` file:

```bash
# Turn on parallel history
shopt -s histappend
history -a

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
"\[${FG_WHITE}\]\w \[${FMT_RESET}${FG_GREEN}\]"\
'$(git_branch "\[${BG_MAGENTA}\] \[${FG_WHITE}\] %s \[${FMT_RESET}${FG_MAGENTA}\]")'\
"\n \[${FG_GREEN}\]╰ \[${FG_CYAN}\]\$ \[${FMT_RESET}\]"
```
