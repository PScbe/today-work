# Possible Studio Dashboard

A comprehensive single-page dashboard for studio operations management, integrating Firebase data and Google Sheets financial metrics.

## Features

- **Financial Summary**: Real-time financial metrics **exclusively from Google Sheets**
  - Total shoots count
  - Total revenue
  - Total expenses
  - Current balance (auto-calculated or from sheet)
  - **Note**: All money calculations come from Google Sheets only, not from Firebase

- **Edit Works Overview**: Live tracking of ongoing editing projects
  - Real-time updates from Firebase
  - Project status (On Process, Up Next, On Hold)
  - Urgent project highlighting
  - Days since shoot tracking
  - Deadline monitoring

- **Today's Shoot Bookings**: Current day's shoot schedule
  - Real-time booking updates
  - Time and location details
  - Equipment and editing flags
  - Zero state when no bookings

## Technology Stack

- **Frontend**: React 18 (via CDN)
- **Styling**: Tailwind CSS
- **Database**: Firebase (Firestore + Realtime Database)
- **Data Source**: Google Sheets API v4
- **Font**: Inter (Google Fonts)

## Setup Instructions

### 1. File Structure

```
PS_today/
├── index.html          # Main dashboard (NEW)
├── edit.html           # Edit management system
├── shoot.html          # Shoot booking system
└── README.md          # This file
```

### 2. Firebase Configuration

The dashboard uses two Firebase projects:

**Edit Database** (`possible-edit`):
- Tracks editing projects and their status
- Already configured in `index.html`

**Shoot Database** (`studio-space-rental-database`):
- Manages shoot bookings and rentals
- Already configured in `index.html`

No additional Firebase setup required - the dashboard reuses existing configurations.

### 3. Google Sheets Integration (Super Simple - No API!)

**Current Status**: The dashboard uses a simple iframe embedding to show revenue from your Google Sheet. **No API keys or complex setup needed!**

**Quick Setup (2 steps)**:

1. **Prepare your Google Sheet**:
   - Put your revenue value in cell **G2**
   - Click "Share" → "Anyone with the link can view"
   - Copy your Google Sheets URL

2. **Update the dashboard**:
   - Open `index.html` in a text editor
   - Find line **~190** (search for "SIMPLE CONFIGURATION")
   - Replace `YOUR_GOOGLE_SHEETS_URL_HERE` with your actual URL
   - Save and refresh

**Example**:
```javascript
// Line ~190 in index.html
const GOOGLE_SHEET_URL = 'https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID/edit';
const REVENUE_CELL = 'G2';  // Change if your revenue is in a different cell
```

**That's it!** The dashboard will embed your sheet and show the revenue from cell G2.

**📖 Detailed Guide**: See [GOOGLE_SHEETS_SETUP.md](file:///Users/premkumar/Desktop/ai%20agent/PS_today/GOOGLE_SHEETS_SETUP.md) for step-by-step instructions.

### 4. Running the Dashboard

**Option 1: Direct File Access**
1. Simply open `index.html` in a modern web browser
2. The dashboard will load with real-time Firebase data
3. Google Sheets data will show mock data until configured

**Option 2: Local Server (Recommended)**
```bash
# Using Python 3
cd /Users/premkumar/Desktop/ai\ agent/PS_today
python3 -m http.server 8000

# Then open: http://localhost:8000
```

**Option 3: VS Code Live Server**
1. Install "Live Server" extension in VS Code
2. Right-click `index.html` → "Open with Live Server"

## Usage

### Dashboard Navigation

- **Header**: Shows current time and date
- **Financial Summary**: 
  - Click refresh icon to manually update Google Sheets data
  - Auto-updates on page load
  
- **Edit Works**: 
  - Updates automatically in real-time
  - Urgent projects highlighted with red border and glow effect
  - Shows project status, days since shoot, and deadline
  
- **Today's Bookings**: 
  - Updates automatically in real-time
  - Filters only current day's bookings
  - Shows "0 Bookings" when no shoots scheduled

### Real-Time Updates

The dashboard automatically syncs with Firebase:
- Edit projects update instantly when changed in `edit.html`
- Shoot bookings update instantly when changed in `shoot.html`
- No manual refresh needed for Firebase data

### Responsive Design

The dashboard is fully responsive:
- **Desktop** (1920px+): 4-column grid for financial metrics
- **Tablet** (768px-1919px): 2-column grid
- **Mobile** (<768px): Single column layout

## Customization

### Changing Colors

Edit the Tailwind classes in `index.html`:
- Primary accent: `yellow-400` (change to any Tailwind color)
- Background: `slate-900`, `slate-800`
- Card backgrounds: `slate-800/50` (adjust opacity)

### Modifying Components

Each component is self-contained:
- `FinancialSummary`: Lines 200-350
- `EditWorksOverview`: Lines 352-550
- `TodayShootBookings`: Lines 552-750
- `Dashboard`: Lines 752-850

### Adding New Metrics

To add new financial metrics:
1. Update Google Sheets with new column
2. Modify `fetchGoogleSheetsData` to parse new data
3. Add new metric card in the grid (copy existing card structure)

## Troubleshooting

### Firebase Connection Issues
- Check browser console for errors
- Verify Firebase configs match `edit.html` and `shoot.html`
- Ensure internet connection is active

### Google Sheets Not Loading
- Verify API key is valid and not restricted
- Check spreadsheet is publicly readable
- Confirm spreadsheet ID is correct
- Check browser console for API errors

### No Data Showing
- **Edit Works**: Check if there are active projects in `edit.html`
- **Today's Bookings**: Verify bookings exist for current date in `shoot.html`
- **Financial Data**: Currently shows mock data until Google Sheets is configured

### Styling Issues
- Clear browser cache
- Ensure Tailwind CSS CDN is loading (check Network tab)
- Verify no ad blockers are interfering

## Browser Compatibility

Tested and working on:
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

## Security Notes

- Firebase security rules should be configured in Firebase Console
- Google Sheets API key should be restricted to specific domains in production
- For production deployment, consider using environment variables for API keys

## Future Enhancements

Potential additions:
- [ ] Weekly/Monthly view toggle
- [ ] Export financial reports to PDF
- [ ] Push notifications for urgent projects
- [ ] Analytics dashboard with charts
- [ ] Dark/Light theme toggle
- [ ] Multi-user authentication
- [ ] Project completion statistics

## Support

For issues or questions:
1. Check the troubleshooting section above
2. Review browser console for error messages
3. Verify Firebase and Google Sheets configurations

## License

© 2024 Possible Studio. All rights reserved.
