# Markdownlint Configuration Guide

## Disabling and Enabling Rules for Parts of a Document

### Disable All Rules

```markdown
<!-- markdownlint-disable -->

This section will not be linted.

<!-- markdownlint-enable -->
```

### Disable Specific Rules

```markdown
<!-- markdownlint-disable MD001 MD005 -->

This section will ignore rules MD001 and MD005.

<!-- markdownlint-enable MD001 MD005 -->
```

### Disable Rules for the Current Line

```markdown
This line will ignore MD009. <!-- markdownlint-disable-line no-trailing-spaces -->
```

### Disable Rules for the Next Line

```markdown
<!-- markdownlint-disable-next-line no-hard-tabs -->

    This line will ignore rule MD010 (no-hard-tabs).
```

### Capture and Restore Rule Configuration

You can capture the current rule configuration, disable rules temporarily,
and then restore the original configuration.

```markdown
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

This section will not be linted.

<!-- markdownlint-restore -->
```

The initial configuration is captured by default, so you can simplify this:

```markdown
<!-- markdownlint-disable -->

This section will not be linted.

<!-- markdownlint-restore -->
```

---

## Disabling and Enabling Rules for Entire Files

You can disable or enable rules for an entire file using the following comments.
These changes apply regardless of where the comment is placed in the file.

### Disable All Rules for a File

```markdown
<!-- markdownlint-disable-file -->
```

### Enable All Rules for a File

```markdown
<!-- markdownlint-enable-file -->
```

### Disable Specific Rules for a File

```markdown
<!-- markdownlint-disable-file MD001 MD005 -->
```

### Enable Specific Rules for a File

```markdown
<!-- markdownlint-enable-file MD001 MD005 -->
```

---

## Configuring Rules for a File

You can configure rules for an entire file using the
`markdownlint-configure-file` comment. This is useful for overriding rule
settings for a specific file.

### Example: Configure Horizontal Rule Style

```markdown
<!-- markdownlint-configure-file {
  "hr-style": {
    "style": "---"
  }
} -->
```

### Example: Disable Multiple Rules

```markdown
<!-- markdownlint-configure-file {
  "no-trailing-spaces": false,
  "line-length": false
} -->
```

---

## Example `.markdownlint.yaml` Configuration File

Below is an example `.markdownlint.yaml` file that disables some common rules
and configures others. This file can be placed in the root of your project to
enforce consistent Markdown styling.

```yaml
# Default state for all rules
default: true

# Disable specific rules
MD013: false # Line length
MD033: false # Inline HTML
MD034: false # Bare URL used
MD041: false # First line in a file should be a top-level heading

# Configure rules
MD007:
  indent: 4 # Unordered list indentation

MD003:
  style: "atx_closed" # Heading style

MD004:
  style: "dash" # Unordered list style

MD029:
  style: "ordered" # Ordered list item prefix
```

### Equivalent `.markdownlint.json` Configuration

If you prefer JSON, here is the equivalent `.markdownlint.json` file:

```json
{
  "default": true,
  "MD013": false,
  "MD033": false,
  "MD034": false,
  "MD041": false,
  "MD007": {
    "indent": 4
  },
  "MD003": {
    "style": "atx_closed"
  },
  "MD004": {
    "style": "dash"
  },
  "MD029": {
    "style": "ordered"
  }
}
```
