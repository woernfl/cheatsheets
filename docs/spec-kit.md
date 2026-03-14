# Spec Kit

## Core commands

### `/speckit.constitution`

Establishes project's governing principles. Defines your tech stack, coding standards, testing requirements, and overall architecture rules so the AI agent stays consistent across the entire project.

Example 

```bash
/speckit.constitution The aim of this project is to provide bleeding edge cheatsheets. Most of the files are un markdown. Mkdocs, a static site generator, is used to transform the Markdown files in HTML/CSS/JavaScript files. The Material for MkDocs addon is used. All the files are build and hosted using Netlify. All the Markdown files are linted using pre-commit hooks and GitHub actions.
```

Create the spec:

```bash
/speckit.specify Deploy a MongoDB cluster on my Kubernetes cluster, it has it's own namespace, focuse on reliability of the deployment, if there is a public helm chart use it
```

Create a technical implementation plan:

```bash
/speckit.plan the deployment uses ArgoCD, implement network policies using Cilium, if there is a public helm chart use it
```

Break down into tasks:

```bash
/speckit.tasks
```

Execute implementation:

```bash
/speckit.implement
```

## Initialisation

Install Spec Kit:

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

Initialize in existing project:

```bash
specify init . --ai copilot
```
