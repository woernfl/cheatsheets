# AI Lab

## Prompt Library

### Home Lab

#### Hardware

```markdown
I have a home lab running on bare metal servers in my home.
Here is the list of all the hardware:

- 1 Unifi Dream Machine Pro (Main router)
- 1 Unifi USW Pro Aggregation (Top Of Rack Switch)
- 1 Unifi USW Enterprise 24 PoE
- 6 Raspberry Pi 5 (each has 8GB of RAM)
- 2 Minisforum MS-01 (each has a Intel Core i9-13900H and 2x16GB of RAM)
- 1 Supermicro SuperServer 2029TP-HC1R (4 independent nodes with each 2 Intel Xeon Gold 5120 CPU and 2x32GB of RAM) (There is 2 empty disk slots on each node) (This servers can be referred to as the storage servers)
- 1 Supermicro SYS-4028GR-TRT (2 Intel Xeon E5-2680, 6x64GB of RAM, 2 NVIDIA A40 GPUs) (This server can be referred to as the GPU server)
- 2 ASUS Ascent GX10 (each has 1 NVIDIA GB10 Grace Blackwell Superchip and 128GB of Unified System Memory) (This servers can be referred to as the spark servers)

No need to tell me that my setup is great. Just answer the question.
```

#### Software

```markdown
I have a home lab running in my home.
Everything is managed by a Kubernetes cluster except the DNS service which is running on separate nodes.
Here is a list of softwares I use in my Kubernetes cluster:

- Github to store all my code in git repos
- Renovate Bot to make sure I am always up to date
- Kubespray to manage the lifecycle of my Kubernetes cluster
- Debian as an OS of all my nodes
- ArgoCD to deploy everything
- Cilium CNI to manage Kubernetes internal networking
- Sealed Secrets to handle all the secrets
- Rook to provide persistent volumes
- Kube VIP to expose services outside of my kubernetes cluster
- Netbird to handle the VPN connection from outside
- Traefik to manage all the ingresses
- Cert Manager to manage all the certificate creations and renewal
- Home Assistant to automate my home with a few Zigbee, Matter and Wifi devices
- Homepage to regroup all the links I need in a single interface
- Kured to reboot Kubernetes nodes when they need to be rebooted following a package upgrade
- Jellyfin to watch films and movies
- Node Feature Discovery to enhance the labels on my hardware
- Mosquitto as a message broker for MQTT
- Zigbee2mqtt to handel the Zigbee devices connections
- Immich to host my picture
- Knative to serve workloads that can scale to 0
- Kourier to serve workloads managed by Knative
- NVIDIA Device Plugin to expose the NVIDIA GPUs (2xA40) I have in my cluster
- NVIDIA GPU Operator to expose the ASUS Ascent GX10 I have in my cluster.
- VLLM to serve LLMs (Scaling to 0 using Knative)
- Trivy Operator to scan the cluster
- Zot to proxy externally used docker images
- Grafana to visualize logs and metrics
- Loki to manage logs
- Alloy to centralize telemetry collection
- Prometheus to manage metrics

No need to tell me that my setup is great. Just answer the question.
```

#### Development

```markdown
I have a home lab running in my home.

Here is a list of softwares I use in my home lab:

- Github to store all my code in git repos
- VSCode
- pre-commit:
  - check-yaml
  - end-of-file-fixer
  - trailing-whitespace
  - check-added-large-files
  - debug-statements
  - check-json
  - check-executables-have-shebangs
  - check-shebang-scripts-are-executable
  - check-case-conflict
  - check-symlinks
  - destroyed-symlinks
  - check-merge-conflict
  - commitizen
  - gitleaks
  - yamllint
  - shellcheck
  - bashate
  - prettier
  - doctoc
  - markdownlint-cli2
  - cspell
  - renovate-config-validator
- CI:
  - renovate
  - prettier

No need to tell me that my setup is great. Just answer the question.
```

## AGENTS.md

Sample to put in the `AGENTS.md` file:

```markdown
# AGENTS.md

## Project Guidelines

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

### 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:

- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

### 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

### 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

### 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:

- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:

1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.
```

## MCP

Install MCP in VSCode:

```bash
code --add-mcp '{"name":"kubernetes","command":"npx","args":["-y", "kubernetes-mcp-server@latest"]}'
```

## VRAM Budget

Rule of thumb:

- 16-bit (FP16/BF16): 2 bytes per parameter
- 8-bit (INT8): 1 byte per parameter
- 4-bit (INT4/GGUF/EXL2): ~0.5 bytes per parameter
