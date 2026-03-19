# Claude Code

## Installation

Install Claude Code:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

## Starting a Session

Start an interactive session in the current directory:

```bash
claude
```

Pipe file contents to Claude:

```bash
cat $FILE | claude -p "$PROMPT"
```

Continue the most recent conversation:

```bash
claude -c
```

Resume a specific session by ID:

```bash
claude -r $SESSION_ID "$PROMPT"
```

## CLI Flags

| Flag | Description |
|------|-------------|
| `-p "$PROMPT"` | Non-interactive mode (print result and exit) |
| `-c` | Continue the most recent conversation |
| `-r $SESSION_ID` | Resume a session by ID |
| `--model $MODEL` | Specify Claude model (e.g. `claude-opus-4-5`, `claude-sonnet-4-5`) |
| `--add-dir $PATH` | Add an extra directory to the working context |
| `--output-format text/json/stream-json` | Choose the output format |
| `--max-turns $N` | Limit agent turns in non-interactive mode |
| `--allowedTools $TOOLS` | Comma-separated list of tools Claude may use |
| `--disallowedTools $TOOLS` | Comma-separated list of tools Claude may not use |
| `--append-system-prompt "$TEXT"` | Append custom instructions to the system prompt |
| `--allow-dangerously-skip-permissions` | Skip permission prompts (use with caution) |

Update Claude Code to the latest version:

```bash
claude update
```

## Slash Commands

| Command | Description |
|---------|-------------|
| `/bug` | Report a bug in the current session |
| `/clear` | Clear conversation history and start fresh |
| `/compact [instructions]` | Summarize context to save tokens while keeping key info |
| `/config` | Open settings (theme, output format, model, etc.) |
| `/cost` | Display API usage and estimated cost for the session |
| `/doctor` | Run diagnostics and environment validation |
| `/exit` | Exit the Claude Code session |
| `/help` | Show all available slash commands |
| `/init` | Create a `CLAUDE.md` project memory file in the repo root |
| `/mcp` | List connected MCP servers and their status |
| `/memory` | View or manage project and session memory |
| `/model` | Switch the Claude model for the current session |
| `/permissions` | Manage tool permissions |
| `/pr_comments` | Review pull request comments |
| `/release` | Trigger a release workflow |
| `/review` | Run a code review on recent changes |
| `/status` | Show session and configuration status |
| `/vim` | Toggle Vim keybindings |

## Keyboard Shortcuts

| Shortcut | Description |
|----------|-------------|
| `Ctrl+C` | Interrupt Claude's current response |
| `Ctrl+D` | Exit the session |
| `Esc` | Cancel/escape current output |
| `Esc` `Esc` | Open the rewind menu to undo recent changes |
| `Shift+Tab` | Toggle auto-accept mode |
| `Ctrl+G` | Open the prompt in an external editor |
| `Option+T` / `Alt+T` | Enable extended thinking mode |
| `Option+P` / `Alt+P` | Open the model picker |

## Project Memory (CLAUDE.md)

Initialize a `CLAUDE.md` file to give Claude persistent project context:

```bash
/init
```

This creates a `CLAUDE.md` in the repo root. Add project-specific conventions, architecture notes, and instructions that Claude will read at the start of every session:

```markdown
# Project Context

## Architecture
- Backend: Node.js + Express
- Database: PostgreSQL
- Frontend: React

## Conventions
- Use kebab-case for file names
- All functions must have JSDoc comments
- Run `npm test` before committing
```

## Custom Slash Commands

Create reusable project commands as markdown files:

- **Project-level** (version-controlled): `.claude/commands/$COMMAND_NAME.md`
- **User-level** (all projects): `~/.claude/commands/$COMMAND_NAME.md`

Example `.claude/commands/deploy-prod.md`:

```markdown
---
description: Deploy the application to production
---
Run the following steps to deploy:
1. Run `npm run build`
2. Run the test suite with `npm test`
3. Deploy using `./scripts/deploy.sh production`
Report any errors and ask before proceeding to the next step.
```

This creates a `/deploy-prod` slash command inside Claude Code.

## MCP (Model Context Protocol)

### Add an MCP Server via CLI

Add a local stdio-based MCP server:

```bash
claude mcp add --transport stdio $SERVER_NAME -- $COMMAND $ARGS
```

Add a remote HTTP-based MCP server:

```bash
claude mcp add --transport http $SERVER_NAME $SERVER_URL
```

Add a server to a specific scope:

```bash
claude mcp add --scope user --transport stdio $SERVER_NAME -- $COMMAND $ARGS
claude mcp add --scope project --transport http $SERVER_NAME $SERVER_URL
```

| Scope | Visibility | Config file |
|-------|-----------|-------------|
| `local` | Current project, current user only | `.claude/settings.local.json` |
| `project` | Current project, all team members | `.claude/settings.json` |
| `user` | All projects for current user | `~/.claude.json` |

### Manage MCP Servers

List all configured MCP servers:

```bash
claude mcp list
```

Remove an MCP server:

```bash
claude mcp remove $SERVER_NAME
```

### Configure MCP via Config File

Edit `~/.claude.json` (user scope) or `.claude/settings.json` (project scope):

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/home/$USER/Documents"],
      "env": {}
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "$GITHUB_TOKEN"
      }
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres", "$DATABASE_URL"],
      "env": {}
    }
  }
}
```

Restart Claude Code after editing the config file for changes to take effect.
