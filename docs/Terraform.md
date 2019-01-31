---
layout: default
title: Terraform
parent: Home
---

# Terraform Cheatsheet

## Basic actions

Initialize Terraform:

```bash
terraform init
<<<<<<< HEAD
#To use a file to describe backend configuration
terraform init -backend-config=backend.tfvars
=======
terraform init -backend-config=backend.tfvars #To use a file to describe backend configuration
>>>>>>> cec169855827e60a3eec60bc3f7cfe3474b2ad23
```

Check what will be modfied:

```bash
terraform plan -out=tfplan .
```

Apply modifications:

```bash
terraform apply -auto-approve plan
```

Delete Terraform ressources:

```bash
terraform destroy -force
```

## To debug

Set TF_LOG env variable:

```bash
export TF_LOG=TRACE
```

## Bonus

Format all your file following the same pattern:

```bash
terraform fmt
```

Install autocompletion:

```bash
terraform -install-autocomplete
```
