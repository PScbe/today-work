# Super Simple Google Sheets Setup (No API!)

## What You Need
- Your Google Sheet with revenue in cell **G2**
- 2 minutes

## Setup Steps

### Step 1: Prepare Your Google Sheet

1. Open your Google Sheet
2. Make sure your **revenue value is in cell G2**
3. Click **"Share"** button (top right)
4. Change to **"Anyone with the link can view"**
5. Copy the entire URL from your browser
   ```
   Example: https://docs.google.com/spreadsheets/d/1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms/edit
   ```

### Step 2: Update Dashboard

1. Open `index.html` in any text editor
2. Find line **~190** (search for "SIMPLE CONFIGURATION")
3. Replace this line:
   ```javascript
   const GOOGLE_SHEET_URL = 'YOUR_GOOGLE_SHEETS_URL_HERE';
   ```
   
   With your actual URL:
   ```javascript
   const GOOGLE_SHEET_URL = 'https://docs.google.com/spreadsheets/d/1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms/edit';
   ```

4. Save the file
5. Refresh your browser

**Done!** Your revenue from cell G2 will now display on the dashboard.

## Want to Change the Cell?

If your revenue is in a different cell (e.g., H5), just change line ~195:

```javascript
const REVENUE_CELL = 'H5';  // Change from 'G2' to your cell
```

## That's It!

- ✅ No API keys needed
- ✅ No Google Cloud setup
- ✅ Just paste your sheet URL
- ✅ Live updates from your sheet

The dashboard will embed your Google Sheet and show the revenue value directly!
