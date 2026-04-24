Update all dependency versions across the project. Run each category in order, showing a summary of changes at the end.

## 1. Docker base images

Check and update `FROM` lines in `Dockerfiles.d/iac/Dockerfile`:

| Image | Files |
|-------|-------|
| `hashicorp/terraform` | iac/Dockerfile |

Check the latest version at https://releases.hashicorp.com/terraform/. Do not change `:latest` tags.

## 2. Terraform providers

Update provider version constraints in:

- `iac/aws/versions.tf` and `iac/aws/ephemeral/versions.tf`
- `iac/azure/versions.tf` and `iac/azure/ephemeral/versions.tf`
- `iac/google/versions.tf` and `iac/google/ephemeral/versions.tf`

Check the latest versions at the Terraform Registry:
- `hashicorp/aws` — https://registry.terraform.io/providers/hashicorp/aws/latest
- `hashicorp/awscc` — https://registry.terraform.io/providers/hashicorp/awscc/latest
- `hashicorp/azurerm` — https://registry.terraform.io/providers/hashicorp/azurerm/latest
- `hashicorp/google` — https://registry.terraform.io/providers/hashicorp/google/latest
- `hashicorp/random` — https://registry.terraform.io/providers/hashicorp/random/latest

Keep the `~>` pessimistic constraint operator but update the minor version floor.

## 3. GitHub Actions

Update action version tags in all files under `.github/workflows/` and `.github/actions/`:

Key actions to check:
- `actions/checkout`
- `aws-actions/configure-aws-credentials`, `aws-actions/amazon-ecr-login`
- `azure/login`
- `google-github-actions/auth`, `google-github-actions/setup-gcloud`
- `hashicorp/setup-terraform`
- `dorny/paths-filter`

Check the latest major version tag for each on GitHub. Only bump major versions if there are no known breaking changes.

## 4. Summary

After all updates, show a table summarizing:
- What was updated (dependency name)
- Old version → New version
- Files changed

Remind the user to:
- Rebuild Docker images
- Review any major version bumps for breaking changes
