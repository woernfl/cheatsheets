# VS Code

## User Settings

`ctrl+maj+p` and type `Preferences: Open Settings (JSON)`, then fill it with:

```json
{
  "editor.tabSize": 2,
  "editor.bracketPairColorization.enabled": true,
  "workbench.colorCustomizations": {
    "editorBracketHighlight.foreground1": "#5caeef",
    "editorBracketHighlight.foreground2": "#dfb976",
    "editorBracketHighlight.foreground3": "#c172d9",
    "editorBracketHighlight.foreground4": "#4fb1bc",
    "editorBracketHighlight.foreground5": "#97c26c",
    "editorBracketHighlight.foreground6": "#abb2c0",
    "editorBracketHighlight.unexpectedBracket.foreground": "#db6165"
  },
  "indentRainbow.includedLanguages": ["yaml", "yml"],
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[python]": {
    "editor.defaultFormatter": "ms-python.python"
  },
  "python.formatting.provider": "black",
  "[terraform]": {
    "editor.defaultFormatter": "hashicorp.terraform",
    "editor.formatOnSave": true,
    "editor.formatOnSaveMode": "file"
  },
  "[terraform-vars]": {
    "editor.defaultFormatter": "hashicorp.terraform",
    "editor.formatOnSave": true,
    "editor.formatOnSaveMode": "file"
  },
  "markdownlint.config": {
    "MD033": false,
    "MD034": false
  },
  "explorer.confirmDragAndDrop": false,
  "terminal.integrated.enableMultiLinePasteWarning": false,
  "redhat.telemetry.enabled": false
}
```

## Extentions

Here is the list of extentions I usually use:

- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
- [TODO Highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight)
- [TODO Tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)
- [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)
- [HashiCorp Terraform](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [indent-rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow)
- [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)
- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [gitignore](https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore)
- [Trivy](https://marketplace.visualstudio.com/items?itemName=AquaSecurityOfficial.trivy-vulnerability-scanner)
- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)
- [Box Comment](https://marketplace.visualstudio.com/items?itemName=polymermallard.box-comment)
- [Groovy](https://marketplace.visualstudio.com/items?itemName=MellowMarshmallow.groovy)
- [Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)

Here is how to install this extentions using the VS Code Quick Open (Ctrl+P):

```
ext install yzhang.markdown-all-in-one
ext install DavidAnson.vscode-markdownlint
ext install wayou.vscode-todo-highlight
ext install Gruntfuggly.todo-tree
ext install ms-azuretools.vscode-docker
ext install HashiCorp.terraform
ext install esbenp.prettier-vscode
ext install oderwat.indent-rainbow
ext install redhat.vscode-yaml
ext install ms-python.python
ext install codezombiech.gitignore
ext install AquaSecurityOfficial.trivy-vulnerability-scanner
ext install streetsidesoftware.code-spell-checker
ext install aaron-bond.better-comments
ext install polymermallard.box-comment
ext install MellowMarshmallow.groovy
ext install ms-vscode-remote.remote-ssh
```

Or via your terminal:

```bash
code --install-extension yzhang.markdown-all-in-one
code --install-extension DavidAnson.vscode-markdownlint
code --install-extension wayou.vscode-todo-highlight
code --install-extension Gruntfuggly.todo-tree
code --install-extension ms-azuretools.vscode-docker
code --install-extension HashiCorp.terraform
code --install-extension esbenp.prettier-vscode
code --install-extension oderwat.indent-rainbow
code --install-extension redhat.vscode-yaml
code --install-extension ms-python.python
code --install-extension codezombiech.gitignore
code --install-extension AquaSecurityOfficial.trivy-vulnerability-scanner
code --install-extension streetsidesoftware.code-spell-checker
code --install-extension aaron-bond.better-comments
code --install-extension polymermallard.box-comment
code --install-extension MellowMarshmallow.groovy
code --install-extension ms-vscode-remote.remote-ssh
```

## Remote SSH extention configuration

Add your SSH host following this steps:

1. Go to your VS Code
2. On the bottom right corner, click on the remote SSH icon
3. Choose `Remote-SSH: Connect to Host`
4. Choose the user configuration file (usually the first one in the list)
5. Enter the following details:
  ```
  Host dev-ec2
    HostName $SERVER_HOSTNAME_OR_IP
    User $USER_TO_BE_USED_TO_CONNECT
    IdentityFile $PATH_TO_PRIVATE_KEY_FILE
  ```

If you need a more detailed instruction set, please visit the [official documentation](https://code.visualstudio.com/docs/remote/ssh).
