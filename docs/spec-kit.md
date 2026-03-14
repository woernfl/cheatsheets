# Spec Kit

## Core commands

### `/speckit.constitution`

Establishes the project governing principles. Defines your tech stack, coding standards, testing requirements, and overall architecture rules so the AI agent stays consistent across the entire project.

```bash
/speckit.constitution The aim of this project is to provide bleeding edge cheatsheets. Most of the files are in markdown. MkDocs, a static site generator, is used to transform the Markdown files to HTML/CSS/JavaScript files. The Material for MkDocs addon is used. All the files are built and hosted using Netlify. All the Markdown files are linted using pre-commit hooks and GitHub Actions.
```

### `/speckit.specify`

Defines what you want to build. You use this to outline the core requirements, user stories, and acceptance criteria for a new feature.

```bash
/speckit.specify Create a new cheatsheets page to document the use of Maven. As a user I should be able to find all the commands I have to type in a chronological order from the start of a project to the build and test of an artefact.
```

### `/speckit.plan`

Determines how to build it. Based on the specifications, this command forces the AI to draft a detailed technical implementation plan, including data models, file structures, and API interactions.

```bash
/speckit.plan Scout the internet to find the best Java/Maven development workflows. Compile your findings. Produce a markdown page containing the end result of your compilation. This page will follow the formatting of the other markdown pages that you will find in the docs folder of this repo.
```

### `/speckit.tasks`

Breaks the technical plan down into a granular, actionable task list.

```bash
/speckit.tasks
```

### `/speckit.implement`

Executes the code generation. The AI reads the task list and writes the actual code, systematically checking off tasks as they are completed.

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
