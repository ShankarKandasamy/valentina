# Valentina Pupic Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a simple, elegant single-page static website for Valentina Pupic that centers her "Tech & Conversation Hour" volunteer program, with a short About section and a spam-safe contact form.

**Architecture:** Plain static files — `index.html`, `css/styles.css`, `js/main.js`, plus `assets/`. No framework, no build step. A single scrolling page with a sticky header. Deploys as-is to GitHub Pages or Netlify. Contact handled by Formspree (no backend).

**Tech Stack:** HTML5, CSS3 (custom properties, fl/grid), vanilla JS, Google Fonts (Fraunces + Inter), Formspree.

## Global Constraints

- Palette (use as CSS custom properties): navy `#1f3a5f`, teal `#3a7d7b`, coral `#e0654f`, cream `#faf6ef`, white `#ffffff`.
- Fonts: Fraunces for headings, Inter for body (via Google Fonts).
- NO phone number anywhere in the site or page source.
- NO plain-text email in page source (contact only via Formspree form).
- NO reuse of the AI-generated poster illustration.
- Mobile-first and responsive; accessible contrast; large, readable type (audience skews older).
- No backend, no build step, no framework.
- No emojis in code or copy.
- Tagline / brand line: "Intergenerational connection through technology."
- Footer line: "Available for retirement homes, seniors' residences, and community programs."

**Verification model:** This is static HTML with no test runner. Each task is verified by opening `index.html` in a browser and confirming the described result. Optional git commits assume Task 0 ran `git init`.

---

### Task 0: Project scaffold

**Files:**
- Create: `index.html`
- Create: `css/styles.css`
- Create: `js/main.js`
- Create: `assets/.gitkeep`
- Create: `.gitignore`
- Create: `README.md`

**Interfaces:**
- Produces: linked skeleton — `index.html` references `css/styles.css` and `js/main.js`; CSS defines the palette/font custom properties consumed by every later task.

- [ ] **Step 1: (Optional) initialize git**

```bash
cd "C:/Users/shank/OneDrive/Documents/Valentina/summer2026"
git init
```

- [ ] **Step 2: Create `.gitignore`**

```
.DS_Store
Thumbs.db
*.log
```

- [ ] **Step 3: Create `css/styles.css` with design tokens and reset**

```css
:root {
  --navy: #1f3a5f;
  --teal: #3a7d7b;
  --coral: #e0654f;
  --cream: #faf6ef;
  --white: #ffffff;
  --ink: #25303b;
  --muted: #5b6b78;
  --maxw: 1080px;
  --radius: 14px;
  --shadow: 0 8px 30px rgba(31, 58, 95, 0.08);
  --font-head: "Fraunces", Georgia, serif;
  --font-body: "Inter", system-ui, -apple-system, sans-serif;
}

*, *::before, *::after { box-sizing: border-box; }

html { scroll-behavior: smooth; }

body {
  margin: 0;
  font-family: var(--font-body);
  color: var(--ink);
  background: var(--cream);
  line-height: 1.6;
  font-size: 18px;
}

h1, h2, h3 {
  font-family: var(--font-head);
  color: var(--navy);
  line-height: 1.15;
  font-weight: 600;
}

a { color: var(--teal); }

img { max-width: 100%; display: block; }

.container {
  width: 100%;
  max-width: var(--maxw);
  margin: 0 auto;
  padding: 0 24px;
}

section { padding: 88px 0; }

.section-alt { background: var(--white); }
```

- [ ] **Step 4: Create `js/main.js` (placeholder, filled in Task 2 and Task 6)**

```js
// Site interactivity. Sections wired up in later tasks.
document.addEventListener("DOMContentLoaded", () => {
  // mobile nav + form handlers added later
});
```

- [ ] **Step 5: Create `assets/.gitkeep`** (empty file so the folder exists)

- [ ] **Step 6: Create `index.html` skeleton**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Valentina Pupic — Tech & Conversation Hour</title>
  <meta name="description" content="Valentina Pupic offers a weekly Tech & Conversation Hour bringing companionship and simple technology help to seniors. Intergenerational connection through technology." />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="css/styles.css" />
