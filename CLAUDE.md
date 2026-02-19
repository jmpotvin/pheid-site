# Pheid Site

Static marketing site for **Pheid** (pheid.app) — a group notification app by Novino Inc.

## What is Pheid?

"Group notifications, no group chat." A one-way broadcast notification app for coaches, landlords, teams, and communities. Admins create **channels**, share a code, and subscribers receive push notifications without the ability to reply.

The name comes from **Pheidippides**, the ancient Greek messenger who ran from Marathon to Athens.

## Site Structure

- `/index.html` — Landing page (hero, features grid, origin story)
- `/support/index.html` — Support and FAQ
- `/privacy/index.html` — Privacy Policy
- `/terms/index.html` — Terms of Service
- `/dmca/index.html` — DMCA Policy
- `/style.css` — Single shared stylesheet
- `/CNAME` — GitHub Pages custom domain (pheid.app)

All pages use subdirectory `index.html` for clean URLs.

## Design System

- **Theme:** Dark background (`#0b1120`) with light text (`#e8ecf1`)
- **Accent color:** Cyan/blue (`#38a3d9`)
- **Font:** DM Sans (Google Fonts), Georgia serif for h1
- **Layout:** Max-width 900px, centered
- **Animations:** `.fade-up` with `.delay-1`, `.delay-2`, `.delay-3` stagger classes
- **Mobile breakpoint:** 600px

## Conventions

- All pages share the same nav/footer template
- CSS variables defined in `:root` for theming
- No build tools — plain HTML/CSS
- Hosted on GitHub Pages
