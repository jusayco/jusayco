# Claude Cowork: Quick Start Guide
## Get Your First Meta Ads AI Agent Running in 30 Minutes

---

## What You'll Have After This Guide

✅ Claude Cowork AI agent monitoring your Meta Ads campaigns  
✅ Automated daily performance tracking  
✅ Slack alerts for critical issues  
✅ Weekly optimization recommendations  
✅ Monthly comprehensive reports  

---

## Prerequisites Checklist

Before starting, make sure you have:

- [ ] Meta Business Account (facebook.com/business)
- [ ] Meta Ads Manager access
- [ ] Google Sheets or Airtable account
- [ ] Slack workspace (optional but recommended)
- [ ] Claude Code session open (this one)

---

## Step 1: Set Up Tracking (5 minutes)

### Option A: Google Sheets (Easiest)

```
1. Open Google Sheets → Create new spreadsheet
2. Name it: "Meta Ads Daily Tracker - [Your Name]"
3. Create these columns in Row 1:
   A: Date
   B: Campaign Name
   C: Campaign ID
   D: Daily Spend ($)
   E: Impressions
   F: Clicks
   G: Conversions
   H: CPA ($)
   I: ROAS
   J: CTR (%)
   K: Status
   L: Notes

4. Format cells:
   - Row 1: Bold, blue background
   - Column D-J: Currency/Number format
   - Add conditional formatting:
     * ROAS > 3 = Green
     * ROAS 1.5-3 = Yellow
     * ROAS < 1.5 = Red

5. Share the sheet with your team
6. Copy the share link and save it
```

### Option B: Airtable (More scalable)

```
1. Go to airtable.com → Create new base
2. Name it: "Meta Ads Management"
3. Create table: "Daily Metrics"
4. Add fields:
   - Date (Date)
   - Campaign Name (Text)
   - Campaign ID (Text)
   - Daily Spend (Currency)
   - Impressions (Number)
   - Clicks (Number)
   - Conversions (Number)
   - CPA (Currency) - Formula
   - ROAS (Number) - Formula
   - Status (Single Select: Active, Paused, Testing)

5. Create formulas:
   - CPA = Daily Spend / Conversions
   - ROAS = Revenue / Daily Spend
   (You'll need conversion value data)

6. Get API key:
   - Account settings → API
   - Create token
   - Save securely
```

---

## Step 2: Get Meta Ads API Access (10 minutes)

### Method 1: Using Meta Business Account

```
1. Go to facebook.com/business
2. Settings → Users and Permissions → System Users
3. Create new System User:
   Name: "Claude Cowork Agent"
   Role: Admin
4. Click on new user → Assign Assets
5. Select your ad account → Assign
6. Generate new access token:
   - Tools & Settings → Access Tokens
   - Copy token
   - Save in secure location (you'll need this)

7. Keep this token safe - it's like a password!
```

### Method 2: Using Personal Account (Simpler for testing)

```
1. Go to facebook.com/business
2. Settings → Users and Permissions
3. Go to your own account → Get access token
4. Create token with scopes:
   - ads_read
   - ads_management
5. Copy token and save securely
```

---

## Step 3: Set Up Slack Alerts (5 minutes) - OPTIONAL

Skip this if you don't use Slack.

```
1. Go to your Slack workspace
2. Click workspace name → Settings & administration → Manage apps
3. Search "Incoming Webhooks"
4. Click Add to Slack
5. Choose channel: #meta-ads-alerts (or create it)
6. Copy the Webhook URL
7. Save it somewhere safe
```

---

## Step 4: Create Your First Routine in Claude Code

### Open This Session in Claude Code (Desktop or Web)

You're already in Claude Code! Now let's create a trigger.

### Create Daily Monitoring Routine

```bash
# In this Claude Code session, I can help you set up the routine
# Just confirm you want to proceed with these details:

ROUTINE NAME: Daily Meta Ads Performance Check
SCHEDULE: 8 AM every day (adjust as needed)
WHAT IT DOES:
  ✓ Check yesterday's campaign metrics
  ✓ Update your tracking spreadsheet
  ✓ Calculate KPIs
  ✓ Alert if problems detected
  ✓ Send summary to your email

ESTIMATED TIME: 15 minutes per day
READY TO SET UP? → Let me know and we'll configure it
```

---

## Step 5: Create Routine Prompt

Save this as your routine's instruction document:

**File: `ROUTINE_DAILY_CHECK.txt`**

