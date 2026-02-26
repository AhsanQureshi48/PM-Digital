# PM-Digital — Revive DTC Theme

Shopify theme deliverables for **Revive** (DTC supplement brand): custom PDP Bundle Banner section (Task 1) and A/B test setup in **Intelligems** (Task 2).

---

## Table of contents

- [Task 1 — Bundle Banner Section](#task-1--bundle-banner-section)
- [Task 2 — A/B Test Setup](#task-2--ab-test-setup)
- [Quick Reference](#quick-reference)

---

## Task 1 — Bundle Banner Section

Standalone Shopify section that displays a benefit-led banner at the top of product pages: headline with accent highlight (e.g. “save 30%.”), subheading, CTA button, and product/bundle imagery. Matches the Revive 30% off Bundle Banner design at **1440px (desktop)** and **390px (mobile)**.

### Files

| Purpose | Path |
|--------|------|
| Section (Liquid) | `sections/bundle-banner.liquid` |
| Styles (CSS) | `assets/section-bundle-banner.css` |
| Product template | `templates/product.json` |

### Approach

- **Mobile-first CSS:** Base styles for mobile; desktop layout and spacing via `min-width: 750px` (and `min-width: 1200px` for large desktop).
- **Mobile-first `<picture>`:** Default `<img>` uses the mobile product image; `<source media="(min-width: 750px)">` serves the desktop image when both desktop and mobile images are set in the schema.
- **Vanilla only:** No CSS frameworks; no jQuery; semantic HTML and appropriate `alt` attributes on images.

### Behaviour

- **Layout:** Mobile — image on top, text below (with gradient behind text). Desktop (750px+) — text left, image right.
- **Mobile gradient:** On mobile only, `.bundle-banner__text` has a vertical linear gradient `rgba(8, 45, 53, 0)` → `rgba(8, 45, 53, 1)` for text readability.
- **Product image:** Schema supports separate **desktop** and **mobile** images; when both are set, `<picture>` switches by viewport.

### Schema (Theme Editor)

- **Content:** Heading, Heading highlight (accent), Subheading, CTA label, CTA link (collection or custom URL).
- **Media:** Background image (optional), Product image (desktop), Product image (mobile, optional).
- **Colors:** Background, Text, Accent.
- **Section padding:** Top/Bottom for desktop and mobile.

To add the section: Theme Editor → Product page → Add section → **Bundle Banner**.

---

## Task 2 — A/B Test Setup

The test is configured in **Intelligems** on the dev store.

### Test configuration

| Item | Setup |
|------|--------|
| **Control** | Existing hero section on a PDP (product page without the bundle banner). |
| **Variation** | Bundle banner section from Task 1 (PDP with the bundle banner at top). |
| **Target** | Product pages only (not homepage or collection pages). |
| **Primary metric** | Add-to-cart rate. |
| **Secondary metric** | Revenue per session. |
| **Traffic split** | 50/50. |

### Hypothesis

We believe that replacing the generic hero section on PDPs with a benefit-led bundle banner (30% off savings and a clear CTA to the bundles collection) will increase add-to-cart rate and AOV by making the bundle value proposition more prominent earlier in the purchase journey.

### Setup in Intelligems

1. **Create test:** Apps → Intelligems → A/B Tests → Create New Test → Content Test → Template Test.
2. **Control:** Assign the product template that shows the existing PDP (no bundle banner).
3. **Variation:** Assign the product template that includes the Bundle Banner section at the top.
4. **Targeting:** Product pages only (e.g. URL contains `/products/` or template = product).
5. **Metrics:** Primary = Add-to-cart rate; Secondary = Revenue per session.
6. **Traffic:** 50/50 split. Save and start the test.

---

## Quick Reference

| Item | Location |
|------|----------|
| Bundle banner section | `sections/bundle-banner.liquid` |
| Bundle banner CSS | `assets/section-bundle-banner.css` |
| Product template (with banner) | `templates/product.json` |
| A/B test | Intelligems (installed on store) |
