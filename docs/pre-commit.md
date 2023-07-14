# pre-commit

## Installation

Install pre-commit:

```bash
pip install pre-commit
```

## pre-commit configuration

Add a `.pre-commit-config.yaml` file in the root of your repo.

### pre-commit configuration

#### Base

Prereq:

- [terraform-docs](https://github.com/terraform-docs/terraform-docs)
- [tfsec](https://github.com/aquasecurity/tfsec)
- [tflint](https://github.com/terraform-linters/tflint)

Here is the content of the `.pre-commit-config.yaml` file:

```yaml
repos:
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
      - id: detect-aws-credentials
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

#### Terraform

Prereq:

- [terraform-docs](https://github.com/terraform-docs/terraform-docs)
- [tfsec](https://github.com/aquasecurity/tfsec)
- [tflint](https://github.com/terraform-linters/tflint)

Here is the content of the `.pre-commit-config.yaml` file:

```yaml
repos:
  - repo: https://github.com/antonbabenko/pre-commit-terraform
    rev: v1.81.0
    hooks:
      - id: terraform_fmt
        args:
          - --args=-recursive
      - id: terraform_docs
        args:
          - --args=--config=.terraform-docs.yml
      - id: terraform_tflint
        args:
          - --args=--disable-rule="terraform_deprecated_interpolation"
      - id: terraform_validate
      - id: terraform_tfsec
      - id: checkov
```

## How to manually run pre-commit

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
