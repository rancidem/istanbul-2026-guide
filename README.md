# Istanbul 2026 Travel Guide

A personal travel reference guide for Istanbul with a retro Windows 3.1 aesthetic.

![Win31 Aesthetic](assets/images/win31-preview.png)

## Features

- **11 HTML Pages** - Complete site with attractions, neighborhoods, food, transport, history, tips, and more
- **5 Neighborhood Guides** - Detailed area guides for Sultanahmet, Beyoğlu, Karaköy, Galata, and Kadıköy
- **60+ Places Index** - Comprehensive listing of monuments, museums, markets, restaurants with Google Maps links
- **Interactive Packing List** - Dashboard-style packing list with progress bar and localStorage persistence
- **Print-Friendly** - Optimized styles for printing packing lists and guides
- **Responsive Design** - Works on desktop and mobile devices
- **Win31 Aesthetic** - Authentic 90s computing vibe with beveled borders, navy titlebars, and bracket notation

## Quick Start

Open `index.html` in any modern web browser:

```bash
# macOS
open index.html

# Linux
xdg-open index.html

# Or use a local server
python3 -m http.server 8000
# Then visit http://localhost:8000
```

## Site Structure

```
istanbul-site-enhanced/
├── index.html              # Home page with overview
├── css/
│   └── styles.css          # Win31 aesthetic styles
├── pages/
│   ├── attractions.html    # Top 10 attractions
│   ├── food.html           # Food & drink guide
│   ├── history.html        # Historical timeline
│   ├── map.html            # Interactive map
│   ├── neighborhoods.html  # Neighborhood overview
│   ├── packing.html        # Interactive packing list
│   ├── personal-picks.html # Curated recommendations
│   ├── places.html         # Complete places index
│   ├── tips.html           # Practical tips
│   ├── transport.html      # Getting around
│   └── neighborhoods/      # Individual neighborhood guides
│       ├── beyoglu.html
│       ├── galata.html
│       ├── kadikoy.html
│       ├── karakoy.html
│       └── sultanahmet.html
├── assets/
│   └── images/             # 14 destination photos
└── vendor/
    ├── leaflet.css         # Map library
    └── leaflet.js
```

## Key Pages

| Page | Description |
|------|-------------|
| **index.html** | Home with trip overview and quick links |
| **attractions.html** | Top 10 must-see attractions |
| **neighborhoods.html** | Area guide with links to detailed pages |
| **food.html** | Where and what to eat |
| **places.html** | Complete index of 60+ locations with maps |
| **packing.html** | Interactive packing checklist with progress tracking |
| **transport.html** | Getting to/from and around Istanbul |
| **tips.html** | Money, etiquette, safety, practical advice |

## Packing List Features

The packing page includes dashboard-style features:

- **Progress Bar** - Visual indicator of packing completion
- **localStorage Persistence** - Checklist state saved between sessions
- **Print Styles** - Optimized layout for printing
- **Two-Column Layout** - Weather forecast + packing list
- **Jump Links** - Quick navigation to sections

## Design System

### Win31 Aesthetic

- **Colors**: Navy (`#000080`), gray (`#c0c0c0`), white (`#ffffff`)
- **Borders**: Beveled 3D effect with light/dark edges
- **Typography**: System fonts, 11px base size
- **Notation**: Brackets instead of emojis (e.g., `[LIKE]` not `👍`)

### CSS Variables

```css
--win-bg: #c0c0c0      /* Window background */
--win-nav: #000080     /* Titlebar/navigation */
--win-dark: #808080    /* Shadow edges */
--win-light: #ffffff   /* Highlight edges */
```

## Cross-Linking

All pages are cross-linked for easy navigation:

- Neighborhood pages → Places index
- Food page → Places index
- Places index → Google Maps
- All pages → Navigation sidebar

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Android)

## Print Support

Optimized print styles for:
- Packing lists
- Day itineraries
- Place reference sheets

Print-optimized pages hide navigation and use full width.

## License

Personal travel guide. Content based on research and personal recommendations.

## Version History

- **v1.0** (2026-02-18) - Initial release with complete site
