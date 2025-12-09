# Deployment Guide - FishCRRM 1.1 Knowledge Base

Complete guide for deploying the FishCRRM 1.1 Knowledge Base to production.

## 📋 Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Pre-Deployment Checklist](#pre-deployment-checklist)
- [Deployment Options](#deployment-options)
- [Post-Deployment](#post-deployment)
- [Monitoring](#monitoring)
- [Troubleshooting](#troubleshooting)

## 🎯 Overview

The FishCRRM 1.1 Knowledge Base can be deployed to various hosting platforms. This guide covers the most common deployment scenarios.

**Recommended**: GitHub Pages (free, easy, automatic)

## ✅ Prerequisites

Before deployment, ensure you have:

1. **Google Sheets Setup**:
   - [ ] Google Sheet created with all required sheets
   - [ ] Sheet is publicly accessible (View permission)
   - [ ] All data populated and tested
   - [ ] Column headers match exactly (case-sensitive)

2. **Google Cloud Console Setup**:
   - [ ] Google Cloud project created
   - [ ] Google Sheets API enabled
   - [ ] API key created
   - [ ] API key restricted to Google Sheets API only
   - [ ] HTTP referrer restrictions configured (if using GitHub Pages)

3. **Code Preparation**:
   - [ ] All files committed to version control
   - [ ] `config.js` prepared (with placeholders or separate config)
   - [ ] No sensitive data in code
   - [ ] All features tested locally

## ✅ Pre-Deployment Checklist

### Code Quality
- [ ] No console errors
- [ ] All pages load correctly
- [ ] All features work as expected
- [ ] Responsive design tested
- [ ] Cross-browser tested
- [ ] Performance acceptable

### Configuration
- [ ] `config.js` has correct Spreadsheet ID
- [ ] `config.js` has valid API key
- [ ] API key has proper restrictions
- [ ] Sheet permissions set correctly

### Documentation
- [ ] README.md updated
- [ ] Version number updated
- [ ] Changelog updated
- [ ] About page updated

### Testing
- [ ] All filters work
- [ ] Search works
- [ ] Export works
- [ ] Map loads correctly
- [ ] Data displays correctly
- [ ] Navigation works
- [ ] Mobile responsive

## 🚀 Deployment Options

### Option 1: GitHub Pages (Recommended)

**Best for**: Public projects, free hosting, automatic deployment

**Steps**:

1. **Create GitHub Repository**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/USERNAME/REPO.git
   git push -u origin main
   ```

2. **Configure Repository**:
   - Go to Settings → Pages
   - Source: Deploy from branch
   - Branch: `main` (or `master`)
   - Folder: `/ (root)`
   - Click Save

3. **Update API Key Restrictions**:
   - Go to Google Cloud Console
   - Edit API key
   - Add HTTP referrer: `https://USERNAME.github.io/*`
   - Save

4. **Verify Deployment**:
   - Visit `https://USERNAME.github.io/REPO/`
   - Test all features
   - Check browser console for errors

**Pros**:
- Free hosting
- Automatic deployment on push
- HTTPS by default
- Custom domain support

**Cons**:
- Public repository (unless using GitHub Pro)
- API key visible in code

**See**: [GITHUB_PAGES_SETUP.md](GITHUB_PAGES_SETUP.md) for detailed instructions

### Option 2: Netlify

**Best for**: Easy deployment, custom domains, form handling

**Steps**:

1. **Prepare Repository**:
   - Push code to GitHub/GitLab/Bitbucket

2. **Deploy to Netlify**:
   - Go to [netlify.com](https://netlify.com)
   - Click "New site from Git"
   - Connect repository
   - Build settings:
     - Build command: (leave empty)
     - Publish directory: `/`
   - Click "Deploy site"

3. **Configure Environment Variables** (Optional):
   - Go to Site settings → Environment variables
   - Add `SPREADSHEET_ID` and `API_KEY`
   - Update `config.js` to use `process.env` (requires build step)

4. **Update API Key Restrictions**:
   - Add Netlify domain to HTTP referrer restrictions

**Pros**:
- Free tier available
- Automatic deployments
- Custom domains
- Environment variables

**Cons**:
- Requires Git repository
- API key still visible in client code

### Option 3: Vercel

**Best for**: Next.js projects, serverless functions

**Steps**:

1. **Install Vercel CLI**:
   ```bash
   npm i -g vercel
   ```

2. **Deploy**:
   ```bash
   vercel
   ```

3. **Follow prompts**:
   - Link to existing project or create new
   - Configure settings
   - Deploy

**Pros**:
- Free tier
- Fast CDN
- Automatic deployments
- Serverless functions support

**Cons**:
- Requires Node.js knowledge for advanced features
- API key visible in client code

### Option 4: Traditional Web Hosting

**Best for**: Existing hosting, custom requirements

**Steps**:

1. **Upload Files**:
   - Use FTP/SFTP to upload all files
   - Maintain directory structure
   - Ensure `index.html` is in root

2. **Configure Server**:
   - Ensure server supports static files
   - Configure MIME types for `.html` files
   - Set up HTTPS (recommended)

3. **Update Configuration**:
   - Update `config.js` on server
   - Update API key restrictions with domain

**Pros**:
- Full control
- Custom server configuration
- Private hosting possible

**Cons**:
- Requires server management
- Manual updates
- May require paid hosting

## 🔒 Security Considerations

### API Key Security

**Important**: API keys are visible in client-side code. Mitigate risks:

1. **Restrict API Key**:
   - Limit to Google Sheets API only
   - Add HTTP referrer restrictions
   - Set usage quotas

2. **Monitor Usage**:
   - Check Google Cloud Console regularly
   - Set up alerts for unusual activity
   - Review API usage reports

3. **Rotate Keys**:
   - Change API keys periodically
   - Update in `config.js`
   - Update restrictions

### Data Security

1. **Sheet Permissions**:
   - Use "Viewer" permission for public sheets
   - Don't include sensitive data
   - Review data before making public

2. **HTTPS**:
   - Always use HTTPS in production
   - GitHub Pages provides HTTPS automatically
   - Configure SSL for custom domains

## 📊 Post-Deployment

### Verification Steps

1. **Functional Testing**:
   - [ ] All pages load
   - [ ] Navigation works
   - [ ] Data displays correctly
   - [ ] Filters work
   - [ ] Search works
   - [ ] Export works
   - [ ] Map loads

2. **Performance Testing**:
   - [ ] Page load time acceptable
   - [ ] Data loads quickly
   - [ ] No console errors
   - [ ] Mobile performance good

3. **Cross-Browser Testing**:
   - [ ] Chrome
   - [ ] Firefox
   - [ ] Safari
   - [ ] Edge

4. **Device Testing**:
   - [ ] Desktop
   - [ ] Tablet
   - [ ] Mobile

### Update Documentation

- [ ] Update README with production URL
- [ ] Update About page with version info
- [ ] Document any deployment-specific notes

## 📈 Monitoring

### Key Metrics to Monitor

1. **Performance**:
   - Page load times
   - API response times
   - Error rates

2. **Usage**:
   - Page views
   - User interactions
   - Feature usage

3. **Errors**:
   - JavaScript errors (browser console)
   - API errors (Google Cloud Console)
   - 404 errors

### Monitoring Tools

1. **Google Analytics** (Optional):
   - Add tracking code
   - Monitor user behavior
   - Track page views

2. **Google Cloud Console**:
   - Monitor API usage
   - Check quota limits
   - Review error logs

3. **Browser Console**:
   - Check for client-side errors
   - Monitor network requests
   - Verify data loading

## 🐛 Troubleshooting

### Common Deployment Issues

#### Issue: 404 Errors on Navigation

**Symptoms**: Pages return 404 when navigating

**Solutions**:
1. Verify all HTML files are in root directory
2. Check file names match ROUTES in app.js
3. Ensure server supports hash-based routing
4. For GitHub Pages, verify Pages is enabled

#### Issue: API Key Errors

**Symptoms**: "API key not valid" or CORS errors

**Solutions**:
1. Verify API key in config.js
2. Check API key restrictions
3. Ensure Google Sheets API is enabled
4. Verify HTTP referrer restrictions include your domain

#### Issue: Data Not Loading

**Symptoms**: Empty tables or "No data available"

**Solutions**:
1. Verify sheet is publicly accessible
2. Check sheet names match exactly
3. Verify column headers are correct
4. Check browser console for errors
5. Verify Spreadsheet ID is correct

#### Issue: Map Not Loading

**Symptoms**: Blank map or "Loading..." persists

**Solutions**:
1. Check Leaflet.js is loaded
2. Verify coordinates exist in data
3. Check browser console for errors
4. Verify internet connection
5. Check if pop-up blockers interfere

### Debugging Steps

1. **Check Browser Console**:
   - Open DevTools (F12)
   - Check Console tab for errors
   - Check Network tab for failed requests

2. **Verify Configuration**:
   - Check config.js values
   - Verify API key is valid
   - Confirm Spreadsheet ID is correct

3. **Test API Directly**:
   ```javascript
   // In browser console
   fetch(`https://sheets.googleapis.com/v4/spreadsheets/YOUR_ID/values/Sheet1?key=YOUR_KEY`)
     .then(r => r.json())
     .then(console.log)
   ```

4. **Check Server Logs**:
   - Review hosting platform logs
   - Check for server errors
   - Verify file permissions

## 🔄 Updates and Maintenance

### Updating the Application

1. **Make Changes Locally**:
   - Test thoroughly
   - Update version number
   - Update changelog

2. **Deploy Updates**:
   - Push to repository (GitHub Pages)
   - Or upload files (traditional hosting)
   - Verify deployment

3. **Post-Update Verification**:
   - Test all features
   - Check for errors
   - Monitor performance

### Regular Maintenance

1. **Weekly**:
   - Check for errors in console
   - Review API usage
   - Verify data is current

2. **Monthly**:
   - Review performance metrics
   - Update documentation if needed
   - Check for security updates

3. **Quarterly**:
   - Review and rotate API keys
   - Update dependencies
   - Performance optimization

## 📞 Support

For deployment issues:

1. Check this guide
2. Review [Troubleshooting](#troubleshooting) section
3. Check browser console for errors
4. Review hosting platform documentation
5. Contact developer (see About page)

## 📚 Related Documentation

- [GitHub Pages Setup](GITHUB_PAGES_SETUP.md) - Detailed GitHub Pages guide
- [Configuration Guide](README.md#configuration) - Configuration details
- [Troubleshooting](README.md#troubleshooting) - General troubleshooting
- [User Guide](USER_GUIDE.md) - End user documentation

---

**Last Updated**: January 2025  
**Version**: 1.1
