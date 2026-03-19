# Project Guidelines

## Overview

Personal technical cheatsheet site built with MkDocs + Material theme, deployed via Netlify to `cheatsheets.woernfl.xyz`. Content is command/reference-heavy — optimized for quick lookup, not tutorials.

## Build and Test

```bash
pip install -r requirements.txt
mkdocs serve          # Dev server on localhost:8000
mkdocs build          # Build to site/
```

Deployment: Netlify runs `mkdocs build` and publishes `site/` on push.

## Content Conventions

- **One cheatsheet per topic** as a markdown file in `docs/`.
- **No frontmatter** — MkDocs derives page names from the H1 heading.
- **Structure**: `# Page Title` → `## Section` → `### Subsection`. Keep prose minimal; prioritize scannable commands and examples.
- **Code blocks**: Always use fenced blocks with a language tag (` ```bash `, ` ```json `, etc.). Use `$VARIABLE_NAME` for placeholders.
- **No admonitions** in practice — keep the style consistent with existing pages.
- **Images** go in `docs/assets/images/` with relative paths.

## Configuration

- Theme, extensions, plugins are configured in `mkdocs.yml`.
- Navigation is **auto-generated** — no manual `nav:` section; adding a file to `docs/` is sufficient.

## When Adding a New Cheatsheet

1. Create `docs/<topic>.md` with an `# H1` title.
2. Follow the structure of existing files (e.g., `git.md`, `kubernetes.md`) for style reference.
3. No other config changes needed — MkDocs picks it up automatically.

## Before Pushing

Run the following steps before every push:

1. **Format with Prettier** — mandatory, run on every modified file:
   ```bash
   npx prettier --write docs/<file>.md
   ```
2. **Verify the build** — ensure MkDocs can build without errors:
   ```bash
   mkdocs build --no-strict
   ```
