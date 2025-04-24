# Alder Security Agent

## Tagline
AI-powered security analysis for your code repositories

## Detailed Description
Alder Security Agent is an advanced AI-powered security scanner that analyzes your code repositories for vulnerabilities across 10 security categories. Using cutting-edge Large Language Models, it provides in-depth analysis that goes beyond traditional static analysis tools, identifying complex security issues and potential attack paths.

## Features
- **Deep Security Analysis**: Uses advanced AI to detect vulnerabilities across 10 security categories
- **Attack Path Analysis**: Identifies chains of vulnerabilities that could be exploited together
- **Comprehensive Reports**: Delivers detailed reports in both markdown and HTML formats
- **Easy Integration**: Simply add to your existing GitHub Actions workflow

## Screenshots
[Include screenshot links here when available]

## Pricing

Alder Security Agent uses a pay-per-scan pricing model, with all scans purchased through our website:

### 1 Scan Package ($5)
- One complete security scan
- All security categories analyzed
- Attack path analysis included
- HTML and Markdown reports

### 5 Scan Package ($20)
- Five complete security scans
- $4 per scan (20% savings)
- All features included
- Standard support

### 10 Scan Package ($35)
- Ten complete security scans
- $3.50 per scan (30% savings)
- All features included
- Priority support

Visit our [website](https://alderaiagent.com/pricing) to purchase scan credits. After purchase, you'll receive an API key to use with the GitHub Action.

## Configuration

Basic configuration with your API key:
```yaml
- name: Run Alder Security Agent
  uses: adamsmith6300/alder-security-agent@v1
  env:
    ALDER_API_KEY: ${{ secrets.ALDER_API_KEY }}
```

With attack path analysis enabled:
```yaml
- name: Run Alder Security Agent
  uses: adamsmith6300/alder-security-agent@v1
  env:
    ALDER_API_KEY: ${{ secrets.ALDER_API_KEY }}
  with:
    analyze-attack-paths: 'true'
```

## Support
Email: adam@alderaiagent.com
GitHub Issues: https://github.com/adamsmith6300/alder-security-agent/issues

## Categories
- DevOps
- Security
- Code Quality
- Utilities 
