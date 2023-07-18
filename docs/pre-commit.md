# pre-commit

## Installation

Install pre-commit:

```bash
pip install pre-commit
```

Install the git hook scripts:

```bash
pre-commit install
```

## pre-commit configuration

Add a `.pre-commit-config.yaml` file in the root of your repo.

### Base

```yaml
repos:
  # ========================================================
  # = Base
  # ========================================================
  # - repo: meta
  #   hooks:
  #     - id: check-hooks-apply
  #     - id: check-useless-excludes
  - repo: https://github.com/commitizen-tools/commitizen
    rev: 3.5.3
    hooks:
      - id: commitizen
        stages: [commit-msg]
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: check-added-large-files
      - id: check-json
      - id: check-yaml
        args:
          - "--allow-multiple-documents"
      - id: detect-private-key
      - id: end-of-file-fixer
      - id: trailing-whitespace
        args:
          - "--markdown-linebreak-ext=md"
  - repo: https://github.com/streetsidesoftware/cspell-cli
    rev: v6.31.0
    hooks:
      - id: cspell
        args:
          - "--config cspell.config.yaml"
  - repo: https://github.com/pre-commit/mirrors-prettier
    rev: "v3.0.0"
    hooks:
      - id: prettier
        stages: [pre-commit]
```

#### cspell

How to start a dictionary in an existing project:

```bash
docker run -v $PWD:/workdir ghcr.io/streetsidesoftware/cspell:latest --words-only --unique "**/*.md" | sort --ignore-case > project-words.txt
```

### Secret

```yaml
repos:
  # ========================================================
  # = Secret
  # ========================================================
  - repo: local
    hooks:
      - id: secretlint
        name: secretlint
        language: docker_image
        entry: secretlint/secretlint:latest secretlint
```

### Markdown

```yaml
repos:
  # ========================================================
  # = Markdown
  # ========================================================
  - repo: https://github.com/thlorenz/doctoc
    rev: v2.2.0
    hooks:
      - id: doctoc
  - repo: https://github.com/igorshubovych/markdownlint-cli
    rev: v0.35.0
    hooks:
      - id: markdownlint
        args: ["--disable", "MD013", "MD033", "MD034", "--"]
```

### yaml

```yaml
repos:
  # ========================================================
  # = yaml
  # ========================================================
  - repo: https://github.com/adrienverge/yamllint.git
    rev: v1.32.0
    hooks:
      - id: yamllint
        # files: (\.yaml|\.yml)$
```

### Shell

```yaml
repos:
  # ========================================================
  # = Shell
  # ========================================================
  - repo: https://github.com/koalaman/shellcheck-precommit
    rev: v0.9.0
    hooks:
      - id: shellcheck
```

### Docker container

```yaml
repos:
  # ========================================================
  # = Docker container
  # ========================================================
  - repo: https://github.com/hadolint/hadolint.git
    rev: v2.12.0
    hooks:
      - id: hadolint-docker
        entry: hadolint/hadolint hadolint
```

### Terraform

```yaml
repos:
  # ========================================================
  # = Terraform
  # ========================================================
  - repo: local
    hooks:
      - id: terraform-fmt
        name: Terraform fmt
        language: docker_image
        entry: -v "./:/data" -w /data hashicorp/terraform:latest
        args: ["fmt", "-recursive"]
        pass_filenames: false
        files: (\.tf|\.tfvars)$
        exclude: \.terraform\/.*$
      - id: terraform-docs
        name: Terraform docs
        language: docker_image
        entry: quay.io/terraform-docs/terraform-docs:latest
        args: ["/src/"]
        pass_filenames: false
        files: (\.tf|\.terraform\.lock\.hcl)$
        exclude: \.terraform\/.*$
      - id: terraform-lint
        name: Terraform lint
        language: docker_image
        entry: ghcr.io/terraform-linters/tflint:latest
        args:
          [
            "--chdir=/src/",
            "--disable-rule=terraform_deprecated_interpolation",
          ]
        pass_filenames: false
        files: (\.tf|\.tfvars)$
        exclude: \.terraform\/.*$
      - id: terraform-tfsec
        name: Terraform tfsec eks cluster
        language: docker_image
        entry: aquasec/tfsec:latest
        args: ["/src/"]
        pass_filenames: false
```

### IAC

```yaml
repos:
  # ========================================================
  # = IAC
  # ========================================================
  - repo: local
    hooks:
      - id: iac-checkov
        name: IAC checkov eks cluster
        language: docker_image
        entry: bridgecrew/checkov:latest
        args: ["--directory", "/src/", "--quiet"]
        pass_filenames: false
```

## How to manually run pre-commit

A single pre-commit:

```bash
pre-commit run $PRE-COMMIT_ID
```

All pre-commits:

```bash
pre-commit run -a
```

## How to update hooks to the latest version

```bash
pre-commit autoupdate
```

## How to skip hooks on commit

```bash
git commit --no-verify -m "$COMMIT_MESSAGE"
```
