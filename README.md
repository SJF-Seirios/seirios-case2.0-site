# Seirios Website

**Brand:** Seirios (Seirios B.V.)  
**Stack:** Pure HTML/CSS/JS — zero build step, zero dependencies, zero cost.  
**Slogan:** AI you can prove.

## What changed (rebrand from Threadledger)

- Name: Threadledger → **Seirios**
- Logo mark: green square "TL" → **8-point Seirios star SVG** (Concept A: deep space)
- CASE 2.0 badge added to nav
- Light theme accent: teal-green `#1D9E75` → stellar blue `#185fba`
- Dark theme accent: cyan `#00e0ff` → stellar blue `#4a9eff`
- Dark bg void: `#080c14` → deep space navy `#0d1117`
- Slogan: "Provable AI Compliance" → "AI you can prove."
- Domain ref: hellothreadledger.io → seirios.ai
- Legal entity: Seirios B.V. preserved in footer

## File Structure

```
seirios-site/
├── index.html              # Main homepage
├── for-ciso.html           # CISO / DPO audience page
├── for-devops.html         # DevSecOps audience page
├── vercel.json             # Vercel deployment config
├── README.md
├── css/
│   └── design-system.css   # Source of truth (not linked; CSS is inlined per page)
├── js/
│   └── theme.js            # Theme toggle + mobile nav
├── pages/
│   ├── regulations.html
│   ├── ai-agent-security.html
│   ├── request-demo.html
│   └── about.html
└── assets/
    ├── favicon.svg         # TODO: update to Seirios star mark
    └── videos/
```

## Favicon

Update `assets/favicon.svg` with the Seirios star mark. Recommended SVG:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
  <rect width="32" height="32" rx="6" fill="#0d1117"/>
  <circle cx="16" cy="16" r="13" fill="none" stroke="#4a9eff" stroke-width="0.6" opacity="0.3"/>
  <line x1="16" y1="4" x2="16" y2="28" stroke="#4a9eff" stroke-width="1.5" stroke-linecap="round"/>
  <line x1="4" y1="16" x2="28" y2="16" stroke="#4a9eff" stroke-width="1.5" stroke-linecap="round"/>
  <line x1="7.5" y1="7.5" x2="24.5" y2="24.5" stroke="#4a9eff" stroke-width="1" stroke-linecap="round" opacity="0.5"/>
  <line x1="24.5" y1="7.5" x2="7.5" y2="24.5" stroke="#4a9eff" stroke-width="1" stroke-linecap="round" opacity="0.5"/>
  <circle cx="16" cy="16" r="4.5" fill="#1a2e50" stroke="#4a9eff" stroke-width="0.8"/>
  <circle cx="16" cy="16" r="2" fill="#4a9eff"/>
  <circle cx="16" cy="16" r="0.8" fill="#c8e0ff"/>
</svg>
```

## Deployment

Same as before — Vercel free tier, zero build step.

```bash
cd seirios-site
vercel
```

Update domain in Vercel dashboard to point to seirios.ai (or your current domain).

## Design Tokens

| Token | Light | Dark | Usage |
|-------|-------|------|-------|
| `--cyan` | `#185fba` | `#4a9eff` | Primary accent — buttons, links, active states |
| `--bg-void` | `#f7f8fb` | `#0d1117` | Page background |
| `--bg-deep` | `#f0f2f8` | `#0f1520` | Section alternates |
| `--text-primary` | `#0a1f3d` | `#e2ecf8` | Main text |
| `--font-display` | DM Serif Display | Space Mono | Headings |
| `--font-mono` | DM Mono | Space Mono | Badges, code, mono |
| `--font-body` | Figtree | DM Sans | Body copy |
