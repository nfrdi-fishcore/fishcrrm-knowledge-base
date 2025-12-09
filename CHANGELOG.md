# Changelog - FishCRRM 1.1 Knowledge Base

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1] - 2025-01-XX

### Added

#### New Pages
- **FMA Municipalities Page** (`fmamunicipalities.html`)
  - Comprehensive municipality listings with advanced filtering
  - Multi-level filtering (FMA, Region, Province with dependent selection)
  - Pagination with customizable items per page (10, 20, 50, 100)
  - Summary statistics sidebar with:
    - Total municipalities count
    - NSAP monitored municipalities count
    - Side-by-side tables: Municipalities by Region and by FMA
  - Real-time filter updates affecting both table and summary
  - Responsive table design with horizontal scrolling on mobile

- **Landing Centers Map Page** (`landingcenters.html`)
  - Interactive map visualization powered by Leaflet.js
  - Multiple filter options (FMA, Region, Province, Fishing Ground, search)
  - Base map controls for switching map layers
  - Real-time marker filtering
  - Collapsible filter sidebar for mobile
  - Info panel with marker count
  - Automatic bounds fitting
  - Only displays locations with valid coordinates

#### New Data Sources
- `FMA_Municipalities` sheet (replaces `FMA_6_&_9_Municipalities`)
- `Landing_Centers` sheet (new)

#### New Functions
- `loadFMAMunicipalities()` - Loads FMA municipalities with filtering and pagination
- `loadLandingCenters()` - Initializes interactive map
- `filterLandingCentersMarkers()` - Real-time marker filtering
- `getFMAMunicipalities()` in data-service.js
- `getLandingCenters()` in data-service.js

#### Navigation Updates
- Added "FMA Municipalities" link to navbar
- Added "Landing Centers" link to navbar
- Removed "Municipalities" link from navbar
- Updated quick links on home page
- Updated quick links in learn more page

### Changed

#### Removed Pages
- **Municipalities Page** (`municipalities.html`)
  - Removed from navigation
  - Replaced by FMA Municipalities page
  - Functionality merged into new page

#### Updated Functions
- Removed `loadMunicipalities()` function
- Updated routing to exclude `municipalities` route
- Updated search mapping to use `fmamunicipalities`

#### Data Structure Changes
- Sheet name changed from `FMA_6_&_9_Municipalities` to `FMA_Municipalities`
- Column names updated:
  - `FMA_ID` → `FMA`
  - `MUNICIPALITY` → `CITY_MUN`
  - Added `NSAP` column

#### Summary Statistics
- Enhanced summary display with side-by-side tables
- Added alphabetical sorting for regions (BARMM at bottom)
- Added numerical sorting for FMAs
- Plain text display (removed badges from tables)

### Improved

#### FMA Municipalities
- Advanced filtering with dependent province selection
- Pagination system for large datasets
- Summary statistics with real-time updates
- Better mobile responsiveness

#### Documentation
- Updated README.md with new features
- Updated API.md with new functions
- Updated DEVELOPER_GUIDE.md with new development patterns
- Created USER_GUIDE.md for end users
- Created FEATURES.md for comprehensive feature documentation
- Created CHANGELOG.md for version tracking

#### About Page
- Enhanced documentation of features
- Added information about FMA Municipalities and Landing Centers
- Updated version information
- Added tips for best experience

### Technical

#### Dependencies
- Added Leaflet.js for map functionality
- Updated data-service.js for new data sources
- Enhanced app.js with new page loaders

#### Performance
- Optimized filtering algorithms
- Improved pagination rendering
- Enhanced map marker clustering

## [1.0] - 2024-12-XX

### Added

#### Initial Release
- Dashboard (Home Page) with quick statistics
- Implementation Structure page
- FMA Profile page
- Municipalities page (basic)
- Activities timeline page
- Directory page (Internal/External/NPMO)
- References page
- Search functionality
- Learn More page
- About page

#### Core Features
- Single Page Application (SPA) architecture
- Google Sheets API integration
- Responsive design
- Global search
- CSV export for directory
- Filtering capabilities
- Pagination for references

#### UI/UX
- Glassmorphism design
- Smooth animations
- Bootstrap 5.3.3 framework
- Bootstrap Icons
- Custom color scheme
- Loading states
- Error handling

#### Responsive Design
- Mobile-optimized tables with horizontal scrolling
- Mobile-optimized activity cards
- Mobile-optimized reference cards
- Responsive filter layouts
- Touch-friendly interactions

### Technical

#### Architecture
- Client-side routing
- Google Sheets as backend
- Client-side caching
- Local storage for state
- Error recovery mechanisms

#### Data Sources
- `Internal_Directory` sheet
- `External_Directory` sheet
- `NPMO_Directory` sheet
- `Activities_Conducted` sheet
- `FMA_6_&_9_Municipalities` sheet
- `Reference_Files` sheet
- `Implementation_Structure` sheet
- `FMA_Profile` sheet

---

## Version History Summary

### Version 1.1 (January 2025)
- Major feature additions: FMA Municipalities and Landing Centers Map
- Enhanced filtering and pagination
- Improved summary statistics
- Updated navigation structure
- Comprehensive documentation updates

### Version 1.0 (December 2024)
- Initial release
- Core functionality
- Basic responsive design
- Google Sheets integration

---

## Migration Notes

### Upgrading from Version 1.0 to 1.1

1. **Update Google Sheets**:
   - Rename `FMA_6_&_9_Municipalities` sheet to `FMA_Municipalities`
   - Update column names: `FMA_ID` → `FMA`, `MUNICIPALITY` → `CITY_MUN`
   - Add `NSAP` column if not present
   - Create new `Landing_Centers` sheet with required columns

2. **Update Configuration**:
   - No changes needed to `config.js`
   - Ensure API key has proper permissions

3. **Navigation Updates**:
   - Old "Municipalities" link replaced with "FMA Municipalities"
   - New "Landing Centers" link added

4. **Data Migration**:
   - Migrate data from old municipalities sheet to new format
   - Add landing centers data with coordinates

---

**Note**: This changelog follows semantic versioning. Major version changes indicate breaking changes, minor versions indicate new features, and patch versions indicate bug fixes.
