# public-gh-workflows

## Update Kirby CMS

```yml
name: Update Kirby CMS

on:
  workflow_dispatch:
    inputs:
      updates:
        description: 'JSON-Objekt mit Paketnamen und Versionen (z. B. {"getkirby/cms":"4.7.1","filp/whoops":"2.18.0"})'
        required: true

jobs:
  call-shared:
    uses: bold-and-bright/public-gh-workflows/.github/workflows/update-kirby.yml@main
    with:
      updates: ${{ inputs.updates }}
    secrets:
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## Deploy Kirby CMS

`Place a maintenance.php file under .github/workflows/ to be used as a temporary index.php during deployment`

```yml
name: Kirby Deployment

on:
  push:
    branches:
      - main
      - stage

jobs:
  deploy:
    uses: bold-and-bright/public-gh-workflows/.github/workflows/deploy-kirby.yml@main
    with:
      branch: ${{ github.ref_name }}
    secrets:
      PROD_HOST: ${{ secrets.PROD_HOST }}
      PROD_USER: ${{ secrets.PROD_USER }}
      PROD_PASSWORD: ${{ secrets.PROD_PASSWORD }}
      PROD_REMOTE_PATH: ${{ secrets.PROD_REMOTE_PATH }}
      PROD_SFTP: ${{ secrets.PROD_SFTP }}
      STAGE_HOST: ${{ secrets.STAGE_HOST }}
      STAGE_USER: ${{ secrets.STAGE_USER }}
      STAGE_PASSWORD: ${{ secrets.STAGE_PASSWORD }}
      STAGE_REMOTE_PATH: ${{ secrets.STAGE_REMOTE_PATH }}
      STAGE_SFTP: ${{ secrets.STAGE_SFTP }}
```

## Deploy NUXT

`Place a maintenance.html file under .github/workflows/ to be used as a temporary index.html during deployment`

```yml
name: Kirby Deployment

on:
  push:
    branches:
      - main
      - stage

jobs:
  deploy:
    uses: bold-and-bright/public-gh-workflows/.github/workflows/deploy-nuxt.yml@main
    with:
      branch: ${{ github.ref_name }}
    secrets:
      PROD_HOST: ${{ secrets.PROD_HOST }}
      PROD_USER: ${{ secrets.PROD_USER }}
      PROD_PASSWORD: ${{ secrets.PROD_PASSWORD }}
      PROD_REMOTE_PATH: ${{ secrets.PROD_REMOTE_PATH }}
      PROD_SFTP: ${{ secrets.PROD_SFTP }}
      STAGE_HOST: ${{ secrets.STAGE_HOST }}
      STAGE_USER: ${{ secrets.STAGE_USER }}
      STAGE_PASSWORD: ${{ secrets.STAGE_PASSWORD }}
      STAGE_REMOTE_PATH: ${{ secrets.STAGE_REMOTE_PATH }}
      STAGE_SFTP: ${{ secrets.STAGE_SFTP }}
```
