# Pi Coding Agent

## Slash Commands

| Command             | Description                                                        |
| ------------------- | ------------------------------------------------------------------ |
| `/login`, `/logout` | Manage OAuth or API-key credentials                                |
| `/model`            | Switch models                                                      |
| `/scoped-models`    | Enable or disable models for cycling                               |
| `/settings`         | Configure thinking level, theme, delivery mode, and transport      |
| `/resume`           | Pick from previous sessions                                        |
| `/new`              | Start a new session                                                |
| `/name <name>`      | Set the current session display name                               |
| `/session`          | Show session file, ID, token usage, and cost                       |
| `/tree`             | Jump to any point in the session tree                              |
| `/fork`             | Create a new session from an earlier user message                  |
| `/clone`            | Duplicate the current active branch into a new session             |
| `/compact [prompt]` | Compact older context, optionally with custom instructions         |
| `/copy`             | Copy the last assistant message                                    |
| `/export [file]`    | Export the session to HTML                                         |
| `/share`            | Upload the session as a private GitHub gist                        |
| `/reload`           | Reload keybindings, extensions, skills, prompts, and context files |
| `/hotkeys`          | Show all keyboard shortcuts                                        |
| `/changelog`        | Display version history                                            |
| `/quit`             | Exit Pi                                                            |

Skills are exposed as `/skill:$NAME`, and prompt templates are exposed as `/$NAME`.

## Keyboard Shortcuts

| Shortcut       | Description                                            |
| -------------- | ------------------------------------------------------ |
| `Enter`        | Submit the current input                               |
| `Shift+Enter`  | Insert a new line                                      |
| `Alt+Enter`    | Queue a follow-up message                              |
| `Alt+Up`       | Restore queued messages to the editor                  |
| `Esc`          | Abort the current run                                  |
| `Ctrl+D`       | Exit when the editor is empty                          |
| `Ctrl+G`       | Open the prompt in `$VISUAL` or `$EDITOR`              |
| `Ctrl+L`       | Open the model selector                                |
| `Ctrl+P`       | Cycle to the next model                                |
| `Shift+Ctrl+P` | Cycle to the previous model                            |
| `Shift+Tab`    | Cycle thinking level                                   |
| `Ctrl+O`       | Collapse or expand tool output                         |
| `Ctrl+V`       | Paste an image from the clipboard (`Alt+V` on Windows) |

Keybindings can be customized in `~/.pi/agent/keybindings.json`. After editing them, run `/reload`.

## Installation

Install Pi with npm:

```bash
npm install -g --ignore-scripts @earendil-works/pi-coding-agent
```

Install Pi with the official install script:

```bash
curl -fsSL https://pi.dev/install.sh | sh
```

Uninstall Pi:

```bash
npm uninstall -g @earendil-works/pi-coding-agent
```

## Extensions

Pi supports extensions that can enhance functionality.

Here are some useful extensions:

- `pi-bar`: status bar extension that shows useful information at the bottom of the interface.
- `pi-lmstudio`: integrating LM Studio with Pi, allowing you to use local LLMs.
- `pi-mcp-adapter`: use MCP servers with Pi 

### Installation

After installation, you may need to run `/reload` to activate the extensions.

```bash
pi install npm:pi-bar
pi install npm:pi-lmstudio
pi install npm:pi-mcp-adapter
```

## Starting a Session

Start Pi in the current project directory:

```bash
pi
```

Start Pi with an initial prompt:

```bash
pi "Summarize this repository and tell me how to run its checks."
```

Continue the most recent session:

```bash
pi -c
```

Browse and resume a previous session:

```bash
pi -r
```

Open a specific session:

```bash
pi --session $SESSION_ID
```

Run a one-shot prompt:

```bash
pi -p "Summarize this codebase"
```

Pipe stdin into a one-shot prompt:

```bash
cat README.md | pi -p "Summarize this text"
```

Reference files directly on the command line:

```bash
pi @README.md "Summarize this"
pi @src/app.ts @src/app.test.ts "Review these together"
```

## CLI Flags

| Flag                            | Description                                                             |
| ------------------------------- | ----------------------------------------------------------------------- |
| `-p`, `--print`                 | Print a response and exit                                               |
| `--mode json`                   | Output events as JSON lines                                             |
| `--mode rpc`                    | Run in RPC mode over stdin/stdout                                       |
| `-c`, `--continue`              | Continue the most recent session                                        |
| `-r`, `--resume`                | Browse and select a previous session                                    |
| `--session <path-or-id>`        | Open a specific session                                                 |
| `--fork <path-or-id>`           | Fork a session into a new one                                           |
| `--name <name>`                 | Set the session display name                                            |
| `--provider <name>`             | Select a provider such as `anthropic` or `openai`                       |
| `--model <pattern>`             | Select a model or model pattern                                         |
| `--thinking <level>`            | Set thinking level (`off`, `minimal`, `low`, `medium`, `high`, `xhigh`) |
| `--tools <list>`                | Allow only specific tools                                               |
| `--exclude-tools <list>`        | Disable specific tools                                                  |
| `--no-tools`                    | Disable all tools                                                       |
| `--skill <path>`                | Load a skill from a path                                                |
| `--prompt-template <path>`      | Load a prompt template from a path                                      |
| `--no-context-files`            | Disable `AGENTS.md` and `CLAUDE.md` discovery                           |
| `--append-system-prompt <text>` | Append custom system prompt text                                        |
| `-h`, `--help`                  | Show help                                                               |
| `-v`, `--version`               | Show version                                                            |

Built-in tools: `read`, `bash`, `edit`, `write`, `grep`, `find`, `ls`.

## Context Files

Pi loads project instructions from:

- `~/.pi/agent/AGENTS.md`
- `AGENTS.md` in the current directory
- `AGENTS.md` or `CLAUDE.md` in parent directories

Example `AGENTS.md`:

```markdown
# Project Instructions

- Run `npm run check` after code changes.
- Do not run production migrations locally.
- Keep responses concise.
```

Disable context file discovery with:

```bash
pi --no-context-files
```

## System Prompt Files

Replace the default system prompt with:

- `.pi/SYSTEM.md` for a project
- `~/.pi/agent/SYSTEM.md` globally

Append to the default prompt with `APPEND_SYSTEM.md` in either location.

## Prompt Templates

Pi loads prompt templates from:

- `~/.pi/agent/prompts/*.md`
- `.pi/prompts/*.md`
- package `prompts/` directories
- `--prompt-template <path>`

Example `.pi/prompts/review.md`:

```markdown
---
description: Review staged git changes
---

Review the staged changes (`git diff --cached`). Focus on:

- Bugs and logic errors
- Security issues
- Error handling gaps
```

This becomes the `/review` command inside Pi.

## Skills

Pi loads skills from:

- `~/.pi/agent/skills/`
- `~/.agents/skills/`
- `.pi/skills/`
- `.agents/skills/`
- `--skill <path>`

Skills are directories containing a `SKILL.md` file and are available as `/skill:$NAME`.

Example skill structure:

```text
my-skill/
├── SKILL.md
├── scripts/
└── references/
```

## Packages and Extensions

Manage Pi packages:

```bash
pi install <source>
pi remove <source>
pi update
pi list
pi config
```

Pi keeps the core intentionally small. Features such as custom workflows are typically added through extensions, skills, prompt templates, and packages rather than built into the core agent.
