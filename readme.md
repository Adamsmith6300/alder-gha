# Alder AI Security Agent

AI-powered security analysis for your code repositories using Large Language Models.

Visit our website: [https://alderaiagent.com/](https://alderaiagent.com/)

## Features

- **AI-Powered Analysis**: Uses LLMs to detect security vulnerabilities
- **Comprehensive Coverage**: Analyzes 10 security categories including authentication, authorization, injection attacks, XSS, and more
- **Detailed Reports**: Generates comprehensive reports in markdown
- **Easy Integration**: Simply add to your existing GitHub Actions workflow

## Prerequisites

1. **API Key Required**: This action requires an API key to run. Purchase scan credits at [alderaiagent.com/](https://alderaiagent.com/).
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
        uses: adamsmith6300/alder-gha@v1.0.0 # Use the appropriate version
        with:
          api-key: ${{ secrets.ALDER_API_KEY }}  # Required API key

      - name: Upload security reports
        uses: actions/upload-artifact@v4
        with:
          name: security-reports
          path: './security-reports'
```

## Setting Up the API Key

1. Purchase scan credits at [alderaiagent.com/](https://alderaiagent.com/)
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

Visit our [website](https://alderaiagent.com/) to purchase scan credits. After purchase, you'll receive an API key to use with the GitHub Action.

## Support

For support with this GitHub Action:
- Email: [adam@alderaiagent.com](mailto:adam@alderaiagent.com)
- GitHub Issues: [Create an issue](https://github.com/adamsmith6300/alder-gha/issues)

## Privacy and Data

This action does not store your code or vulnerability findings. All analysis is performed using AI models, and your code is not used to train the models. For more details, please read our [Privacy Policy](PRIVACY-POLICY.md).

## License

[MIT License](LICENSE)