```
You are Claude, Meta Ads Management AI Agent.

MISSION: Track Meta Ads campaign performance and alert on issues.

DAILY TASK (Runs at 8 AM every day):

STEP 1: Get Yesterday's Data
─────────────────────────────
Access Meta Ads API and retrieve:
- Campaign name
- Campaign ID  
- Daily spend
- Impressions
- Clicks
- Conversions
- Cost per acquisition (CPA)
- Return on Ad Spend (ROAS)

API Endpoint: GET /act_[YOUR_AD_ACCOUNT_ID]/campaigns
API Token: [YOUR_TOKEN_HERE]

STEP 2: Calculate KPIs
─────────────────────────────
For each campaign, calculate:
- ROAS = Revenue ÷ Spend
- CPA = Spend ÷ Conversions
- CTR = Clicks ÷ Impressions × 100
- Conv Rate = Conversions ÷ Clicks × 100

STEP 3: Update Tracking Spreadsheet
─────────────────────────────────────
Open Google Sheet: [YOUR_SHEET_LINK]
Add new row with:
- Today's date
- All metrics calculated above
- Update Status column based on performance:
  * Green (✅): ROAS > 3
  * Yellow (⚠️): ROAS 1.5-3
  * Red (🚨): ROAS < 1.5

STEP 4: Check for Issues
──────────────────────────
Alert if ANY of these:
- ROAS < 1.5 on any campaign
- CPA > $[YOUR_TARGET]
- No conversions for 24 hours
- Spend > 120% of daily budget

STEP 5: Send Alert (if needed)
──────────────────────────────
If issues found, send Slack message to #meta-ads-alerts:
"🚨 META ADS ALERT
Campaign: [Name]
Issue: [What's wrong]
ROAS: [Current]
Target: [Goal]
Recommendation: [What to do]
Action needed by: [Time]"

STEP 6: Send Daily Summary
───────────────────────────
Send email to [YOUR_EMAIL]:
Subject: "Daily Meta Ads Report - [Date]"
Body:
"📊 Yesterday's Performance

Total Spend: $[X]
Total Conversions: [X]
Average ROAS: [X:1]
Status: [✅ Good / ⚠️ Monitor / 🚨 Issues]

Top Campaign: [Name] - ROAS [X:1]
Needs Attention: [Name] - ROAS [X:1]

Next steps: [Recommendations]"

STEP 7: Log Activity
────────────────────
Record in database:
- Timestamp: [Current time]
- Routine: Daily Check
- Campaigns monitored: [Count]
- Issues found: [Yes/No]
- Actions recommended: [List]

COMPLETION NOTES:
─────────────────
✓ Report sent to: [email]
✓ Alerts sent to: [Slack channel if issues]
✓ Spreadsheet updated: [Yes/No]
✓ Next run: [Tomorrow at 8 AM]
```

---

## Step 6: Set Up Environment Variables

These are like passwords that the AI agent will use. Keep them secure!

**In your system, save these:**

```bash
# Meta Ads API
META_ACCESS_TOKEN=your_access_token_here
META_AD_ACCOUNT_ID=act_xxxxxxxxxxxxx

# Google Sheets
GOOGLE_SHEETS_API_KEY=your_api_key_here
GOOGLE_SHEET_ID=your_sheet_id_here

# Slack (optional)
SLACK_WEBHOOK_URL=https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXX

# Your details
EMAIL_ADDRESS=your.email@example.com
CAMPAIGN_TARGET_CPA=your_target_cpa
SLACK_CHANNEL=#meta-ads-alerts
```

---

## Step 7: Test Your Routine

**IMPORTANT: Test before automating!**

```
1. Manually run the routine once
2. Check these results:
   ✓ Spreadsheet updated?
   ✓ Email received?
   ✓ Slack alert sent (if issue found)?
   ✓ Data accuracy correct?
   ✓ Calculations correct?

3. If anything failed:
   - Check API token validity
   - Verify spreadsheet permissions
   - Test Slack webhook URL
   - Review error messages

4. Once everything works → You're ready to automate!
```

---

## Step 8: Schedule the Routine

**Once testing is complete:**

```
Ask Claude to set up recurring schedule:
- Daily check: 8 AM every day
- Weekly optimization: 9 AM every Monday
- Monthly report: 10 AM on 1st of month

Or use this command structure:
  Name: Daily Meta Ads Check
  Schedule: 0 8 * * * (8 AM UTC every day)
  Action: Run routine_daily_check.txt
  Create new session each time: Yes
  Alert on failure: Yes
```

