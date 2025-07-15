# Cheatsheets

This repository contains a collection of technical reference documents and cheatsheets for various tools, platforms, and technologies. It's built using [MkDocs](https://www.mkdocs.org/) with the [Material theme](https://squidfunk.github.io/mkdocs-material/).

## Content

The documentation covers a wide range of technologies and tools:

- AWS (CLI, CDK)
- Bash
- Certificates and security (OpenSSL, GPG)
- Containers
- Git and GitHub
- Jenkins and CI/CD
- Kubernetes and Helm
- Various programming languages and tools (Python, Node.js, Maven)
- DevOps tools (Terraform, Vault)
- And much more...

## Local Development

### Prerequisites

- Python 3.x
- Pip

### Setup

1. Clone this repository
2. Install the required packages:

```bash
pip install -r requirements.txt
```

### Running Locally

To serve the documentation locally:

```bash
mkdocs serve
```

This will start a local server at http://127.0.0.1:8000/

### Building the Documentation

To build the static site:

```bash
mkdocs build
```

The built site will be in the `site` directory.

## Deployment

This documentation is configured to deploy to Netlify. The configuration is defined in the `netlify.toml` file.

## Contributing

Contributions are welcome! To add a new cheatsheet:

1. Create a new markdown file in the `docs` directory
2. Follow the existing format and style
3. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgment

Thanks to [Martin Donath (@squidfunk)](https://github.com/squidfunk) for providing the [Material for MkDocs template](https://squidfunk.github.io/mkdocs-material/) which this site is built on top of.
