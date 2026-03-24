# OpenCode

## TUI Slash Commands

Inside the TUI, type `/` to trigger a slash command:

| Command     | Description                                         |
| ----------- | --------------------------------------------------- |
| `/connect`  | Add a model provider and set API keys interactively |
| `/models`   | Switch or list available models                     |
| `/init`     | Scan project and generate/update `AGENTS.md`        |
| `/new`      | Start a new chat session                            |
| `/sessions` | Open session history and switch or resume sessions  |
| `/compact`  | Summarize the session to manage context length      |
| `/undo`     | Undo the last code change (git-based)               |
| `/redo`     | Redo the last undone code change (git-based)        |
| `/editor`   | Open your external editor to compose a prompt       |
| `/export`   | Export the session as Markdown or JSON              |
| `/share`    | Generate a share link for the current session       |
| `/unshare`  | Cancel a previously generated share link            |
| `/details`  | Toggle display of execution and tool details        |
| `/theme`    | Change the TUI theme                                |
| `/help`     | Show interactive command help                       |
| `/exit`     | Quit OpenCode                                       |

## Keyboard Shortcuts

The default leader key is `Ctrl+X`. Press the leader key followed by the next key to trigger an action.

| Shortcut            | Description                      |
| ------------------- | -------------------------------- |
| `Ctrl+C` / `Ctrl+D` | Exit the app                     |
| `<leader>q`         | Quit OpenCode                    |
| `<leader>n`         | Start a new session              |
| `<leader>l`         | List sessions                    |
| `<leader>e`         | Open external editor             |
| `<leader>m`         | Cycle available models           |
| `<leader>a`         | Show agent list                  |
| `<leader>b`         | Toggle sidebar                   |
| `<leader>t`         | List and change themes           |
| `<leader>x`         | Export session                   |
| `<leader>u`         | Undo last message                |
| `<leader>r`         | Redo last message                |
| `<leader>h`         | Show help dialog                 |
| `Ctrl+A`            | Move cursor to beginning of line |
| `Ctrl+E`            | Move cursor to end of line       |

## MCP (Model Context Protocol)

Add an MCP server:

```bash
opencode mcp add
```

Example `opencode.json` MCP configuration:

```json
{
  "mcp": {
    "servers": {
      "filesystem": {
        "type": "local",
        "command": "npx",
        "args": [
          "-y",
          "@modelcontextprotocol/server-filesystem",
          "/home/$USER/Documents"
        ]
      },
      "github": {
        "type": "local",
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-github"],
        "env": {
          "GITHUB_PERSONAL_ACCESS_TOKEN": "$GITHUB_TOKEN"
        }
      }
    }
  }
}
```

## Installation

Install using the official install script (Linux/macOS):

```bash
curl -fsSL https://opencode.ai/install | bash
```

Install via Homebrew (macOS/Linux):

```bash
brew install opencode-ai/tap/opencode
```

Verify the installation:

```bash
opencode --version
```

## Starting a Session

Launch the interactive TUI:

```bash
opencode
```

Run a one-shot prompt without opening the TUI:

```bash
opencode run "$PROMPT"
```

Attach a TUI client to a running remote OpenCode server:

```bash
opencode attach $SERVER_URL
```

## CLI Flags

| Flag           | Description                                      |
| -------------- | ------------------------------------------------ |
| `--version`    | Print the current version                        |
| `--print-logs` | Print logs to stderr                             |
| `--log-level`  | Set log level (`debug`, `info`, `warn`, `error`) |
| `-h`, `--help` | Show help                                        |

## Authentication

Authenticate to a model provider:

```bash
opencode auth login
```

List all configured providers and their auth status:

```bash
opencode auth list
```

## Models

List all available models from configured providers:

```bash
opencode models
```

## Sessions

List all session histories:

```bash
opencode session list
```

## Configuration

OpenCode is configured via `opencode.json`. Place it in the project root (project-scoped) or `~/.config/opencode/opencode.json` (user-scoped).

```json
{
  "model": "anthropic/claude-opus-4-5",
  "theme": "opencode",
  "keybinds": {
    "leader": "ctrl+x",
    "app_exit": "ctrl+c,ctrl+d,<leader>q",
    "editor_open": "<leader>e",
    "session_new": "<leader>n",
    "session_list": "<leader>l"
  }
}
```

## Project Context (AGENTS.md)

Initialize an `AGENTS.md` file to give OpenCode persistent project context:

```bash
/init
```

This creates an `AGENTS.md` in the repo root. Add project-specific conventions, architecture notes, and instructions:

```markdown
# Project Context

## Architecture

- Backend: Node.js + Express
- Database: PostgreSQL
- Frontend: React

## Conventions

- Use kebab-case for file names
- Run `npm test` before committing
```

## Custom Commands

Create reusable commands as Markdown files in `.opencode/commands/`:

```bash
mkdir -p .opencode/commands
```

Example `.opencode/commands/review.md`:

```markdown
Review the following code for bugs, security issues, and style violations:

$ARGUMENTS
```

Arguments are passed when invoking the command. Use `$ARGUMENTS`, `$1`, `$2`, etc., as placeholders.

Shell command output can be injected into prompts with `!$COMMAND`:

```
!git diff HEAD
```
