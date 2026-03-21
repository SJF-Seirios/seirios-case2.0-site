# Threadledger Website

**Stack:** Pure HTML/CSS/JS — zero build step, zero dependencies, zero cost.

## File Structure

```
threadledger-site/
├── index.html              # Main homepage
├── vercel.json             # Vercel deployment config
├── css/
│   └── design-system.css   # Shared design system (all pages import this)
├── pages/
│   ├── for-ciso.html       # CISO / DPO audience page
│   └── for-devops.html     # DevSecOps audience page
└── assets/
    ├── favicon.svg
    └── videos/             # Add demo videos here (see below)
```

---

## Deployment: Vercel (Free tier)

### Step 1 — Connect your domain

Your domain is `serios.xyz`. The website will live at a subdomain, e.g. `threadledger.serios.xyz` or you can point the apex domain.

### Step 2 — Deploy to Vercel

```bash
# Install Vercel CLI
npm i -g vercel

# From the threadledger-site/ directory
cd threadledger-site
vercel

# Follow prompts:
# - Link to existing project or create new: New
# - Project name: threadledger
# - Detected framework: Other (static)
# - Root directory: ./
```

### Step 3 — Add custom domain in Vercel dashboard

1. Go to Project Settings → Domains
2. Add `threadledger.serios.xyz` (or your preferred subdomain)
3. Add the CNAME record in your DNS provider pointing to `cns1.vercel-dns.com`

### Step 4 — Set up email routing

Since you have `serios.xyz` email, `contact@threadledger.io` CTA links in the site use `mailto:contact@threadledger.io`. 

If you want to use a Threadledger subdomain email:
- **Cloudflare Email Routing** (free): forward `contact@threadledger.serios.xyz` → your real inbox
- Or use **Forwardemail.net** (free) for custom domain email forwarding

---

## Adding Demo Videos

### Recommended approach: Cloudflare Stream (free tier) or Loom

1. Record your terminal demos using **Loom** (free) or **OBS**
2. For the CISO demo (~4 min): record the Eclipse threat modeling workbench + OCL verification output
3. For the DevSecOps demo (~5 min): record the terminal running `./threadledger-ci run --mode=full` showing all 3 tiers

### Embed in the pages

Replace the video placeholder `<div class="video-frame">` sections in both pages with:

```html
<!-- Loom embed -->
<div style="position:relative; padding-bottom:56.25%; height:0; overflow:hidden; border-radius:12px;">
  <iframe 
    src="https://www.loom.com/embed/YOUR_VIDEO_ID" 
    style="position:absolute; top:0; left:0; width:100%; height:100%;" 
    frameborder="0" 
    allowfullscreen>
  </iframe>
</div>

<!-- OR: Self-hosted video file in /assets/videos/ -->
<video 
  controls 
  poster="/assets/videos/ciso-demo-thumb.jpg"
  style="width:100%; border-radius:12px; border:1px solid var(--border-subtle);">
  <source src="/assets/videos/ciso-demo.mp4" type="video/mp4">
</video>
```

**Video size limit on Vercel free tier:** 100MB per deployment. For larger videos, use Loom, YouTube (unlisted), or Cloudflare Stream.

---

## Design System

The CSS design system in `css/design-system.css` defines:

| Token | Value | Usage |
|-------|-------|-------|
| `--cyan` | `#00e0ff` | Primary accent, interactive elements |
| `--green` | `#00ff88` | Success states, DevSecOps page |
| `--amber` | `#ffaa00` | Warnings, urgency indicators |
| `--red` | `#ff4466` | Failures, BUILD FAIL states |
| `--bg-void` | `#080c14` | Page background |
| `--font-mono` | Space Mono | Headers, code, badges |
| `--font-body` | DM Sans | Body text, descriptions |

---

## Pages

| URL | File | Audience |
|-----|------|----------|
| `/` | `index.html` | General — investors, inbound |
| `/pages/for-ciso.html` | `pages/for-ciso.html` | CISOs, DPOs, Compliance Officers |
| `/pages/for-devops.html` | `pages/for-devops.html` | Security Engineers, DevSecOps |

---

## Next pages to add

- `/pages/pricing.html` — Dedicated pricing comparison
- `/pages/eu-ai-act.html` — EU AI Act compliance deep-dive (SEO play)
- `/pages/request-demo.html` — Demo request form (use Tally.so free tier for the form)
- `/pages/about.html` — Team page (add when co-founders are confirmed)

---

## Analytics (free)

Add **Plausible** or **Umami** (self-hosted on Vercel) for privacy-respecting analytics:

```html
<!-- Plausible (add to <head> of each page) -->
<script defer data-domain="threadledger.serios.xyz" src="https://plausible.io/js/script.js"></script>
```

---

## Security headers

`vercel.json` already sets:
- `X-Frame-Options: DENY`
- `X-Content-Type-Options: nosniff`
- `X-XSS-Protection`
- `Referrer-Policy: strict-origin-when-cross-origin`
- `Permissions-Policy` (camera, mic, geo off)

These are appropriate for a security company's website.
