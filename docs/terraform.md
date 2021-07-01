# Terraform

## Basic actions

Initialize Terraform:

```bash
terraform init
# To use a file to describe backend configuration
terraform init -backend-config=backend.tfvars
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

Delete Terraform ressources:

```bash
terraform destroy -force
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

## Bonus

Format all your file following the same pattern:

```bash
terraform fmt
```

Install autocompletion:

```bash
terraform -install-autocomplete
```
