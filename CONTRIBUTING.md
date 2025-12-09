# Contributing to FishCRRM 1.1 Knowledge Base

Thank you for your interest in contributing to the FishCRRM 1.1 Knowledge Base! This document provides guidelines and instructions for contributing.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Making Changes](#making-changes)
- [Coding Standards](#coding-standards)
- [Testing](#testing)
- [Submitting Changes](#submitting-changes)
- [Documentation](#documentation)
- [Issue Reporting](#issue-reporting)

## 🤝 Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Focus on what is best for the project
- Show empathy towards other contributors

## 🚀 Getting Started

### Prerequisites

- Basic knowledge of HTML, CSS, and JavaScript
- Familiarity with Google Sheets API
- Understanding of Single Page Applications (SPA)
- Git version control

### Development Environment

1. **Fork the Repository**
   ```bash
   # Fork on GitHub, then clone
   git clone https://github.com/YOUR_USERNAME/FISHCRRM-Knowledge-Base.git
   cd FISHCRRM-Knowledge-Base
   ```

2. **Set Up Configuration**
   - Copy `config.js.example` to `config.js` (if available)
   - Update with your Spreadsheet ID and API Key
   - Keep `config.js` out of version control

3. **Local Testing**
   - Use a local web server (e.g., Python's `http.server` or Node's `http-server`)
   - Test all features before submitting

## 💻 Development Setup

### Project Structure

```
FishCRRM-Knowledge-Base/
├── index.html              # Main entry point
├── config.js              # Configuration (not in repo)
├── data-service.js        # Data fetching service
├── app.js                 # Main application logic
├── *.html                 # Page templates
├── styles.html            # CSS styles
└── docs/                  # Documentation files
```

### Local Development Server

**Option 1: Python**
```bash
python -m http.server 8000
# Access at http://localhost:8000
```

**Option 2: Node.js**
```bash
npx http-server -p 8000
# Access at http://localhost:8000
```

**Option 3: VS Code Live Server**
- Install "Live Server" extension
- Right-click `index.html` → "Open with Live Server"

## ✏️ Making Changes

### Branch Naming

Use descriptive branch names:
- `feature/fma-municipalities-filter`
- `bugfix/search-error`
- `docs/update-readme`
- `refactor/data-service`

### Commit Messages

Follow conventional commit format:
```
type(scope): description

[optional body]

[optional footer]
```

**Types**:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting)
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance tasks

**Examples**:
```
feat(fma-municipalities): add pagination support

fix(search): resolve case-insensitive matching issue

docs(readme): update installation instructions
```

## 📝 Coding Standards

### JavaScript

**Naming Conventions**:
```javascript
// Functions: camelCase
function loadFMAMunicipalities() { }

// Constants: UPPER_SNAKE_CASE
const CACHE_TTL = 300;

// Variables: camelCase
let currentPage = 'home';

// Classes: PascalCase
class DataService { }
```

**Code Style**:
- Use ES6+ features (arrow functions, const/let, template literals)
- Use async/await for asynchronous operations
- Add comments for complex logic
- Keep functions focused and single-purpose

**Example**:
```javascript
// Good
async function loadData() {
  try {
    const data = await dataService.getData();
    renderData(data);
  } catch (err) {
    console.error('Error loading data:', err);
    showError('Failed to load data');
  }
}

// Avoid
function loadData() {
  dataService.getData().then(data => {
    renderData(data);
  }).catch(err => {
    console.error(err);
  });
}
```

### HTML

**Structure**:
- Use semantic HTML5 elements
- Include proper ARIA labels
- Maintain consistent indentation (2 spaces)
- Add comments for complex sections

**Example**:
```html
<!-- Good -->
<section class="municipalities-section">
  <h2>FMA Municipalities</h2>
  <div id="municipalities-table-container" role="region" aria-label="Municipalities table">
    <!-- Table content -->
  </div>
</section>

<!-- Avoid -->
<div>
  <div>
    <div>FMA Municipalities</div>
  </div>
</div>
```

### CSS

**Organization**:
- Use consistent spacing (Bootstrap utilities when possible)
- Group related styles
- Use CSS variables for colors
- Follow mobile-first approach

**Example**:
```css
/* Good */
.municipalities-table {
  width: 100%;
  border-collapse: collapse;
}

@media (max-width: 991.98px) {
  .municipalities-table {
    min-width: 800px;
  }
}

/* Avoid */
.municipalities-table { width: 100%; border-collapse: collapse; }
@media (max-width: 991.98px) { .municipalities-table { min-width: 800px; } }
```

## 🧪 Testing

### Manual Testing Checklist

Before submitting changes, test:

- [ ] All pages load correctly
- [ ] Navigation works (navbar, quick links, browser back/forward)
- [ ] Filters work on all pages
- [ ] Search functionality works
- [ ] Data displays correctly
- [ ] Responsive design works (mobile, tablet, desktop)
- [ ] No console errors
- [ ] No broken links
- [ ] Export functions work (if applicable)

### Browser Testing

Test in multiple browsers:
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)

### Device Testing

Test on different devices:
- [ ] Desktop (1920x1080)
- [ ] Tablet (768x1024)
- [ ] Mobile (375x667)

## 📤 Submitting Changes

### Pull Request Process

1. **Update Your Branch**:
   ```bash
   git checkout main
   git pull origin main
   git checkout your-branch
   git rebase main
   ```

2. **Create Pull Request**:
   - Push your branch to GitHub
   - Create pull request with:
     - Clear title
     - Description of changes
     - Screenshots (if UI changes)
     - Reference to related issues

3. **Pull Request Template**:
   ```markdown
   ## Description
   Brief description of changes

   ## Type of Change
   - [ ] Bug fix
   - [ ] New feature
   - [ ] Documentation update
   - [ ] Code refactoring

   ## Testing
   - [ ] Tested on desktop
   - [ ] Tested on mobile
   - [ ] Tested in multiple browsers
   - [ ] No console errors

   ## Screenshots (if applicable)
   [Add screenshots here]

   ## Related Issues
   Fixes #123
   ```

### Review Process

- Maintainers will review your PR
- Address any feedback or requested changes
- Ensure all tests pass
- Update documentation if needed

## 📚 Documentation

### Updating Documentation

When adding features, update:

1. **README.md**: Add feature to features list
2. **USER_GUIDE.md**: Add usage instructions
3. **FEATURES.md**: Add detailed feature description
4. **API.md**: Add new functions (if applicable)
5. **CHANGELOG.md**: Add entry under "Unreleased"

### Documentation Style

- Use clear, concise language
- Include code examples
- Add screenshots for UI changes
- Keep formatting consistent

## 🐛 Issue Reporting

### Before Reporting

1. Check existing issues
2. Verify it's a bug (not a feature request)
3. Test in multiple browsers
4. Check browser console for errors

### Bug Report Template

```markdown
**Description**
Clear description of the bug

**Steps to Reproduce**
1. Go to '...'
2. Click on '...'
3. See error

**Expected Behavior**
What should happen

**Actual Behavior**
What actually happens

**Screenshots**
If applicable

**Environment**
- Browser: [e.g., Chrome 120]
- OS: [e.g., Windows 11]
- Device: [e.g., Desktop]

**Console Errors**
Any errors from browser console
```

### Feature Request Template

```markdown
**Feature Description**
Clear description of the feature

**Use Case**
Why is this feature needed?

**Proposed Solution**
How should it work?

**Alternatives Considered**
Other approaches you've thought about

**Additional Context**
Any other relevant information
```

## 🎯 Areas for Contribution

### High Priority

- Bug fixes
- Performance improvements
- Accessibility enhancements
- Mobile optimization
- Documentation improvements

### Feature Ideas

- Advanced analytics
- Data visualization charts
- Export enhancements
- User preferences
- Offline capabilities

### Code Quality

- Code refactoring
- Test coverage
- Error handling improvements
- Performance optimization
- Security enhancements

## 📞 Getting Help

### Resources

- **Documentation**: See README.md and other .md files
- **Issues**: Check existing GitHub issues
- **Discussions**: Use GitHub Discussions (if enabled)

### Contact

For questions or clarifications:
- Open a GitHub issue
- Contact the maintainer (see About page)

## ✅ Checklist for Contributors

Before submitting:

- [ ] Code follows style guidelines
- [ ] All tests pass
- [ ] Documentation updated
- [ ] No console errors
- [ ] Responsive design tested
- [ ] Cross-browser tested
- [ ] Commit messages follow convention
- [ ] Pull request description complete

---

Thank you for contributing to the FishCRRM 1.1 Knowledge Base! 🎉

**Last Updated**: January 2025