</head>
<body>
  <!-- header: Task 2 -->
  <!-- hero: Task 1 -->
  <!-- about: Task 3 -->
  <!-- program: Task 4 -->
  <!-- why it matters: Task 5 -->
  <!-- contact: Task 6 -->
  <!-- footer: Task 7 -->
  <script src="js/main.js"></script>
</body>
</html>
```

- [ ] **Step 7: Create `README.md`**

```markdown
# Valentina Pupic — Website

Single-page static site for the Tech & Conversation Hour program.

## Run locally
Double-click `index.html`, or serve the folder:
`python -m http.server` then open http://localhost:8000

## Deploy
Push this folder to a GitHub repo and enable GitHub Pages (Settings -> Pages -> deploy from branch, root),
or drag the folder onto https://app.netlify.com/drop.

## Before going live
1. Add Valentina's photo as `assets/valentina.jpg` (see Task 3 placeholder).
2. Create a free Formspree form at https://formspree.io and paste its endpoint
   into the form `action` in `index.html` (replace `YOUR_FORM_ID`).
```

- [ ] **Step 8: Verify**

Open `index.html` in a browser. Expected: a blank cream page, no console errors, Fraunces/Inter loaded (check Network tab shows the fonts CSS).

- [ ] **Step 9: (Optional) commit**

```bash
git add -A
git commit -m "chore: project scaffold and design tokens"
```

---

### Task 1: Hero section

**Files:**
- Modify: `index.html` (replace `<!-- hero: Task 1 -->`)
- Modify: `css/styles.css` (append)

**Interfaces:**
- Consumes: `.container`, palette/font tokens from Task 0.
- Produces: `#hero` landmark; CTA anchor linking to `#contact` (built in Task 6).

- [ ] **Step 1: Add the hero markup** (replace the `<!-- hero: Task 1 -->` comment)

```html
<main id="top">
<section id="hero" class="hero">
  <div class="container hero__inner">
    <p class="eyebrow">Friendly student volunteer</p>
    <h1 class="hero__title">Intergenerational connection through technology.</h1>
    <p class="hero__lead">
      A warm weekly visit that brings companionship, curiosity, and simple
      technology help to seniors — one friendly hour at a time.
    </p>
    <a class="btn btn--primary" href="#contact">Get in touch</a>
  </div>
</section>
```

(Note: `<main id="top">` opens here and closes after the Contact section in Task 6.)

- [ ] **Step 2: Add hero styles** (append to `styles.css`)

```css
.eyebrow {
  text-transform: uppercase;
  letter-spacing: 0.12em;
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--coral);
  margin: 0 0 12px;
}

.hero { padding: 120px 0 96px; background: var(--cream); }

.hero__inner { max-width: 760px; }

.hero__title { font-size: clamp(2.4rem, 6vw, 4rem); margin: 0 0 20px; }

.hero__lead { font-size: 1.2rem; color: var(--muted); margin: 0 0 32px; }

.btn {
  display: inline-block;
  padding: 14px 28px;
  border-radius: 999px;
  font-weight: 600;
  text-decoration: none;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}

.btn--primary { background: var(--coral); color: var(--white); }

.btn--primary:hover { transform: translateY(-2px); box-shadow: var(--shadow); }

.btn:focus-visible { outline: 3px solid var(--navy); outline-offset: 2px; }
```

- [ ] **Step 3: Verify**

Reload `index.html`. Expected: large serif headline, coral eyebrow text, muted lead paragraph, a coral pill "Get in touch" button. Hover lifts the button.

- [ ] **Step 4: (Optional) commit**

```bash
git add -A && git commit -m "feat: hero section"
```

---

### Task 2: Sticky header and mobile nav

**Files:**
- Modify: `index.html` (replace `<!-- header: Task 2 -->`)
- Modify: `css/styles.css` (append)
- Modify: `js/main.js` (add nav toggle)

**Interfaces:**
- Consumes: section ids `#about`, `#program`, `#contact` (created in later tasks; anchors are valid even before targets exist).
- Produces: `.site-header` with a `#navToggle` button toggling `.nav--open` on `#primaryNav`.

- [ ] **Step 1: Add header markup** (replace `<!-- header: Task 2 -->`)

