# Email Setup - Google Sheets (Recommended)

Your website now uses **Google Sheets** to collect form submissions!

## Why Google Sheets?
✅ **Completely FREE** - Forever, no limits  
✅ **Unlimited storage** - Store millions of submissions  
✅ **No monthly limits** - Unlimited form submissions  
✅ **Easy management** - View/export data anytime  
✅ **Secure** - Your Google Drive, you control access  
✅ **Team-friendly** - Share with colleagues easily  

## Setup (12 minutes total)

**→ Follow:** [GOOGLE_SHEETS_SETUP.md](./GOOGLE_SHEETS_SETUP.md)

Quick summary:
1. Create Google Sheet (2 min)
2. Create Google Apps Script (3 min)
3. Get Sheet ID and update script (1 min)
4. Deploy script as web app (2 min)
5. Update your website URLs (2 min)
6. Test forms (2 min)

---

## Alternative: Other Email Options

### Option A: AWS SES
- **Cost**: ~$0.10 per 1000 emails (very cheap)
- **Setup**: Moderate
- **Best for**: High-volume production

### Option B: SendGrid
- **Cost**: Free tier (100 emails/day)
- **Setup**: Moderate
- **Best for**: Professional email marketing

### Option C: Mailgun
- **Cost**: Free tier, then ~$35/month
- **Setup**: Moderate
- **Best for**: Transactional emails

### Option D: Custom Backend
- **Cost**: Depends on hosting
- **Setup**: Complex
- **Best for**: Full control and integration

---

## Current Setup: Google Sheets ✅

Your website is **already configured** for Google Sheets.

### What's Done
- ✅ Contact form configured
- ✅ Newsletter form configured
- ✅ JavaScript handler added
- ✅ Google Apps Script template ready

### What You Need to Do
1. Create Google Sheet
2. Create Google Apps Script
3. Deploy and get URL
4. Paste URL in index.html (2 places)

---

## Form Configuration

### Contact Form
- Sends to: `Contact Submissions` tab
- Fields: name, email, message, consent, timestamp
- Trigger: "Send Question" button

### Newsletter Form
- Sends to: `Newsletter Subscriptions` tab
- Fields: email, consent, timestamp
- Trigger: "Subscribe Now" button

---

## Data Flow

```
User fills form
        ↓
Clicks submit button
        ↓
JavaScript collects data
        ↓
Sends to Google Apps Script
        ↓
Script adds row to Google Sheet
        ↓
Your Google Drive (you see it immediately)
```

---

## Full Setup Guide

**→ See: [GOOGLE_SHEETS_SETUP.md](./GOOGLE_SHEETS_SETUP.md) for detailed instructions**

This document has:
- Step-by-step setup with screenshots descriptions
- Code to copy/paste
- Troubleshooting section
- How to share data with team
- How to export data

---

## Security & Privacy

- ✅ Data stored in YOUR Google Drive
- ✅ No third-party access
- ✅ HTTPS encrypted
- ✅ Automatic Google backups
- ✅ Only you can modify the script
- ✅ GDPR compliant

---

## Support

### Official Resources
- Google Apps Script Docs: https://developers.google.com/apps-script
- Google Sheets Help: https://support.google.com/docs

### Your Forms
After setup, manage data directly in Google Sheets:
- View submissions anytime
- Export to Excel/CSV
- Share with team
- Set up alerts

---

**Ready? → Start with [QUICK_START.md](./QUICK_START.md)**


