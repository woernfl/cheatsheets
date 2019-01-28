---
layout: default
title: Terraform
nav_order: 2
---

# Terraform Cheatsheet

Initialize Terraform:

```bash
terraform init
```

Check what will be modfied:

```bash
terraform plan
```

Apply modifications:

```bash
terraform apply -auto-approve
```

Delete Terraform ressources:

```bash
terraform destroy -force
```

Install autocompletion:

```bash
terraform -install-autocomplete
```