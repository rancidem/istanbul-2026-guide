# Contributing to Istanbul 2026 Guide

## Publishing a Release

### Prerequisites

- Git installed and configured
- GitHub CLI (`gh`) installed and authenticated
- Write access to the repository

### Release Process

#### 1. Prepare the Release

```bash
# Ensure you're on main branch with latest changes
git checkout main
git pull origin main

# Run validation checks
./scripts/validate.sh
```

#### 2. Version Bump

Update version references in:
- `README.md` - version badge
- `package.json` - if applicable
- Any version strings in HTML comments

#### 3. Create Release Package

```bash
# Create clean release folder
mkdir -p releases/istanbul-2026-guide-v{VERSION}
cp -r index.html css/ pages/ assets/ vendor/ releases/istanbul-2026-guide-v{VERSION}/

# Remove development files
rm -f releases/istanbul-2026-guide-v{VERSION}/README.txt
rm -f releases/istanbul-2026-guide-v{VERSION}/.DS_Store

# Create zip archive
cd releases
zip -r istanbul-2026-guide-v{VERSION}.zip istanbul-2026-guide-v{VERSION}/
```

#### 4. Tag and Release on GitHub

```bash
# Create annotated tag
git tag -a v{VERSION} -m "Istanbul 2026 Travel Guide v{VERSION}"

# Push tag
git push origin v{VERSION}

# Create GitHub release with assets
gh release create v{VERSION} \
  --title "Istanbul 2026 Travel Guide v{VERSION}" \
  --notes-file release-notes.md \
  releases/istanbul-2026-guide-v{VERSION}.zip
```

#### 5. Update GitHub Pages

GitHub Pages auto-deploys from `main` branch. Verify at:
https://rancidem.github.io/istanbul-2026-guide/

### Release Checklist

- [ ] All HTML files validated
- [ ] All images optimized
- [ ] No broken links
- [ ] README.md updated
- [ ] Version bumped
- [ ] Tag created
- [ ] Release published
- [ ] GitHub Pages updated

---

## Working on Design

### Design System Overview

The site uses a **Windows 3.1 aesthetic** with:

- **Colors**: Navy (`#000080`), gray (`#c0c0c0`), white (`#ffffff`)
- **Borders**: Beveled 3D effect with light/dark edges
- **Typography**: System fonts, 11px base size
- **Notation**: Brackets instead of emojis (e.g., `[LIKE]`)

### CSS Architecture

```
css/styles.css
├── CSS Variables (Win31 palette)
├── Layout Components
│   ├── .container
│   ├── .main-grid
│   └── .sidebar
├── Box Components
│   ├── .box-raised
│   └── .box-sunken
├── Navigation
│   ├── .titlebar
│   └── .nav-link
└── Utilities
    ├── .page-img
    └── .meter (progress bar)
```

### Making Design Changes

#### 1. Local Development

```bash
# Serve locally for testing
python3 -m http.server 8000
# Visit http://localhost:8000
```

#### 2. Edit Styles

```bash
# Main stylesheet
css/styles.css

# Page-specific styles (inline in HTML)
pages/example.html → <style> section
```

#### 3. Test Changes

Check across:
- **Desktop**: Chrome, Firefox, Safari
- **Mobile**: iOS Safari, Chrome Android
- **Print**: Print preview for packing list

#### 4. Visual Regression

```bash
# Capture screenshots for comparison
./scripts/screenshot.sh

# Compare with baseline
diff baseline/ current/
```

### Design Patterns

#### Adding a New Component

```css
/* 1. Use CSS variables */
.my-component {
  background: var(--win-bg);
  border-top: 2px solid var(--win-light);
  border-left: 2px solid var(--win-light);
  border-bottom: 2px solid var(--win-dark);
  border-right: 2px solid var(--win-dark);
}

/* 2. Maintain 11px base font */
.my-component {
  font-size: 11px;
}

/* 3. Use bracket notation for icons */
/* [TIP] not 💡 */
```

#### Color Reference

| Purpose | Color | Hex |
|---------|-------|-----|
| Titlebars | Navy | `#000080` |
| Background | Gray | `#c0c0c0` |
| Highlights | White | `#ffffff` |
| Shadows | Dark Gray | `#808080` |
| Success | Green | `#008000` |
| Warning | Orange | `#ff6600` |
| Error | Red | `#ff0000` |
| Info | Blue | `#000080` |

#### Common Markers

```html
<!-- Navigation -->
<span style="color:#ffd700;">[H]</span> Home
<span style="color:#ff6600;">[P]</span> Picks
<span style="color:#008000;">[PK]</span> Pack

<!-- Section Headers -->
<span style="color:#800000;font-weight:bold;">[MON]</span> Monuments
<span style="color:#800000;font-weight:bold;">[EAT]</span> Where to Eat
<span style="color:#000080;font-weight:bold;">[TRN]</span> Transport

<!-- Priority Markers -->
<span style="color:#ff0000;font-weight:bold;">[***]</span> Essential
<span style="color:#ff6600;font-weight:bold;">[**]</span> Recommended
<span style="color:#ff9900;font-weight:bold;">[*]</span> Worthwhile
```

### Adding a New Page

1. **Create HTML file** in `pages/`
2. **Copy base structure** from existing page
3. **Add navigation links** to all pages
4. **Update sidebar** with new page link
5. **Test cross-links** work correctly

### Responsive Design

The site uses a simple responsive approach:

```css
/* Desktop: Two-column layout */
.main-grid {
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 8px;
}

/* Mobile: Single column */
@media (max-width: 700px) {
  .main-grid {
    grid-template-columns: 1fr;
  }
  .sidebar { display: none; }
}
```

### Print Styles

For print-friendly pages (like packing list):

```css
@media print {
  .titlebar, .sidebar { display: none; }
  body { background: #fff; }
  .container { max-width: 100%; }
}
```

---

## Testing

### Manual Testing Checklist

- [ ] All navigation links work
- [ ] Images load correctly
- [ ] Map displays (if applicable)
- [ ] Packing list progress bar updates
- [ ] localStorage persistence works
- [ ] Print preview looks correct
- [ ] Mobile layout is usable

### Automated Validation

```bash
# Run all checks
npm run validate

# Check HTML validity
npm run validate:html

# Check links
npm run validate:links

# Check accessibility
npm run validate:a11y
```

---

## Questions?

Open an issue at: https://github.com/rancidem/istanbul-2026-guide/issues
