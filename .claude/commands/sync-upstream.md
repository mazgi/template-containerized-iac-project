# Sync with upstream template

Import and reflect features from the upstream template repository into this IaC-only repo.

## Upstream template

- Repository: https://github.com/mazgi/template-containerized-oauth2-project
- Branch: main

## Process

1. **Fetch the upstream file tree** from `https://api.github.com/repos/mazgi/template-containerized-oauth2-project/git/trees/main?recursive=1` to understand the full structure.

2. **Fetch IaC-relevant files** from the upstream using raw GitHub URLs (`https://raw.githubusercontent.com/mazgi/template-containerized-oauth2-project/main/{path}`). Focus on:
   - `Dockerfiles.d/iac/Dockerfile`
   - `compose.yaml` (iac service only)
   - `.example.env` and `.example.secrets.env` (IaC-relevant sections only)
   - `.github/workflows/iac.yaml`, `.github/workflows/iac.ephemeral.yaml`, `.github/workflows/_reusable-iac.yaml`
   - `.github/actions/bootstrap-tfstate-s3/action.yaml`, `.github/actions/bootstrap-tfstate-azurerm/action.yaml`, `.github/actions/bootstrap-tfstate-gcs/action.yaml`
   - `iac/aws/**/*.tf`, `iac/azure/**/*.tf`, `iac/google/**/*.tf`
   - `docs/*.md`

3. **Read the corresponding local files** in this repo to compare.

4. **Identify differences**, focusing on:
   - Provider version bumps (AWS, Azure, Google, and any new providers like awscc)
   - GitHub Actions version bumps (checkout, setup-terraform, cloud auth actions, paths-filter, etc.)
   - New Terraform resources or files (e.g. acm.tf, new outputs)
   - Dockerfile changes
   - compose.yaml changes (iac service only)
   - Environment file changes (IaC-relevant sections only)
   - Documentation updates
   - Workflow/action improvements

5. **Skip app-specific features** that belong only in the OAuth2 template:
   - Backend, web, android, apple, windows app layers
   - OAuth2/JWT/SMTP configuration (in .example.env, .example.secrets.env)
   - App-specific workflows (build, e2e tests)
   - App-specific Dockerfiles (backend, web, etc.)
   - App-specific compose services (backend, db, web, mailpit, etc.)

6. **Apply changes** to the local repo, reporting each change clearly.

7. **Show a summary** of all changes applied, organized by category.
