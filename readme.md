# Alder AI Security Agent

AI-powered security analysis for your code repositories using Large Language Models.

Visit our website: [https://alderagent.com/](https://alderagent.com/)

## Features

- **AI-Powered Analysis**: Uses LLMs to detect security vulnerabilities
- **Comprehensive Coverage**: Analyzes 10 security categories including authentication, authorization, injection attacks, XSS, and more
- **Detailed Reports**: Generates comprehensive reports in markdown
- **Easy Integration**: Simply add to your existing GitHub Actions workflow

## Prerequisites

1. **API Key Required**: This action requires an API key to run. Purchase scan credits at [alderagent.com/](https://alderagent.com/).
2. **GitHub Secret**: After obtaining your API key, add it as a repository secret named `ALDER_API_KEY`.

## Usage

Add this action to your GitHub workflow:

```yaml
name: Security Analysis

on:
  # Allows manual triggering from the Actions tab
  workflow_dispatch:

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Run Alder AI Security Agent
        uses: adamsmith6300/alder-gha@v1.0.6 # Use the appropriate version
        with:
          api-key: ${{ secrets.ALDER_API_KEY }}  # Required API key
          extra-ignore-dirs: 'dist,build,docs' # Optional: Comma-separated list of extra directories to ignore
          create-issues: 'true'              # Optional: Set to true to create GitHub issues
          github-token: ${{ secrets.GITHUB_TOKEN }}       # Required if create-issues is true
          github-repository: ${{ github.repository }} # Required if create-issues is true

      - name: Upload security reports
        uses: actions/upload-artifact@v4
        with:
          name: security-reports
          path: './security-reports'
```

## Setting Up the API Key

1. Purchase scan credits at [alderagent.com/](https://alderagent.com/)
2. Copy the API key provided after purchase. **It will be sent to the email address used during checkout.**
3. In your GitHub repository:
   - Go to Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name: `ALDER_API_KEY`
   - Value: Your API key
   - Click "Add secret"

## Inputs

| Input                | Description                            | Required | Default |
|---------------------|----------------------------------------|----------|---------|
| `api-key` | Your Alder Security Agent API key | Yes       | N/A   |
| `extra-ignore-dirs` | Comma-separated list of additional directory names to ignore (e.g., 'data,tmp,specific_folder'). Optional. | No | `''` |
| `create-issues`     | Set to `'true'` to create GitHub issues for discovered vulnerabilities. Issues will be labeled with `security-alder`. | No       | `'false'` |
| `github-token`      | GitHub token for creating issues. Only needed if `create-issues` is `true`. | Conditionally | `${{ secrets.GITHUB_TOKEN }}` |
| `github-repository` | Repository slug (owner/repo) where issues should be created. Only needed if `create-issues` is `true`. | Conditionally | `${{ github.repository }}` |

**Note on `extra-ignore-dirs`**: Be careful when adding directories to this list. Any directory matching a name provided here (e.g., `data`) will be completely ignored during the scanning process, including all of its subdirectories and files. This can significantly affect the analysis results if directories containing source code or relevant configuration are inadvertently excluded.

**Note on `github-token` and `github-repository`**: These inputs are only necessary if you enable the `create-issues` option. The default values shown are standard GitHub Actions contexts and should typically be sufficient for creating issues in the same repository where the workflow runs.

## Default Settings

The action uses these default settings:
- Output Directory: `./security-reports`
- Report Format: markdown
- All Security Categories: Analyzed

## Security Categories Analyzed

- Authentication
- Authorization
- Injection attacks
- Cross-site scripting (XSS)
- Data protection
- API security
- Configuration issues
- Cryptography
- Client-side vulnerabilities
- Business logic flaws

## Pricing

Alder AI Security Agent uses a pay-per-scan pricing model to cover costs, with all scans purchased through our website:

Visit our [website](https://alderagent.com/) to purchase scan credits. After purchase, you'll receive an API key to use with the GitHub Action.

## Support

For support with this GitHub Action:
- Email: [adam@alderagent.com](mailto:adam@alderagent.com)
- GitHub Issues: [Create an issue](https://github.com/adamsmith6300/alder-gha/issues)

## Privacy and Data

This action does not store your code or vulnerability findings. All analysis is performed using AI models, and your code is not used to train the models. For more details, please read our [Privacy Policy](PRIVACY-POLICY.md).

## License

[MIT License](LICENSE)

