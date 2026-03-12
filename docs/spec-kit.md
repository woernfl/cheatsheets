# Spec Kit

## Basic actions

Install Spec Kit:

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

Initialize in existing project:

```bash
specify init . --ai copilot
```

Establish project principles:

```bash
/speckit.constitution Create principles focused on code quality, testing standards, user experience consistency, and performance requirements
```

Create the spec:

```bash
/speckit.specify Deploy a MongoDB cluster on my Kubernetes cluster, it has it's own namespace, focuse on reliability of the deployment, if there is a public helm chart use it
```

Create a technical implementation plan:

```bash
/speckit.plan the deployment uses ArgoCD, implement network policies using Cilium, if there is a public helm chart use it
```

Break down into tasks:

```bash
/speckit.tasks
```

Execute implementation:

```bash
/speckit.implement
```
