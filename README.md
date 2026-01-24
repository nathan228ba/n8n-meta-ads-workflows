# n8n Meta Ads Workflows

> **Empire Amplify** - Ready-to-import n8n workflows for Meta Ads automation.

## Overview

Pre-built n8n workflows for:
- **Daily Reporting** - Performance reports to Slack/Email
- **Budget Optimization** - Auto-adjust budgets based on performance
- **Lead Routing** - Route leads to CRM automatically
- **Creative Testing** - Automate A/B test management

## Workflows

### `daily-reporting.json`
Automated daily Meta Ads performance reports sent to Slack.

### `budget-optimization.json`
Automatically adjusts campaign budgets based on ROAS and CPA thresholds.

### `lead-routing.json`
Routes Meta Lead Ads submissions to your CRM with enrichment.

### `creative-testing.json`
Manages creative testing by pausing low performers and scaling winners.

## Quick Start

1. Import JSON file into n8n
2. Configure Meta Marketing API credentials
3. Set your Ad Account ID
4. Configure Slack/Email notifications
5. Activate workflow

## Required Credentials

- **Meta Marketing API** - OAuth2 or System User Token
- **Slack** - Webhook or OAuth
- **Google Sheets** - For logging (optional)

## Configuration

Edit thresholds in the Code nodes:

```javascript
const CONFIG = {
  targetCPA: 50,
  targetROAS: 3.0,
  minSpendForEvaluation: 100,
  budgetIncreasePercent: 20,
  budgetDecreasePercent: 15
};
```

## License

MIT License - Empire Amplify 2025
