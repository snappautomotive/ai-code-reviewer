# Ollama Code Reviewer

A GitHub Action that uses the HTTP interface of an ollama installation to review pull request changes and post feedback as a comment.

## Features

- Analyzes code changes in pull requests
- Provides feedback on code quality, potential bugs, security issues, and performance
- Posts the review as a comment on the PR
- Ignores binary files and deleted files

## Setup

### Prerequisites

- Access to an ollama instance that has the appropriate model installed

### Usage

Add the following to your GitHub workflow file (e.g., `.github/workflows/code-review.yml`):

```yaml
name: Code Review

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Claude Code Review
        uses: snappautomotive/ollama-code-reviewer@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          url: ${{ secrets.OLLAMA_URL }}
          model: ${{ secrets.OLLAMA_MODEL }}
```

### Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `github-token` | GitHub token for API access | Yes | N/A |
| `url` | URL to access the ollama install | Yes | N/A |
| `model` | The AI model to use for the review | Yes | N/A |

## Development

1. Clone the repository
2. Install dependencies with `npm install`
3. Build the action with `npm run build`
4. Test with `npm test`

## License

MIT