```html
<header class="site-header">
  <div class="container site-header__inner">
    <a class="wordmark" href="#top">Valentina&nbsp;Pupic</a>
    <button id="navToggle" class="nav-toggle" aria-label="Menu" aria-expanded="false" aria-controls="primaryNav">
      <span></span><span></span><span></span>
    </button>
    <nav id="primaryNav" class="nav" aria-label="Primary">
      <a href="#about">About</a>
      <a href="#program">The Program</a>
      <a href="#contact">Contact</a>
    </nav>
  </div>
</header>
```

- [ ] **Step 2: Add header styles** (append to `styles.css`)

```css
.site-header {
  position: sticky;
  top: 0;
  z-index: 50;
  background: rgba(250, 246, 239, 0.9);
  backdrop-filter: blur(8px);
  border-bottom: 1px solid rgba(31, 58, 95, 0.08);
}

.site-header__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 68px;
}

.wordmark {
  font-family: var(--font-head);
  font-weight: 600;
  font-size: 1.25rem;
  color: var(--navy);
  text-decoration: none;
}

.nav { display: flex; gap: 28px; }

.nav a {
  color: var(--navy);
  text-decoration: none;
  font-weight: 500;
}

.nav a:hover { color: var(--coral); }

.nav-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: 0;
  cursor: pointer;
  padding: 8px;
}

.nav-toggle span {
  width: 24px;
  height: 2px;
  background: var(--navy);
  display: block;
}

@media (max-width: 720px) {
  .nav-toggle { display: flex; }
  .nav {
    position: absolute;
    top: 68px;
    left: 0;
    right: 0;
    flex-direction: column;
    gap: 0;
    background: var(--cream);
    border-bottom: 1px solid rgba(31, 58, 95, 0.08);
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.25s ease;
  }
  .nav a { padding: 16px 24px; border-top: 1px solid rgba(31, 58, 95, 0.06); }
  .nav--open { max-height: 240px; }
}
```

- [ ] **Step 3: Wire the toggle** (replace the body of the `DOMContentLoaded` callback in `js/main.js`)

```js
document.addEventListener("DOMContentLoaded", () => {
  const toggle = document.getElementById("navToggle");
  const nav = document.getElementById("primaryNav");
  if (toggle && nav) {
    toggle.addEventListener("click", () => {
      const open = nav.classList.toggle("nav--open");
      toggle.setAttribute("aria-expanded", String(open));
    });
    nav.querySelectorAll("a").forEach((link) =>
      link.addEventListener("click", () => {
        nav.classList.remove("nav--open");
        toggle.setAttribute("aria-expanded", "false");
      })
    );
  }
});
```

- [ ] **Step 4: Verify (desktop)**

Reload at full width. Expected: sticky translucent header, wordmark left, three links right; clicking "About"/"Contact" smooth-scrolls (targets land once later tasks add them).

- [ ] **Step 5: Verify (mobile)**

Narrow the window below 720px. Expected: links collapse into a hamburger; clicking it opens the menu; clicking a link closes it; `aria-expanded` flips in devtools.

- [ ] **Step 6: (Optional) commit**

```bash
git add -A && git commit -m "feat: sticky header with mobile nav"
```

---

### Task 3: About Valentina section

**Files:**
- Modify: `index.html` (replace `<!-- about: Task 3 -->`)
- Modify: `css/styles.css` (append)
- Create: `assets/valentina-placeholder.svg`

**Interfaces:**
- Consumes: `.container`, `.section-alt`, tokens.
- Produces: `#about` landmark.

- [ ] **Step 1: Create a photo placeholder** `assets/valentina-placeholder.svg`

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="480" height="560" viewBox="0 0 480 560" role="img" aria-label="Photo placeholder">
  <rect width="480" height="560" fill="#e7efee"/>
  <circle cx="240" cy="220" r="92" fill="#bcd3d1"/>
  <rect x="120" y="330" width="240" height="170" rx="90" fill="#bcd3d1"/>
  <text x="240" y="535" text-anchor="middle" font-family="Inter, sans-serif" font-size="20" fill="#3a7d7b">Photo of Valentina</text>
