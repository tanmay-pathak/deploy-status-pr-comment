# PR Deployment Status Dashboard

## Overview

This GitHub Action automatically adds and updates a comment to Pull Requests showing the deployment status across all environments. It creates a nicely formatted table that displays the current status of all deployments, including environment details, status, branch/commit information, deployment author, timestamp, and deployment URL.

## Usage

To use this action in your workflow, add the following step to your `.github/workflows/[workflow_file].yml`:

```yaml
- name: Add Deployment Status to PR
  uses: your-org/your-repo/.github/actions/deploy-status@v1
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    timezone: 'America/New_York'
```

### Inputs

| Parameter | Description | Required | Default |
|-----------|-------------|----------|---------|
| github-token | GitHub token used to create/update comments | true | ${{ github.token }} |
| timezone | Timezone for date formatting (IANA time zone format) | false | 'America/Regina' |

### Outputs

This action doesn't produce any outputs.
