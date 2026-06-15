# Pi Coding Agent

## Slash Commands

| Command             | Description                                                        |
| ------------------- | ------------------------------------------------------------------ |
| `/login`, `/logout` | Manage OAuth or API-key credentials                                |
| `/model`            | Switch models                                                      |
| `/scoped-models`    | Enable or disable models for cycling                               |
| `/settings`         | Configure thinking level, theme, delivery mode, and transport      |
| `/new`              | Start a new session                                                |
| `/session`          | Show session file, ID, token usage, and cost                       |
| `/compact`          | Compact older context, optionally with custom instructions         |
| `/reload`           | Reload keybindings, extensions, skills, prompts, and context files |
| `/hotkeys`          | Show all keyboard shortcuts                                        |
| `/quit`             | Exit Pi                                                            |

Skills are exposed as `/skill:$NAME`, and prompt templates are exposed as `/$NAME`.

## Keyboard Shortcuts

| Shortcut    | Description                           |
| ----------- | ------------------------------------- |
| `Alt+Enter` | Queue a follow-up message             |
| `Alt+Up`    | Restore queued messages to the editor |
| `Esc`       | Abort the current run                 |
| `Ctrl+P`    | Cycle to the next model               |
| `Shift+Tab` | Cycle thinking level                  |

Keybindings can be customized in `~/.pi/agent/keybindings.json`. After editing them, run `/reload`.

## Installation

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
- `pi-mcp-adapter`: use MCP servers with Pi.
- `pi-subagents`: lets Pi delegate work to focused child agents.
- `@juicesharp/rpiv-web-tools`: let the model search the web and read pages.
- `@juicesharp/rpiv-ask-user-question`: ask clarifying questions instead of guessing.
- `@juicesharp/rpiv-advisor`: ask a stronger model for a second opinion before it acts.
- `@gotgenes/pi-permission-system`: provides permission gates over tool, bash, MCP, skill, and special operations.
- `pi-lmstudio`: integrating LM Studio with Pi, allowing you to use local LLMs.

### Installation

After installation, you may need to run `/reload` to activate the extensions.

```bash
pi install npm:pi-bar
pi install npm:pi-mcp-adapter
pi install npm:pi-subagents
pi install npm:@juicesharp/rpiv-web-tools
pi install npm:@juicesharp/rpiv-ask-user-question
pi install npm:@juicesharp/rpiv-advisor
pi install npm:@gotgenes/pi-permission-system
pi install npm:pi-lmstudio
```

### Post Installation

Configure web searches:

```bash
/web-tools
```

## Starting a Session

Start Pi in the current project directory:

```bash
pi
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

## Context Files

Pi loads project instructions from:

- `~/.pi/agent/AGENTS.md`
- `AGENTS.md` in the current directory
- `AGENTS.md` or `CLAUDE.md` in parent directories

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
