# Valentina Pupic — Website Design Spec

**Date:** 2026-06-28
**Owner:** Valentina Pupic (incoming Nutrition student, University of Guelph)

## Purpose

A simple, elegant personal website that centers Valentina's volunteer program,
the **Tech & Conversation Hour**, with a short section about Valentina herself.
It acts as the digital companion to her printed poster: coordinators and families
who receive the poster visit the site to learn more and get in touch.

Audience: retirement-home Recreation / Life Enrichment / Volunteer Coordinators,
and families of seniors.

## Goals

- Recognizably extend the poster's brand, but cleaner and more modern.
- Tell the story top-to-bottom in ~30 seconds of skimming.
- Make contact easy without exposing Valentina's personal info to scrapers.
- Stay clear of clinical / scope-of-practice claims (she is a student, not a
  Registered Dietitian).

## Non-goals

- No blog, CMS, accounts, or backend.
- No e-commerce or payment.
- No reuse of the AI-generated poster illustration.
- No phone number on the public site (kept to the printed poster only).

## Approach

Single-page scrolling static site. Plain `index.html` + `css/styles.css` + a
small amount of JS for the mobile menu and form handling. No build step, no
framework. Deploys as-is to GitHub Pages or Netlify.

### Tech choices

- **Fonts (Google Fonts):** Fraunces (serif headings) + Inter (sans body).
- **Contact form:** Formspree (free). Keeps email out of page source.
- **Icons:** inline SVG line icons (no icon-font dependency).
- **Botanical accents:** subtle inline SVG, used sparingly.

## Palette

- Navy `#1f3a5f` (primary text / headings)
- Teal `#3a7d7b` (secondary accent)
- Warm coral `#e0654f` (calls to action / highlights)
- Cream `#faf6ef` (page background)
- Neutral white `#ffffff` (cards / sections)

Accessible contrast; large, readable type (audience skews older).

## Page structure (single page, top to bottom)

1. **Sticky header** — "Valentina Pupic" wordmark + anchor links
   (About · The Program · Contact). Collapses to a toggle menu on mobile.
2. **Hero** — Headline ("Intergenerational connection through technology."),
   one-line subhead, primary CTA button → Contact. Soft botanical SVG accent,
   generous whitespace.
3. **About Valentina** — real photo (placeholder until provided) beside a short,
   warm bio: Nutrition student at University of Guelph; why she started this.
4. **The Tech & Conversation Hour** — two columns mirroring the poster:
   *What I offer* and *Ideal for residents who'd enjoy*, each with line icons.
5. **Why it matters** — short, calm strip on loneliness / connection. General and
   non-clinical.
6. **Contact** — Formspree form: name, email, an "I'm a…" dropdown
   (Coordinator / Family member / Other), message. Note that it's for Recreation,
   Life Enrichment, and Volunteer Coordinators, and for families.
7. **Footer** — "Available for retirement homes, seniors' residences, and
   community programs."

## Responsiveness & accessibility

- Mobile-first, single breakpoint or two as needed.
- Semantic HTML landmarks; alt text on the photo; labelled form fields.
- Focus-visible states; tap targets sized for older users.

## Content placeholders (provided later)

- Valentina's photo file → `assets/valentina.jpg` (placeholder until provided).
- Formspree form ID → inserted into the form `action`.
- Final bio wording (draft provided, user to tweak).

## Deliverables / file layout

```
index.html
css/styles.css
js/main.js
assets/            (photo + any SVG)
README.md          (deploy + Formspree + photo instructions)
```

## Success criteria

- Opens correctly by double-clicking `index.html` and on a static host.
- Looks polished on phone and desktop.
- Form submits to Formspree once an ID is added.
- No phone number or plain-text email in the page source.
