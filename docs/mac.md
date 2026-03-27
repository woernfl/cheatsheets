# Mac

## Keyboard shortcut

### Symboles

Symbole | FR Shortcut     | CH DE Shortcut
------- | --------------- | ----------- 
\|      | Alt + Maj + L   | Alt + 7
\       | Alt + Maj + /   | Alt + Maj + 7
[       | Alt + Maj + (   | Alt + 5
]       | Alt + Maj + )   | Alt + 6
{       | Alt + (         | Alt + 8
}       | Alt + )         | Alt + 9
 
### Systeme

Shortcut            | Action
------------------- | ------------- 
Ctrl + Cmd + Q      | Lock the screen
Cmd + Alt + Maj + V | Paste without formatting
Cmd + Maj + R       | Reload the navigator window
Cmd + Maj + D       | Once in the finder, go to Desktop
Cmd + Maj + H       | Once in the finder, go to Home

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

## Package managment

Install [Homebrew](https://brew.sh/):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Packages

Here is the list of packages I usually use:

- [Git](https://git-scm.com/)
- [Bash Completion](https://github.com/scop/bash-completion)
- [Chrome](https://www.google.com/chrome/)
- [Rectangle](https://github.com/rxhanson/Rectangle)
- [AltTab](https://alt-tab-macos.netlify.app/)
- [Whatsapp](https://www.whatsapp.com/)
- [VS Code](https://code.visualstudio.com/)
- [LM Studio](https://lmstudio.ai/)
- [Nodejs](https://github.com/nodejs/node)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
- [kubeseal](https://github.com/bitnami-labs/sealed-secrets)
- [pipx](https://pipx.pypa.io/stable/)
- [watch](https://gitlab.com/procps-ng/procps)
- [pre-commit](https://pre-commit.com/)
- [Netbird](https://docs.netbird.io/)

Here is how to install this packages using the terminal:

```
brew install git
brew install bash-completion@2
brew install --cask google-chrome
brew install rectangle
brew install --cask alt-tab
brew install --cask whatsapp
brew install --cask visual-studio-code
brew install --cask lm-studio
brew install node@24
echo 'export PATH="/opt/homebrew/opt/node@24/bin:$PATH"' >> /Users/woernfl/.bashrc
brew install kubernetes-cli
brew install kubeseal
brew install pipx && pipx ensurepath
brew install watch
brew install pre-commit
brew install netbirdio/tap/netbird
brew install --cask netbirdio/tap/netbird-ui
```

## Some easy fix

Remove the binary malware virification:

```bash
sudo xattr -rc $BINARY
```
