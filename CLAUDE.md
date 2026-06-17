# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

NPLWeb is the static portfolio and landing page for NeoPrimLabs, hosted on GitHub Pages. This is a pure HTML/CSS project with no build system, dependencies, or runtime environment. Changes are made directly to HTML files and deployed automatically when pushed to `main`.

## Architecture

### Files

- [index.html](index.html) — Main landing page with all CSS embedded inline. Sections in order: fixed nav, hero, services grid (3-column), apps showcase, contact, footer with social links.
- [privacy.html](privacy.html) — Index listing all app privacy policies.
- [privacy-app1.html](privacy-app1.html) — Ship Something privacy policy; use as template for additional apps.

### Design System

All styling is in `<style>` tags using CSS custom properties:

```css
:root {
  --bg: #080808;
  --surface: #111111;
  --border: #1f1f1f;
  --accent: #6db33f;       /* Primary green */
  --text: #e8e4dc;
  --font-display: 'Bebas Neue';
  --font-body: 'DM Mono';
}
```

Both fonts are loaded from Google Fonts CDN. Responsive breakpoint at 640px; fluid headline sizing via `clamp()`.

### Visual Patterns

- **Grain overlay:** Fixed SVG `<feTurbulence>` noise on `body::before`.
- **Animations:** `fadeUp` (section entrance), `pulse` (background text).
- **Hover states:** Service cards animate a left border; app items animate a left bar and an arrow (`→`) with `translateX`.
- **Cursor:** Site-wide `crosshair`.

## Common Tasks

### Adding a New App to the Showcase

In [index.html](index.html), inside the `.apps-list` div (around line 552):

```html
<div class="app-item">
  <div class="app-item-left">
    <img src="AppLogo.png" alt="App name icon" class="app-icon"/>
    <span class="app-name">App Name</span>
  </div>
  <div class="app-meta">
    <a href="https://example.com" target="_blank" rel="noopener" class="app-tag">Web</a>
    <a href="https://play.google.com/store/apps/details?id=..." target="_blank" rel="noopener" class="app-tag">Android</a>
  </div>
</div>
```

### Adding a Privacy Policy for a New App

1. Copy `privacy-app1.html` to `privacy-appN.html` and update the title, "Last updated" date, and policy sections.
2. Add a link block in [privacy.html](privacy.html):

```html
<a href="privacy-appN.html" class="app-policy-item">
  <span class="app-policy-name">App Name</span>
  <div class="app-policy-right">
    <span>View Policy</span>
    <span class="app-arrow">→</span>
  </div>
</a>
```

## Deployment

No build step. Open `index.html` in a browser to test locally. Push to `main` to deploy via GitHub Pages.
