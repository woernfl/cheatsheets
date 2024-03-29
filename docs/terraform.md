# Terraform

## Basic actions

Initialize Terraform:

```bash
terraform init
# To use a file to describe backend configuration
terraform init -backend-config=vars/dev.backend.tfvars
```

Check what will be modfied:

```bash
terraform plan -out=tfplan .
terraform plan -var-file=vars/dev.terraform.tfvars
```

Apply modifications:

```bash
terraform apply -var-file=vars/dev.terraform.tfvars -auto-approve
```

Get the list of existing ressources:

```bash
terraform state list
```

Apply modifications on a specific ressource:

```bash
terraform apply -target="aws_eks_node_group.eks-worker[\"node-group\"]" -var-file=vars/dev.terraform.tfvars -auto-approve
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

## Customize Terraform Error Messages

```bash
resource "aws_instance" "web" {
  # ...

  provisioner "local-exec" {
    command    = "echo The server's IP address is ${self.private_ip}"
    on_failure = fail("Custom error message")
  }
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

Visualizes the resource dependencies:

```bash
terraform graph | dot -Tsvg > graph.svg
```

Install autocompletion:

```bash
terraform -install-autocomplete
```

If you use TF in a CI system, set this env variable to adjusts TFs output to avoid suggesting specific commands to run next:

```bash
TF_IN_AUTOMATION: "true"
```
