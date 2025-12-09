# FishCRRM 1.1 Knowledge Base

A centralized repository web application for the Fisheries and Coastal Resilient Resource Planning and Management (FishCRRM) 1.1 Component of the National Fisheries Research and Development Institute's FishCoRe Project Management Office.

## 📋 Table of Contents

- [Overview](#overview)
- [Quick Start Guide](#quick-start-guide)
- [Features](#features)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Google Sheets Structure](#google-sheets-structure)
- [Usage Guide](#usage-guide)
- [Technical Details](#technical-details)
- [Troubleshooting](#troubleshooting)
- [Maintenance](#maintenance)
- [Additional Documentation](#additional-documentation)

## 🎯 Overview

The FishCRRM 1.1 Knowledge Base is a Single Page Application (SPA) that provides a centralized platform for accessing curated resources, tools, and data related to the FishCRRM 1.1 Component. The application features a modern, responsive design with glassmorphism UI elements and seamless navigation.

**This version has been converted from Google Apps Script to a standalone web application that can be hosted on GitHub Pages.**

### Key Objectives

- Centralize all FishCRRM 1.1 Component resources and information
- Provide easy access to personnel directories, activities, municipalities, and reference materials
- Enable quick search across all content
- Display implementation structure and FMA profiles
- Maintain an organized, user-friendly interface

## 🚀 Quick Start Guide

### Option 1: GitHub Pages Deployment (Recommended)

See [GITHUB_PAGES_SETUP.md](GITHUB_PAGES_SETUP.md) for detailed instructions.

**Quick Steps:**
1. Set up Google Sheets API (get API key from Google Cloud Console)
2. Update `config.js` with your Spreadsheet ID and API Key
3. Make your Google Sheet publicly accessible
4. Push files to GitHub repository
5. Enable GitHub Pages in repository settings
6. Your site will be live at `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/`

### Option 2: Google Apps Script (Legacy)

If you prefer to use the original Google Apps Script version:

1. **Create Google Apps Script Project**
   ```bash
   # Go to https://script.google.com/
   # Click "New Project"
   # Rename to "FishCRRM 1.1 Knowledge Base"
   ```

2. **Upload Files**
   - Copy `code.js` content to `Code.gs`
   - Create HTML files: `layout.html`, `index.html`, `structure.html`, `municipalities.html`, `activities.html`, `directory.html`, `references.html`, `search.html`, `about.html`, `learnmore.html`, `fmaprofile.html`, `pagenavbar.html`, `pagefooter.html`, `pagetoast.html`, `scripts.html`, `styles.html`

3. **Configure Spreadsheet**
   ```javascript
   // In Code.gs, update:
   const SPREADSHEET_ID = 'YOUR_SPREADSHEET_ID';
   ```

4. **Set Up Google Sheets**
   - Create sheets: `Internal_Directory`, `External_Directory`, `NPMO_Directory`, `Activities_Conducted`, `FMA_Municipalities`, `Landing_Centers`, `Reference_Files`, `Implementation_Structure`, `FMA_Profile`
   - Add column headers (see [Google Sheets Structure](#google-sheets-structure))

5. **Deploy**
   - Click "Deploy" → "New deployment" → "Web app"
   - Set "Execute as": "Me"
   - Set "Who has access": "Anyone" (or your preference)
   - Copy the Web App URL

6. **Test**
   - Open the Web App URL
   - Verify navigation works
   - Check data loads correctly

### For Developers

- See [API Documentation](API.md) for backend function details
- See [Developer Guide](DEVELOPER_GUIDE.md) for development workflows
- Check [Troubleshooting](#troubleshooting) for common issues

### For Users

- Navigate using the navbar or quick links
- Use the search feature to find content
- Filter data using dropdowns and search boxes
- Export directory data as CSV

## ✨ Features

### Core Features

1. **Dashboard (Home Page)**
   - Quick statistics overview (Personnel, Activities, Resources)
   - Recent activities timeline
   - Quick access links to all major sections

2. **Implementation Structure**
   - Visual representation of the FishCoRe Project structure
   - Detailed organizational information

3. **FMA Profile**
   - Characteristics and measurements for FMA 06 and FMA 09
   - Tabular data with merged cells for similar characteristics
   - Preserved text formatting from source data
   - Maximized table width on desktop with horizontal scrolling on mobile

4. **FMA Municipalities**
   - Comprehensive list of municipalities by FMA with regional and provincial breakdown
   - Advanced multi-level filtering by FMA, Region, and Province (with dependent province selection)
   - Pagination with customizable items per page (10, 20, 50, 100)
   - Summary statistics sidebar showing:
     - Total number of municipalities
     - Number of NSAP monitored municipalities
     - Side-by-side tables: Municipalities by Region (alphabetically sorted, BARMM at bottom) and Municipalities by FMA (numerically sorted)
   - Real-time filtering that updates both table and summary statistics
   - Maximized table width on desktop with horizontal scrolling on mobile

5. **Landing Centers Map**
   - Interactive map visualization powered by Leaflet.js
   - Multiple filter options:
     - Filter by FMA, Region, Province, Fishing Ground
     - Search by city/municipality or landing center name
   - Base map controls allowing switch between different map tile layers (OpenStreetMap, Satellite, etc.)
   - Real-time marker filtering that updates the map as filters change
   - Info panel displaying count of visible markers
   - Collapsible filter sidebar for mobile-friendly access
   - Reset filters button for quick clearing
   - Automatic bounds fitting to show all filtered markers
   - Only locations with valid coordinates are displayed

6. **Activities Conducted**
   - Timeline view of all activities and workshops
   - Year and search filters
   - Activity details including title, location, date, and resource person
   - Mobile-optimized cards with vertical stacking and full-width buttons

7. **Directory**
   - Three directory types:
     - **Internal**: NFRDI FishCore Personnel
     - **External**: External contacts
     - **NPMO**: National Project Management Office personnel
   - Custom filters per directory type
   - CSV export functionality
   - Search functionality
   - Maximized table width on desktop with horizontal scrolling on mobile

8. **References**
   - Document library with categories
   - Search and category filters
   - Pagination (10, 20, 50, 100 items per page)
   - Alphabetical sorting
   - Direct links to documents
   - Mobile-optimized cards with improved spacing and touch interactions

9. **Search**
   - Dual search system:
     - Keyword-based page matching
     - Content-based sheet data searching
   - Recent searches storage
   - Matching items display
   - Quick links to relevant pages

10. **Learn More**
   - Detailed information about FishCRRM 1.1 Component
   - Key interventions and activities
   - Quick links to related sections

11. **About**
    - Knowledge Base information
    - Contact developer section
    - Version information

### UI/UX Features

- **Responsive Design**: Works on desktop, tablet, and mobile devices
  - **Tables**: FMA Profile, Municipalities, and Directory tables are horizontally scrollable on mobile while maximizing width on desktop
  - **Activity Cards**: Optimized timeline cards that stack vertically on mobile with full-width buttons
  - **Reference Cards**: Mobile-optimized cards with improved spacing and touch interactions
  - **Filters**: Responsive filter layouts that stack vertically on mobile devices
- **Glassmorphism**: Modern glass-effect UI elements
- **Smooth Animations**: Fade-in, hover effects, and transitions
- **Color Scheme**: Consistent branding with primary colors (#151269, #0f1056)
- **Loading States**: Spinners and loading indicators
- **Error Handling**: User-friendly error messages
- **Page Persistence**: Maintains current page on refresh using localStorage

## 🏗️ Architecture

### Technology Stack

- **Backend**: Google Sheets API v4 (client-side)
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **UI Framework**: Bootstrap 5.3.3
- **Icons**: Bootstrap Icons
- **Fonts**: Google Fonts (Outfit, Science Gothic)
- **Data Source**: Google Sheets
- **Caching**: Client-side caching (5 minutes TTL)
- **Hosting**: GitHub Pages (or any static hosting)

### Application Flow

```
User Request
    ↓
Google Apps Script (doGet)
    ↓
Layout Template (layout.html)
    ↓
Page Template (index.html, structure.html, etc.)
    ↓
Client-Side JavaScript (scripts.html)
    ↓
Data Fetching (google.script.run)
    ↓
Google Sheets API
    ↓
Response Rendering
```

### Single Page Application (SPA) Routing

The application uses hash-based routing:
- Navigation uses `#page` format (e.g., `#references`, `#activities`)
- Client-side JavaScript handles routing without full page reloads
- Page state is preserved using localStorage
- History API is used for browser back/forward navigation

## 📦 Prerequisites

Before setting up the project, ensure you have:

1. **Google Account** with access to:
   - Google Apps Script
   - Google Sheets
   - Google Drive

2. **Google Sheets Spreadsheet** containing the following sheets:
   - `Internal_Directory`
   - `External_Directory`
   - `NPMO_Directory`
   - `Activities_Conducted`
   - `FMA_6_&_9_Municipalities`
   - `Reference_Files`
   - `Implementation_Structure`
   - `FMA_Profile`

3. **Basic Knowledge** of:
   - HTML/CSS/JavaScript
   - Google Apps Script
   - Google Sheets

## 🚀 Setup Instructions

### Step 1: Create Google Apps Script Project

1. Go to [Google Apps Script](https://script.google.com/)
2. Click **"New Project"**
3. Rename the project to "FishCRRM 1.1 Knowledge Base"

### Step 2: Upload Project Files

1. In the Apps Script editor, create the following files:
   - `Code.gs` (copy content from `code.js`)
   - `layout.html`
   - `index.html`
   - `structure.html`
   - `municipalities.html`
   - `activities.html`
   - `directory.html`
   - `references.html`
   - `search.html`
   - `about.html`
   - `learnmore.html`
   - `fmaprofile.html`
   - `pagenavbar.html`
   - `pagefooter.html`
   - `pagetoast.html`
   - `scripts.html`
   - `styles.html`

2. For each HTML file:
   - Click **"+"** next to Files
   - Select **"HTML"**
   - Name the file (e.g., `index.html`)
   - Paste the corresponding content

3. For `Code.gs`:
   - The default `Code.gs` file should already exist
   - Replace its content with the content from `code.js`

### Step 3: Configure Spreadsheet ID

1. Open `Code.gs` (or `code.js`)
2. Locate the line:
   ```javascript
   const SPREADSHEET_ID = '1LDtZ9VOSgKI5B0c_GtmOhRJiTOA0sb_4dGD4wAJKfqc';
   ```
3. Replace with your Google Sheets Spreadsheet ID
   - Open your Google Sheet
   - The ID is in the URL: `https://docs.google.com/spreadsheets/d/[SPREADSHEET_ID]/edit`

### Step 4: Set Up Google Sheets

1. Create a new Google Sheet or use an existing one
2. Create the following sheets with the exact names:
   - `Internal_Directory`
   - `External_Directory`
   - `NPMO_Directory`
   - `Activities_Conducted`
   - `FMA_6_&_9_Municipalities`
   - `Reference_Files`
   - `Implementation_Structure`
   - `FMA_Profile`

3. Add column headers to each sheet (see [Google Sheets Structure](#google-sheets-structure))

4. Populate with data

### Step 5: Deploy as Web App

1. In Apps Script editor, click **"Deploy"** → **"New deployment"**
2. Click the gear icon ⚙️ next to **"Select type"**
3. Choose **"Web app"**
4. Configure:
   - **Description**: "FishCRRM 1.1 Knowledge Base v1.0"
   - **Execute as**: "Me"
   - **Who has access**: Choose based on your needs:
     - "Only myself" (for testing)
     - "Anyone" (for public access)
5. Click **"Deploy"**
6. Copy the **Web App URL**
7. Click **"Done"**

### Step 6: Test the Application

1. Open the Web App URL in a browser
2. Test navigation between pages
3. Verify data loading from Google Sheets
4. Test search functionality
5. Check responsive design on different devices

## 📁 Project Structure

```
FishCRRM-1.1-Knowledge-Base/
│
├── code.js (Code.gs)              # Google Apps Script backend
│
├── layout.html                    # Main layout template
│
├── Page Templates/
│   ├── index.html                 # Home/Dashboard page
│   ├── structure.html             # Implementation Structure
│   ├── fmaprofile.html            # FMA Profile page
│   ├── municipalities.html        # Municipalities listing
│   ├── activities.html            # Activities timeline
│   ├── directory.html             # Directory (Internal/External/NPMO)
│   ├── references.html            # Reference documents
│   ├── search.html                # Search page
│   ├── learnmore.html             # Learn More page
│   └── about.html                 # About page
│
├── Component Templates/
│   ├── pagenavbar.html            # Navigation bar
│   ├── pagefooter.html            # Footer
│   └── pagetoast.html             # Toast notifications
│
├── Assets/
│   ├── scripts.html               # Client-side JavaScript
│   └── styles.html                # CSS styles
│
└── README.md                      # This documentation
```

### File Descriptions

#### Backend (`code.js` / `Code.gs`)

- **`doGet(e)`**: Entry point for web app requests
- **`loadPage(page)`**: Loads page templates with layout
- **`getPageContent(page)`**: Returns page HTML for SPA navigation
- **`include(filename)`**: Includes partial templates
- **`getQuickStats()`**: Fetches dashboard statistics
- **`getSheetData(sheetName)`**: Generic function to fetch sheet data with caching
- **`getDirectory(type)`**: Fetches directory data (internal/external/npmo)
- **`getActivities()`**: Fetches activities data
- **`getMunicipalities()`**: Fetches municipalities data
- **`getReferenceFiles()`**: Fetches reference documents
- **`getFMAProfile()`**: Fetches FMA profile data
- **`searchAll(query)`**: Searches across all sheets
- **`exportDirectoryToCSV(type)`**: Exports directory data as CSV

#### Frontend Templates

- **`layout.html`**: Main layout wrapper, includes navbar, footer, and scripts
- **`index.html`**: Dashboard with stats, quick links, and recent activities
- **`structure.html`**: Static content about implementation structure
- **`fmaprofile.html`**: FMA 06 and FMA 09 profile tables
- **`municipalities.html`**: Municipalities table with FMA filter
- **`activities.html`**: Timeline view with year and search filters
- **`directory.html`**: Three-tab directory with custom filters
- **`references.html`**: Reference documents with pagination
- **`search.html`**: Search interface with results
- **`learnmore.html`**: Information about FishCRRM 1.1 Component
- **`about.html`**: About the Knowledge Base

#### Client-Side Scripts (`scripts.html`)

- **Routing**: Hash-based SPA navigation
- **Data Loading**: Functions to load data for each page
- **Event Handlers**: Click handlers, search, filters
- **UI Updates**: Dynamic content rendering
- **localStorage**: Page state persistence

#### Styles (`styles.html`)

- **Bootstrap 5.3.3**: UI framework
- **Custom CSS**: Glassmorphism, animations, color scheme
- **Responsive Design**: Mobile-first approach
- **Icons**: Bootstrap Icons integration

## ⚙️ Configuration

### Spreadsheet ID

Update in `code.js`:
```javascript
const SPREADSHEET_ID = 'YOUR_SPREADSHEET_ID_HERE';
```

### Cache TTL

Adjust cache duration in `code.js`:
```javascript
const CACHE_TTL = 300; // 5 minutes (in seconds)
```

### Color Scheme

Update in `styles.html`:
```css
--primary-dark: #151269;  /* Navbar, titles, icons */
--footer-color: #0f1056;  /* Footer, buttons */
```

### Pagination Options

Update in `references.html` and `scripts.html`:
```javascript
const itemsPerPageOptions = [10, 20, 50, 100];
```

## 📊 Google Sheets Structure

### Required Sheets

#### 1. `Internal_Directory`
Columns:
- `GIVEN_NAME`
- `LAST_NAME`
- `MIDDLE_INITIAL`
- `COMPONENT`
- `POSITION_DESIGNATION`
- `EMPLOYMENT_TYPE`
- `EMAIL`
- (Additional columns as needed)

#### 2. `External_Directory`
Columns:
- `GIVEN_NAME`
- `LAST_NAME`
- `MIDDLE_INITIAL`
- `OFFICE`
- `POSITION_DESIGNATION`
- `FMA_LEAD`
- `EMAIL`
- (Additional columns as needed)

#### 3. `NPMO_Directory`
Columns:
- `GIVEN_NAME`
- `LAST_NAME`
- `MIDDLE_INITIAL`
- `OFFICE`
- `POSITION_DESIGNATION`
- `COMPONENT`
- `EMAIL`
- (Additional columns as needed)

#### 4. `Activities_Conducted`
Columns:
- `ACTIVITY_TITLE`
- `DATE_CONDUCTED` (Date format: YYYY-MM-DD)
- `LOCATION`
- `RESOURCE_PERSON`
- `REFERENCE_DOC`
- (Additional columns as needed)

#### 5. `FMA_Municipalities`
Columns:
- `FMA` (e.g., "6", "9", or "FMA 6", "FMA 9")
- `REGION`
- `PROVINCE`
- `CITY_MUN` (City/Municipality)
- `NSAP` (NSAP monitoring indicator - Yes/No or similar)
- (Additional columns as needed)

**Note:** This replaces the old `FMA_6_&_9_Municipalities` sheet.

#### 6. `Landing_Centers`
Columns:
- `FMA` (e.g., "6", "9")
- `REGION`
- `PROVINCE`
- `CITY_MUN` (City/Municipality)
- `LANDING_CENTER` (Landing center name)
- `FISHING_GROUND` (Fishing ground name)
- `LATITUDE` (Decimal degrees, e.g., 10.1234)
- `LONGITUDE` (Decimal degrees, e.g., 123.5678)
- (Additional columns as needed)

**Note:** Only rows with valid latitude and longitude coordinates will be displayed on the map.

#### 7. `Reference_Files`
Columns:
- `DOCUMENT_TITLE`
- `FILE_URL` (Full URL to document)
- `CATEGORY`
- (Additional columns as needed)

#### 8. `Implementation_Structure`
Columns:
- `COMPONENT`
- `FULL_NAME`
- `LEVEL` (National, FMA, Regional)
- `HEAD`
- `COMPOSITION`
- (Additional columns as needed)

#### 9. `FMA_Profile`
Columns:
- `KEY_CHARACTERISTICS`
- `MEASUREMENT`
- `FMA 06` (Text with formatting preserved)
- `FMA 09` (Text with formatting preserved)

### Sheet Naming

**Important**: Sheet names must match exactly (case-sensitive):
- `Internal_Directory`
- `External_Directory`
- `NPMO_Directory`
- `Activities_Conducted`
- `FMA_Municipalities` (Note: replaces old `FMA_6_&_9_Municipalities`)
- `Landing_Centers` (New sheet for map visualization)
- `Reference_Files`
- `Implementation_Structure`
- `FMA_Profile`

## 📖 Usage Guide

### For End Users

#### Navigation

- Use the navbar links to navigate between pages
- Click the logo/title to return to home
- Use browser back/forward buttons
- Quick links on home page for fast access

#### Searching

1. Click the search icon in navbar or go to Search page
2. Enter search query
3. View results grouped by page and content matches
4. Click "View Page" to navigate to relevant sections
5. View matching items listed below each result

#### Filtering

- **FMA Municipalities**: Use multi-level filters (FMA, Region, Province). Province options depend on selected region. Use pagination to navigate large datasets.
- **Landing Centers Map**: Use multiple filters (FMA, Region, Province, Fishing Ground) or search by city/municipality or landing center name. Filters update markers in real-time.
- **Activities**: Use year dropdown and search box
- **Directory**: Use type-specific filters (Component, Employment Type, Office)
- **References**: Use category dropdown and search box

#### Exporting Data

- **Directory**: Click "Download as CSV" button
- Data is exported in CSV format
- Opens in browser or downloads based on browser settings

### For Administrators

#### Updating Data

1. Open the Google Sheet
2. Edit data directly in the sheets
3. Changes are reflected after cache expires (5 minutes by default)
4. To force refresh, clear cache or wait for TTL

#### Adding New Pages

1. Create new HTML template file
2. Add to `validPages` array in `code.js`
3. Add route to `ROUTES` object in `scripts.html`
4. Add navigation link in `pagenavbar.html`
5. Create data loading function if needed

#### Modifying Styles

1. Edit `styles.html`
2. Update CSS variables for colors
3. Add new styles as needed
4. Test responsive design

## 🔧 Technical Details

### Caching Strategy

- **CacheService**: Google Apps Script caching
- **TTL**: 5 minutes (300 seconds)
- **Cache Keys**: 
  - `quickstats`: Dashboard statistics
  - `sheet_[SHEET_NAME]`: Individual sheet data
- **Benefits**: Reduces API calls, improves performance

### Data Fetching

- **Asynchronous**: Uses `google.script.run` with promises
- **Error Handling**: Try-catch blocks with user-friendly messages
- **Loading States**: Spinners during data fetch
- **Timeout**: 15 seconds default timeout

### Routing Mechanism

```javascript
// Hash-based routing
navigate('#references')  // Navigates to references page
navigate('#activities?year=2024')  // With query parameters

// Page persistence
localStorage.setItem('lastPage', '#references')
// Restored on refresh
```

### Search Algorithm

1. **Keyword Matching**: Exact, partial, contains
2. **Scoring**: Exact match = 10 points, partial = 1 point
3. **Deduplication**: Removes duplicate results
4. **Sorting**: By relevance score (highest first)
5. **Limits**: 50 results max

### Responsive Breakpoints

- **Mobile**: < 576px
  - Tables: Horizontal scrolling enabled with minimum widths
  - Cards: Stack vertically with full-width buttons
  - Filters: Stack vertically with full-width inputs
  - Reduced padding and font sizes for better fit
- **Tablet**: 576px - 992px
  - Tables: Horizontal scrolling when content exceeds viewport
  - Cards: Maintain desktop layout with adjusted spacing
  - Filters: Side-by-side layout with responsive columns
- **Desktop**: > 992px
  - Tables: Maximized width with optimal column distribution
  - Cards: Full horizontal layout with optimal spacing
  - Filters: Side-by-side layout with optimal spacing

## 🐛 Troubleshooting

### Common Issues

#### 1. "Failed to load page" Error

**Cause**: Invalid page name or missing template
**Solution**: 
- Check `validPages` array in `code.js`
- Verify HTML file exists in Apps Script project
- Check browser console for specific error

#### 2. Data Not Loading

**Cause**: 
- Incorrect sheet name
- Missing columns
- Spreadsheet ID mismatch
- Cache issues

**Solution**:
- Verify sheet names match exactly
- Check column headers
- Confirm `SPREADSHEET_ID` in `code.js`
- Clear cache or wait for TTL

#### 3. Navigation Not Working

**Cause**: JavaScript errors or missing event handlers
**Solution**:
- Check browser console for errors
- Verify `scripts.html` is included in `layout.html`
- Ensure `navigate()` function is defined

#### 4. Styling Issues

**Cause**: Missing CSS or Bootstrap not loaded
**Solution**:
- Verify `styles.html` is included
- Check Bootstrap CDN link
- Clear browser cache

#### 5. Search Returns No Results

**Cause**: 
- Query too specific
- Data not indexed
- Case sensitivity

**Solution**:
- Try broader search terms
- Check if data exists in sheets
- Search is case-insensitive, verify query

#### 6. CSV Export Not Working

**Cause**: Browser blocking download or data format issue
**Solution**:
- Check browser download settings
- Verify data format in directory sheets
- Test in different browser

### Debugging Tips

1. **Browser Console**: Check for JavaScript errors
2. **Network Tab**: Monitor API calls to Google Apps Script
3. **Apps Script Execution Log**: View server-side logs
4. **Test in Incognito**: Rule out cache/extensions
5. **Check Permissions**: Ensure proper access to Google Sheet

## 🔄 Maintenance

### Regular Tasks

1. **Data Updates**: Keep Google Sheets data current
2. **Cache Management**: Monitor cache performance
3. **Error Monitoring**: Check Apps Script execution logs
4. **User Feedback**: Collect and address user issues
5. **Performance**: Monitor load times and optimize

### Version Control

- Keep backup of all HTML/JS files
- Document changes in version history
- Test changes in staging before production

### Updates

When updating:
1. Test locally first
2. Deploy new version in Apps Script
3. Update version number in About page
4. Notify users of changes

## 📝 Notes

- The application uses Google Apps Script's free tier limitations
- Cache TTL can be adjusted based on update frequency needs
- All data is stored in Google Sheets (no database required)
- The application is optimized for modern browsers
- Mobile responsiveness is built-in

## 📞 Support

For issues or questions:
- Check this documentation first
- Review browser console for errors
- Check Apps Script execution logs
- Contact the developer (see About page)

## 📚 Additional Documentation

### For Users
- **[User Guide](USER_GUIDE.md)**: Comprehensive guide for end users with step-by-step instructions
- **[Features Documentation](FEATURES.md)**: Detailed documentation of all features and capabilities

### For Developers
- **[API Documentation](API.md)**: Complete reference for all backend functions and data structures
- **[Developer Guide](DEVELOPER_GUIDE.md)**: Development workflows, best practices, and advanced topics
- **[Contributing Guide](CONTRIBUTING.md)**: Guidelines for contributing to the project

### Deployment & Migration
- **[GitHub Pages Setup](GITHUB_PAGES_SETUP.md)**: Step-by-step deployment guide
- **[Conversion Notes](CONVERSION_NOTES.md)**: Migration from Google Apps Script to GitHub Pages
- **[Changelog](CHANGELOG.md)**: Version history and changes

## 📄 License

This project is developed for the National Fisheries Research and Development Institute's FishCoRe Project Management Office - FishCRRM Subcomponent 1.1.

---

**Version**: 1.1  
**Last Updated**: January 2025  
**Maintained by**: FishCoRe Project Management Office

## 📖 Documentation Index

- **[User Guide](USER_GUIDE.md)** - Complete guide for end users
- **[Features Documentation](FEATURES.md)** - Detailed feature descriptions
- **[API Documentation](API.md)** - Backend function reference
- **[Developer Guide](DEVELOPER_GUIDE.md)** - Development workflows
- **[Contributing Guide](CONTRIBUTING.md)** - Contribution guidelines
- **[Quick Reference](QUICK_REFERENCE.md)** - Quick lookup guide
- **[Changelog](CHANGELOG.md)** - Version history
- **[GitHub Pages Setup](GITHUB_PAGES_SETUP.md)** - Deployment guide
- **[Conversion Notes](CONVERSION_NOTES.md)** - Migration documentation

### Recent Updates (Version 1.1 - January 2025)

- **New Features**:
  - **FMA Municipalities Page**: Comprehensive municipality listings with advanced filtering, pagination, and summary statistics
  - **Landing Centers Interactive Map**: Full-screen map visualization with multiple filter options, base map controls, and real-time marker updates
  - **Enhanced Summary Statistics**: Side-by-side tables showing municipalities by Region and FMA with alphabetical/numerical sorting
  - **Improved Navigation**: Updated navbar with FMA Municipalities and Landing Centers links
  - **Removed Legacy Pages**: Old Municipalities page replaced by FMA Municipalities

- **Responsive Design Improvements**:
  - FMA Profile table: Maximized width on desktop, horizontal scrolling on mobile
  - FMA Municipalities table: Maximized width on desktop, horizontal scrolling on mobile
  - Directory table: Horizontal scrolling enabled for better mobile experience
  - Activities timeline: Mobile-optimized cards with vertical stacking and full-width buttons
  - References: Mobile-optimized cards with improved spacing and touch interactions
  - Landing Centers map: Mobile-optimized filter sidebar with collapsible controls
  - All filters: Responsive layouts that stack vertically on mobile devices

