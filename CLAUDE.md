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

- **Theme:** Dark background (`#0b1120`) with light text (`#e8ecf1`)
- **Accent color:** Cyan/blue (`#38a3d9`)
- **Font:** DM Sans (Google Fonts), Georgia serif for h1
- **Layout:** Max-width 900px, centered
- **Animations:** `.fade-up` with `.delay-1`, `.delay-2`, `.delay-3` stagger classes
- **Mobile breakpoint:** 600px

## Conventions

- All pages share the same nav/footer template (EXCEPT the `/join` + `/fr/join` landing pages, which are deliberately self-contained with inline styles/JS)
- CSS variables defined in `:root` for theming
- No build tools — plain HTML/CSS
- Hosted on GitHub Pages
