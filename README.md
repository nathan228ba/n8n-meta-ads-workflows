# n8n Meta Ads Workflows

Pre-built n8n Pro workflow templates for Meta Ads automation integrated with Gemini Enterprise.

## 🚀 Features

- **Daily Reporting** - Automated daily performance reports with Gemini analysis
- **Budget Optimization** - Auto-scale successful campaigns, pause underperformers
- **Lead Routing** - Route Meta leads to CRM with enrichment
- **Slack Alerts** - Real-time alerts for anomalies and milestones
- **Gemini Analysis** - AI-powered insights and recommendations

## 📁 Workflows Included

### 1. Daily Meta Ads Reporting (daily-reporting.json)

**Trigger**: Daily at 5 AM AEDT

**Steps**:
1. Pull Meta campaign metrics (24h)
2. Pull previous day comparison
3. Generate Gemini AI insights
4. Create formatted report
5. Send to Google Sheets
6. Email summary to team
7. Post Slack notification

**Expected Duration**: 2-3 minutes

### 2. Budget Optimization (budget-optimization.json)

**Trigger**: Hourly

**Steps**:
1. Check all active campaigns
2. Analyze 7-day ROAS
3. Scale winners (+10%) if ROAS > 2.0
4. Pause underperformers if ROAS < 0.5
5. Cap daily budget adjustments at 20%
6. Log changes to Google Sheets
7. Alert team of major adjustments via Slack

**Safety Features**:
- Maximum daily budget cap
- Approval required for >50% changes
- Rate limiting

### 3. Lead Routing (lead-routing.json)

**Trigger**: Real-time (every 5 minutes)

**Steps**:
1. Check Meta Lead Ads form for new leads
2. Extract lead data
3. Enrich with Clearbit (if email)
4. Map to CRM fields
5. Create contact in CRM
6. Send to sales channel on Slack
7. Email lead confirmation
8. Log to Google Sheets

## 📄 Setup Instructions

### Prerequisites

- n8n Pro or self-hosted (€50/month)
- Meta Business Account with API access
- Gemini Enterprise API key
- Google Sheets API enabled
- Slack workspace
- CRM account (HubSpot, Pipedrive, etc.)

### Import Workflow

1. Open n8n Editor
2. Click **Import** → **From URL**
3. Paste workflow JSON URL
4. Configure credentials:
   - Meta API token
   - Gemini API key
   - Google Sheets connection
   - Slack webhook
   - CRM API key
5. Test workflow
6. Deploy

### Manual Import

1. Download JSON file
2. n8n → **Import** → **From File**
3. Select downloaded JSON
4. Configure as above
5. Test → Deploy

## 🔠 Environment Variables

Set in n8n Configuration:

```
META_API_TOKEN=your_token
GEMINI_API_KEY=your_key
GOOGLE_SHEETS_ID=spreadsheet_id
SLACK_WEBHOOK=your_webhook
CRM_API_KEY=your_crm_key
ADVERTISER_ID=your_account_id
```

## 📊 Execution Examples

### Daily Report Output

```
📊 DAILY META ADS REPORT - Jan 24, 2026

Campaigns Analyzed: 24
Total Spend (24h): $2,450
Total Results: 1,247
Average ROAS: 2.18
Top Performer: Q1_Spring_Mobile (ROAS: 3.42)

🔜 Gemini Insights:
"Your audience targeting for Q1_Spring_Mobile is outperforming benchmarks by 58%. 
Consider increasing budget allocation to this campaign."

❌ Campaigns Paused: 2
✅ Campaigns Scaled: 3
```

### Lead Routing Output

```
🏃 NEW LEAD CAPTURED

Name: Sarah Johnson
Email: sarah@company.com
Phone: +61 2 XXXX XXXX
Company: Tech Corp
Interest: B2B Services
Lead Score: 42/100

✨ Status: Created in CRM (ID: #12485)
```

## 📅 Workflow Execution Log

All workflows log to Google Sheets with:
- Timestamp
- Workflow name
- Status (success/error)
- Records processed
- Execution time
- Error details (if failed)

## 🛂 Troubleshooting

### Common Issues

**API Rate Limiting**
- Solution: Increase execution interval or add delay nodes

**Missing Credentials**
- Solution: Verify environment variables in n8n Configuration

**Gemini API Errors**
- Solution: Check API key validity and rate limits

## 🤝 Related Repos

- [meta-campaign-management](https://github.com/gordongeraghty/meta-campaign-management)
- [meta-creative-ai-generation](https://github.com/gordongeraghty/meta-creative-ai-generation)
- [zapier-meta-integration](https://github.com/gordongeraghty/zapier-meta-integration)
- [gemini-ads-ai-analysis](https://github.com/gordongeraghty/gemini-ads-ai-analysis)

## 📝 License

MIT
