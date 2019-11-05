# Autocompletion

A list of commande to enable autocompletion for things I use everyday:

```bash
echo "complete -C '$(which aws_completer)' aws" >> ~/.bashrc
echo "source <(kubectl completion bash)" >> ~/.bashrc
echo "source <(helm completion bash)" >> ~/.bashrc
echo "source <(minikube completion bash)" >> ~/.bashrc
echo "source <(skaffold completion bash)" >> ~/.bashrc
terraform -install-autocomplete
```
