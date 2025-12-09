# Quick Reference Guide - FishCRRM 1.1 Knowledge Base

Quick reference for common tasks and information.

## 🚀 Quick Start

### For Users
1. Navigate to the Knowledge Base URL
2. Use navbar or quick links to access sections
3. Use search bar for quick lookups
4. Apply filters to narrow results

### For Developers
1. Clone repository
2. Update `config.js` with Spreadsheet ID and API Key
3. Run local server: `python -m http.server 8000`
4. Open `http://localhost:8000`

## 📍 Navigation Shortcuts

| Page | URL Hash | Description |
|------|----------|-------------|
| Home | `#home` | Dashboard with statistics |
| Implementation Structure | `#structure` | Organizational hierarchy |
| FMA Profile | `#fmaprofile` | FMA 06 and 09 characteristics |
| FMA Municipalities | `#fmamunicipalities` | Municipality listings |
| Landing Centers | `#landingcenters` | Interactive map |
| Activities | `#activities` | Timeline of activities |
| Directory | `#directory` | Contact information |
| References | `#references` | Document library |
| Search | `#search` | Global search |
| Learn More | `#learnmore` | Project information |
| About | `#about` | Platform information |

## 🔍 Common Tasks

### Find Municipalities by Region
1. Go to FMA Municipalities
2. Select Region from dropdown
3. View filtered results

### View Landing Centers on Map
1. Go to Landing Centers
2. Select FMA filter
3. Optionally add Region/Province filters
4. View markers on map

### Export Directory Contacts
1. Go to Directory
2. Select directory type (Internal/External/NPMO)
3. Apply filters if needed
4. Click "Download as CSV"

### Search for Information
1. Type in search bar (top right)
2. Press Enter or click search icon
3. View results grouped by section
4. Click "View Page" to navigate

### Filter Activities by Year
1. Go to Activities
2. Select year from dropdown
3. View filtered timeline

## 📊 Data Sheet Reference

| Sheet Name | Purpose | Key Columns |
|------------|---------|-------------|
| `FMA_Municipalities` | Municipality listings | FMA, REGION, PROVINCE, CITY_MUN, NSAP |
| `Landing_Centers` | Map locations | FMA, REGION, PROVINCE, LANDING_CENTER, LATITUDE, LONGITUDE |
| `Activities_Conducted` | Activity timeline | ACTIVITY_TITLE, DATE_CONDUCTED, LOCATION, RESOURCE_PERSON |
| `Internal_Directory` | Internal contacts | GIVEN_NAME, LAST_NAME, COMPONENT, POSITION_DESIGNATION, EMAIL |
| `External_Directory` | External contacts | GIVEN_NAME, LAST_NAME, OFFICE, FMA_LEAD, EMAIL |
| `NPMO_Directory` | NPMO contacts | GIVEN_NAME, LAST_NAME, OFFICE, COMPONENT, EMAIL |
| `Reference_Files` | Documents | DOCUMENT_TITLE, FILE_URL, CATEGORY |
| `Implementation_Structure` | Org structure | COMPONENT, FULL_NAME, LEVEL, HEAD, COMPOSITION |
| `FMA_Profile` | FMA characteristics | KEY_CHARACTERISTICS, MEASUREMENT, FMA 06, FMA 09 |

## 🎨 Color Reference

| Color | Hex Code | Usage |
|-------|----------|-------|
| Primary Dark | `#151269` | Navbar, titles, icons |
| Footer/Buttons | `#0f1056` | Footer, buttons, accents |
| Success | `#00b894` | Success indicators, NSAP badges |
| Warning | `#fdcb6e` | Tips, highlights |

## 🔧 Configuration

### config.js
```javascript
const CONFIG = {
  SPREADSHEET_ID: 'YOUR_SPREADSHEET_ID',
  API_KEY: 'YOUR_API_KEY'
};
```

### Required Google Sheets API Setup
1. Enable Google Sheets API in Google Cloud Console
2. Create API key
3. Restrict to Google Sheets API only
4. Add HTTP referrer restrictions (GitHub Pages URL)

## 🐛 Common Issues & Solutions

| Issue | Solution |
|-------|----------|
| Data not loading | Check API key, verify sheet is public, check console |
| Map not showing | Verify coordinates exist, check Leaflet.js loaded |
| Filters not working | Clear filters, refresh page, check console |
| Export not working | Check browser download settings, allow pop-ups |
| Navigation broken | Check ROUTES in app.js, verify hash format |

## 📱 Responsive Breakpoints

| Device | Width | Behavior |
|--------|-------|----------|
| Mobile | < 576px | Filters stack, tables scroll horizontally |
| Tablet | 576px - 992px | Mixed layout, adaptive spacing |
| Desktop | > 992px | Full layout, side-by-side components |

## 🔑 Key Functions

### Data Loading
- `loadFMAMunicipalities()` - Load FMA municipalities
- `loadLandingCenters()` - Initialize map
- `loadActivities()` - Load activities timeline
- `loadDirectory(type)` - Load directory data

### Navigation
- `navigate(hash)` - Navigate to page
- `updateActiveNavLink(page)` - Update active state

### Filtering
- `filterLandingCentersMarkers()` - Filter map markers
- Filter functions update in real-time

## 📞 Support

- **Email**: josesgpadasas@gmail.com
- **Documentation**: See USER_GUIDE.md for detailed help
- **Issues**: Check browser console (F12) for errors

## 📚 Documentation Links

- [User Guide](USER_GUIDE.md) - Complete user instructions
- [Features](FEATURES.md) - Feature documentation
- [API Reference](API.md) - Function documentation
- [Developer Guide](DEVELOPER_GUIDE.md) - Development help
- [Contributing](CONTRIBUTING.md) - Contribution guidelines

---

**Version**: 1.1  
**Last Updated**: January 2025