---

## Step 9: Monitor & Refine

**After first week of automated runs:**

```
✓ Check if routine runs at correct time
✓ Review quality of recommendations
✓ Adjust alert thresholds if needed
✓ Refine prompts based on outputs
✓ Get team feedback
✓ Make improvements

Common refinements:
- Adjust ROAS thresholds
- Change email recipients
- Modify alert frequency
- Add new metrics to track
```

---

## What's Happening Behind the Scenes?

```
DAY 1-7 (Manual testing)
  8 AM → You trigger routine manually
       → Claude pulls Meta Ads data
       → Updates your spreadsheet
       → Sends report
       → You verify it works

DAY 8+ (Automated)
  8 AM → Routine runs automatically
       → Claude checks campaigns
       → Updates tracking
       → Alerts you if issues
       → No manual work needed!

Result: You gain 30+ minutes per day back!
```

---

## Quick Reference: Your First Week

| Day | Time | Action | Expected Result |
|-----|------|--------|-----------------|
| Day 1 | Morning | Set up spreadsheet | Tracking ready |
| Day 1 | Afternoon | Get API access | Credentials saved |
| Day 2 | Morning | Create routine prompt | Instructions ready |
| Day 2 | Afternoon | First manual test | Verify it works |
| Day 2 | Evening | Fix any issues | System functioning |
| Day 3 | Morning | Enable automation | Routine runs at 8 AM |
| Day 3-7 | 8 AM | Monitor runs | Watch system work |
| Day 8+ | 8 AM | Automated daily checks | Passive monitoring |

---

## Troubleshooting Quick Fixes

### Routine didn't run
```
❌ Problem: Routine didn't execute at scheduled time
✅ Fix:
  1. Check routine is enabled
  2. Verify cron time format
  3. Check browser/system timezone
  4. Review routine logs
```

### Data not showing in spreadsheet
```
❌ Problem: Spreadsheet not updating
✅ Fix:
  1. Verify spreadsheet link is correct
  2. Check API permissions
  3. Confirm sheet is shared correctly
  4. Test API connection manually
```

### No alert received
```
❌ Problem: Slack/email alerts not sent
✅ Fix:
  1. Verify email address/Slack channel
  2. Check spam folder for email
  3. Test Slack webhook manually
  4. Verify alert threshold was met
```

### Metrics look wrong
```
❌ Problem: Numbers don't match Meta Ads Manager
✅ Fix:
  1. Check calculation formulas
  2. Verify data source is correct
  3. Confirm time zone alignment
  4. Test API data retrieval
```

---

## Next Level: Add Weekly Optimization

Once daily is working smoothly (after ~1 week):

```
CREATE: Weekly Optimization Routine
SCHEDULE: 9 AM every Monday
DOES:
  1. Analyze 7-day trend
  2. Identify top/bottom performers
  3. Recommend budget adjustments
  4. Suggest creative updates
  5. Generate optimization report
  6. Send to your email + Slack

TIME SAVING: 1+ hour of analysis per week
```

---

## Success Indicators

### After 1 Week:
- ✅ Daily reports arriving automatically
- ✅ Spreadsheet staying up-to-date
- ✅ Alerts catching issues early
- ✅ Zero manual data entry

### After 1 Month:
- ✅ Weekly optimizations implemented
- ✅ ROAS improving by 5-10%
- ✅ CPA decreasing
- ✅ Campaigns running on autopilot

### After 3 Months:
- ✅ Fully autonomous management
- ✅ 20-30% performance improvement
- ✅ Scalable to multiple clients
- ✅ 10+ hours saved per week

---

## Ready to Set Up? Let Me Know!

I can help you with:

1. **Setting up your tracking spreadsheet** → Save template
2. **Getting Meta Ads API access** → Step-by-step guide
3. **Creating your routine prompts** → Customized for your needs
4. **Testing everything** → Verify it all works
5. **Scheduling automation** → Go live with monitoring

Just reply with:
- Which tracking system? (Google Sheets / Airtable)
- When should routine run? (8 AM / 9 AM / other)
- What's your target ROAS? (3:1 / 4:1 / other)
- Use Slack for alerts? (Yes / No)

Then I'll set everything up for you! 🚀

---

**Version**: 1.0  
**Time to Complete**: 30 minutes  
**Complexity**: Beginner-friendly  
**Support**: Ask me any questions!

---
