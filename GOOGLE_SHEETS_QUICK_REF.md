# 📚 Google Sheets Setup - Quick Reference

## The Three Files You Need

### 1. **QUICK_START.md** ⚡ (Read First!)
- 12-minute step-by-step setup
- All you need to get started
- Copy/paste code provided

### 2. **GOOGLE_SHEETS_SETUP.md** 📖 (Detailed Guide)
- Complete reference
- Troubleshooting section
- Advanced options

### 3. **GOOGLE_SHEETS_UPDATE.md** 🔄 (Why We Changed)
- Explains the change
- Formspree → Google Sheets
- Benefits of new approach

---

## The 6 Simple Steps

```
Step 1: Create Google Sheet (2 min)
         └─→ Add 2 tabs with headers

Step 2: Create Google Apps Script (3 min)
         └─→ Copy/paste code

Step 3: Get Sheet ID (1 min)
         └─→ Copy from URL

Step 4: Deploy Script (2 min)
         └─→ Get deployment URL

Step 5: Update Website (2 min)
         └─→ Paste URL in index.html

Step 6: Test Forms (2 min)
         └─→ Submit form, check Google Sheet
```

---

## Your Website Changes

### Before (Formspree)
```html
<form action="https://formspree.io/f/xxx" method="POST">
```

### After (Google Sheets)
```html
<form action="https://script.google.com/macros/d/xxx/usercontent" method="POST">
  <input type="hidden" name="tab" value="Contact Submissions" />
```

✅ **Both forms updated**  
✅ **JavaScript handler added**  
✅ **Ready to go!**

---

## What You'll Get

- 📊 All form data in Google Sheets
- 📅 Automatic timestamps
- 👥 Easy team sharing
- 💾 Export to Excel/CSV anytime
- 🔔 Optional email alerts
- 🔐 Full data control
- 💰 Completely FREE

---

## Start Here

→ **Read [QUICK_START.md](./QUICK_START.md) (12 minutes)**

Then:
1. Create Google Sheet
2. Copy/paste Google Apps Script code
3. Get Sheet ID
4. Deploy script
5. Update 2 URLs in your website
6. Test forms

**You're done!** 🚀

---

## Files in Your Project

```
die-amsel/
├── 📚 DOCUMENTATION
│   ├── QUICK_START.md              ← START HERE!
│   ├── GOOGLE_SHEETS_SETUP.md      ← Detailed guide
│   ├── GOOGLE_SHEETS_UPDATE.md     ← Why we changed
│   ├── GOOGLE_SHEETS_QUICK_REF.md  ← This file
│   ├── SETUP_GUIDE.md              ← General setup
│   └── ... (other docs)
│
├── 💻 WEBSITE FILES
│   ├── index.html                  (Updated)
│   ├── style.css
│   ├── gdpr.html
│   └── assets/
│
└── 📝 README_DOCUMENTATION.md      ← Doc index
```

---

## Next Actions

✅ **Completed:**
- Modern website design
- Contact form setup
- Newsletter form setup
- Cookie consent banner
- Mobile responsive
- All documentation

⏳ **You Need to Do:**
1. Create Google Sheet
2. Create Google Apps Script
3. Deploy and get URL
4. Update 2 URLs in index.html
5. Test forms

**Estimated time: 12 minutes**

---

## Questions?

- **"How do I start?"** → [QUICK_START.md](./QUICK_START.md)
- **"I need more details"** → [GOOGLE_SHEETS_SETUP.md](./GOOGLE_SHEETS_SETUP.md)
- **"Why Google Sheets?"** → [GOOGLE_SHEETS_UPDATE.md](./GOOGLE_SHEETS_UPDATE.md)
- **"General help"** → [MAINTENANCE.md](./MAINTENANCE.md)
- **"What changed?"** → [README_DOCUMENTATION.md](./README_DOCUMENTATION.md)

---

**You've got this!** 💪 Start with [QUICK_START.md](./QUICK_START.md)
