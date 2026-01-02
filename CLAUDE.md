# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a collection of standalone, single-file HTML/CSS/JavaScript web tools deployed as a static site at `tools.jasonvan.com`. The project is inspired by Simon Willison's "Useful patterns for building HTML tools" philosophy.

**Deployment**: Static hosting via GitHub Pages (configured via CNAME file)

## Architecture Pattern

Every tool in this repository follows a strict **single-file architecture**:

- **One HTML file per tool** containing all HTML, CSS (in `<style>` tags), and JavaScript (in `<script>` tags)
- **No build process** - files are used directly in production
- **No external dependencies** except Google Fonts and occasionally CDN-hosted libraries (e.g., pdf-lib)
- **Vanilla JavaScript only** - no frameworks (React, Vue, etc.)
- **Client-side only** - all processing happens in the browser
- **localStorage for persistence** - each tool uses a unique key

### File Structure

```
tool-name.html          # Complete standalone app
tool-name.md            # Documentation (prompt history, features, technical details)
tool-name-assets.*      # Optional: favicons, images (rare)
```

## Design Philosophy

### Single-File Implementation
- All HTML, CSS, and JavaScript must be in a single `.html` file
- Embedded `<style>` block for all CSS
- Embedded `<script>` block for all JavaScript
- Self-contained and directly deployable

### Vanilla JavaScript Patterns
- **State management**: Simple object-based state (no frameworks)
- **localStorage**: Used for data persistence with tool-specific keys
- **DOM manipulation**: Direct `getElementById()` and `.innerHTML`
- **Event listeners**: Standard `addEventListener()` patterns

### CSS & Styling Conventions

Each tool has a unique, distinctive design aesthetic - **never reuse or copy designs between tools**:

**Common CSS Patterns**:
```css
/* CSS Variables for theming */
:root { --primary-color: ...; --font-display: ...; }

/* Semantic structure */
.nav, .container, .card { /* layout patterns */ }

/* Responsive breakpoints */
@media (max-width: 640px) { /* mobile */ }
@media (min-width: 768px) { /* tablet+ */ }
```

**Typography**: Use distinctive Google Fonts (avoid generic system fonts like Inter, Roboto, Arial). Pair a characterful display font with a clean body font.

**Color**: Each tool should have its own unique color palette. Avoid converging on similar color schemes.

**Animation**: CSS animations for micro-interactions, staggered entrance effects with `animation-delay`

### Data Storage Pattern

```javascript
const STORAGE_KEY = 'uniqueToolName';  // Unique per tool

function saveToStorage() {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
}

function loadFromStorage() {
  const saved = localStorage.getItem(STORAGE_KEY);
  if (saved) state = JSON.parse(saved);
}
```

## Creating New Tools

When building a new tool, follow these steps:

1. **Design Direction First**: Commit to a bold, distinctive aesthetic (brutalist, editorial, retro-futuristic, etc.). Never create generic "AI slop" designs.

2. **Single File Structure**:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <title>Tool Name</title>
     <link href="https://fonts.googleapis.com/..." rel="stylesheet">
     <style>
       /* All CSS here */
     </style>
   </head>
   <body>
     <!-- All HTML here -->
     <script>
       // All JavaScript here
     </script>
   </body>
   </html>
   ```

3. **Documentation File**: Create a matching `.md` file with:
   - Description and key features
   - Prompt history (how the tool was created)
   - Technical details (libraries, data structure, localStorage key)
   - Design system (fonts, colors, animations)
   - Model used (Claude version)
   - Known limitations
   - Future enhancements

4. **Update README.md**: Add tool link to the main README

## Existing Tools Reference

### Storage Keys
- `pushupPlankTracker` - Pushup & Plank Tracker
- `fatLossTracker` - Fat Loss Tracker
- Document Size Convertor - no storage (stateless)
- Resistor Laboratory - no storage (educational tool)

### Design Aesthetics
- **Pushup Tracker**: Athletic scoreboard (Anton + Outfit, orange accents)
- **Document Size Convertor**: Blueprint cyan theme (IBM Plex Mono + DM Sans)
- **Resistor Laboratory**: Dark navy educational (system fonts)
- **Fat Loss Tracker**: Neo-brutalist editorial (Fraunces + Sora, orange palette, bold borders, offset shadows)

## Git Workflow

- **Feature branches**: `claude/[feature-name]-[ID]` format
- **Pull requests**: Used even for solo work to maintain clean history
- **Commit messages**: Descriptive, explain the "why" not just the "what"
- **Co-authored by**: Include Claude attribution in commits:
  ```
  Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>
  ```

## Important Constraints

- **Never use React, Vue, or any framework** - vanilla JS only
- **Never split files** - each tool must be completely self-contained
- **Never use build tools** - files run directly in browsers
- **Never reuse designs** - each tool needs a unique aesthetic
- **Never use generic fonts** - choose distinctive typefaces
- **Always use localStorage for persistence** - with unique keys per tool
- **Always include documentation** - create/update the `.md` file

## Testing

No automated tests. Manual testing in browser:
1. Open the `.html` file directly in a browser
2. Test core functionality
3. Verify localStorage persistence (check DevTools → Application → Local Storage)
4. Test responsive behavior (mobile, tablet, desktop)
5. Check animations and interactions

## Deployment

Push to `main` branch - GitHub Pages automatically deploys to `tools.jasonvan.com`.
