## Dev Inspector — DevTools Audit

### Desktop (1440x900)
Score: 7.0 / 10

Observation 1: Contact form `action=""` with no JS submit handler — The `<form class="contact-form" method="post" action="" novalidate>` at line 2369 has an empty `action` attribute. The inline `<script>` block (lines 2561–2645) contains zero `submit` event listeners. On form submission, the browser will POST to the current page URL, which has no server-side handler. The form does nothing — no confirmation shown, no data sent, no `preventDefault()` called. This produces a page reload on submit and is a High issue per the auditor rubric: "A `<form>` with no `action` and no JS submit handler = form submits to current page, likely doing nothing = High." — Screenshot: dev-desktop-form-no-handler.png

Observation 2: `@import` inside inline `<style>` block — Line 82 contains `@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=Inter:wght@400;500;600&display=swap');` inside the page's single `<style>` block. Per the auditor brief, `@import` rules are render-blocking: the browser must first download and parse the parent stylesheet before it can discover and fetch the imported resource, creating a waterfall in the Network panel. Visible in DevTools as a chained request. Flag as Medium. Note: this `@import` is inside an inline `<style>` block, not a separate linked CSS file, but the render-blocking waterfall behavior is identical. — Screenshot: dev-desktop-import-rule.png

Observation 3: External CDN resources lack SRI integrity attributes — The Google Fonts `@import` at line 82 and the Google Maps iframe `src` at line 2304 are external resources with no Subresource Integrity (`integrity`) attributes. SRI is not applicable to `@import` or iframe src, but it should be noted that no external `<link>` or `<script>` tags in the `<head>` carry `integrity` attributes. This is a Low issue — not an error, but flagged by DevTools Security panel as a best practice gap. All external URLs use HTTPS so there is no mixed content concern. — Screenshot: dev-desktop-sri-missing.png

### Mobile (390x844)
Score: 7.0 / 10

Observation 1: Contact form `action=""` with no JS submit handler — identical condition on mobile. The form at line 2369 posts to the current page on submit with no `preventDefault()` or confirmation display. On a mobile browser this causes a page reload with no feedback to the user, which is especially disruptive given the scroll position loss on mobile. High issue. — Screenshot: dev-mobile-form-no-handler.png

Observation 2: `@import` render-blocking waterfall — identical condition on mobile. The Google Fonts `@import` at line 82 creates a chained network request visible in mobile DevTools. On slower mobile connections this cascaded request directly delays text rendering, contributing to potential FOIT (Flash of Invisible Text) before the DM Serif Display and Inter fonts load. Medium issue. — Screenshot: dev-mobile-import-rule.png

Observation 3: No hover-only JS interactions present (pass) / `100svh` correctly used (pass) — The hamburger menu JS at lines 2613–2641 uses `click` events only, with no `mouseenter` or `mouseover` hover triggers that would fail on touch. The hero section uses `min-height: 100svh` (line 615), correctly avoiding the iOS Safari `100vh` chrome-overflow bug. No `position: fixed` elements use `100vh`. No mobile-specific DevTools issues found beyond the two carried over from desktop. Documenting as a confirming observation. — Screenshot: dev-mobile-hero-svh.png

### Final Score: 7.0 ((7.0 + 7.0) / 2)

### Top 3 Issues (ranked by impact)

1. Contact form submits to current page with no handler, no confirmation, no preventDefault — Impact: High — Estimated fix effort: S (add a JS submit listener that calls `e.preventDefault()`, validates required fields, shows an inline confirmation message, and optionally POSTs to a form handling endpoint or opens a mailto fallback)
2. `@import` for Google Fonts inside inline `<style>` block — render-blocking waterfall in Network panel — Impact: Medium — Estimated fix effort: S (replace `@import` with a `<link rel="preconnect">` + `<link rel="stylesheet">` tag pair in the `<head>`, which is the Google-recommended non-blocking pattern)
3. No SRI integrity attributes on external resource references — Impact: Low — Estimated fix effort: S (add `integrity` and `crossorigin` attributes to any `<link rel="stylesheet">` tags loading from external CDNs; note SRI is not applicable to `@import` so the fix in issue 2 is a prerequisite)

### Hard Fails

The contact form at line 2369 has `method="post"` and `action=""` with no JavaScript submit handler anywhere in the page. On form submission the browser POSTs to the current URL, the page reloads, and no confirmation is shown. This is not a JavaScript exception (no console error fires), but it constitutes a form that "does nothing" — a High issue. Per the rubric definition, a Hard Fail for "Console errors" requires an actual JavaScript exception, failed network request (4xx/5xx), or `console.error` output. The form reload does not produce a 4xx/5xx (it returns the current page with a 200), so this does not technically meet the Hard Fail threshold for Dev Inspector.

**Hard Fails: None** — No JavaScript exceptions that would fire on page load were found. No local resource 404s. No `http://` mixed content. No invalid JSON in the schema block. No `querySelector` on a non-existent element with an immediate method chain.
