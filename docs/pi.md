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

## Pi Installation

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

- `pi-footer`: statusline extension for pi.
- `pi-loadout`: adds a `/loadout` command for choosing which tools and skills are active in the current Pi session.
- `pi-linter`: deterministic linter that renders findings above the input bar in pi.
- `pi-mcp-adapter`: use MCP servers with Pi.
- `@juicesharp/rpiv-web-tools`: let the model search the web and read pages.
- `@juicesharp/rpiv-ask-user-question`: ask clarifying questions instead of guessing.
- `@juicesharp/rpiv-advisor`: ask a stronger model for a second opinion before it acts.
- `@gotgenes/pi-permission-system`: provides permission gates over tool, bash, MCP, skill, and special operations.
- `@gotgenes/pi-subagents`: gives pi a focused, in-process sub-agent core.
- `@gotgenes/pi-subagents-worktrees`: git worktree isolation for `@gotgenes/pi-subagents`.
- `@pi-unipi/notify`; push notifications when things happen.
- `pi-lmstudio`: integrating LM Studio with Pi, allowing you to use local LLMs.

### Installation

After installation, you may need to run `/reload` to activate the extensions.

```bash
pi install npm:pi-footer
pi install npm:pi-loadout
pi install npm:pi-linter
pi install npm:pi-mcp-adapter
pi install npm:@juicesharp/rpiv-web-tools
pi install npm:@juicesharp/rpiv-ask-user-question
pi install npm:@juicesharp/rpiv-advisor
pi install npm:@gotgenes/pi-permission-system
pi install npm:@gotgenes/pi-subagents
pi install npm:@gotgenes/pi-subagents-worktrees
pi install npm:@pi-unipi/notify
pi install npm:pi-lmstudio
```

### Post Installation

#### pi-footer

File to modify: `~/.pi/agent/extensions/pi-footer.json`:

```json
{
  "version": 1,
  "enabled": true,
  "preset": "default",
  "lines": [
    [
      {
        "id": "model-provider-mqkmgzr8-a69yw3",
        "type": "model-provider",
        "enabled": true,
        "options": {
          "raw": false,
          "icon": "",
          "fg": "yellow",
          "bg": "default",
          "bold": false
        }
      },
      {
        "id": "thinking-level-mqkmgzr8-nu19hx",
        "type": "thinking-level",
        "enabled": true,
        "options": {
          "raw": false,
          "hideWhenEmpty": false,
          "icon": "",
          "text": "",
          "fg": "default",
          "bg": "default",
          "bold": false
        }
      },
      {
        "id": "context-mqknp2ad-7m5n9n",
        "type": "context",
        "enabled": true,
        "options": {
          "raw": false,
          "icon": "",
          "fg": "green",
          "bg": "default",
          "bold": false,
          "contextConditionalColors": false,
          "contextWarningPercent": 70,
          "contextDangerPercent": 90,
          "warningFg": "yellow",
          "warningBg": "default",
          "dangerFg": "red",
          "dangerBg": "default"
        }
      }
    ],
    [
      {
        "id": "cwd-mqknjnms-ja69vr",
        "type": "cwd",
        "enabled": true,
        "options": {
          "raw": false,
          "icon": "",
          "fg": "magenta",
          "bg": "default",
          "bold": false,
          "cwdDisplayStyle": "full-home",
          "segments": 2
        }
      },
      {
        "id": "git-branch-mqknims8-f95pb8",
        "type": "git-branch",
        "enabled": true,
        "options": {
          "raw": false,
          "hideWhenEmpty": false,
          "icon": "",
          "text": "",
          "fg": "cyan",
          "bg": "default",
          "bold": false,
          "gitBranchDisplayStyle": "round-brackets",
          "surroundLeft": "",
          "surroundRight": ""
        }
      }
    ]
  ],
  "separator": "pipe",
  "separatorFg": "default",
  "separatorBg": "default",
  "iconMode": "text",
  "minimalist": true,
  "terminal": {
    "widthMode": "full",
    "colorLevel": "ansi256"
  },
  "extensionStatusRow": {
    "hiddenKeys": [],
    "knownKeys": ["loadout"]
  }
}
```

#### pi-linter

Use slash commands directly in `pi`:

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

#### @juicesharp/rpiv-web-tools

Use slash commands directly in `pi`:

```bash
/web-tools
```

#### @gotgenes/pi-permission-system

File to modify: `~/.pi/agent/extensions/pi-permission-system/config.json`:

```json
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
    "find": "allow",
    "ls": "allow",
    "grep": "allow",
    "web_search": "allow",
    "web_fetch": "allow",
    "advisor": "allow",
    "ask_user_question": "allow",
    "bash": {
      "xargs *": "allow",
      "pre-commit *": "allow",
      "gh pr create *": "allow",
      "gh --version*": "allow",
      "curl *": "allow",
      "cp *": "allow",
      "kubectl get *": "allow",
      "kubectl logs *": "allow",
      "kubectl describe *": "allow",
      "helm repo *": "allow",
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
      "curl -o *": "ask",
      "curl -O *": "ask",
      "rm -rf *": "deny",
      "rm -fr *": "deny",
      "chmod 777 *": "deny",
      ":(){ :|:& };:": "deny"
    },
    "mcp": { "mcp_status": "allow" },
    "skill": { "*": "allow" },
    "external_directory": "ask"
  }
}
```

#### @pi-unipi/notify

File to modify: `~/.unipi/config/notify/config.json`:

```json
{
  "defaultPlatforms": ["native"],
  "events": {
    "workflow_end": {
      "enabled": false,
      "platforms": []
    },
    "ralph_loop_end": {
      "enabled": false,
      "platforms": []
    },
    "mcp_server_error": {
      "enabled": false,
      "platforms": []
    },
    "agent_end": {
      "enabled": false,
      "platforms": []
    },
    "memory_consolidated": {
      "enabled": false,
      "platforms": []
    },
    "session_shutdown": {
      "enabled": false,
      "platforms": []
    },
    "ask_user_prompt": {
      "enabled": true,
      "platforms": []
    }
  },
  "native": {
    "enabled": true,
    "suppressWhenFocused": true
  },
  "gotify": {
    "enabled": false,
    "priority": 5
  },
  "telegram": {
    "enabled": false
  },
  "ntfy": {
    "enabled": false,
    "serverUrl": "https://ntfy.sh",
    "priority": 3
  },
  "recap": {
    "enabled": false,
    "model": "openrouter/openai/gpt-oss-20b"
  }
}
```

### Updates

Core:

```bash
pi update
```

Extensions:

```bash
pi update --extensions
```

Everything:

```bash
pi update --all
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
