# Alder Security Agent GitHub Action

AI-powered security analysis for your code repositories using Large Language Models.

## Features

- **AI-Powered Analysis**: Uses LLMs to detect security vulnerabilities
- **Comprehensive Coverage**: Analyzes 10 security categories including authentication, authorization, injection attacks, XSS, and more
- **Attack Path Analysis**: Identifies chains of vulnerabilities that could be exploited together
- **Detailed Reports**: Generates comprehensive reports in markdown and HTML

## Usage

Add this action to your GitHub workflow:

```yaml
name: Security Analysis

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
        with:
          fetch-depth: 0  # Full git history for better analysis

      - name: Run Alder Security Agent
        uses: adamsmith6300/alder-security-agent@v1
        with:
          analyze-attack-paths: 'true'  # Enable attack path analysis

      - name: Upload security reports
        uses: actions/upload-artifact@v3
        with:
          name: security-reports
          path: './security-reports'
```

## Inputs

| Input                | Description                            | Required | Default |
|---------------------|----------------------------------------|----------|---------|
| `analyze-attack-paths` | Whether to perform attack path analysis | No       | false   |

## Default Settings

The action uses these default settings:
- Output Directory: `./security-reports`
- Report Format: Both markdown and HTML
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

Alder Security Agent uses a pay-per-scan pricing model:

| Package | Price | Value |
|---------|-------|-------|
| 1 Scan | $5 | Basic security scan |
| 5 Scans | $20 | $4 per scan (20% savings) |
| 10 Scans | $35 | $3.50 per scan (30% savings) |

To purchase scan credits, visit our [website](https://alderaiagent.com/pricing). Once purchased, you'll receive an API key to use with the action.

Each scan includes:
- Full codebase security analysis
- All 10 security categories
- Attack path analysis
- Comprehensive HTML and Markdown reports

For enterprise customers or larger scan volumes, please [contact us](mailto:adam@alderaiagent.com) for custom pricing.

## Support

For support with this GitHub Action:
- Email: [adam@alderaiagent.com](mailto:adam@alderaiagent.com)
- GitHub Issues: [Create an issue](https://github.com/adamsmith6300/alder-security-agent/issues)

## Privacy and Data

This action does not store your code or vulnerability findings. All analysis is performed using AI models, and your code is not used to train the models. For more details, read our [Privacy Policy](https://example.com/privacy).

## License

[MIT License](LICENSE)

*For commercial use in GitHub Marketplace, please see [commercial terms](https://example.com/commercial-terms).*

