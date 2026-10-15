---
name: flash-landing-page
description: Generate a single-file HTML "flash" landing page for a new product, workshop, or launch. Use when the user wants a quick, simple-but-classy sales page (Indonesian-first) with a direct-buy CTA to lynk.id or a payment gateway, a fresh visual style per product, and only the HTML code as output. Triggers on "bikin landing page", "flash page", "landing page produk baru", "sales page", "halaman jualan".
---

# Flash Landing Page Generator

Produces ONE self-contained `.html` file for a single product launch. The owner will paste it into their own hosting / page builder, so the output must run with no build step and no local assets required.

## What the owner wants (defaults — do not re-ask)

- **Output:** HTML code only. No frameworks, no build tooling, no extra files.
- **Language:** Indonesian first, with light English phrases where they make things clearer ("Early Bird", "What You Will Get", "Register now").
- **Goal:** direct purchase. Every CTA points to ONE checkout URL (lynk.id or a payment gateway).
- **Look:** simple but classy. Restrained, editorial, generous whitespace. Not a template, not a gradient-and-emoji "AI page".
- **Style is fresh per product.** Palette, typefaces, and hero composition are chosen from the product itself. Never reuse the previous product's look.
- **Plain by default.** No countdown, testimonials, FAQ, popups, or social-proof widgets unless the owner explicitly asks.

## Inputs to collect

Ask only for what is missing, in ONE short message. Anything unanswered becomes a clearly marked placeholder, never an invention.

| Need | Notes |
|---|---|
| Product name + one-line promise | Becomes H1 and meta description |
| Target audience (main / secondary) | Drives "Untuk Siapa" section copy |
| Key benefits or outcomes | 3–6 items |
| What's inside (deliverables / modules / bonuses) | Becomes the "What You Will Get" grid |
| Price, strikethrough price, deadline/period | Price block |
| Event details (date, time, format) if it's a live product | Info bar |
| Checkout URL | Goes in `CHECKOUT_URL` |
| Flyer / reference image / brand colors / photos | Used for palette + mood; if a photo is unusable, do not embed it |
| Mood words or a reference | Optional; otherwise infer from the product |

**Never fabricate:** testimonials, student counts, ratings, "as seen on", guarantees, mentor credentials, income claims, or deadlines the owner did not state. If the source says "praktisi berpengalaman", write exactly that.

## Process

1. **Read the brief and any flyer/reference.** Extract facts verbatim (names, dates, prices, item titles). These are the single source of truth.
2. **Pick a design direction** (2–3 lines, say it to the user before building):
   - Palette: 1 ink, 1 background, 1 accent, 1 soft surface. Derive from the flyer/brand if given, else from the product's world.
   - Type: one display face + one body face from Google Fonts; optional single handwritten accent used sparingly.
   - Hero: the one distinctive move for this product (huge serif headline, split panel, numeric proof, etc.).
3. **Build from the structure below**, using `reference/example-workshop.html` as a *structural and quality* reference only. Re-theme and re-compose; do not copy its colors or fonts.
4. **Verify** (see checklist) in a browser at desktop and 375px width.
5. **Deliver** the file path plus a short list of what the owner must still fill in.

## Page structure (adapt, don't force)

1. **Hero** — eyebrow, H1, one-line promise, primary CTA, small supporting visual/panel
2. **Info bar** — date/time/format (live products) or key facts (digital products)
3. **Untuk Siapa** — main target + secondary target
4. **What You Will Get** — 3 or 6 items in a bordered grid, numbered
5. **Price block** — strikethrough normal price, highlighted price, short note, CTA
6. **Trust line** — 2–3 short factual points taken from the brief
7. **Footer** — brand/trademark note if a third-party product is named
8. **Mobile sticky CTA bar** — price + button, hidden on desktop

Drop sections the product doesn't need. A short page that is true beats a long page that is padded.

## Engineering rules

- Single file; CSS in `<style>`, JS in one small `<script>`; fonts via Google Fonts `<link>` only.
- Design tokens as CSS variables on `:root` with a comment "EDIT BAGIAN INI SAJA UNTUK PRODUK BARU".
- One `const CHECKOUT_URL = "https://lynk.id/USERNAME/PRODUK";` at the top of the script; every `[data-cta]` anchor reads from it. Leave a `TODO` comment for the owner.
- Inline SVG icons (stroke style, `currentColor`). **No emoji as icons.**
- Responsive mobile-first; no horizontal scroll at 375px; `clamp()` for headline sizes.
- Reveal-on-scroll with IntersectionObserver, with `prefers-reduced-motion` fallback and a no-IO fallback.
- Accessible: semantic landmarks (`header`, `section`, `footer`), focus-visible styles, text contrast ≥ 4.5:1, alt/aria on meaningful visuals, `lang="id"`.
- `<title>`, meta description, and viewport meta present.
- Handwritten/script accent text must stay decorative and never carry required information.
- Decorative annotations must not overlap or overflow on mobile (position them absolutely only at ≥ 820px).

## Verification checklist

- [ ] Every price, date, name, and item title matches the source exactly
- [ ] All CTAs resolve to `CHECKOUT_URL` (or `#daftar` for the hero scroll)
- [ ] `document.documentElement.scrollWidth <= innerWidth` at 375px and 1024px
- [ ] No text overlaps at 375px; sticky bar doesn't cover footer content (body has bottom padding)
- [ ] No invented claims, numbers, or credentials
- [ ] Only the sections the owner asked for are present

## Delivery message (keep short, Indonesian, casual)

State: file path, design direction in one line, and a "yang perlu lu isi" list (checkout link, photo, mentor name, anything left as placeholder). Offer one concrete next tweak, not a menu.
