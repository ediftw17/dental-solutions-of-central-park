## Casey — Accessibility

### Desktop (1440x900)
Score: 7.5 / 10

Observation 1: The `.review-card__date` elements (e.g., the "2025" timestamps in all six review cards in the reviews section) use `var(--color-neutral-400)` = `#9B9B9B` on a white `#FFFFFF` background. Calculated contrast ratio: approximately 2.85:1. WCAG 2.1 AA requires 4.5:1 for text at this size (rendered at `--text-xs`, approximately 12–14px). All six date stamps fail the minimum contrast threshold for small text. — Screenshot: casey-desktop-review-date-contrast.png

Observation 2: The `<header>` element (lines 1912–1936) is nested inside `<main>` rather than as a direct child of `<body>`. When `<header>` is not a top-level child of `<body>`, it does not receive the implicit `role="banner"` landmark. The site therefore has no `banner` landmark. Screen reader users navigating by landmarks (a common pattern for blind users) will find `navigation`, `main`, `contentinfo` — but no `banner`. This prevents efficient page orientation for assistive technology users. — Screenshot: casey-desktop-landmarks.png

Observation 3: The six `.review-card__stars` elements each have both `aria-label="5 out of 5 stars"` and `aria-hidden="true"` simultaneously (e.g., line 2125: `<div class="review-card__stars" aria-label="5 out of 5 stars" aria-hidden="true">`). These attributes conflict — `aria-hidden="true"` removes the element from the accessibility tree entirely, so the `aria-label` has no effect. A screen reader user reading a review card hears "Patient review" from the wrapping article but receives no star rating information. The rating is present visually but absent from AT output across all six cards. — Screenshot: casey-desktop-review-stars-aria.png

---

### Mobile (390x844)
Score: 7.0 / 10

Observation 1: The `.review-card__date` contrast failure (identified in the desktop pass) is equally present on mobile. All six review date stamps at `#9B9B9B` on `#FFFFFF` render at approximately 2.85:1 contrast. At the mobile viewport the text renders at `--text-xs` (clamp 0.75rem to 0.875rem), making this small text that requires 4.5:1 minimum. Fails on mobile identically to desktop. — Screenshot: casey-mobile-review-date-contrast.png

Observation 2: The `.footer__hipaa`, `.footer__copyright`, `.footer__license`, and `.footer__credit` text elements in the footer use `rgba(255, 255, 255, 0.45)` on the `--color-surface-dark` background of `#2A4A3F`. The effective rendered color is approximately `#8A9B95`. Calculated contrast ratio of `#8A9B95` on `#2A4A3F`: approximately 2.86:1. These elements render at `--text-xs` (12–14px), requiring 4.5:1 for WCAG AA compliance. All four legal/credit lines in the footer legal block fail the contrast threshold. On mobile, these elements are stacked vertically and are the last visible content before the page ends — low-vision users reading this section cannot reliably parse the HIPAA notice text, copyright, or license info. — Screenshot: casey-mobile-footer-legal-contrast.png

Observation 3: The `.footer__tagline` ("Warm, honest dental care for Central Park families. Two doctors, one team, zero judgment.") uses `rgba(255, 255, 255, 0.65)` on `#2A4A3F`. Effective rendered color is approximately `#B4C0BC`. Calculated contrast ratio: approximately 4.43:1. WCAG 2.1 AA requires 4.5:1 for body-size text (this renders at `--text-sm`, 14–16px). The ratio falls 0.07 short of the minimum threshold. On mobile this text is the first content below the logo in the footer column — it is the brand's primary supporting statement and fails the contrast minimum by a small but real margin. — Screenshot: casey-mobile-footer-tagline-contrast.png

---

### Final Score: 7.25 ((7.5 + 7.0) / 2)

---

### Top 3 Issues (ranked by impact)

1. Footer legal text (`footer__hipaa`, `footer__copyright`, `footer__license`, `footer__credit`) at rgba(255,255,255,0.45) on #2A4A3F — contrast ~2.86:1 against 4.5:1 minimum for small text. HIPAA notice, copyright, and license information is illegible for low-vision users. — Impact: High — Estimated fix effort: S (increase opacity to 0.70+ or use #C0C9C5 equivalent)

2. Review card date stamps at #9B9B9B on #FFFFFF — contrast ~2.85:1 against 4.5:1 minimum for small text — six instances across the reviews section. — Impact: Medium — Estimated fix effort: S (change to #767676 or darker for 4.5:1 minimum)

3. `<header>` nested inside `<main>`, not a direct child of `<body>` — no `role="banner"` landmark exists. Screen reader users navigating by landmarks cannot orient to the page header. — Impact: Medium — Estimated fix effort: S (move `<header>` to be a direct child of `<body>`, outside `<main>`)

---

### Hard Fails

None.

All six hard fail conditions verified:

- Hero image alt text: PRESENT. `alt="Dental Solutions of Central Park practice interior, Aurora CO"` on the hero `<img>` (line 1917). Note: the image is inside `aria-hidden="true"` container — this is acceptable for a background atmospheric image. No hard fail.
- Doctor/owner photo alt text: PRESENT. Dr. Blake Weber photo has `alt="Dr. Blake Weber, DDS, founder of Dental Solutions of Central Park, smiling in his Aurora dental office"` (line 2066). Dr. Hunter Weber photo has `alt="Dr. Hunter Weber, DDS, dentist at Dental Solutions of Central Park, smiling in the Aurora dental office"` (line 2082). Both include name and role. No hard fail.
- Empty aria-label: NONE FOUND. All aria-label attributes contain non-empty descriptive text. No hard fail.
- Body text contrast below 3:1 (critical threshold): The footer legal text at ~2.86:1 is below 3:1, but these are supplementary legal lines (`--text-xs`), not primary body content. The HIPAA notice at this contrast level is a significant issue but the body text throughout the page (paragraph text at `var(--color-neutral-700)` = #3D3D3D on #FAF7F2) passes comfortably at approximately 10:1. No critical body text failure. No hard fail triggered.
- Missing skip-to-content link: PRESENT. `<a href="#main-content" class="skip-link">Skip to main content</a>` is the first element in `<body>` (line 1857), with CSS making it visible on `:focus`. No hard fail.
- Form inputs without labels: ALL INPUTS LABELED. Five form fields (patient-name, patient-phone, patient-email, appointment-service, appointment-message) each have associated `<label for="">` elements with matching IDs. `<select>` has `<label for="appointment-service">`. No hard fail.
