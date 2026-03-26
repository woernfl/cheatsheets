# Spec Kit

## Available Slash Commands

### Core commands

Essential commands for the Spec-Driven Development workflow:

| Command                 | Description                                                              |
| ----------------------- | ------------------------------------------------------------------------ |
| `/speckit.constitution` | Create or update project governing principles and development guidelines |
| `/speckit.specify`      | Define what you want to build (requirements and user stories)            |
| `/speckit.plan`         | Create technical implementation plans with your chosen tech stack        |
| `/speckit.tasks`        | Generate actionable task lists for implementation                        |
| `/speckit.implement`    | Execute all tasks to build the feature according to the plan             |

### Optional Commands

Additional commands for enhanced quality and validation:

| Command              | Description                                                                                                                          |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `/speckit.clarify`   | Clarify underspecified areas (recommended before `/speckit.plan`; formerly `/quizme`)                                                |
| `/speckit.analyze`   | Cross-artifact consistency & coverage analysis (run after `/speckit.tasks`, before `/speckit.implement`)                             |
| `/speckit.checklist` | Generate custom quality checklists that validate requirements completeness, clarity, and consistency (like "unit tests for English") |

## Examples

### `/speckit.constitution`

```text
/speckit.constitution The aim of this project is to provide bleeding edge cheatsheets. Most of the files are in markdown. MkDocs, a static site generator, is used to transform the Markdown files to HTML/CSS/JavaScript files. The Material for MkDocs theme is used. All the files are built and hosted using Netlify. All the Markdown files are linted using pre-commit hooks and GitHub Actions.
```

### `/speckit.specify`

```bash
/speckit.specify Create a new cheatsheets page to document the use of Maven. As a user I should be able to find all the commands I have to type in a chronological order from the start of a project to the build and test of an artefact.
```

### `/speckit.plan`

```bash
/speckit.plan Scout the internet to find the best Java/Maven development workflows. Compile your findings. Produce a markdown page containing the end result of your compilation. This page will follow the formatting of the other markdown pages that you will find in the docs folder of this repo.
```

### `/speckit.tasks`

```bash
/speckit.tasks
```

### `/speckit.implement`

```bash
/speckit.implement
```

## Initialization

Install Spec Kit:

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

Initialize in existing project:

```bash
specify init . --ai copilot
```
