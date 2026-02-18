# Development Quick Reference

## Common Tasks

### Add a New Restaurant to Places Index

1. Open `pages/places.html`
2. Find the "Food & Drink" section
3. Add a new table row following the pattern:

```html
<tr style="background:#e8e8e8;">
  <td>
    <b>Restaurant Name</b>
    <a href="https://maps.google.com/?q=Restaurant+Name,Istanbul" style="color:#000080;font-size:9px;" target="_blank">[map]</a>
  </td>
  <td>Neighborhood</td>
  <td style="color:#444;">Brief description.</td>
  <td style="font-size:10px;color:#555;">Pro tip goes here</td>
</tr>
```

4. Alternate row colors: use `background:#e8e8e8;` for every other row
5. Add priority marker if recommended: `<span style="color:#ff9900;font-weight:bold;">[*]</span>`

### Update Pricing Information

1. Find the attraction in relevant HTML files
2. Update price in:
   - `pages/attractions.html` - main listing
   - `pages/neighborhoods/[area].html` - neighborhood guide
   - `pages/places.html` - places index
3. Use format: `XXX TL (~€XX)` or just `€XX` for major attractions

### Fix a Broken Link

```bash
# Find all occurrences
grep -r "old-link" pages/

# Replace with new link
sed -i 's/old-link/new-link/g' pages/*.html
```

### Add a New Neighborhood Guide

1. Create `pages/neighborhoods/newarea.html`
2. Copy structure from existing guide (e.g., `karakoy.html`)
3. Update content following the template sections
4. Add to `pages/neighborhoods.html` sidebar
5. Add to all page sidebars
6. Update `index.html` with quick link

### Update the Packing List

1. Open `pages/packing.html`
2. Find the relevant section (carry-on, checked, etc.)
3. Add checkbox item:

```html
<li><label><input type="checkbox"> Item description</label></li>
```

4. The progress bar updates automatically via JavaScript

---

## File Organization

```
index.html              # Home page - start here
├── pages/
│   ├── attractions.html    # Top 10 sights
│   ├── food.html           # Food & drink guide
│   ├── history.html        # Historical timeline
│   ├── map.html            # Interactive map
│   ├── neighborhoods.html  # Area overview
│   ├── packing.html        # Interactive checklist
│   ├── personal-picks.html # Curated recommendations
│   ├── places.html         # 60+ places index
│   ├── tips.html           # Practical tips
│   ├── transport.html      # Getting around
│   └── neighborhoods/      # Detailed area guides
│       ├── beyoglu.html
│       ├── galata.html
│       ├── kadikoy.html
│       ├── karakoy.html
│       └── sultanahmet.html
├── css/
│   └── styles.css          # Win31 aesthetic styles
├── assets/
│   └── images/             # 14 destination photos
└── vendor/
    ├── leaflet.css         # Map library
    └── leaflet.js
```

---

## Design Tokens

### Colors

```css
--win-bg: #c0c0c0      /* Window background */
--win-nav: #000080     /* Titlebar/navigation */
--win-dark: #808080    /* Shadow edges */
--win-light: #ffffff   /* Highlight edges */
```

### Typography

```css
font-family: system-ui, -apple-system, sans-serif;
font-size: 11px;        /* Base size */
line-height: 1.4;
```

### Spacing

```css
/* Standard spacing scale */
4px   - Tight (internal padding)
8px   - Default gap
12px  - Section padding
16px  - Large gap
```

---

## Testing Checklist

Before committing changes:

- [ ] HTML validates (no unclosed tags)
- [ ] All images load
- [ ] Navigation works from all pages
- [ ] Mobile layout acceptable
- [ ] Print styles work (for packing list)
- [ ] No broken internal links
- [ ] Google Maps links open correctly

---

## Git Workflow

```bash
# Start new work
git checkout -b feature/description

# Make changes
# ... edit files ...

# Test locally
python3 -m http.server 8000

# Commit
git add -A
git commit -m "Description of changes"

# Push
git push origin feature/description

# Create PR via GitHub CLI
gh pr create --title "Description" --body "Details"
```

---

## Emergency Fixes

### Site Won't Load

1. Check `index.html` exists in root
2. Verify `css/styles.css` exists
3. Check browser console for 404s

### Images Not Showing

1. Verify image in `assets/images/`
2. Check filename matches reference
3. Check file extension (.jpg vs .jpeg)

### Packing List Not Saving

1. Check browser localStorage is enabled
2. Verify JavaScript console for errors
3. Test in incognito/private mode

---

## Resources

- **Live Site**: https://rancidem.github.io/istanbul-2026-guide/
- **Repository**: https://github.com/rancidem/istanbul-2026-guide
- **Issues**: https://github.com/rancidem/istanbul-2026-guide/issues
