# Win31 Component Toolkit

Ready-to-use CSS components for the Istanbul 2026 Guide.

## Status Bar

```html
<!-- Add before closing body tag -->
<div class="status-bar">
  <span id="status-text">Ready</span>
  <span id="status-info">Istanbul 2026 Guide</span>
</div>
```

```css
.status-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 20px;
  background: var(--win-bg);
  border-top: 2px solid var(--win-light);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 8px;
  font-size: 11px;
  z-index: 100;
}

/* Add padding to body to prevent content overlap */
body {
  padding-bottom: 24px;
}
```

## Custom Scrollbars

```css
/* Webkit browsers */
::-webkit-scrollbar {
  width: 16px;
  height: 16px;
  background: var(--win-bg);
}

::-webkit-scrollbar-thumb {
  background: var(--win-bg);
  border: 2px solid;
  border-color: var(--win-light) var(--win-dark) var(--win-dark) var(--win-light);
}

::-webkit-scrollbar-button {
  background: var(--win-bg);
  border: 2px solid;
  border-color: var(--win-light) var(--win-dark) var(--win-dark) var(--win-light);
  height: 16px;
}

::-webkit-scrollbar-corner {
  background: var(--win-bg);
}

/* Firefox */
* {
  scrollbar-width: 16px;
  scrollbar-color: var(--win-bg) var(--win-bg);
}
```

## Tooltip ("What's This?")

```html
<button title="Click to print this page">Print</button>
<span class="tooltip" data-tip="Opens in new window">Link</span>
```

```css
.tooltip {
  position: relative;
  cursor: help;
}

.tooltip:hover::after {
  content: attr(data-tip);
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  background: #ffffcc;
  border: 1px solid #000;
  padding: 2px 6px;
  font-size: 10px;
  white-space: nowrap;
  z-index: 1000;
  box-shadow: 2px 2px 0 rgba(0,0,0,0.2);
}
```

## Dialog/Modal

```html
<div class="dialog-overlay" id="dialog">
  <div class="dialog-box">
    <div class="dialog-titlebar">
      <span>Confirm</span>
      <button class="dialog-close">×</button>
    </div>
    <div class="dialog-content">
      <p>Are you sure you want to proceed?</p>
    </div>
    <div class="dialog-buttons">
      <button class="btn-primary">OK</button>
      <button class="btn-secondary">Cancel</button>
    </div>
  </div>
</div>
```

```css
.dialog-overlay {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
  align-items: center;
  justify-content: center;
}

.dialog-overlay.active {
  display: flex;
}

.dialog-box {
  background: var(--win-bg);
  border: 2px solid;
  border-color: var(--win-light) var(--win-dark) var(--win-dark) var(--win-light);
  min-width: 300px;
  max-width: 90vw;
}

.dialog-titlebar {
  background: var(--win-nav);
  color: white;
  padding: 3px 6px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: bold;
}

.dialog-close {
  background: var(--win-bg);
  border: 2px solid;
  border-color: var(--win-light) var(--win-dark) var(--win-dark) var(--win-light);
  width: 18px;
  height: 16px;
  font-size: 12px;
  line-height: 1;
  cursor: pointer;
}

.dialog-content {
  padding: 12px;
}

.dialog-buttons {
  padding: 12px;
  display: flex;
  justify-content: flex-end;
  gap: 8px;
}
```

## Group Box (Collapsible)

```html
<div class="group-box">
  <div class="group-header" onclick="toggleGroup(this)">
    <span class="group-icon">[-]</span>
    <span class="group-title">Essential Sights</span>
  </div>
  <div class="group-content">
    <!-- Content here -->
  </div>
</div>
```

```css
.group-box {
  border: 2px solid;
  border-color: var(--win-light) var(--win-dark) var(--win-dark) var(--win-light);
  margin-bottom: 8px;
}

.group-header {
  background: var(--win-bg);
  padding: 4px 8px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 6px;
  font-weight: bold;
}

.group-header:hover {
  background: var(--win-nav);
  color: white;
}

.group-icon {
  font-family: monospace;
}

.group-content {
  padding: 8px;
  border-top: 1px solid var(--win-dark);
}

.group-box.collapsed .group-content {
  display: none;
}

.group-box.collapsed .group-icon {
  content: '[+]';
}
```

```javascript
function toggleGroup(header) {
  const group = header.parentElement;
  group.classList.toggle('collapsed');
  const icon = header.querySelector('.group-icon');
  icon.textContent = group.classList.contains('collapsed') ? '[+]' : '[-]';
}
```

## Enhanced Button States

```css
/* Base button */
.btn {
  background: var(--win-bg);
  border: 2px solid;
  border-color: var(--win-light) var(--win-dark) var(--win-dark) var(--win-light);
  padding: 4px 12px;
  font-size: 11px;
  cursor: pointer;
}

/* Hover state */
.btn:hover {
  background: var(--win-nav);
  color: white;
}

/* Active/pressed state */
.btn:active {
  border-color: var(--win-dark) var(--win-light) var(--win-light) var(--win-dark);
  padding: 5px 11px 3px 13px; /* Visual press effect */
}

/* Disabled state */
.btn:disabled {
  color: var(--win-dark);
  cursor: not-allowed;
}

/* Primary action */
.btn-primary {
  font-weight: bold;
}
```

## Focus Indicators

```css
/* Visible focus for accessibility */
a:focus-visible,
button:focus-visible,
input:focus-visible {
  outline: 1px dotted #000;
  outline-offset: 2px;
}

/* Alternative: Win31-style focus rectangle */
.win31-focus:focus-visible {
  outline: none;
  box-shadow: inset 0 0 0 1px #000, inset 0 0 0 2px #fff;
}
```

## Hourglass Cursor (Loading State)

```css
.loading {
  cursor: wait;
}

/* Optional: Custom hourglass cursor */
.loading-custom {
  cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16"><text y="14" font-size="14">⏳</text></svg>'), wait;
}
```

## Print Button

```html
<button class="btn btn-primary" onclick="window.print()">
  <span class="print-icon">🖨</span> Print
</button>
```

```css
.print-icon {
  font-family: monospace;
  margin-right: 4px;
}

@media print {
  .btn {
    display: none;
  }
}
```

## Usage Examples

### Add to Existing Page

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="../css/styles.css">
  <style>
    /* Add component styles here or in styles.css */
  </style>
</head>
<body>
  <!-- Page content -->
  
  <!-- Status bar -->
  <div class="status-bar">
    <span id="status-text">Ready</span>
    <span>Istanbul 2026 Guide</span>
  </div>
  
  <script>
    // Update status on page load
    window.addEventListener('load', () => {
      document.getElementById('status-text').textContent = 'Ready';
    });
  </script>
</body>
</html>
```

### Initialize Components

```javascript
// Initialize all group boxes
document.querySelectorAll('.group-header').forEach(header => {
  header.addEventListener('click', () => toggleGroup(header));
});

// Show dialog
function showDialog(message) {
  const dialog = document.getElementById('dialog');
  dialog.querySelector('.dialog-content p').textContent = message;
  dialog.classList.add('active');
}

// Close dialog
document.querySelector('.dialog-close').addEventListener('click', () => {
  document.getElementById('dialog').classList.remove('active');
});
```

---

**Integration:** Copy desired components into `css/styles.css` and add HTML to pages.
