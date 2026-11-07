# Pheid Site

Static marketing site for **Pheid** (pheid.app) — a group notification app by Novino Inc.

## What is Pheid?

"Group notifications, no group chat." A one-way broadcast notification app for coaches, landlords, teams, and communities. Every user has a **handle**. Share `@handle` (or `name@handle` for a sub-channel) and anyone who enters it receives your push notifications — focused, one-way broadcasts that land as clear, actionable updates.

The name comes from **Pheidippides**, the ancient Greek messenger who ran from Marathon to Athens.

## Site Structure

- `/index.html` — Landing page (hero, features grid, origin story)
- `/support/index.html` — Support and FAQ
- `/privacy/index.html` — Privacy Policy
- `/terms/index.html` — Terms of Service
- `/dmca/index.html` — DMCA Policy
- `/style.css` — Single shared stylesheet
- `/CNAME` — GitHub Pages custom domain (pheid.app)
- `/join/index.html` + `/fr/join/index.html` — channel-preview landing pages (self-contained, inline styles/JS)
- `/.well-known/apple-app-site-association` + `/.well-known/assetlinks.json` — Universal Links (iOS) / App Links (Android) verification files (added v1.2). **Never move, rename, or add an extension to these**; the paths and content-type expectations are fixed by Apple/Google. The AASA lists `ZS777CXGKK.app.pheid` for `/join` + `/fr/join` (+ trailing-slash variants). assetlinks lists the SHA-256s of all three signing certs (debug, upload, Play App Signing); never commit a placeholder — a malformed fingerprint can void the whole statement. When the Android signing key changes, update assetlinks.json.
- `/.nojekyll` — REQUIRED: disables GitHub Pages' Jekyll processing, which would otherwise silently exclude the `.well-known/` dot-directory from the published site.

All pages use subdirectory `index.html` for clean URLs.

## Design System

Same visual language as novino.ca (`D:\source\novino\styles.css` is the reference), in the style of linear.app: flat near-black, tight Inter type, grey secondary text, content grouped in 1px-bordered panels.

- **Tokens** (`:root` in `style.css`; `/join` + `/fr/join` repeat the values inline): `--bg #08090a`, `--surface #0f1011`, `--border rgba(255,255,255,0.08)`, `--text #f7f8f8`, `--text-2 #8a8f98` (secondary text), `--text-3 #62666d` (tertiary, © line), `--accent #d0bcff`
- **Accent:** lavender is the only accent. Use it for link hover, `:focus-visible` outlines (2px) and at most one highlighted element per page (the Pro plan label on the landing page, the Pro column in the support table). No other UI colours; the only exception is the channel avatar colours on `/join`, which mirror the app's channel colours.
- **Fonts:** Inter 400/500/600 for everything. DM Serif Display is loaded only for the text "Pheid" wordmark (`&text=Pheid` subset).
- **Type:** headings weight 500; h1 `letter-spacing -0.03em`, line-height 1.05 (hero h1 `clamp(2.75rem, 6vw, 4.5rem)`); h2/h3 `-0.015em`, section h2 1.75rem. Body 16px; secondary text in `--text-2`. Small labels above headings (`.eyebrow`, `.faq-group`, `.toc-title`) are plain text: no uppercase, no letter-spacing.
- **Panels:** each section is an h2 followed by ONE `.panel` (`--surface`, 1px `--border`, radius 10px, overflow hidden). Grids inside a panel (`.steps`, `.usecases`, `.features`, `.plans`) get their 1px dividers from `gap: 1px` over a `--border` background, so they stack cleanly below 720px. Sections are separated by spacing (~6rem), not rules. FAQ groups are one panel each, with dividers between questions.
- **Radius:** 10px for panels, 6px for buttons. Nothing else.
- **Nav:** sticky, `rgba(8,9,10,0.8)` + `backdrop-filter: blur(12px)`, 1px bottom border; logo left, muted text links right, exactly one light button (`.nav-cta`: `#e6e6e6` on `#08090a`, `#fff` on hover).
- **Footer:** one quiet row with a 1px top border; links in `--text-2`, © in `--text-3` at 0.85rem.
- **Screenshots:** `/img/*-en.jpg` / `*-fr.jpg` are 540px-wide JPEGs resized from `D:\source\pheid\screenshots\iphone-6.9[-fr]`; regenerate them when the app UI changes. Show them plainly in a 1px `--border` frame (`.phone`).
- **Store badges:** Apple SVG at 40px. Google's PNG has built-in padding, so `.badge-google` crops it (`overflow:hidden`, radius 6px): EN img 60px tall with `margin:-10px`; FR (`html:lang(fr)`) 52px with `margin:-6px 0`.
- **Avoid:** gradients, glows, box-shadows, pill chips, hover lift, entrance animations, coloured icon tiles (feature icons are 20px monochrome in `--text-2`).
- **Layout:** max-width 1040px; legal pages use a sticky table of contents beside a ~68ch column.
- **Breakpoints:** 900px (legal TOC hidden), 720px (mobile: hero and panel grids stack), 420px (nav drops the Support link).

## Conventions

- All pages share the same nav/footer template (EXCEPT the `/join` + `/fr/join` landing pages, which are deliberately self-contained with inline styles/JS)
- CSS variables defined in `:root` for theming
- No build tools — plain HTML/CSS
- Hosted on GitHub Pages
