# Claude Code Review Workflow

This repository includes an automated code review workflow powered by Claude AI.

## Setup Instructions

To enable the Claude code review workflow, you need to add your Anthropic API key as a GitHub secret:

### 1. Get an Anthropic API Key

1. Go to [Anthropic Console](https://console.anthropic.com/)
2. Sign up or log in
3. Navigate to API Keys section
4. Create a new API key

### 2. Add the API Key to GitHub Secrets

1. Go to your repository on GitHub
2. Click on **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Name: `ANTHROPIC_API_KEY`
5. Value: Paste your Anthropic API key
6. Click **Add secret**

## How It Works

The workflow automatically triggers when:
- A pull request is opened
- New commits are pushed to an existing pull request
- A pull request is reopened

### What It Does

1. **Fetches the PR diff** - Gets all changes in the pull request
2. **Checks diff size** - Ensures the diff isn't too large (max 100KB)
3. **Sends to Claude** - Submits the diff to Claude Sonnet 4.5 for review
4. **Posts review** - Adds a comment to the PR with Claude's analysis

### Review Content

Claude provides:
- Summary of changes
- Potential issues or bugs
- Security concerns
- Code quality suggestions
- Best practices recommendations

## Limitations

- Maximum diff size: 100KB
- For larger PRs, the workflow will post a warning suggesting to break it into smaller PRs
- Reviews are automated and should be used as a complement to human review, not a replacement

## Customization

You can customize the workflow by editing `.github/workflows/claude-code-review.yml`:

- Change the Claude model version
- Adjust the review prompt
- Modify the diff size limit
- Add additional checks or steps

## Permissions

The workflow requires:
- `contents: read` - To read the repository code
- `pull-requests: write` - To post comments on PRs

These permissions are already configured in the workflow file.
