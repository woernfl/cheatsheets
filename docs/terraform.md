# Terraform

## Basic actions

Initialize Terraform:

```bash
terraform init
# To use a file to describe backend configuration
terraform init -backend-config=dev.backend.tfvars
```

Check what will be modfied:

```bash
terraform plan -out=tfplan .
terraform plan -var-file=dev.terraform.tfvars
```

Apply modifications:

```bash
terraform apply -var-file=dev.terraform.tfvars -auto-approve
```

Apply modifications on a specific ressource:

```bash
terraform apply -target="aws_eks_node_group.eks-worker" -var-file=dev.terraform.tfvars -auto-approve
```

Delete Terraform ressources:

```bash
terraform destroy -force
```

## Exposing the content of a file as a viarable

```bash
locals {
  config = yamldecode(file("./config.yaml"))
}
```

## Terraform Cloud

Generate user token and put it in the `~/.terraformrc` file like that:

```bash
credentials "app.terraform.io" {
  token = "$TF_CLOUD_TOKEN"
}
```

## To debug

Set TF_LOG env variable:

```bash
export TF_LOG=TRACE
```

Test the output of an internal Terraform function:

```bash
# Drops you in an interactive shell
terraform console
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

If you use TF in a CI system, set this env variable to adjusts TFs output to avoid suggesting specific commands to run next:

```bash
TF_IN_AUTOMATION: "true"
```
