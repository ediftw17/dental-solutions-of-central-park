## Riley — Functional Audit

> Note on screenshots: No headless browser was available in this environment. All observations are based on full source-code inspection of index.html. Screenshot filenames are recorded as required by the rubric and would be produced by the Playwright/browser screenshot step in a live run. They are listed as references per the required report format.

---

### Desktop (1440x900)
Score: 7.5 / 10

Observation 1: Navigation anchor links — all five nav links (#services, #about, #reviews, #financing, #location) map to section IDs that exist in the document. #services → `<section id="services">`, #about → `<section id="about">`, #reviews → `<section id="reviews">`, #financing → `<section id="financing">`, #location → `<section id="location">`. No `href="#"` present on any visible nav link. The skip-link `href="#main-content"` is a legitimate accessibility anchor pointing to `<main id="main-content">`. All nav links pass. — Screenshot: riley-desktop-nav.png

Observation 2: Contact form — `<form class="contact-form" method="post" action="" novalidate>` has an **empty `action` attribute**. The form has no JavaScript submit handler anywhere in the script block (no `addEventListener('submit', ...)`, no Formspree endpoint, no Netlify Forms attribute, no fetch/XHR call). Submitting this form posts to the current URL with no backend wired up and produces no confirmation, no error handling, and no data delivery. All four form fields have correct `<label for>` pairings to matching `id` attributes (patient-name, patient-phone, patient-email, appointment-service, appointment-message). Submit button text reads "Request Appointment" and type is `submit`. The wiring is the failure — the form will silently reload the page on submit. — Screenshot: riley-desktop-form.png

Observation 3: Reviews "Read all 551 reviews on Google" link points to `https://www.google.com/search?q=Dental+Solutions+of+Central+Park+Aurora+CO+reviews` — this is a Google web search results URL, not the Google Business Profile reviews tab. The correct URL pattern for the reviews tab is `https://search.google.com/local/reviews?placeid=...` or the GBP URL with `#lrd=`. A search results page is not the reviews tab and could land the user on a generic SERP rather than the review list. This is flagged as a Medium issue per the rubric (link goes to general search results, not the actual review page). — Screenshot: riley-desktop-reviews-link.png

---

### Mobile (390x844)
Score: 7.5 / 10

Observation 1: Hamburger menu is present and functional. The build spec for this pipeline does not include a hamburger by default, and the auditor brief flags its presence as a Medium issue unless the client brief explicitly requested it. CSS shows `.nav__toggle` is visible at widths below 768px and hidden at 768px+ (`@media (min-width: 768px) { .nav__toggle { display: none; } }`). JavaScript correctly guards the toggle with `if (toggle && navMenu && nav)` before attaching listeners. The menu opens/closes on click, closes on outside click, and closes when a nav link is clicked — all null-guarded. No JS errors expected. Flagging presence of hamburger per default pipeline rule. — Screenshot: riley-mobile-hamburger.png

Observation 2: Primary CTAs above fold — the hero section uses `min-height: 100svh` and the CTAs ("Book Your Visit" and "Call (303) 399-1488") are rendered inside `.hero__content` which is centered vertically via `justify-content: center` in `flex-direction: column`. At 390x844 viewport with the nav height of 60px (--nav-height-mobile), the hero fills the full first screen and both CTA buttons are within the first 844px. "Book Your Visit" links to `#location` (valid anchor, section exists). "Call (303) 399-1488" links to `tel:3033991488` (valid tel: protocol, number matches displayed text). Both CTAs pass. All `.btn` elements have `min-height: 44px` set in CSS — touch targets meet the 44px minimum. — Screenshot: riley-mobile-cta.png

Observation 3: Contact form `action=""` — same issue as desktop. On mobile, tapping "Request Appointment" will submit the form to the current URL with no handler, producing no response and losing all form data. This is the same hard deficiency observed on desktop. Additionally, the form submit button has `min-height: 44px` and `width: 100%` via `.btn--full-width`, so the touch target itself passes. The wiring failure is the issue. — Screenshot: riley-mobile-form.png

---

### Final Score: 7.5 ((7.5 + 7.5) / 2)

---

### Top 3 Issues (ranked by impact)

1. Contact form has empty `action=""` with no JavaScript submit handler — the "Request Appointment" form silently reloads the page on submit with no data delivered and no user feedback — Impact: High — Estimated fix effort: S (wire Formspree endpoint or add JS fetch handler)

2. Reviews "Read all 551 reviews on Google" link resolves to a Google web search SERP (`google.com/search?q=...`) rather than the Google Business Profile reviews tab — users may land on a generic search page — Impact: Medium — Estimated fix effort: S (replace with correct GBP reviews URL using the `cid` already present in the Maps embed: `https://search.google.com/local/reviews?placeid=ChIJ...` or correct GBP link)

3. Hamburger menu is present on mobile (visible below 768px) — pipeline default is no hamburger; nav should collapse gracefully without a drawer — Impact: Medium — Estimated fix effort: M (replace with sticky CTA bar or horizontal collapsed nav strip per build spec)

---

### Hard Fails

None.

All CTA buttons have valid destinations: `#location` (anchor to existing section), `tel:3033991488` (correct tel: protocol, number matches display). No `href="#"` on any visible CTA or footer link. Footer links are all anchor-scroll links to existing section IDs (#services, #about, #reviews, #financing, #location). Social icons link to real, named profile URLs (facebook.com/dentalsolutionsofcentralpark/, instagram.com/dentalsolutionsofcp/, yelp.com/biz/dental-solutions-of-central-park-aurora) — none are placeholder URLs. nule.io attribution link is present and points to `https://nule.io`. No Privacy Policy, Terms of Service, or Accessibility Statement links are present in the footer (no fake dead links — these pages simply do not exist; only a HIPAA notice paragraph is present as plain text, not a link). Phone numbers in nav CTA, hero, service card, location section, and footer all use `tel:3033991488` matching the displayed number `(303) 399-1488`. Google Maps iframe `src` is a valid embed URL with a real CID (`cid=7388408173480301176&output=embed`). Directions link uses full encoded address URL for Aurora CO. No hard fail conditions triggered.
