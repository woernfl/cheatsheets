# VS Code

## User Settings

`ctrl+maj+p` and type `Preferences: Open Settings (JSON)`, then fill it with:

```json
{
  "editor.tabSize": 2,
  "editor.bracketPairColorization.enabled": true,
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
  }
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
- [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)
- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [gitignore](https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore)
- [Trivy](https://marketplace.visualstudio.com/items?itemName=AquaSecurityOfficial.trivy-vulnerability-scanner)
- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
- [Kite](https://marketplace.visualstudio.com/items?itemName=kiteco.kite)
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)
- [Box Comment](https://marketplace.visualstudio.com/items?itemName=polymermallard.box-comment)
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
ext install redhat.vscode-yaml
ext install mikestead.dotenv
ext install ms-python.python
ext install codezombiech.gitignore
ext install AquaSecurityOfficial.trivy-vulnerability-scanner
ext install streetsidesoftware.code-spell-checker
ext install kiteco.kite
ext install aaron-bond.better-comments
ext install polymermallard.box-comment
ext install ms-vscode-remote.remote-ssh
```
