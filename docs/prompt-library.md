# Prompt Library

## Home Lab

### Hardware

```markdown
I have a home lab running on bare metal servers in my home.
Here is the list of all the hardware:
- 1 Unifi Dream Machine Pro (Main router)
- 1 Unifi USW Pro Aggregation (Top Of Rack Switch)
- 1 Unifi USW Enterprise 24 PoE
- 6 Raspberry Pi 5 (each has 8GB of RAM)
- 2 Minisforum MS-01 (each has a Intel Core i9-13900H and 2x16GB of RAM)
- 1 Supermicro SuperServer 2029TP-HC1R (4 independant nodes with each 2 Intel Xeon Gold 5120 CPU and 2x32GB of RAM) (There is 2 empty disk slots on each node) (This servers can be refred to as the storage servers)
- 1 DGX Spark (each has 1 NVIDIA GB10 Grace Blackwell Superchip and 128GB of Unified System Memory) (This servers can be refred to as the spark servers)
- 1 Supermicro SYS-4028GR-TRT (2 Intel Xeon, 6x64GB of RAM, 2 NVIDIA A40 GPUs) (This server can be refered to as the GPU server)

No need to tell me that my setup is great. Just answer the question.
```

### Software

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
- Nvidia Device Plugin to expose the NVIDIA GPUs (2xA40) I have in my cluster
- VLLM to serve LLMs (Scaling to 0 using Knative)

No need to tell me that my setup is great. Just answer the question.
```

### Development

```markdown
I have a home lab running in my home.

Here is a list of softwares I use in my home lab:
- Github to store all my code in git repos
- VSCode
- pre-commit
- CI:
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

No need to tell me that my setup is great. Just answer the question.
```
