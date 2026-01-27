# n8n Meta Ads Workflows

> **Empire Amplify** - Ready-to-import n8n workflows for Meta Ads automation.
> 
> **No coding required!** Just import, configure, and activate.

[![n8n](https://img.shields.io/badge/n8n-workflow-ff6d5a.svg)](https://n8n.io)
[![licence: MIT](https://img.shields.io/badge/licence-MIT-yellow.svg)](licence)

---

## Who Is This For?

| User Type | What You Get |
|-----------|--------------|
| **Meta Ads Managers** | Automated daily reports to Slack |
| **Agency Teams** | Multi-client campaign monitoring |
| **Performance Marketers** | Auto-pause underperformers, scale winners |

---

## Available Workflows

### 1. `daily-reporting.json` - Daily Performance Report

**What it does:**
- Runs every day at 7 AM
- Pulls yesterday's Meta Ads performance
- Sends formatted report to Slack

**Metrics included:**
- Spend
- Impressions & Reach
- Clicks & CTR
- Conversions & CPA
- ROAS

**Use case:**
> "I want my team to see Meta Ads performance every morning without logging into Ads Manager."

---

### 2. `budget-automation.json` - Automated Budget Rules

**What it does:**
- Runs every 4 hours
- Evaluates campaigns against your thresholds
- Auto-pauses high CPA campaigns
- Auto-scales high ROAS campaigns
- Sends Slack alerts for all actions

**Rules:**
| Condition | Action |
|-----------|--------|
| CPA > threshold | Pause campaign |
| ROAS > threshold | Increase budget 20% |
| Frequency > threshold | Alert for creative refresh |

**Use case:**
> "I don't want to check ads every few hours. Pause losers and scale winners automatically."

---

### 3. `budget-optimisation.json` - Advanced Budget Allocation

**What it does:**
- Reallocates budget from underperformers to top performers
- Maintains total daily budget
- Logs all changes to Google Sheets

**Use case:**
> "I have $500/day budget. Automatically move money from bad campaigns to good ones."

---

## Quick Start

### Step 1: Import Workflow

1. Open n8n
2. Click **Import** (top-right)
3. Select the JSON file from this repo
4. Workflow appears in your canvas

### Step 2: Configure Credentials

**Meta Marketing API:**
1. In n8n, go to **Credentials**
2. Add new **HTTP Query Auth** credential
3. Enter your Meta Access Token

**Slack:**
1. Add **Slack** credential
2. Use OAuth or Webhook URL

### Step 3: Update Config Node

Each workflow has a **Config** node. Update:
- `adAccountId`: Your Meta Ad Account ID (act_XXXXXXXXX)
- `accessToken`: Your Meta API token
- Thresholds (CPA, ROAS, etc.)

### Step 4: Activate

1. Click **Active** toggle (top-right)
2. Workflow now runs on schedule

---

## Use Cases by Business Type

### E-Commerce

**Workflow:** `budget-automation.json`

**Settings:**
```
pauseCpaThreshold: 30 (your target CPA)
scaleRoasThreshold: 3.0
budgetIncreasePercent: 20
maxDailyBudget: 500
```

**What happens:**
- Ad sets with CPA > $30 get paused
- Ad sets with ROAS > 3x get 20% more budget
- You get Slack alerts for all changes

---

### Lead Generation

**Workflow:** `daily-reporting.json` + `budget-automation.json`

**Settings:**
```
pauseCpaThreshold: [Your max cost per lead]
scaleRoasThreshold: 2.0 (leads have different ROAS)
```

**What happens:**
- Morning reports show lead volume and cost
- High-cost lead campaigns get paused
- Top-performing campaigns get more budget

---

### App Install Campaigns

**Workflow:** `budget-automation.json`

**Settings:**
```
pauseCpaThreshold: [Target CPI × 1.5]
frequencyThreshold: 4.0 (app users tolerate higher frequency)
```

---

## Files In This Repository

```
n8n-meta-ads-workflows/
├── README.md
├── licence
├── .gitignore
├── daily-reporting.json # Daily Slack reports
├── budget-automation.json # Auto pause/scale rules
└── budget-optimisation.json # Budget reallocation
```

---

## JavaScript Code Snippets

### Calculate CPA & ROAS
```javascript
const spend = parseFloat(data.spend || 0);
const conversions = parseInt(data.conversions || 0);
const cpa = conversions > 0 ? spend / conversions : 0;
const roas = data.purchase_roas ? parseFloat(data.purchase_roas[0].value) : 0;
```

### Format Slack Message
```javascript
const message = ` *Meta Ads Report*\n` +
 ` Spend: $${spend.toFixed(2)}\n` +
 ` Conversions: ${conversions}\n` +
 ` CPA: $${cpa.toFixed(2)}\n` +
 ` ROAS: ${roas.toFixed(2)}x`;
```

### Evaluate Automation Rules
```javascript
if (cpa > config.pauseCpaThreshold) {
 actions.push({action: 'PAUSE', reason: `CPA too high`});
}
if (roas > config.scaleRoasThreshold) {
 actions.push({action: 'SCALE', reason: `ROAS excellent`});
}
```

---

## Related Repositories

| Repo | Description |
|------|-------------|
| [meta-ads-automation](../meta-ads-automation) | Python scripts & Google Sheets |
| [n8n-google-ads-workflows](../n8n-google-ads-workflows) | Google Ads n8n workflows |
| [zapier-meta-integration](../zapier-meta-integration) | Zapier integrations |

---

## FAQ

**Q: Do I need n8n Cloud or self-hosted?**
A: Either works. Self-hosted is free, Cloud starts at €20/month.

**Q: How do I get a Meta Access Token?**
A: Business Settings → System Users → Generate Token with `ads_management` permission.

**Q: Can I modify the workflows?**
A: Absolutely! Import, customize, and save your own versions.

---

## Support

- **Email:** gordon@empireamplify.com.au
- **Issues:** Open a GitHub issue

---

## licence

MIT licence - see [licence](licence) file.

**Empire Amplify** | Melbourne, Australia | 2025
