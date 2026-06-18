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
- `pi-loadout`: adds a `/loadout` command for choosing which tools and skills are active in the current Pi session.
- `pi-linter`: deterministic linter that renders findings above the input bar in pi.
- `pi-mcp-adapter`: use MCP servers with Pi.
- `@juicesharp/rpiv-web-tools`: let the model search the web and read pages.
- `@juicesharp/rpiv-ask-user-question`: ask clarifying questions instead of guessing.
- `@juicesharp/rpiv-advisor`: ask a stronger model for a second opinion before it acts.
- `@gotgenes/pi-permission-system`: provides permission gates over tool, bash, MCP, skill, and special operations.
- `@gotgenes/pi-subagents`: gives pi a focused, in-process sub-agent core.
- `@gotgenes/pi-subagents-worktrees`: git worktree isolation for `@gotgenes/pi-subagents`.
- `@kylebrodeur/pi-model-router`: intelligent per-turn model router extension.
- `pi-lmstudio`: integrating LM Studio with Pi, allowing you to use local LLMs.

### Installation

After installation, you may need to run `/reload` to activate the extensions.

```bash
pi install npm:pi-bar
pi install npm:pi-loadout
pi install npm:pi-linter
pi install npm:pi-mcp-adapter
pi install npm:@juicesharp/rpiv-web-tools
pi install npm:@juicesharp/rpiv-ask-user-question
pi install npm:@juicesharp/rpiv-advisor
pi install npm:@gotgenes/pi-permission-system
pi install npm:@gotgenes/pi-subagents
pi install npm:@gotgenes/pi-subagents-worktrees
pi install npm:@kylebrodeur/pi-model-router
pi install npm:pi-lmstudio
```

### Post Installation

Enable pi-linter rules (`pi-linter`):

```bash
/linter enable vague-opener
/linter enable pronoun-soup
/linter enable reactive-noop
/linter enable imperative-only
/linter enable scope-creep
/linter enable reversal
/linter enable unbounded-loop
/linter enable naked-review-paste
/linter enable review-drip
```

Check if all the rules have been enabled:

```bash
/linter status
```

Configure web searches (`@juicesharp/rpiv-web-tools`):

```bash
/web-tools
```

Configure the permission system extention (`~/.pi/agent/extensions/pi-permission-system/config.json`)(`@gotgenes/pi-permission-system`):

```bash
{
  "permission": {
    "*": "ask",
    "path": {
      "*": "allow",
      "*.env": "deny",
      "*.env.*": "deny",
      "*.env.example": "allow"
    },
    "read": "allow",
    "write": "deny",
    "edit": "deny",
    "web_search": "allow",
    "web_fetch": "ask",
    "bash": {
      "ls *": "allow",
      "ls": "allow",
      "pwd": "allow",
      "cat *": "allow",
      "head *": "allow",
      "tail *": "allow",
      "less *": "allow",
      "more *": "allow",
      "file *": "allow",
      "stat *": "allow",
      "wc *": "allow",
      "tree *": "allow",
      "tree": "allow",
      "realpath *": "allow",
      "basename *": "allow",
      "dirname *": "allow",
      "readlink *": "allow",
      "find *": "allow",
      "grep *": "allow",
      "rg *": "allow",
      "ag *": "allow",
      "fd *": "allow",
      "awk *": "allow",
      "sed *": "allow",
      "sort *": "allow",
      "uniq *": "allow",
      "cut *": "allow",
      "tr *": "allow",
      "diff *": "allow",
      "jq *": "allow",
      "yq *": "allow",
      "echo *": "allow",
      "printf *": "allow",
      "env": "allow",
      "printenv *": "allow",
      "printenv": "allow",
      "date *": "allow",
      "date": "allow",
      "whoami": "allow",
      "hostname": "allow",
      "uname *": "allow",
      "uname": "allow",
      "id": "allow",
      "uptime": "allow",
      "which *": "allow",
      "whereis *": "allow",
      "type *": "allow",
      "command -v *": "allow",
      "git *": "ask",
      "git status": "allow",
      "git status *": "allow",
      "git diff": "allow",
      "git diff *": "allow",
      "git log": "allow",
      "git log *": "allow",
      "git show": "allow",
      "git show *": "allow",
      "git branch": "allow",
      "git branch *": "allow",
      "git remote": "allow",
      "git remote *": "allow",
      "git rev-parse *": "allow",
      "git ls-files *": "allow",
      "git ls-files": "allow",
      "git ls-tree *": "allow",
      "git blame *": "allow",
      "git config --get *": "allow",
      "git config -l": "allow",
      "git tag": "allow",
      "git tag -l*": "allow",
      "git describe *": "allow",
      "git stash list": "allow",
      "git reflog": "allow",
      "git reflog *": "allow",
      "git shortlog *": "allow",
      "gh auth status": "allow",
      "gh repo view *": "allow",
      "gh pr view *": "allow",
      "gh pr list *": "allow",
      "gh issue view *": "allow",
      "gh issue list *": "allow",
      "sudo *": "ask",
      "curl * | sh": "ask",
      "curl * | bash": "ask",
      "wget * | sh": "ask",
      "wget * | bash": "ask",
      "rm -rf *": "deny",
      "rm -fr *": "deny",
      "chmod 777 *": "deny",
      ":(){ :|:& };:": "deny"
    },
    "mcp": { "mcp_status": "allow" },
    "skill": { "*": "ask" },
    "external_directory": "ask"
  }
}
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

Run a one-shot prompt with a specific model:

```bash
pi --model gemma-4-31b-qat:high -p "Commit to git. Follow conventional commit. Then push and open a PR on GitHub."
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