</svg>
```

- [ ] **Step 2: Add About markup** (replace `<!-- about: Task 3 -->`)

```html
<section id="about" class="section-alt">
  <div class="container about">
    <div class="about__photo">
      <!-- Replace src with assets/valentina.jpg once available -->
      <img src="assets/valentina-placeholder.svg" alt="Valentina Pupic" width="480" height="560" />
    </div>
    <div class="about__text">
      <h2>Hi, I'm Valentina.</h2>
      <p>
        I'm an incoming Nutrition student at the University of Guelph, and I love
        helping people feel connected and confident. I started the Tech &amp;
        Conversation Hour because so many older adults have stories to share and
        family they'd love to reach — and a little patient help with a phone or
        tablet goes a long way.
      </p>
      <p>
        Each visit is unhurried and friendly: a real conversation first, then
        whatever simple technology help would brighten someone's week.
      </p>
    </div>
  </div>
</section>
```

- [ ] **Step 3: Add About styles** (append to `styles.css`)

```css
.about {
  display: grid;
  grid-template-columns: 0.8fr 1.2fr;
  gap: 56px;
  align-items: center;
}

.about__photo img {
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  width: 100%;
  height: auto;
}

.about__text h2 { font-size: clamp(1.8rem, 4vw, 2.6rem); margin: 0 0 18px; }

.about__text p { color: var(--muted); margin: 0 0 16px; }

@media (max-width: 720px) {
  .about { grid-template-columns: 1fr; gap: 28px; }
  .about__photo { max-width: 320px; }
}
```

- [ ] **Step 4: Verify**

Reload. Expected: two-column About on desktop (placeholder image left, text right), stacking to one column on mobile with the image capped at 320px.

- [ ] **Step 5: (Optional) commit**

```bash
git add -A && git commit -m "feat: about section with photo placeholder"
```

---

### Task 4: The Tech & Conversation Hour (program) section

**Files:**
- Modify: `index.html` (replace `<!-- program: Task 4 -->`)
- Modify: `css/styles.css` (append)

**Interfaces:**
- Consumes: `.container`, tokens.
- Produces: `#program` landmark. Uses inline SVG icons (no external dependency).

- [ ] **Step 1: Add program markup** (replace `<!-- program: Task 4 -->`)

```html
<section id="program">
  <div class="container">
    <header class="section-head">
      <p class="eyebrow">The Tech &amp; Conversation Hour</p>
      <h2>A friendly weekly visit, built around the resident.</h2>
    </header>
    <div class="cards">
      <div class="card">
        <h3>What I offer</h3>
        <ul class="ticks">
          <li>One-hour weekly visits</li>
          <li>Friendly conversation and companionship</li>
          <li>Simple help with phones, tablets, photos, and video calls</li>
          <li>Gentle, safe introductions to new technology</li>
          <li>Patience, kindness, and consistency</li>
        </ul>
      </div>
      <div class="card card--accent">
        <h3>Ideal for residents who'd enjoy</h3>
        <ul class="ticks">
          <li>Social connection</li>
          <li>Learning basic technology</li>
          <li>Exploring family photos or video-calling loved ones</li>
          <li>Trying something new in a low-pressure setting</li>
        </ul>
      </div>
    </div>
  </div>
</section>
```

- [ ] **Step 2: Add program styles** (append to `styles.css`)

```css
.section-head { max-width: 680px; margin: 0 0 48px; }

.section-head h2 { font-size: clamp(1.8rem, 4vw, 2.6rem); margin: 8px 0 0; }

.cards {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 28px;
}

.card {
  background: var(--white);
  border: 1px solid rgba(31, 58, 95, 0.08);
  border-radius: var(--radius);
  padding: 32px;
  box-shadow: var(--shadow);
}

.card--accent { background: #f0f6f5; }

.card h3 { font-size: 1.4rem; margin: 0 0 18px; }

.ticks { list-style: none; margin: 0; padding: 0; }

.ticks li {
  position: relative;
  padding: 0 0 14px 30px;
  color: var(--ink);
}

.ticks li::before {
  content: "";
  position: absolute;
  left: 0;
  top: 9px;
  width: 14px;
  height: 8px;
  border-left: 2px solid var(--coral);
  border-bottom: 2px solid var(--coral);
  transform: rotate(-45deg);
}

@media (max-width: 720px) {
  .cards { grid-template-columns: 1fr; }
}
```

