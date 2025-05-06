# Alder AI Security Agent

Alder AI Security Agent is an advanced AI-powered security scanner that analyzes your code repositories for vulnerabilities across 10 security categories. Powered by Large Language Models, it provides in-depth analysis that goes beyond traditional static analysis tools, identifying complex security issues.

## Features
- **Deep Security Analysis**: Uses advanced AI to detect vulnerabilities across 10 security categories
- **Comprehensive Reports**: Delivers detailed reports in markdown formats
- **Easy Integration**: Simply add to your existing GitHub Actions workflow

## Pricing

Alder AI Security Agent uses a pay-per-scan pricing model to cover costs, with all scans purchased through our website:

Visit our [website](https://alderaiagent.com/) to purchase scan credits. After purchase, you'll receive an API key to use with the GitHub Action.

## Configuration

Basic configuration with your API key:
```yaml
- name: Run Alder AI Security Agent
    uses: adamsmith6300/alder-gha@v1
    with:
      # Your API key from purchasing scan credits
      api-key: ${{ secrets.ALDER_API_KEY }}
```

## Support
Email: adam@alderaiagent.com
GitHub Issues: https://github.com/adamsmith6300/alder-gha/issues
