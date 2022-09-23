# Desription

Repository for general workflows in the getprotocolab repo that handles CI/CD tasks

## How to use

You need to setup 2 workflow files. 1 for PR's and 1 for push.
The PR workflow will handle adding info to PR requests like argocd diff and linting.
The push workflow will handle building and deploying images.

### on_pr

We will create 2 action files (one for pr and one for push).
for the push one create a file called `.github/workflows/getprotocollab-push.yml`

```yaml
on: [push]

concurrency:
  group: ${{ github.ref }}

jobs:
  push_workflow:
    uses: GETProtocolLab/workflows/.github/workflows/on_pr.yml@master
    secrets: inherit
    with:
      image: ghcr.io/getprotocollab/oesophagus
      argocd_app_name: { { YOUR APP NAME IN ARGOCD } }
```

for the pr one create a file called `.github/workflows/getprotocollab-pr.yml`

```yaml
permissions:
  id-token: write
  pull-requests: write

on:
  pull_request:
    types: [opened, synchronize, reopened]

concurrency:
  group: ${{ github.ref }}
  cancel-in-progress: true

jobs:
  pr_workflow:
    uses: GETProtocolLab/workflows/.github/workflows/on_pr.yml@master
    secrets: inherit
```

## Lint

```bash
docker run --rm -v $(pwd):/work tmknom/prettier --write .
```
