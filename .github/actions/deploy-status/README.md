# PR Deployment Status Dashboard

## Overview

This GitHub Action automatically adds and updates a comment to Pull Requests showing the deployment status across all environments. It creates a nicely formatted table that displays the current status of all deployments, including environment details, status, branch/commit information, deployment author, timestamp, deployment URL, and environment availability.

The action helps teams quickly understand:

- Current deployment status across environments
- Which environments are occupied by other branches/PRs
- Which environments are available for deployment of the current PR
- Whether the current PR is already deployed to specific environments

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

### Availability Status

The dashboard includes an "Availability" column that shows one of these statuses:

- ✓ Currently deployed from this PR - This PR is currently deployed to this environment
- ⚠️ Occupied by [branch-name] - Another branch is deployed to this environment
- 🔄 Deployment failed, can be redeployed - A failed deployment that can be retried
- ✅ Available for deployment - Environment is free for deployment

### Outputs

This action doesn't produce any outputs.
