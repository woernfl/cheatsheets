# Mac

## Keyboard shortcut

### Symbols

| Symbol | FR Shortcut   | CH DE Shortcut |
| ------ | ------------- | -------------- |
| \|     | Alt + Maj + L | Alt + 7        |
| \      | Alt + Maj + / | Alt + Maj + 7  |
| [      | Alt + Maj + ( | Alt + 5        |
| ]      | Alt + Maj + ) | Alt + 6        |
| {      | Alt + (       | Alt + 8        |
| }      | Alt + )       | Alt + 9        |
| #      | Maj + #       | Alt + 3        |

### System

| Shortcut            | Action                            |
| ------------------- | --------------------------------- |
| Ctrl + Cmd + Q      | Lock the screen                   |
| Cmd + Alt + Maj + V | Paste without formatting          |
| Cmd + Maj + R       | Reload the navigator window       |
| Cmd + Maj + D       | Once in the finder, go to Desktop |
| Cmd + Maj + H       | Once in the finder, go to Home    |

## Shell config

Check which shell is used:

```bash
echo $SHELL
```

Switch to a bash shell:

```bash
chsh -s /bin/bash
```

Add this to your `.bash_profile`:

```bash
source ~/.bashrc
```

## Homebrew

### Install Homebrew

Install [Homebrew](https://brew.sh/):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Packages

Here is the list of packages I usually use:

- [Git](https://git-scm.com/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Bash Completion](https://github.com/scop/bash-completion)
- [Chrome](https://www.google.com/chrome/)
- [Rectangle](https://github.com/rxhanson/Rectangle)
- [Logi Options+](https://www.logitech.com/en-us/software/logi-options-plus)
- [AltTab](https://alt-tab-macos.netlify.app/)
- [Whatsapp](https://www.whatsapp.com/)
- [VS Code](https://code.visualstudio.com/)
- [LM Studio](https://lmstudio.ai/)
- [Nodejs](https://github.com/nodejs/node)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
- [Helm](https://helm.sh/)
- [kubeseal](https://github.com/bitnami-labs/sealed-secrets)
- [pipx](https://pipx.pypa.io/stable/)
- [watch](https://gitlab.com/procps-ng/procps)
- [pre-commit](https://pre-commit.com/)
- [argocd](https://argoproj.github.io/cd/)
- [Netbird](https://docs.netbird.io/)
- [ripgrep](https://github.com/BurntSushi/ripgrep)
- [Pi](https://pi.dev/)
- [iTerm2](https://github.com/gnachman/iterm2)
- [GitUI](https://github.com/gitui-org/gitui)
- [Hunk](https://github.com/modem-dev/hunk)
- [diffnav](https://github.com/dlvhdr/diffnav)
- [bat](https://github.com/sharkdp/bat)
- [gh](https://cli.github.com/)
- [lychee](https://lychee.cli.rs/)

### Install Packages

Here is how to install this packages using the terminal:

```bash
brew install git
brew install --cask docker-desktop
brew install bash-completion@2
brew install --cask google-chrome
brew install rectangle
brew install --cask logi-options+
brew install --cask alt-tab
brew install --cask whatsapp
brew install --cask visual-studio-code
brew install --cask lm-studio
brew install node@24
echo 'export PATH="/opt/homebrew/opt/node@24/bin:$PATH"' >> ~/.bashrc
brew install kubernetes-cli
brew install helm
brew install kubeseal
brew install pipx && pipx ensurepath
brew install watch
brew install pre-commit
brew install argocd
brew install netbirdio/tap/netbird
brew install --cask netbirdio/tap/netbird-ui
brew install ripgrep
brew install pi-coding-agent
brew install --cask iterm2
brew install gitui
brew install modem-dev/tap/hunk
brew install dlvhdr/formulae/diffnav
git config --global pager.diff diffnav
brew install bat
brew install gh
brew install lychee
```

## Some easy fix

Remove the macOS quarantine flag from a binary (used when you get "app is damaged" or "cannot be opened because it is from an unidentified developer" errors):

```bash
sudo xattr -rc $BINARY
```
