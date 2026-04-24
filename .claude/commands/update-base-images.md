Update base Docker image versions in all Dockerfiles under `Dockerfiles.d/`.

## Steps

1. List all `FROM` lines across `Dockerfiles.d/*/Dockerfile`.
2. For each image, check the latest stable version:
   - `hashicorp/terraform`: check https://releases.hashicorp.com/terraform/
3. Update each `FROM` line.
4. Do not change `:latest` or `:nonroot` suffix tags. Only update the version portion.
5. Show a summary of changes and remind the user to rebuild.
