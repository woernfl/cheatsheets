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
  "aws.telemetry": false,
  "redhat.telemetry.enabled": false,
  "editor.stickyScroll.enabled": false,
  "terminal.integrated.defaultProfile.osx": "bash",
  "chat.tools.terminal.autoApprove": {
    "cd": true,
    "echo": true,
    "ls": true,
    "dir": true,
    "pwd": true,
    "cat": true,
    "head": true,
    "tail": true,
    "findstr": true,
    "wc": true,
    "tr": true,
    "cut": true,
    "cmp": true,
    "which": true,
    "basename": true,
    "dirname": true,
    "realpath": true,
    "readlink": true,
    "stat": true,
    "file": true,
    "od": true,
    "du": true,
    "df": true,
    "sleep": true,
    "nl": true,
    "grep": true,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+status\\b/": true,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+log\\b/": true,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+log\\b.*\\s--output(=|\\s|$)/": false,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+show\\b/": true,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+diff\\b/": true,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+ls-files\\b/": true,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+grep\\b/": true,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+branch\\b/": true,
    "/^git(\\s+(-C\\s+\\S+|--no-pager))*\\s+branch\\b.*\\s-(d|D|m|M|-delete|-force)\\b/": false,
    "/^docker\\s+(ps|images|info|version|inspect|logs|top|stats|port|diff|search|events)\\b/": true,
    "/^docker\\s+(container|image|network|volume|context|system)\\s+(ls|ps|inspect|history|show|df|info)\\b/": true,
    "/^docker\\s+compose\\s+(ps|ls|top|logs|images|config|version|port|events)\\b/": true,
    "Get-ChildItem": true,
    "Get-Content": true,
    "Get-Date": true,
    "Get-Random": true,
    "Get-Location": true,
    "Set-Location": true,
    "Write-Host": true,
    "Write-Output": true,
    "Out-String": true,
    "Split-Path": true,
    "Join-Path": true,
    "Start-Sleep": true,
    "Where-Object": true,
    "/^Select-[a-z0-9]/i": true,
    "/^Measure-[a-z0-9]/i": true,
    "/^Compare-[a-z0-9]/i": true,
    "/^Format-[a-z0-9]/i": true,
    "/^Sort-[a-z0-9]/i": true,
    "/^npm\\s+(ls|list|outdated|view|info|show|explain|why|root|prefix|bin|search|doctor|fund|repo|bugs|docs|home|help(-search)?)\\b/": true,
    "/^npm\\s+config\\s+(list|get)\\b/": true,
    "/^npm\\s+pkg\\s+get\\b/": true,
    "/^npm\\s+audit$/": true,
    "/^npm\\s+cache\\s+verify\\b/": true,
    "/^yarn\\s+(list|outdated|info|why|bin|help|versions)\\b/": true,
    "/^yarn\\s+licenses\\b/": true,
    "/^yarn\\s+audit\\b(?!.*\\bfix\\b)/": true,
    "/^yarn\\s+config\\s+(list|get)\\b/": true,
    "/^yarn\\s+cache\\s+dir\\b/": true,
    "/^pnpm\\s+(ls|list|outdated|why|root|bin|doctor)\\b/": true,
    "/^pnpm\\s+licenses\\b/": true,
    "/^pnpm\\s+audit\\b(?!.*\\bfix\\b)/": true,
    "/^pnpm\\s+config\\s+(list|get)\\b/": true,
    "npm ci": true,
    "/^yarn\\s+install\\s+--frozen-lockfile\\b/": true,
    "/^pnpm\\s+install\\s+--frozen-lockfile\\b/": true,
    "column": true,
    "/^column\\b.*\\s-c\\s+[0-9]{4,}/": false,
    "date": true,
    "/^date\\b.*\\s(-s|--set)\\b/": false,
    "find": true,
    "/^find\\b.*\\s-(delete|exec|execdir|fprint|fprintf|fls|ok|okdir)\\b/": false,
    "rg": true,
    "/^rg\\b.*\\s(--pre|--hostname-bin)\\b/": false,
    "sed": true,
    "/^sed\\b.*\\s(-[a-zA-Z]*(e|f)[a-zA-Z]*|--expression|--file)\\b/": false,
    "/^sed\\b.*s\\/.*\\/.*\\/[ew]/": false,
    "/^sed\\b.*;W/": false,
    "sort": true,
    "/^sort\\b.*\\s-(o|S)\\b/": false,
    "tree": true,
    "/^tree\\b.*\\s-o\\b/": false,
    "/^xxd$/": true,
    "/^xxd\\b(\\s+-\\S+)*\\s+[^-\\s]\\S*$/": true,
    "rm": false,
    "rmdir": false,
    "del": false,
    "Remove-Item": false,
    "ri": false,
    "rd": false,
    "erase": false,
    "dd": false,
    "kill": false,
    "ps": false,
    "top": false,
    "Stop-Process": false,
    "spps": false,
    "taskkill": false,
    "taskkill.exe": false,
    "curl": false,
    "wget": false,
    "Invoke-RestMethod": false,
    "Invoke-WebRequest": false,
    "irm": false,
    "iwr": false,
    "chmod": false,
    "chown": false,
    "Set-ItemProperty": false,
    "sp": false,
    "Set-Acl": false,
    "jq": false,
    "xargs": false,
    "eval": false,
    "Invoke-Expression": false,
    "iex": false,
    "/^kubectl\\s+(explain|get|cluster-info|top|describe|logs|auth|events|diff|wait|api-resources|api-versions|version?)\\b/": true,
}
```

## Extensions

Here is the list of extensions I usually use:

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
- [Groovy](https://marketplace.visualstudio.com/items?itemName=MellowMarshmallow.groovy)
- [tfsec](https://marketplace.visualstudio.com/items?itemName=tfsec.tfsec)
- [Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)

Here is how to install these extensions using the VS Code Quick Open (Ctrl+P):

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
ext install MellowMarshmallow.groovy
ext install tfsec.tfsec
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
code --install-extension MellowMarshmallow.groovy
code --install-extension tfsec.tfsec
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
