# Haystack Code Reviewer

Haystack Code Reviewer automatically analyzes and segments pull requests, and creates a nice canvas view you can use to take a "guided tour" of the PR. This action will automatically trigger Haystack Code Reviewer for all new PRs in your repo, and comment the appropriate link on that PR.

## Features

- Creates an AI-powered "guided tour" on an infinite canvas whenever PRs are opened or updated
- Automatically comments on the PR with link
- Configurable polling settings

## Usage

Create a `.github/workflows/haystack-code-reviewer.yml` file in your repository:

```yaml
name: Haystack Code Reviewer

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
      - uses: haystackeditor/haystack-pr-action@v1
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
