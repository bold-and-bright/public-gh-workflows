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
    uses: bold-and-bright/public-gh-workflows/.github/workflows
/update-kirby.yml@main
    with:
      updates: ${{ inputs.updates }}
    secrets:
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```