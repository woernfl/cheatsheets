# Elephant-Goldfish Model (EGM)

[Elephant-Goldfish Model (EGM)](https://github.com/google/elephant-goldfish-model) is an open-source plugin for AI coding assistants for designing and reviewing software with agents.

- **Elephant** holds your project context and drafts the specification.
- **Goldfish** reviewers examine the draft with fresh eyes, without the earlier conversation, exposing unstated assumptions and blind spots.
- **You** resolve trade-offs and approve the specification before implementing.

## Workflow

The built-in workflow targets software specifications. For other documents, choose reviewers and standards with `/egm-review-loop`.

```text
/egm-brainstorm  ->  /egm-draft  ->  /egm-review  ->  implement
```

Commands are shown without a prefix. In Antigravity (agy CLI) and Claude Code, add the `/egm:` prefix, for example `/egm:egm-brainstorm`. In Codex, select the corresponding EGM skill from the skill picker.

### Brainstorm

Explore an idea and write a concept brief:

```text
/egm-brainstorm Add webhook delivery to this project.
```

Discuss requirements and trade-offs with the agent. Fresh reviewers challenge the proposal, and the agent saves the agreed direction in `concepts_brief.md`.

### Draft

Turn the brief into a design document:

```text
/egm-draft
```

The agent turns the brief into `design_draft.md`, pausing after each section for your feedback in chat.

### Review

Review the draft with fresh reviewers:

```text
/egm-review design_draft.md
```

Use the draft path returned by the agent. Fresh reviewers check the design, its clarity, its fit with the code, and its implementation plan. Choose which findings to address. When you approve the design, ask your coding agent to implement it.

Save approved specifications under `docs/designs/`.

### Resolve

Work through review findings and agree on changes. Run it in the session that produced the document, and provide the target file, a line range, and the aggregated findings list:

```text
/egm-resolve design_draft.md lines 1-120
```

Each finding is categorized as **CONTEST** (the critique is inaccurate; the agent cites evidence), **ACCEPT** (the agent applies a textual repair), or **NEGOTIATE** (the agent presents options and waits for your decision).

### Bootstrap

Create or update `README.md` contract files across a directory tree of an existing codebase:

```text
/egm-bootstrap src/services/
```

The agent writes leaf-level component READMEs (**Peanuts**) and parent-level repository blueprints (**Hay**) that roll up child interfaces. It only writes documentation — no source code and no git commits. Use `target_filename` to write to an alternate name such as `EGM.md` when existing human-maintained READMEs must not be modified.

### Review loop

Run a configured group of reviewers against a document with specific reviewer and standard combinations — useful for documents other than software specifications:

```text
/egm-review-loop docs/designs/webhooks.md full file reviewers=design_critic,comprehension standards=feature-spec-standard
```

Reviewers (for example `design_critic`, `structural`, `style`, `implementation_readiness`, `comprehension`) audit the document in fresh contexts, then the Elephant context resolves the findings. Standards map reviewers to document standards such as `feature-spec-standard` or `implementation-readiness-standard`.

## Reviewing Existing Documents

A 60-second review of an existing design document, README, or PR plan against the live code — no new specification required.

**Review an existing document:**

```text
/egm:egm-review docs/designs/webhooks.md
```

**Check for drift** between checked-in documents and the current source code:

```text
/egm:egm-drift-report docs/designs/
```

The agent compares each document in the folder with the current source code and reports where they diverge. You decide whether to update the document or the code.

## Skills

| Skill        | Use it to…                                                      |
| ------------ | --------------------------------------------------------------- |
| Brainstorm   | Test an idea and write a concept brief.                         |
| Draft        | Turn a brief or existing notes into a design document.          |
| Resolve      | Work through review findings and agree on changes.              |
| Bootstrap    | Create or update documentation for an existing codebase.        |
| Review       | Review a design with fresh agents across five stages.           |
| Review loop  | Run a configured group of reviewers for a specific review task. |
| Drift report | Compare checked-in documents with the current source code.      |

## Roles

| Role         | Context                                                                           | Responsibility                                                            |
| ------------ | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Elephant** | Your project, requirements, and earlier decisions                                 | Explore the problem and draft the specification.                          |
| **Goldfish** | The document and its referenced source material, without the earlier conversation | Find missing assumptions, unclear requirements, and implementation risks. |
| **You**      | The goals and constraints that matter                                             | Resolve trade-offs, approve the design, and decide what to build.         |

## Limitations

- Brainstorming and review require a session that can create fresh subagents.
- A review does not replace tests or human judgment.
- Bootstrap and drift reporting apply to software codebases.

## Links

- [Repository](https://github.com/google/elephant-goldfish-model)
- [Website](https://egm.dev)
