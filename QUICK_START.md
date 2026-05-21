# ⚡ QUICK START - Google Sheets Setup (10 Minutes)

## Your Setup (Two Separate Sheets)

✅ **Subscription Sheet**: `10Ar6riV_lK8KtMPe6CcZh6QJbZC4VZbm5TNgAoxdZr4`  
✅ **Questions Sheet**: `1OnK6VqC9VXGyL_ezIyBYhrjPQK0U28fNmqViBKlbm5o`

---

## Step 1: Add Headers to Your Sheets (1 min)

### Subscription Sheet
- A1: `timestamp` | B1: `email` | C1: `consent`

### Questions Sheet
- A1: `timestamp` | B1: `name` | C1: `email` | D1: `message` | E1: `consent` | F1: `message_id`

---

## Step 2: Create First Google Apps Script (2 min)

**For QUESTIONS form:**

1. Open your **Questions sheet**
2. Click **"Extensions"** → **"Apps Script"**
3. Delete default code, paste this:

```javascript
const SHEET_ID = "1OnK6VqC9VXGyL_ezIyBYhrjPQK0U28fNmqViBKlbm5o";

function doPost(e) {
  try {
    const sheet = SpreadsheetApp.openById(SHEET_ID);
    const ws = sheet.getActiveSheet();
    const data = JSON.parse(e.postData.contents);
    
    const lastRow = ws.getLastRow();
    let nextId = 1;
    if (lastRow > 1) {
      const lastId = ws.getRange(lastRow, 6).getValue();
      nextId = (parseInt(lastId, 10) || 0) + 1;
    }

    const row = [
      new Date().toLocaleString(),
      data.name || "",
      data.email || "",
      data.message || "",
      data.consent || "no",
      nextId
    ];
    
    ws.appendRow(row);
    
    return ContentService.createTextOutput(JSON.stringify({
      success: true,
      message: "Question saved to Google Sheets"
    })).setMimeType(ContentService.MimeType.JSON);
    
  } catch (error) {
    return ContentService.createTextOutput(JSON.stringify({
      success: false,
      error: error.toString()
    })).setMimeType(ContentService.MimeType.JSON);
  }
}
```

4. Click **Save** (Ctrl+S)
5. Click **"Deploy"** → **"New Deployment"**
6. Select **"Web app"**, set:
   - Execute as: **Me**
   - Who has access: **Anyone**
7. Click **"Deploy"**
8. **Authorize** when prompted
9. **Copy the URL** (save it as `QUESTIONS_URL`)

---

## Step 3: Create Second Google Apps Script (2 min)

**For NEWSLETTER form:**

1. Open your **Subscription sheet**
2. Click **"Extensions"** → **"Apps Script"**
3. Delete default code, paste this:

```javascript
const SHEET_ID = "10Ar6riV_lK8KtMPe6CcZh6QJbZC4VZbm5TNgAoxdZr4";

function doPost(e) {
  try {
    const sheet = SpreadsheetApp.openById(SHEET_ID);
    const ws = sheet.getActiveSheet();
    const data = JSON.parse(e.postData.contents);
    
    const row = [
      new Date().toLocaleString(),
      data.email || "",
      data.consent || "no"
    ];
    
    ws.appendRow(row);
    
    return ContentService.createTextOutput(JSON.stringify({
      success: true,
      message: "Email saved to Google Sheets"
    })).setMimeType(ContentService.MimeType.JSON);
    
  } catch (error) {
    return ContentService.createTextOutput(JSON.stringify({
      success: false,
      error: error.toString()
    })).setMimeType(ContentService.MimeType.JSON);
  }
}
```

4. Click **Save** (Ctrl+S)
5. Click **"Deploy"** → **"New Deployment"**
6. Select **"Web app"**, set:
   - Execute as: **Me**
   - Who has access: **Anyone**
7. Click **"Deploy"**
8. **Authorize** when prompted
9. **Copy the URL** (save it as `NEWSLETTER_URL`)

---

## Step 4: Update Your Website (2 min)

Open **`index.html`** and find these two sections:

### Contact Form (Search "Have Questions")
Replace the `action` URL with your **QUESTIONS_URL**:
```html
action="YOUR_QUESTIONS_URL_HERE" method="POST"
```

### Newsletter Form (Search "Stay Updated")
Replace the `action` URL with your **NEWSLETTER_URL**:
```html
action="YOUR_NEWSLETTER_URL_HERE" method="POST"
```

Remove the `<input type="hidden" name="tab" ...>` line from both forms if it exists.

---

## Step 5: Test (1 min)

1. Open your website
2. Fill out **Contact Form** → Submit
3. Check your **Questions Sheet** ✅
4. Fill out **Newsletter Form** → Submit
5. Check your **Subscription Sheet** ✅

---

## 🎉 Done!

Your forms now:
- ✅ Send to YOUR Google Sheets
- ✅ Completely FREE
- ✅ Unlimited submissions
- ✅ Direct access to all data

---

## 📊 Access Your Data

- **Questions**: https://docs.google.com/spreadsheets/d/1OnK6VqC9VXGyL_ezIyBYhrjPQK0U28fNmqViBKlbm5o/
- **Subscriptions**: https://docs.google.com/spreadsheets/d/10Ar6riV_lK8KtMPe6CcZh6QJbZC4VZbm5TNgAoxdZr4/

View/share/export anytime!

---

**Setup time: ~10 minutes. Your website is ready!** 🚀


