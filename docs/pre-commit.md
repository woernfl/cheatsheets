# pre-commit

## Installation

Install pre-commit:

```bash
pip install pre-commit
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
    rev: v3.5.2
    hooks:
      - id: commitizen
        stages: [commit-msg]
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: check-added-large-files
      - id: check-executables-have-shebangs
      - id: check-json
      - id: check-symlinks
      - id: check-toml
      - id: check-yaml
        args:
          - "--allow-multiple-documents"
      - id: detect-private-key
      - id: end-of-file-fixer
      - id: pretty-format-json
        args:
          - "--autofix"
          - "--indent=2"
          - "--no-sort-keys"
      - id: trailing-whitespace
        args:
          - "--markdown-linebreak-ext=md"
```

### Markdown

```yaml
repos:
  # ========================================================
  # = Markdown
  # ========================================================
  - repo: https://github.com/igorshubovych/markdownlint-cli
    rev: v0.35.0
    hooks:
      - id: markdownlint
        args: ["--disable", "MD013", "MD033", "MD034", "--"]
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
    rev: v2.10.0
    hooks:
      - id: hadolint-docker
        entry: hadolint/hadolint:v2.8.0 hadolint
```

### Terraform

Prerequisite:

- [Docker](https://docs.docker.com/get-docker/)

Here is the content of the `.pre-commit-config.yaml` file:

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
        entry: -v "./:/data" -w /data hashicorp/terraform
        args: ["fmt", "-recursive"]
        pass_filenames: false
      - id: terraform-validate
        name: Terraform validate
        language: docker_image
        entry: -v "./:/data" -w /data hashicorp/terraform
        args: ["validate"]
        pass_filenames: false
      - id: terraform-docs
        name: Terraform docs
        language: docker_image
        entry: -v "./:/terraform-docs" quay.io/terraform-docs/terraform-docs:latest
        args:
          ["--config=/terraform-docs/.terraform-docs.yml", "/terraform-docs"]
        pass_filenames: false
      - id: terraform-lint
        name: Terraform lint
        language: docker_image
        entry: -v "./:/data" ghcr.io/terraform-linters/tflint
        args:
          ["--chdir=/data", "--disable-rule=terraform_deprecated_interpolation"]
        pass_filenames: false
      - id: terraform-tfsec
        name: Terraform tfsec
        language: docker_image
        entry: aquasec/tfsec
        args: ["/src"]
        pass_filenames: false
```

### IAC

Prerequisite:

- [Docker](https://docs.docker.com/get-docker/)

Here is the content of the `.pre-commit-config.yaml` file:

```yaml
repos:
  # ========================================================
  # = IAC
  # ========================================================
  - repo: local
    hooks:
      - id: iac-checkov
        name: IAC checkov
        language: docker_image
        entry: -v ./:/tf bridgecrew/checkov
        args: ["--directory", "/tf"]
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