- [ ] **Step 3: Verify**

Reload. Expected: section heading, then two cards side by side (the second tinted), each with a checkmark list. Cards stack on mobile.

- [ ] **Step 4: (Optional) commit**

```bash
git add -A && git commit -m "feat: program section"
```

---

### Task 5: Why it matters strip

**Files:**
- Modify: `index.html` (replace `<!-- why it matters: Task 5 -->`)
- Modify: `css/styles.css` (append)

**Interfaces:**
- Consumes: `.container`, tokens.
- Produces: `#why` landmark. Copy is general/non-clinical per Global Constraints.

- [ ] **Step 1: Add markup** (replace `<!-- why it matters: Task 5 -->`)

```html
<section id="why" class="why">
  <div class="container why__inner">
    <h2>Why it matters</h2>
    <p>
      Loneliness is one of the quieter challenges of aging. A reliable, friendly
      hour each week — sharing a conversation, reaching family on a screen,
      learning something new — can make a real difference to how connected
      someone feels. That's the whole idea: intergenerational connection through
      technology.
    </p>
  </div>
</section>
```

- [ ] **Step 2: Add styles** (append to `styles.css`)

```css
.why { background: var(--navy); color: #eaf1f0; }

.why__inner { max-width: 760px; text-align: center; }

.why h2 { color: var(--white); font-size: clamp(1.8rem, 4vw, 2.6rem); margin: 0 0 18px; }

.why p { font-size: 1.2rem; color: #d6e2e1; margin: 0; }
```

- [ ] **Step 3: Verify**

Reload. Expected: a full-width navy band with centered white heading and light paragraph. Contrast is comfortable.

- [ ] **Step 4: (Optional) commit**

```bash
git add -A && git commit -m "feat: why-it-matters strip"
```

---

### Task 6: Contact section with Formspree form

**Files:**
- Modify: `index.html` (replace `<!-- contact: Task 6 -->`, then close `</main>`)
- Modify: `css/styles.css` (append)
- Modify: `js/main.js` (add async submit handler)

**Interfaces:**
- Consumes: `.container`, `.btn`, tokens; CTA target `#contact` from Task 1.
- Produces: `#contact` landmark; form posts to Formspree via fetch and shows an inline success message without leaving the page.

- [ ] **Step 1: Add contact markup** (replace `<!-- contact: Task 6 -->`)

```html
<section id="contact" class="section-alt">
  <div class="container contact">
    <header class="section-head">
      <p class="eyebrow">Get in touch</p>
      <h2>Interested in a visit? Let's talk.</h2>
      <p class="contact__note">
        For Recreation, Life Enrichment, and Volunteer Coordinators — and for
        families. Send a note and Valentina will reply by email.
      </p>
    </header>

    <form id="contactForm" class="form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
      <div class="form__row">
        <label for="name">Your name</label>
        <input id="name" name="name" type="text" required autocomplete="name" />
      </div>
      <div class="form__row">
        <label for="email">Your email</label>
        <input id="email" name="email" type="email" required autocomplete="email" />
      </div>
      <div class="form__row">
        <label for="role">I'm a…</label>
        <select id="role" name="role">
          <option>Recreation / Life Enrichment / Volunteer Coordinator</option>
          <option>Family member</option>
          <option>Other</option>
        </select>
      </div>
      <div class="form__row">
        <label for="message">Message</label>
        <textarea id="message" name="message" rows="5" required></textarea>
      </div>
      <button class="btn btn--primary" type="submit">Send message</button>
      <p id="formStatus" class="form__status" role="status" aria-live="polite"></p>
    </form>
  </div>
</section>
</main>
```

- [ ] **Step 2: Add form styles** (append to `styles.css`)

