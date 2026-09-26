# Claude Cowork Setup: Meta Ads Management Automation
## AI Agent Framework for Campaign Tracking, Optimization & Client Reporting

---

## 📋 Table of Contents
1. [Overview](#overview)
2. [What is Claude Cowork](#what-is-claude-cowork)
3. [Setup Requirements](#setup-requirements)
4. [Automated Tasks & Workflows](#automated-tasks--workflows)
5. [Routine Scheduling](#routine-scheduling)
6. [Tracking & Monitoring](#tracking--monitoring)
7. [Integration Architecture](#integration-architecture)
8. [Implementation Steps](#implementation-steps)
9. [Sample Routines](#sample-routines)
10. [Monitoring Dashboard](#monitoring-dashboard)

---

## Overview

**Goal**: Use Claude Cowork as your AI Virtual Assistant to:
- ✅ Monitor Meta Ads campaigns daily
- ✅ Optimize underperforming ads
- ✅ Track KPIs and performance metrics
- ✅ Generate automated reports
- ✅ Manage budgets and allocations
- ✅ Conduct A/B testing
- ✅ Alert on issues and anomalies
- ✅ Provide recommendations
- ✅ Handle client communications
- ✅ Maintain audit trails

---

## What is Claude Cowork

**Claude Cowork** is an AI agent platform that allows you to:
- Create autonomous agents that perform tasks independently
- Schedule recurring workflows with `create_trigger` (cron-based)
- Monitor and track campaign performance automatically
- Generate insights and recommendations
- Integrate with multiple tools and APIs
- Maintain persistent state across sessions
- Collaborate with human oversight

### Key Capabilities for Meta Ads:
```
✓ Scheduled monitoring (daily, weekly, monthly)
✓ Real-time performance tracking
✓ Automated optimization suggestions
✓ Report generation and distribution
✓ Multi-client management
✓ Budget allocation and adjustments
✓ A/B test management and analysis
✓ Client notification and alerts
✓ Historical data analysis
✓ Predictive insights
```

---

## Setup Requirements

### 1. **Prerequisites**
- [ ] Claude Code session active (this one)
- [ ] Meta Ads account with API access
- [ ] Meta Business Account setup
- [ ] Conversion pixel installed on client website
- [ ] Database or tracking system (Google Sheets, Airtable, or custom)
- [ ] Client communication channel (email, Slack)
- [ ] GitHub repository setup (for version control)

### 2. **Connectors & Integrations Needed**

| Service | Purpose | How to Enable |
|---|---|---|
| **Meta Ads API** | Access campaign data, metrics | Facebook Graph API setup |
| **Google Sheets** | Track performance data | Google Workspace connector |
| **Slack** | Send alerts and reports | Slack App integration |
| **Gmail** | Send client reports | Gmail connector |
| **Airtable** | Manage campaigns database | Airtable API connection |
| **Zapier** (optional) | Connect additional services | Zapier integration |

### 3. **Data Structure Setup**

**Google Sheets Template** (Recommended):
```
Columns needed:
- Client Name
- Campaign ID
- Campaign Name
- Daily Spend ($)
- Impressions
- Clicks
- Conversions
- CPA ($)
- ROAS
- Status (Active/Paused/Testing)
- Last Updated
- Notes
```

**Airtable Base** (Alternative):
```
Tables:
- Clients (name, contact, budget, KPIs)
- Campaigns (client, campaign details, metrics)
- Performance (daily metrics, trends)
- Recommendations (optimizations needed)
- Reports (generated reports history)
- Tasks (action items)
```

---

## Automated Tasks & Workflows

### Daily Tasks (Run at 8 AM)

```yaml
Task: Daily Campaign Performance Review
Schedule: Every day at 8:00 AM
Duration: 15-20 minutes

Steps:
1. Pull previous day's metrics from Meta Ads
2. Calculate KPIs (ROAS, CPA, CTR, etc.)
3. Compare against targets
4. Identify underperforming campaigns (ROAS < 1.5:1)
5. Flag for optimization
6. Update tracking spreadsheet
7. Send alert if major issues detected
8. Log findings for weekly review
```

### Weekly Tasks (Run Every Monday at 9 AM)

```yaml
Task: Weekly Performance Review & Optimization
Schedule: Every Monday at 9:00 AM
Duration: 30-45 minutes

Steps:
1. Aggregate weekly performance data
2. Calculate week-over-week trends
3. Analyze top/bottom performing campaigns
4. Review A/B test results
5. Generate optimization recommendations:
   - Pause underperformers
   - Increase budget for winners
   - Adjust targeting for struggling campaigns
   - Suggest creative refreshes
6. Document recommendations
7. Generate weekly report
8. Alert team of changes needed
9. Update client-facing dashboard
```

### Monthly Tasks (Run 1st of month at 10 AM)

```yaml
Task: Comprehensive Monthly Performance Review
Schedule: 1st of each month at 10:00 AM
Duration: 1-2 hours

Steps:
1. Compile all campaign performance data
2. Calculate monthly ROI/ROAS
3. Analyze spend vs. budget performance
4. Review audience performance
5. Analyze creative performance
6. Assess testing results
7. Generate comprehensive monthly report:
   - Executive summary
   - Performance metrics
   - Top/bottom performers
   - Budget analysis
   - Creative analysis
   - Recommendations
   - Next month strategy
8. Send to client
9. Schedule follow-up call
10. Update strategy document
```

---

## Routine Scheduling

### Using Claude Cowork `create_trigger`

**Syntax** (Pseudo-code):
```python
create_trigger(
    name="Daily Meta Ads Performance Review",
    cron_expression="0 8 * * *",  # 8 AM daily
    prompt="""
    Review Meta Ads performance for all clients:
    1. Pull metrics from Meta Ads API
    2. Calculate KPIs against targets
    3. Flag underperformers
    4. Update tracking spreadsheet
    5. Alert on critical issues
    """,
    create_new_session_on_fire=True,  # Fresh session each run
    initiation="own_initiative"
)
```

### Routine Configurations

#### Routine 1: Daily Performance Check
```
Name: Daily Meta Ads Performance Check
Schedule: 0 8 * * * (8 AM, every day)
Duration: 15 min
Output: Slack alert + Spreadsheet update
Alert Level: Critical issues only
```

#### Routine 2: Weekly Optimization Review
```
Name: Weekly Campaign Optimization
Schedule: 0 9 * * 1 (9 AM, every Monday)
Duration: 45 min
Output: Weekly report + Recommendations
Alert Level: All opportunities
```

#### Routine 3: Monthly Strategic Review
```
Name: Monthly Performance & Strategy Review
Schedule: 0 10 1 * * (10 AM, 1st of month)
Duration: 2 hours
Output: Comprehensive report + Client presentation
Alert Level: Strategic insights
```

#### Routine 4: A/B Test Analysis
```
Name: Weekly A/B Test Results Analysis
Schedule: 0 5 * * 2 (5 AM, every Tuesday)
Duration: 30 min
Output: Test findings + Recommendations
Alert Level: Significant results only
```

#### Routine 5: Budget Allocation Review
```
Name: Budget Allocation Optimization
Schedule: 0 9 * * 5 (9 AM, every Friday)
Duration: 20 min
Output: Budget recommendations + Allocation plan
Alert Level: Reallocation opportunities
```

---

## Tracking & Monitoring

### Real-Time Monitoring Dashboard

**What to Track**:
```
PER CLIENT:
├─ Current Month Spend
├─ Current Month Revenue
├─ Current Month ROAS
├─ Current Month CPA
├─ Status (On track / At risk / Exceeding)
├─ Number of Active Campaigns
├─ Number of Active A/B Tests
├─ Last Updated
└─ Next Review Date

PER CAMPAIGN:
├─ Campaign Name & ID
├─ Status (Active/Paused/Testing)
├─ Daily Budget
├─ Current Spend
├─ Conversions
├─ ROAS
├─ CPA
├─ CTR
├─ Quality Score
├─ Relevance Score
├─ Trend (↑ improving / ↓ declining / → stable)
└─ Recommended Action
```

### Tracking Methods

#### Option 1: Google Sheets (Recommended for simplicity)
```
Sheet 1: Daily Metrics
  - Auto-update via Claude agent pulling API data
  - Formulas for KPI calculations
  - Conditional formatting for alerts
  - Charts for trend visualization

Sheet 2: Weekly Summary
  - Aggregated data from daily sheet
  - Week-over-week comparisons
  - Performance vs. goals

Sheet 3: Monthly Summary
  - Month-over-month comparisons
  - ROI calculations
  - Trend analysis

Sheet 4: Client Dashboard
  - Client-friendly view of performance
  - Key metrics highlighted
  - Goals vs. actual
```

#### Option 2: Airtable (Better for scalability)
```
Base: Meta Ads Management

Tables:
1. Clients
   - Name, contact info, KPIs, monthly budget
   
2. Campaigns
   - Client link, campaign details, status
   
3. Daily Performance
   - Campaign link, date, metrics (spend, conversions, etc.)
   
4. A/B Tests
   - Campaign link, test details, control/variation
   
5. Actions Needed
   - Campaign link, action type, priority, status
   
6. Reports
   - Client link, report date, report link
```

#### Option 3: Custom Database (Most control)
```
Database: MetaAdsTracker

Tables:
- clients (id, name, email, monthly_budget, kpis)
- campaigns (id, client_id, name, budget, status)
- daily_metrics (id, campaign_id, date, spend, conversions, roas)
- a_b_tests (id, campaign_id, control, variation, results)
- recommendations (id, campaign_id, type, priority, date_created)
- reports (id, client_id, type, date_generated, url)
```

---

## Integration Architecture

### System Flow Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                    CLAUDE COWORK AGENT                      │
│  (Runs on scheduled routines, triggers, and manual requests) │
└─────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
   │ Meta Ads    │    │Google Sheets│    │ Slack/Email │
   │ API Access  │    │ Airtable    │    │ Alerting    │
   │ Campaign    │    │ Database    │    │ Reports     │
   │ Metrics     │    │ Tracking    │    │ Distribution│
   └─────────────┘    └─────────────┘    └─────────────┘
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
   ┌────────────┐    ┌────────────┐    ┌────────────┐
   │ Daily      │    │ Weekly     │    │ Monthly    │
   │ Monitoring │    │ Optimization│   │ Reporting  │
   │ & Alerts   │    │ & Testing  │    │ & Analysis │
   └────────────┘    └────────────┘    └────────────┘
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              │
                    ┌─────────▼──────────┐
                    │ Recommendations &  │
                    │ Action Items       │
                    └────────────────────┘
```

### Data Flow for Each Routine

```
DAILY ROUTINE (8 AM):
1. Claude Cowork wakes up
2. Calls Meta Ads API for previous day metrics
3. Calculates KPIs using formulas
4. Compares against daily targets
5. Updates Google Sheets
6. If issues detected → Send Slack alert
7. Creates action items for team
8. Logs activity in database

WEEKLY ROUTINE (9 AM Monday):
1. Claude Cowork wakes up
2. Pulls last 7 days of data from tracking sheet
3. Analyzes trends and patterns
4. Reviews A/B test results
5. Generates optimization recommendations
6. Identifies top/bottom performers
7. Creates weekly report
8. Sends report to team/client
9. Creates action items for implementation

MONTHLY ROUTINE (10 AM, 1st):
1. Claude Cowork wakes up
2. Aggregates all monthly data
3. Calculates ROI, ROAS, conversion rates
4. Compares month-over-month
5. Analyzes creative and audience performance
6. Generates comprehensive report with insights
7. Creates strategic recommendations
8. Sends to client with presentation format
9. Schedules client call
10. Documents learnings for future reference
```

---

## Implementation Steps

### Step 1: Set Up Tracking Infrastructure (Day 1)

```bash
# Create Google Sheet or Airtable base
1. Create new Google Sheet named "Meta Ads Tracking [Client Name]"
2. Set up columns: Date, Campaign, Spend, Conversions, ROAS, CPA, Status
3. Create formulas for KPI calculations
4. Set up conditional formatting for alerts
5. Share with team for access

OR

1. Create Airtable base "Meta Ads Management"
2. Create tables: Clients, Campaigns, Daily Performance, A/B Tests
3. Set up relationships between tables
4. Create views and filters
5. Generate API key for Claude access
```

### Step 2: Grant API Access (Day 1)

```bash
# Meta Ads API Setup
1. Go to Facebook Business Manager
2. Settings → Users and Permissions
3. Add Claude as app (or use service account)
4. Grant permissions: ads_read, ads_management
5. Generate access token
6. Store securely in Claude environment variables

# Google Sheets API (if using)
1. Create Google Cloud project
2. Enable Google Sheets API
3. Create service account
4. Generate API key
5. Share spreadsheet with service account email

# Slack Integration
1. Create Slack App in your workspace
2. Enable Incoming Webhooks
3. Get webhook URL
4. Store in Claude environment
```

### Step 3: Create Prompt Instructions (Day 2)

**Create a file**: `META_ADS_COWORK_INSTRUCTIONS.md`

```markdown
# Claude Cowork: Meta Ads Management Instructions

## Role
You are an AI Virtual Assistant managing Meta Ads campaigns for [Client Name(s)].

## Responsibilities
1. Monitor campaign performance daily
2. Optimize campaigns based on KPIs
3. Generate reports and insights
4. Track A/B tests
5. Manage budgets
6. Alert on issues

## Daily Routine (8 AM)
- Pull metrics from Meta Ads API
- Update tracking spreadsheet
- Calculate KPIs
- Alert if ROAS < 1.5:1 or CPA > target
- Log findings

## Weekly Routine (9 AM Monday)
- Analyze weekly trends
- Review A/B test results
- Make optimization recommendations
- Generate weekly report
- Send to stakeholders

## Monthly Routine (1st of month, 10 AM)
- Comprehensive performance analysis
- ROI calculation
- Creative performance review
- Strategic recommendations
- Generate client report

## Key Metrics to Track
- ROAS (target: 3:1+)
- CPA (target: [client-specific])
- CTR (target: 1-3%)
- Conversion rate (target: [client-specific])
- Daily/monthly spend
- Conversions

## Alert Thresholds
- ROAS < 1.5:1: CRITICAL
- CPA > 2x target: WARNING
- CTR declining > 20%: WARNING
- Spend pace off > 10%: MONITOR

## Tools & Access
- Meta Ads API: [credentials]
- Google Sheets: [spreadsheet link]
- Slack webhook: [URL]
- Airtable API: [key]

## Reporting Format
- Daily: Brief alert only (if issues)
- Weekly: 1-2 page report with charts
- Monthly: Full report with insights and recommendations
```

### Step 4: Set Up Routines (Day 2-3)

**Using Claude Cowork Commands** (in this session):

```bash
# Create Daily Routine
/create-trigger daily-meta-ads-check \
  --schedule "0 8 * * *" \
  --file "META_ADS_COWORK_INSTRUCTIONS.md" \
  --description "Daily campaign performance review"

# Create Weekly Routine
/create-trigger weekly-optimization-review \
  --schedule "0 9 * * 1" \
  --file "META_ADS_COWORK_INSTRUCTIONS.md" \
  --description "Weekly optimization and testing analysis"

# Create Monthly Routine
/create-trigger monthly-strategic-review \
  --schedule "0 10 1 * *" \
  --file "META_ADS_COWORK_INSTRUCTIONS.md" \
  --description "Comprehensive monthly performance review"
```

### Step 5: Test & Validate (Day 3-4)

```bash
# Run first test manually
1. Trigger the daily routine manually
2. Check that it:
   - Connects to Meta Ads API
   - Pulls correct data
   - Updates tracking sheet
   - Sends alerts properly
3. Verify data accuracy
4. Check formatting of outputs
5. Iterate on any issues
```

### Step 6: Go Live & Monitor (Day 4+)

```bash
# Activate all routines
1. Enable all scheduled routines
2. Monitor first week of runs
3. Make adjustments as needed
4. Get team feedback
5. Refine prompts based on outputs
6. Document any issues
```

---

## Sample Routines

### Routine 1: Daily Performance Check

**Prompt Template:**
```
You are Meta Ads Management AI for [Client Name].

DAILY TASK (Run at 8 AM every day):

1. PULL METRICS
   - Access Meta Ads API
   - Get yesterday's campaign metrics
   - Retrieve: spend, clicks, conversions, ROAS, CPA, impressions

2. UPDATE TRACKING
   - Open Google Sheet: [Link]
   - Add row with yesterday's data
   - Calculate KPIs using formulas
   - Update status column

3. ANALYZE PERFORMANCE
   - Compare to daily targets
   - Calculate ROAS for each campaign
   - Flag campaigns with ROAS < 1.5:1
   - Check budget spend pace

4. ALERTS
   If any of these conditions met:
   - ROAS < 1.5:1 on any campaign → CRITICAL ALERT
   - CPA > [target] → WARNING ALERT
   - Conversions below daily average → MONITOR
   → Send Slack message to #meta-ads-alerts

5. DOCUMENTATION
   - Log findings in database
   - Note any patterns noticed
   - Flag for weekly review

6. OUTPUT
   - Send brief report to [team-email]
   - Update client dashboard
   - Log completion

Report Format:
📊 Meta Ads Daily Report - [Date]
✅ Overall ROAS: X:1
⚠️ Campaigns needing attention: [list]
🔔 Alerts: [if any]
📈 Trend: [improving/stable/declining]
```

### Routine 2: Weekly Optimization Review

**Prompt Template:**
```
You are Meta Ads Optimization AI.

WEEKLY TASK (Run 9 AM every Monday):

1. GATHER DATA
   - Pull last 7 days of metrics
   - Calculate weekly totals
   - Compare to previous week
   - Calculate week-over-week %

2. TOP PERFORMERS ANALYSIS
   - Identify top 3 campaigns by ROAS
   - Note what's working
   - Recommend budget increases
   - Document creative elements

3. BOTTOM PERFORMERS ANALYSIS
   - Identify bottom 3 campaigns by ROAS
   - Analyze why underperforming
   - Recommend optimizations:
     * Pause underperformers
     * Refine targeting
     * Refresh creatives
     * Reduce budget

4. A/B TEST REVIEW
   - Pull all active A/B tests
   - Calculate statistical significance
   - Identify winners
   - Recommend implementation

5. BUDGET ANALYSIS
   - Total spend vs. budget
   - Pace analysis (on track?)
   - ROI per client
   - Budget reallocation recommendations

6. RECOMMENDATIONS
   - List top 5 actions for team
   - Prioritize by impact
   - Estimate expected results

7. REPORTING
   - Generate weekly report
   - Include charts/graphs
   - Send to team + clients
   - Schedule optimization call

Report Format:
📊 WEEKLY META ADS REPORT - Week of [Date]
┌─ Performance Summary
│  • Total Spend: $X
│  • Total Revenue: $X
│  • Overall ROAS: X:1
│  • Week-over-week: +/-X%
├─ Top 3 Campaigns
│  1. [Campaign] - ROAS X:1
│  2. [Campaign] - ROAS X:1
│  3. [Campaign] - ROAS X:1
├─ Needs Attention
│  1. [Campaign] - ROAS X:1 (Action: X)
│  2. [Campaign] - ROAS X:1 (Action: X)
│  3. [Campaign] - ROAS X:1 (Action: X)
├─ A/B Test Results
│  • [Test Name]: Winner is [Variation] (+X% performance)
├─ Top 5 Recommended Actions
│  1. [Action] - Expected ROI impact: +X%
│  2. [Action] - Expected impact: $X revenue
│  3. ...
└─ Next Week Focus
   • [Focus area 1]
   • [Focus area 2]
```

### Routine 3: Monthly Strategic Review

**Prompt Template:**
```
You are Meta Ads Strategic Analyst.

MONTHLY TASK (Run 10 AM on 1st of month):

1. COMPILE MONTHLY DATA
   - Aggregate all daily metrics
   - Calculate monthly totals
   - Month-over-month comparison
   - Year-to-date analysis

2. FINANCIAL ANALYSIS
   - Total spend: $X
   - Total revenue: $X
   - Net profit: $X
   - ROI: X%
   - ROAS: X:1

3. PERFORMANCE ANALYSIS
   - Top performing campaign
   - Most improved campaign
   - Campaign needing attention
   - Average metrics across all campaigns

4. AUDIENCE INSIGHTS
   - Best performing demographics
   - Best performing interests
   - Geographic performance
   - Device type performance

5. CREATIVE ANALYSIS
   - Top 5 performing ads
   - Most improved ads
   - Ads ready for retirement
   - Creative themes that resonated

6. BUDGET EFFICIENCY
   - Budget utilization rate
   - Cost per result trends
   - Spending patterns
   - Reallocation opportunities

7. STRATEGIC RECOMMENDATIONS
   - 3-5 high-impact recommendations
   - Budget allocation for next month
   - Campaign adjustments
   - New testing opportunities
   - Long-term strategy adjustments

8. GENERATE REPORT
   - Professional formatted report
   - Include charts and data visualizations
   - Executive summary
   - Detailed findings
   - Action plan for next month

9. CLIENT DELIVERY
   - Send comprehensive report
   - Schedule strategy call
   - Present recommendations
   - Get client feedback

Report Format:
📊 MONTHLY PERFORMANCE REPORT
[Month & Year]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
EXECUTIVE SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Spend: $X,XXX
Total Revenue: $X,XXX
Profit: $X,XXX
ROI: XXX%
Overall ROAS: X:1

Key Achievement: [Most significant result]
Area of Focus: [What needs improvement]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DETAILED PERFORMANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Detailed metrics, charts, analysis]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TOP CAMPAIGNS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Top 5 performers with metrics]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRATEGIC RECOMMENDATIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[5 actionable recommendations]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT MONTH STRATEGY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Focus areas, budget allocation, tests]
```

---

## Monitoring Dashboard

### Example Google Sheets Dashboard

**Sheet Setup:**
```
Tab 1: Daily Metrics
  Row 1: Headers (Date, Campaign, Spend, Impressions, Clicks, Conversions, CPA, ROAS)
  Rows 2+: Daily data (auto-populated by Claude agent)
  Columns: A-H
  Format:
    - ROAS < 1.5:1 → Red background
    - ROAS 1.5-3:1 → Yellow background
    - ROAS > 3:1 → Green background

Tab 2: Weekly Summary
  Metric | Value | Target | Status | Trend
  -------|-------|--------|--------|------
  ROAS | 2.8:1 | 3:1 | 93% | ↑
  CPA | $42 | $35 | 120% | ↓
  ...

Tab 3: Campaign Performance
  Campaign | Status | Daily Budget | Spend | ROAS | CPA | Action
  ---------|--------|--------------|-------|------|-----|--------
  Campaign A | Active | $100 | $98 | 3.5:1 | $28 | Scale
  Campaign B | Active | $50 | $52 | 1.2:1 | $65 | Pause
  ...

Tab 4: Client Dashboard
  [Client-friendly format]
  - Month to date spend
  - Month to date revenue
  - ROI percentage
  - Key metrics
  - Status dashboard
```

### Real-Time Monitoring via Slack

```
Slack Integration Alerts:

✅ Daily Check-in (8:15 AM):
   "📊 Meta Ads Daily Report
    • Total Spend: $2,847
    • Conversions: 84
    • ROAS: 3.2:1
    • Status: ✅ All campaigns performing well"

⚠️ Alert Example:
   "🚨 ALERT: Campaign Performance Issue
    Campaign: Newsletter_Q4
    ROAS: 1.2:1 (Target: 3:1)
    Recommendation: Review targeting or pause
    Action: Review in next 24 hours"

📊 Weekly Summary (Monday 10 AM):
   "📈 Weekly Optimization Report
    • Best performer: Back-to-School (ROAS 4.1:1)
    • Needs attention: Winter Sale (ROAS 1.1:1)
    • Recommendation: Scale Back-to-School +30%
    • A/B Tests: 2 winners identified
    Full report: [link to Google Sheet]"
```

---

## Implementation Checklist

### Phase 1: Setup (Week 1)
- [ ] Create tracking spreadsheet (Google Sheets or Airtable)
- [ ] Set up Meta Ads API access
- [ ] Create Slack webhook for alerts
- [ ] Test API connections
- [ ] Document tracking structure
- [ ] Brief team on new system

### Phase 2: Automation (Week 2)
- [ ] Create daily routine prompt
- [ ] Create weekly routine prompt
- [ ] Create monthly routine prompt
- [ ] Set up email templates
- [ ] Configure Slack alerts
- [ ] Test all routines manually

### Phase 3: Deployment (Week 3)
- [ ] Enable daily routine (8 AM)
- [ ] Enable weekly routine (Monday 9 AM)
- [ ] Enable monthly routine (1st of month 10 AM)
- [ ] Monitor first week of runs
- [ ] Document any issues
- [ ] Refine based on initial runs

### Phase 4: Optimization (Ongoing)
- [ ] Gather feedback from team
- [ ] Adjust alert thresholds
- [ ] Refine report formats
- [ ] Add new metrics as needed
- [ ] Update routines quarterly
- [ ] Scale to more clients

---

## Expected Outcomes

### After 1 Month:
- ✅ 100% of daily metrics being tracked automatically
- ✅ Weekly optimization recommendations implemented
- ✅ A/B tests being managed automatically
- ✅ Alerts caught issues early
- ✅ Time saved: 10+ hours/month per client

### After 3 Months:
- ✅ Average ROAS improved by 15-25%
- ✅ CPA reduced by 10-20%
- ✅ Campaigns optimized monthly
- ✅ Scalable to multiple clients
- ✅ Time saved: 40+ hours/month

### After 6 Months:
- ✅ Fully autonomous campaign management
- ✅ Predictive optimization recommendations
- ✅ Historical insights and learning
- ✅ Multiple clients managed efficiently
- ✅ System handles edge cases and anomalies

---

## Troubleshooting

### Issue: Routine not running at scheduled time
**Solution**: 
- Check routine is enabled
- Verify cron expression is correct
- Check timezone settings
- Review error logs

### Issue: Data not updating in spreadsheet
**Solution**:
- Verify API credentials are valid
- Check spreadsheet permissions
- Test API connection
- Review data format

### Issue: Alerts not sending to Slack
**Solution**:
- Verify webhook URL is correct
- Check Slack channel permissions
- Test webhook manually
- Review alert thresholds

### Issue: Metrics calculations incorrect
**Solution**:
- Verify formula definitions
- Check data sources
- Test calculation manually
- Compare to Meta Ads Manager

---

## Next Steps

1. **Choose your infrastructure** (Google Sheets vs. Airtable)
2. **Set up tracking** and test data flow
3. **Create prompt instructions** for Claude Cowork
4. **Set up first routine** (daily check)
5. **Test thoroughly** before automation
6. **Deploy remaining routines**
7. **Monitor and refine** based on results
8. **Scale to more clients** as system matures

---

**Document Version**: 1.0  
**Created**: 2026-09-26  
**Status**: Ready for Implementation

---
