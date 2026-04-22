# UAE PASS Digital Vault — 2026 Roadmap Tracker

A password-protected, single-file web tracker for the UAE PASS Digital Vault (DV) 2026 product roadmap. Deployed as a static site via GitHub Pages.

**Live URL:** https://fadicog.github.io/tasktracker/

## Overview

- 28 roadmap features across 6 categories (Product, Design, Design (DDA), UX, Technical, SP)
- Two-level hierarchy: Features (parent rows) -> Sub-tasks (collapsible child rows)
- Progress bars per feature based on % of sub-tasks completed
- Category filter chips, status dropdown, search, expand/collapse all
- KPI summary cards at the top
- "DDA Dependent" badges on features requiring Design Authority alignment
- Responsive for mobile and desktop

## Access

Password-gated on first load. Password is stored in `sessionStorage` so the user is not re-prompted during the same browser session.

Password protection uses SHA-256 hashing of the password in-browser (via `crypto.subtle.digest`). The plaintext password is never stored in code. Note: client-side password protection is a deterrent, not enterprise-grade security.

## Updating Data

All data lives in the `FEATURES` and `OTHER_ACTIONS` arrays inside `index.html`. To update:

1. Edit the relevant object entries
2. Commit and push to `main`
3. GitHub Pages rebuilds the site automatically within 1-2 minutes

### Feature schema

```js
{
  slide: 6,                              // slide number from source deck
  name: "Feature Name",
  category: "Product",                   // Product | Design | Design (DDA) | UX | Technical | SP
  quarter: "Q1",                         // Q1, Q2, Q3, Q4, Q1-Q2, or "-"
  status: "In Progress",                 // Completed | In Progress | Started | Pending | Not started
  dda: false,                            // true to show "DDA Dependent" badge
  sub: [                                 // array of sub-tasks (can be empty)
    { task: "...", due: "YYYY-MM-DD", status: "Completed", owner: "Name" }
  ]
}
```

## Last Updated

22 April 2026

## File Structure

```
tasktracker/
  index.html    - Single-file tracker (HTML + CSS + JS + data)
  README.md     - This file
```

No build step. No external runtime dependencies beyond Google Fonts for the Inter typeface.
