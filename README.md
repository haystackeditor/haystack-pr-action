# PR Analysis Action

This GitHub Action automatically analyzes pull requests and provides an enhanced view through the Haystack service.

## Features

- Triggers AI-powered analysis when PRs are opened or updated
- Polls for completion status
- Automatically comments on the PR with results link
- Configurable API endpoints and polling settings

## Usage

Create a `.github/workflows/pr-analysis.yml` file in your repository:

```yaml
name: PR Analysis

on:
  pull_request:
    types: [opened, synchronize, reopened]

permissions:
  contents: read
  pull-requests: write

jobs:
  analyze-pr:
    runs-on: ubuntu-latest
    steps:
      - uses: your-username/pr-analysis-action@v1
```

## Configuration

You can customize the action with these optional inputs:

| Input | Description | Default |
|-------|-------------|---------|
| `api-endpoint` | API endpoint for the analysis service | https://8z9ssbamdj.execute-api.us-west-2.amazonaws.com/prod |
| `poll-interval` | Seconds between status checks | 5 |
| `max-attempts` | Maximum number of polling attempts | 60 |

Example with custom settings:

```yaml
- uses: your-username/pr-analysis-action@v1
  with:
    api-endpoint: 'https://custom-endpoint.example.com'
    poll-interval: '10'
    max-attempts: '30'
```

## Requirements

- The action needs `pull-requests: write` permission to comment on PRs
