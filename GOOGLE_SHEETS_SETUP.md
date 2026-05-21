# 📊 Setup Forms with Google Sheets (FREE & UNLIMITED)

## Why Google Sheets?
✅ Completely FREE  
✅ Unlimited storage  
✅ No monthly limits  
✅ Easy to manage in Google Drive  
✅ Automatic backups  
✅ Share access with your team  

---

## Step 1: Create Google Sheet (2 minutes)

1. Go to [Google Drive](https://drive.google.com)
2. Click **"+ New"** → **"Google Sheet"**
3. Name it: `dieAmsel Form Submissions`
4. You now have an empty sheet

### Set Up Sheet Tabs
1. Bottom of sheet, right-click the default "Sheet1"
2. Rename it to: `Contact Submissions`
3. Add another sheet, name it: `Newsletter Subscriptions`

### Add Headers to Contact Sheet
In **Contact Submissions** tab:
- A1: `timestamp`
- B1: `name`
- C1: `email`
- D1: `message`
- E1: `consent`

### Add Headers to Newsletter Sheet
In **Newsletter Subscriptions** tab:
- A1: `timestamp`
- B1: `email`
- C1: `consent`

---

## Step 2: Create Google Apps Script (3 minutes)

1. In your Google Sheet, click **"Extensions"** → **"Apps Script"**
2. You'll see a code editor with a default function
3. **Delete all the code** and replace it with:

```javascript
const SHEET_ID = "YOUR_SHEET_ID_HERE"; // You'll get this in Step 3

function doPost(e) {
  try {
    const sheet = SpreadsheetApp.openById(SHEET_ID);
    const data = JSON.parse(e.postData.contents);
    const tabName = data.tab || "Contact Submissions";
    const ws = sheet.getSheetByName(tabName);
    
    if (!ws) {
      return ContentService.createTextOutput(JSON.stringify({
        success: false,
        error: "Sheet tab not found"
      })).setMimeType(ContentService.MimeType.JSON);
    }
    
    // Add timestamp and data row
    const row = [
      new Date().toLocaleString(),
      data.name || data.email || "",
      data.email || "",
      data.message || "",
      data.consent || "no"
    ];
    
    ws.appendRow(row);
    
    return ContentService.createTextOutput(JSON.stringify({
      success: true,
      message: "Data saved successfully"
    })).setMimeType(ContentService.MimeType.JSON);
    
  } catch (error) {
    return ContentService.createTextOutput(JSON.stringify({
      success: false,
      error: error.toString()
    })).setMimeType(ContentService.MimeType.JSON);
  }
}
```

---

## Step 3: Get Your Sheet ID (1 minute)

1. In your Google Sheet URL, find the ID:
   ```
   https://docs.google.com/spreadsheets/d/[THIS_IS_YOUR_ID]/edit
   ```
2. Copy that long ID
3. Go back to Apps Script editor
4. Replace `"YOUR_SHEET_ID_HERE"` with your actual Sheet ID
   ```javascript
   const SHEET_ID = "1a2b3c4d5e6f7g8h9i10j11k12l13m14n15o";
   ```
5. Save (Ctrl+S)

---

## Step 4: Deploy as Web App (2 minutes)

1. In Apps Script editor, click **"Deploy"** → **"New Deployment"**
2. Click gear icon, select **"Web app"**
3. In the dialog:
   - Execute as: `Me` (your account)
   - Who has access: **"Anyone"**
4. Click **"Deploy"**
5. Click **"Authorize access"** and grant permissions
6. Copy the **Deployment URL** (looks like: `https://script.google.com/macros/d/...`)
7. **Save this URL!** You'll need it in Step 5

---

## Step 5: Update Your Website (2 minutes)

1. Open your **index.html**
2. Find the **Contact Form** (search for "Have Questions")
3. Update the form action to your Google Apps Script URL:
   ```html
   <form class="contact-form-wrapper" 
     action="YOUR_GOOGLE_APPS_SCRIPT_URL" method="POST">
   ```
4. Find the **Newsletter Form** (search for "Stay Updated")
5. Update its action too:
   ```html
   <form class="newsletter-form-wrapper"
     action="YOUR_GOOGLE_APPS_SCRIPT_URL" method="POST">
   ```

### Also Add Hidden Field for Sheet Tab

In Contact Form add this **after** the form tag:
```html
<input type="hidden" name="tab" value="Contact Submissions" />
```

In Newsletter Form add this **after** the form tag:
```html
<input type="hidden" name="tab" value="Newsletter Subscriptions" />
```

---

## Step 6: Add JavaScript Handler (2 minutes)

Add this code to your **index.html** right before the closing `</body>` tag:

```javascript
<script>
  // Handle form submissions to Google Sheets
  document.addEventListener('submit', function(e) {
    if (e.target.classList.contains('contact-form-wrapper') || 
        e.target.classList.contains('newsletter-form-wrapper')) {
      
      e.preventDefault();
      const form = e.target;
      const action = form.getAttribute('action');
      
      // Collect form data
      const formData = new FormData(form);
      const data = {
        tab: formData.get('tab') || 'Contact Submissions',
        name: formData.get('name') || '',
        email: formData.get('email') || '',
        message: formData.get('message') || '',
        consent: formData.get('consent') ? 'yes' : 'no'
      };
      
      // Send to Google Apps Script
      fetch(action, {
        method: 'POST',
        body: JSON.stringify(data),
        headers: {
          'Content-Type': 'application/json'
        }
      })
      .then(response => response.json())
      .then(result => {
        if (result.success) {
          alert('✅ Thank you! Your message was received.');
          form.reset();
        } else {
          alert('❌ Error: ' + result.error);
        }
      })
      .catch(error => {
        console.error('Error:', error);
        alert('❌ Error sending form. Please try again.');
      });
    }
  });
</script>
```

---

## 🧪 Test Your Setup

1. Open your website
2. Fill out the contact form with test data
3. Click "Send Question"
4. Go back to your Google Sheet
5. Check if data appeared in **Contact Submissions** tab ✅
6. Try the newsletter form
7. Check **Newsletter Subscriptions** tab ✅

---

## 📱 Accessing Your Data

### View Submissions
1. Open your Google Sheet anytime
2. Click the tab: **Contact Submissions** or **Newsletter Subscriptions**
3. All data appears with timestamps

### Download Data
1. Click **File** → **Download** → **CSV** or **Excel**
2. Use in Excel, Google Sheets, or analytics

### Share Access
1. Click **Share** button (top right)
2. Add team member email
3. They can now see submissions in real-time

### Get Email Notifications (Optional)
1. In Google Sheet, click **"Tools"** → **"Notification rules"**
2. Set up: Notify when any cell changes
3. You'll get email alerts for new submissions

---

## 🔒 Security Notes

✅ Data is stored in YOUR Google Drive (you control it)  
✅ No third-party service has access  
✅ HTTPS encrypted  
✅ Automatic backups  
✅ Only you can modify the script  

**Optional**: Limit script access to your IP only in Apps Script settings.

---

## ⚠️ Limits (You Won't Hit These)

- Google Sheets: Unlimited rows
- Apps Script: 100,000+ API calls/day (more than enough)
- Storage: Unlimited
- Cost: $0

---

## 🆘 Troubleshooting

### "Script deployment URL not working"
1. Check the URL is copied completely
2. Make sure you clicked "Deploy" and "Authorize"
3. Try redeploying the script

### "Form doesn't submit"
1. Open browser console (F12)
2. Check for error messages
3. Verify Apps Script URL is correct
4. Make sure form has hidden `tab` field

### "Data doesn't appear in Sheet"
1. Check you're looking at the right tab
2. Verify Sheet ID is correct in the script
3. Check Apps Script authorization was granted

### "Getting CORS error"
1. This is normal - Google Apps Script handles it
2. Data should still save to the sheet
3. Check your Google Sheet for the data

---

## ✅ Final Checklist

- [ ] Created Google Sheet with 2 tabs
- [ ] Added headers to both tabs
- [ ] Created Google Apps Script with code
- [ ] Got Sheet ID and updated script
- [ ] Deployed script as web app
- [ ] Copied deployment URL
- [ ] Updated both form action URLs in HTML
- [ ] Added hidden `tab` fields to forms
- [ ] Added JavaScript submission handler
- [ ] Tested contact form
- [ ] Tested newsletter form
- [ ] Verified data in Google Sheet

---

## 🚀 You're Done!

Your forms now:
✅ Send data directly to Google Sheets  
✅ Are completely FREE (forever)  
✅ Have unlimited storage  
✅ Are secure and private  
✅ Can be shared with your team  

---

## 📞 Need Help?

### Common Tasks

**Share data with team member:**
- Google Sheet → Share → Add email

**Get notified of submissions:**
- Google Sheet → Tools → Notification rules

**Export data:**
- Google Sheet → File → Download as CSV/Excel

**Add more columns:**
- Edit script to add more fields
- Add headers to sheet

---

Generated: May 20, 2026  
Status: ✅ Complete & Ready to Use
