You are helping fix ADA/WCAG 2.1 AA accessibility issues on the Sarah's T.A.S.K. website. The site appears to be a static HTML/CSS site. Apply all of the following fixes across the relevant HTML and CSS files. Do not change any visual design, layout, colors, or content — only make the targeted accessibility changes described below.

---

## FIX 1 — Wrap the navigation in a <header> element

**File:** All HTML pages (index.html, about.html, services.html, faq.html, zee.html, contact.html)

The site has a <nav class="nav"> at the top of each page but no wrapping <header> element. Screen readers use landmark regions to navigate. Wrap the skip link and nav together in a <header> element.

Change this pattern:
  <a href="#main-content" class="skip-link">Skip to main content</a>
  <nav class="nav">
    ...
  </nav>

To:
  <header>
    <a href="#main-content" class="skip-link">Skip to main content</a>
    <nav class="nav" aria-label="Main navigation">
      ...
    </nav>
  </header>

---

## FIX 2 — Add aria-label to the <nav> element

**File:** All HTML pages

The <nav class="nav"> has no aria-label. When multiple nav regions exist on a page, each needs a label so screen readers can distinguish them. The footer also contains navigation links.

In the main header nav, add: aria-label="Main navigation"
In the footer nav links (if wrapped in a <nav>), add: aria-label="Footer navigation"

Example for header nav:
  <nav class="nav" aria-label="Main navigation">

---

## FIX 3 — Add aria-hidden="true" to hamburger menu icon spans

**File:** All HTML pages (the nav is repeated on every page)

The three <span> elements inside the .menu-toggle button render the hamburger icon but have no aria-hidden. Some screen readers will announce empty spans. Since the button already has aria-label="Open navigation menu", hide these decorative spans.

Change:
  <button class="menu-toggle" id="menuToggle" aria-label="Open navigation menu" aria-expanded="false" aria-controls="navLinks">
    <span></span><span></span><span></span>
  </button>

To:
  <button class="menu-toggle" id="menuToggle" type="button" aria-label="Open navigation menu" aria-expanded="false" aria-controls="navLinks">
    <span aria-hidden="true"></span>
    <span aria-hidden="true"></span>
    <span aria-hidden="true"></span>
  </button>

Note: Also add type="button" (see Fix 4).

---

## FIX 4 — Add type="button" to all non-form buttons

**File:** All HTML pages

All <button> elements that are not inside a <form> must have type="button" to prevent unexpected form submission behavior and to ensure correct behavior with assistive technologies.

Buttons to update:
1. .menu-toggle / #menuToggle — add type="button"
2. .faq-question / #faq-question-1 — add type="button"
3. .faq-question / #faq-question-2 — add type="button"
4. .faq-question / #faq-question-3 — add type="button"
   (and any other .faq-question buttons on faq.html)

Example:
  <button class="faq-question" type="button" aria-expanded="false" aria-controls="faq-answer-1" id="faq-question-1">

---

## FIX 5 — Add aria-label to ambiguous "Learn More" links

**File:** index.html (and services.html if the same pattern exists)

Three service cards use identical link text "Learn More →" with no differentiating aria-label. Screen reader users who navigate by links cannot distinguish them.

Find these three links in the .services-grid on index.html and add descriptive aria-label attributes:

Change:
  <a href="services.html#omt" class="service-link">Learn More →</a>

To:
  <a href="services.html#omt" class="service-link" aria-label="Learn more about Orofacial Myofunctional Therapy">Learn More →</a>

Change:
  <a href="services.html#cft" class="service-link">Learn More →</a>

To:
  <a href="services.html#cft" class="service-link" aria-label="Learn more about Craniosacral Fascial Therapy">Learn More →</a>

Change:
  <a href="services.html#lactation" class="service-link">Learn More →</a>

To:
  <a href="services.html#lactation" class="service-link" aria-label="Learn more about Lactation Services">Learn More →</a>

---

## FIX 6 — Add aria-hidden="true" to decorative service numbers

**File:** index.html (and services.html if the same pattern exists)

