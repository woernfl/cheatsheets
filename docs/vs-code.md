# VS Code

## User Settings

`ctrl+p` and type `User/settings.json`, then fille it with:

```json
{
  "editor.tabSize": 2,
  "editor.bracketPairColorization.enabled": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[python]": {
    "editor.defaultFormatter": "ms-python.python"
  },
  "python.formatting.provider": "black"
}
```

## Extentions

Here is the list of extentions I usually use:

- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [TODO Highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight)
- [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)
- [HashiCorp Terraform](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)
- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [gitignore](https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore)
- [Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)

Here is how to install this extentions using the VS Code Quick Open (Ctrl+P):

```
ext install yzhang.markdown-all-in-one
ext install wayou.vscode-todo-highlight
ext install ms-azuretools.vscode-docker
ext install HashiCorp.terraform
ext install esbenp.prettier-vscode
ext install redhat.vscode-yaml
ext install mikestead.dotenv
ext install ms-python.python
ext install codezombiech.gitignore
```