```css
.contact__note { color: var(--muted); margin: 8px 0 0; }

.form { max-width: 560px; }

.form__row { margin: 0 0 20px; }

.form label {
  display: block;
  font-weight: 600;
  color: var(--navy);
  margin: 0 0 8px;
}

.form input,
.form select,
.form textarea {
  width: 100%;
  padding: 12px 14px;
  border: 1px solid rgba(31, 58, 95, 0.2);
  border-radius: 10px;
  font-family: inherit;
  font-size: 1rem;
  background: var(--white);
}

.form input:focus,
.form select:focus,
.form textarea:focus {
  outline: 3px solid rgba(58, 125, 123, 0.4);
  outline-offset: 1px;
  border-color: var(--teal);
}

.form__status { margin: 14px 0 0; font-weight: 500; min-height: 1.4em; }

.form__status--ok { color: var(--teal); }

.form__status--err { color: var(--coral); }
```

- [ ] **Step 3: Add submit handler** (append inside the `DOMContentLoaded` callback in `js/main.js`, after the nav code)

```js
  const form = document.getElementById("contactForm");
  const status = document.getElementById("formStatus");
  if (form && status) {
    form.addEventListener("submit", async (e) => {
      e.preventDefault();
      status.textContent = "Sending…";
      status.className = "form__status";
      try {
        const res = await fetch(form.action, {
          method: "POST",
          body: new FormData(form),
          headers: { Accept: "application/json" },
        });
        if (res.ok) {
          form.reset();
          status.textContent = "Thank you — your message has been sent.";
          status.classList.add("form__status--ok");
        } else {
          status.textContent = "Something went wrong. Please try again later.";
          status.classList.add("form__status--err");
        }
      } catch {
        status.textContent = "Network error. Please try again later.";
        status.classList.add("form__status--err");
      }
    });
  }
```

- [ ] **Step 4: Verify (layout + validation)**

Reload. Expected: a tidy form (name, email, role dropdown, message, Send button). Submitting with empty required fields triggers the browser's built-in validation prompts.

- [ ] **Step 5: Verify (submission path)**

With the placeholder `YOUR_FORM_ID` still in place, fill the form and submit. Expected: status shows "Sending…" then the error message (the endpoint isn't real yet). This confirms the JS path works; real success comes after a Formspree ID is added per README.

- [ ] **Step 6: (Optional) commit**

```bash
git add -A && git commit -m "feat: contact form with formspree handler"
```

---

### Task 7: Footer and final polish

**Files:**
- Modify: `index.html` (replace `<!-- footer: Task 7 -->`)
- Modify: `css/styles.css` (append)

**Interfaces:**
- Consumes: `.container`, tokens.
- Produces: `<footer>` with the brand availability line.

- [ ] **Step 1: Add footer markup** (replace `<!-- footer: Task 7 -->`)

```html
<footer class="site-footer">
  <div class="container site-footer__inner">
    <p class="site-footer__brand">Valentina Pupic</p>
    <p class="site-footer__line">Available for retirement homes, seniors' residences, and community programs.</p>
  </div>
</footer>
```

- [ ] **Step 2: Add footer styles** (append to `styles.css`)

```css
.site-footer { background: var(--cream); border-top: 1px solid rgba(31, 58, 95, 0.1); padding: 40px 0; }

.site-footer__inner { text-align: center; }

.site-footer__brand { font-family: var(--font-head); color: var(--navy); font-weight: 600; font-size: 1.2rem; margin: 0 0 6px; }

.site-footer__line { color: var(--muted); margin: 0; }
```

- [ ] **Step 3: Final full-page review**

Open `index.html` and scroll top to bottom. Checklist:
- Header sticks; all three nav links scroll to their sections.
- Sections in order: hero, about, program, why, contact, footer.
- No phone number anywhere; no plain-text email in page source (View Source -> search "@" and "647").
- No console errors.
- Resize to mobile width: nav collapses, all sections stack cleanly.

- [ ] **Step 4: (Optional) commit**

```bash
git add -A && git commit -m "feat: footer and final polish"
```

---

## Post-build handoff (not code tasks)

These are done by Valentina/owner, documented in `README.md`:
1. Add real photo: save as `assets/valentina.jpg`, update the `<img src>` in the About section.
2. Create a free Formspree form, replace `YOUR_FORM_ID` in the form `action`, and submit a real test message.
3. Deploy to GitHub Pages or Netlify; put the resulting URL on the poster.
