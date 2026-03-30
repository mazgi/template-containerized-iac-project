# template-containerized-iac-project

A template project for Infrastructure as Code (IaC) using Terraform with containerized development, supporting AWS, Azure, and Google Cloud.

## Prerequisites

- Docker Engine + Docker Compose (e.g. [Docker Desktop](https://www.docker.com/products/docker-desktop/), [Podman](https://podman.io/), [Colima](https://github.com/abiosoft/colima))

## Quick Start

```sh
cp .example.env .env            # then fill in cloud provider settings
cp .example.secrets.env .secrets.env  # then fill in secrets
docker compose run --rm iac
```

## Use This Template

After creating a repository from this template:

1. Copy `.example.env` → `.env` and `.example.secrets.env` → `.secrets.env`, then fill in your cloud provider settings.
2. **Cloud deployment via CI** — Set up OIDC authentication, configure GitHub Actions variables, and run IaC workflows. See [CI](docs/ci.md) and [OIDC Setup](docs/oidc-setup.md).
3. **Manual cloud deployment** — Deploy directly with Terraform. See [Cloud Deployment](docs/cloud-deployment.md).

## Project Structure

```
.
├── compose.yaml
├── .example.env
├── .example.secrets.env
├── iac/                   # Terraform IaC (AWS, Azure, GCP)
├── Dockerfiles.d/
│   └── iac/               # IaC container Dockerfile
├── .github/               # GitHub Actions workflows + custom actions
└── docs/
```

## Documentation

- Cloud Deployment — [overview](docs/cloud-deployment.md) / [AWS](docs/cloud-deployment-aws.md) / [Azure](docs/cloud-deployment-azure.md) / [Google Cloud](docs/cloud-deployment-google.md)
- [CI / GitHub Actions](docs/ci.md) — workflows, required secrets and variables
- [Secrets Management](docs/secrets.md) — cloud provider secret stores (AWS, Azure, GCP)
- [OIDC Setup](docs/oidc-setup.md) — one-time cloud provider authentication setup
- [Environment Variables](.example.secrets.env) — secrets
- [GitHub Actions Variables](.example.env) — CI/CD and cloud deployment variables
