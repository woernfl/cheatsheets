# GitHub Copilot

## Installation

Install the GitHub Copilot extension in VS Code:

```text
ext install GitHub.copilot
ext install GitHub.copilot-chat
```

Or via terminal:

```bash
code --install-extension GitHub.copilot
code --install-extension GitHub.copilot-chat
```

## Keyboard Shortcuts

### Inline Suggestions

| Shortcut             | Description                           |
| -------------------- | ------------------------------------- |
| `Tab`                | Accept the current inline suggestion  |
| `Esc`                | Dismiss the current inline suggestion |
| `Alt+]` / `Option+]` | Show next inline suggestion           |
| `Alt+[` / `Option+[` | Show previous inline suggestion       |
| `Ctrl+Enter`         | Open Copilot completions panel        |
| `Alt+\` / `Option+\` | Trigger inline suggestion manually    |

### Chat

| Shortcut                    | Description                       |
| --------------------------- | --------------------------------- |
| `Ctrl+Alt+I` / `Ctrl+Cmd+I` | Open Copilot Chat panel           |
| `Ctrl+I`                    | Open inline chat in the editor    |
| `Ctrl+Shift+I`              | Open Copilot Chat in a new window |

## Chat Slash Commands

| Command        | Description                                     |
| -------------- | ----------------------------------------------- |
| `/explain`     | Explain how the selected code works             |
| `/fix`         | Propose a fix for bugs in the selected code     |
| `/tests`       | Generate unit tests for the selected code       |
| `/doc`         | Add documentation comments to the selected code |
| `/simplify`    | Simplify the selected code                      |
| `/new`         | Scaffold a new workspace or file                |
| `/newNotebook` | Create a new Jupyter notebook                   |
| `/clear`       | Start a new chat session                        |
| `/help`        | Show available slash commands and chat tips     |

## Chat Variables

Reference context directly in your chat prompts using `#` variables:

| Variable               | Description                                          |
| ---------------------- | ---------------------------------------------------- |
| `#file`                | Reference a specific file from the workspace         |
| `#editor`              | Reference the currently active editor content        |
| `#selection`           | Reference the current text selection                 |
| `#terminalSelection`   | Reference the current terminal selection             |
| `#terminalLastCommand` | Reference the last terminal command and output       |
| `#codebase`            | Search across the entire codebase for relevant files |
| `#sym`                 | Reference a specific symbol (function, class, etc.)  |

Example usage:

```text
Explain how authentication works in #file:src/auth.ts
```

## Chat Participants

Prefix your message with `@` to target a specific agent:

| Participant  | Description                                                    |
| ------------ | -------------------------------------------------------------- |
| `@workspace` | Ask questions about the entire workspace/codebase              |
| `@vscode`    | Ask questions about VS Code settings, commands, and extensions |
| `@terminal`  | Get help with shell commands and terminal usage                |
| `@github`    | Search GitHub repositories, issues, PRs and docs               |

Example usage:

```text
@workspace Where is the database connection configured?
@vscode How do I change the default terminal shell?
```

## Agent Mode

Agent mode lets Copilot autonomously plan and execute multi-step tasks across your codebase.

Enable agent mode by selecting **Agent** from the chat mode dropdown, then describe your task:

```text
Create a REST API endpoint for user registration with validation and tests
```

Copilot will iteratively run tools (read files, run commands, edit code) and ask for confirmation before applying changes.

## MCP (Model Context Protocol)

MCP servers extend Copilot's capabilities with external tools and data sources.

### Configure MCP in VS Code

Edit your VS Code settings (`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`) or create `.vscode/mcp.json` in the workspace root:

```json
{
  "mcp": {
    "servers": {
      "filesystem": {
        "type": "stdio",
        "command": "npx",
        "args": [
          "-y",
          "@modelcontextprotocol/server-filesystem",
          "/home/$USER/Documents"
        ]
      },
      "github": {
        "type": "stdio",
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-github"],
        "env": {
          "GITHUB_PERSONAL_ACCESS_TOKEN": "$GITHUB_TOKEN"
        }
      },
      "postgres": {
        "type": "stdio",
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-postgres", "$DATABASE_URL"]
      },
      "fetch": {
        "type": "stdio",
        "command": "uvx",
        "args": ["mcp-server-fetch"]
      }
    }
  }
}
```

Place `.vscode/mcp.json` in your repository to share the MCP configuration with your team. Secrets (env vars) are resolved at runtime from your environment and are not stored in the file.

### MCP Server Types

| Type    | Description                                            |
| ------- | ------------------------------------------------------ |
| `stdio` | Spawns a local process communicating over stdin/stdout |
| `sse`   | Connects to a remote server via Server-Sent Events     |

### Manage MCP Servers

List, enable, or disable MCP servers from the VS Code Chat view using the tools icon (⚙️) or via the Command Palette (`Ctrl+Shift+P`):

```text
MCP: List Servers
MCP: Add Server
```