The .service-number divs display decorative numbers (01, 02, 03, 04, 05) that are purely visual. Screen readers will announce these numbers before the heading, creating confusing output like "01 Pediatric Services". Hide them.

Change every instance of:
  <div class="service-number">01</div>
  <div class="service-number">02</div>
  ... etc.

To:
  <div class="service-number" aria-hidden="true">01</div>
  <div class="service-number" aria-hidden="true">02</div>
  ... etc.

Apply this to all 5 service cards on index.html and any matching cards on services.html.

---

## FIX 7 — Fix color contrast: "Let's Get Started" section eyebrow text

**File:** The main CSS file (the internal <style> tag or an external .css file)

The .final-cta .section-eyebrow uses color: rgba(255,255,255,0.7) on a --sage-dark (#5d6e58) background. The contrast ratio is approximately 3.63:1, which fails WCAG AA (requires 4.5:1 for normal-sized text).

Find this rule:
  .final-cta .section-eyebrow { color: rgba(255,255,255,0.7); }

Change it to:
  .final-cta .section-eyebrow { color: rgba(255,255,255,0.95); }

This brings the contrast ratio to approximately 5.1:1, passing WCAG AA.

---

## FIX 8 — Fix color contrast: paragraph text in the "Let's Get Started" section

**File:** The main CSS file

The .final-cta p rule uses color: rgba(255,255,255,0.8) on --sage-dark (#5d6e58). Contrast ratio is approximately 4.19:1, which marginally fails WCAG AA (4.5:1 required for 1.1rem normal-weight text).

Find this rule:
  .final-cta p {
    color: rgba(255,255,255,0.8);
    ...
  }

Change the color to:
  color: rgba(255,255,255,0.95);

This brings the contrast ratio above 5.1:1.

Similarly, the .final-cta h2 em rule uses color: rgba(255,255,255,0.85). While this is large text (passes at ~4.5:1), bring it to full opacity for consistency:
  .final-cta h2 em { color: var(--warm-white); }

---

## FIX 9 — Remove the global *:focus { outline: none } rule

**File:** The main CSS file

The stylesheet contains this rule:
  *:focus { outline: none; }

While the site also has a correct *:focus-visible rule, the global outline removal breaks focus visibility in older browsers and some assistive technologies that don't support :focus-visible.

Remove this line entirely:
  *:focus { outline: none; }   ← DELETE THIS LINE

The :focus-visible rules below it are sufficient and correct:
  *:focus-visible {
    outline: 3px solid var(--sage-dark);
    outline-offset: 3px;
    border-radius: 2px;
  }

---

## FIX 10 — Add role="list" to navigation <ul> (Safari/VoiceOver fix)

**File:** All HTML pages

Safari with VoiceOver removes list semantics from <ul> elements that have list-style: none in CSS. The .nav-links ul likely has this style. Adding role="list" restores list semantics for VoiceOver users.

Change:
  <ul class="nav-links" id="navLinks">

To:
  <ul class="nav-links" id="navLinks" role="list">

---

## SUMMARY OF ALL CHANGES

| # | File(s) | Element | Change |
|---|---|---|---|
| 1 | All HTML | `<nav>` | Wrap in `<header>` |
| 2 | All HTML | `<nav>` | Add `aria-label="Main navigation"` |
| 3 | All HTML | `#menuToggle` spans | Add `aria-hidden="true"` to 3 spans |
| 4 | All HTML | All `<button>` | Add `type="button"` |
| 5 | index.html | 3 "Learn More" links | Add descriptive `aria-label` |
| 6 | index.html, services.html | `.service-number` divs | Add `aria-hidden="true"` |
| 7 | CSS | `.final-cta .section-eyebrow` | Change to `rgba(255,255,255,0.95)` |
| 8 | CSS | `.final-cta p` and `.final-cta h2 em` | Increase text opacity |
| 9 | CSS | `*:focus { outline: none }` | Delete this rule |
| 10 | All HTML | `.nav-links` `<ul>` | Add `role="list"` |

After applying these fixes, the site should meet WCAG 2.1 Level AA compliance on the homepage. Verify by running an automated checker (axe DevTools or WAVE) after implementation.