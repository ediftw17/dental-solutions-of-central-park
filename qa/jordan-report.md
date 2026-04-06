# Jordan — Visual/UX

**Site:** Dental Solutions of Central Park — index.html
**Niche:** Dental (warm, calm, trust-first)
**Audited:** 2026-04-06
**Auditor weight:** 1.25x

---

## Niche Calibration Applied

Before scoring: loaded dental niche profile. Expected palette — sage green #3D6B5E primary, champagne gold #C4973B accent, linen #FAF7F2 background. Expected typography — DM Serif Display headings, Inter body, 17-18px minimum body, generous line-height (1.65-1.75). Expected hero — real doctor photo (face fully visible, warm lighting, in-office setting). Expected section order — hero > stats > services > about > reviews > why-us > financing > location > footer. Expected aesthetic — warm without clinical, approachable serif, human-first.

---

## Desktop (1440x900)

**Score: 8.5 / 10**

**Observation 1:** Hero headline "The Only Dentist You'll Actually Look Forward to Visiting" is set in DM Serif Display at the clamp(2.5rem, 2.00rem + 2.50vw, 4rem) scale — resolves to approximately 56-64px at 1440px viewport. Combined with the eyebrow "Aurora's Father & Son Dental Team" in Inter 500 weight and gold accent color, the reading order is clean: eyebrow → headline → subheadline → dual CTAs. Hierarchy passes the 5-second identification test comfortably. Business name is visible in the nav logo, service is clear from headline, contact is in the nav CTA button ("Call (303) 399-1488") in the gold accent color — all above the fold. — Screenshot: jordan-desktop-hero.png

**Observation 2:** The hero uses `assets/hero.jpg` (sourced as a background image on the full-bleed hero section) with a 135-degree gradient overlay — sage green at 75% opacity blending to near-black at 40%. The overlay is well-calibrated: enough coverage to ensure white text passes contrast but not so heavy that the underlying photo loses all warmth. The hero does NOT feature a doctor's face as the primary visual — it uses the practice interior per the image reference. Per the niche profile, the ideal hero features the doctor in-person (face visible). However the hero copy introduces both doctors by name immediately ("Dr. Blake and Dr. Hunter Weber"), and both doctors are photographed with fully visible faces in the About section with descriptive alt text. This is a mild niche gap — the hero is interior-led rather than doctor-led — but not a hard fail given the immediate personal copy and the doctor photos appearing in section 4. Deducting 0.5 for missing doctor face in the hero. — Screenshot: jordan-desktop-hero-doctor-presence.png

**Observation 3:** Color palette execution is on-spec. All section backgrounds alternate correctly between --color-neutral-50 (#FAF7F2 linen) and --color-neutral-100 (#F0EDE7 deeper linen) — services and why-us on linen, about and reviews on the deeper linen, financing on sage green primary (#3D6B5E). The stats bar uses sage green as its background with champagne gold for stat values — visually strong. The financing section reverses out to white text on sage green with a gold CTA button, creating the right punctuation break. No cold grays, no clinical blues — full palette compliance. CTA buttons across all sections use btn--primary with --color-accent (#C4973B gold) consistently. No variance in button style detected. Border-radii on service cards (radius-xl = 1.5rem), doctor cards (radius-xl), and review cards (radius-lg = 1rem) are intentionally graduated by card importance — acceptable hierarchy, not inconsistency. — Screenshot: jordan-desktop-palette-consistency.png

**Observation 4:** Doctor cards in the About section (desktop 1024px+ breakpoint) switch to flex-direction: row with the photo at 220px width and aspect-ratio 3/4. The `object-position: center top` on `.doctor-card__img` is correctly set — faces will anchor to the top of the cropped area rather than centering, which is the correct behavior for portrait-oriented doctor photos. At 1440px, the two doctor cards sit side by side in a 2-column grid. This layout reads as polished and intentional. Text hierarchy within the card — name (Inter 600 at h3 scale), credentials (Inter 500 sage green, text-sm), and story paragraph (Inter 400 at text-base, 1.75 line-height) — is clean and progressive. — Screenshot: jordan-desktop-about-doctors.png

**Observation 5:** The stats bar renders as a 4-column grid at 768px+. The "Father & Son" stat item uses a string value ("Father & Son") where the other three use numerics — this creates a visual break in the rhythm since the DM Serif Display headline font at h2 scale renders the string at a different visual weight than numbers. Minor inconsistency: the 4th stat reads "Father & Son / Dr. Blake & Dr. Hunter Weber" which wraps to two lines, while the other three stats are single-line values. At 1440px this is readable but breaks the grid's visual uniformity. — Screenshot: jordan-desktop-stats-fourth-item.png

**Observation 6:** Whitespace is generous throughout. Section padding uses `clamp(5rem, 8vw, 8rem)` at 1440px — sections breathe without feeling sparse. The 6-card services grid at 1024px+ renders as 3 columns with --space-8 (2rem) gap. Service card copy is appropriately detailed but not dense. The financing section's two-column layout places insurance on the left and financing options on the right — the gold CTA ("Ask About Financing") sits below the financing copy with margin-top: space-6, giving it room. No sections feel compressed or rushed. — Screenshot: jordan-desktop-whitespace.png

---

## Mobile (390x844)

**Score: 8.0 / 10**

**Observation 1:** Hero on mobile: the `.section--hero` is set to `min-height: 100svh` with padding-top of nav-height-mobile (60px). At 390x844, the hero content column renders headline, subheadline, and CTAs fully above the fold — the two CTA buttons stack vertically (`flex-direction: column` on `.hero__ctas` at mobile) and are both min-height 52px with min-width 180px. Primary CTA ("Book Your Visit") and secondary ("Call (303) 399-1488") are visible without scrolling. The hero headline clamps down appropriately at 390px — at the low end of the `clamp(2.5rem, 2.00rem + 2.50vw, 4rem)` scale, it resolves to approximately 40px, which wraps the 10-word headline to 3 lines but remains fully legible without orphan issues. CTA above the fold confirmed. — Screenshot: jordan-mobile-hero.png

**Observation 2:** Stats bar on mobile renders as a 2x2 grid (`grid-template-columns: repeat(2, 1fr)` — the default before the 768px breakpoint). At 390px, the 4 stats split into 2 columns. The "Father & Son" item with the longer label line wraps to 3 lines within its grid cell, while the other three items are 2 lines (value + label). This creates a ragged bottom edge on the stats row — the two items in the second row sit at different heights. The visual disruption is low-severity but noticeable. A min-height on `.stats__item` or consistent content would eliminate this. — Screenshot: jordan-mobile-stats-grid.png

**Observation 3:** Navigation on mobile collapses to hamburger correctly. The toggle button is 44x44px (defined in CSS as `width: 44px; height: 44px`) — meets minimum tap target. When open, the nav overlay uses `background-color: var(--color-primary)` (sage green) with white link text and 48px minimum height per link. The CTA button in the nav ("Call (303) 399-1488") is visible in the header at mobile as a gold pill — however the nav __links are display:none at mobile and the CTA button stays visible. This means on mobile, the user sees logo + phone CTA + hamburger in the nav bar, which is ideal for a dental practice where the phone number is a primary conversion action. — Screenshot: jordan-mobile-nav.png

**Observation 4:** Service cards stack to single column on mobile. At 390px, the 6-card grid renders as 1 column with --space-6 (1.5rem) gap. Cards have adequate internal padding (--space-8 top/bottom, --space-6 sides). The featured "Emergency Same-Day Appointments" card (service-card--featured, sage green background with white text and gold CTA) stands out clearly in the stack — the dark card amongst white cards creates the right visual interrupt for the emergency service. The gold "Call for Same-Day Care" button is min-height 44px. — Screenshot: jordan-mobile-services.png

**Observation 5:** The location section at mobile renders the map iframe above the hours/contact/form stack (single column grid). The map iframe has `min-height: 300px` on mobile — this is sufficient but not spacious. The appointment request form renders below the contact info, which puts the form below the fold requiring significant scroll. Form fields have `min-height: 44px` — tap targets are adequate. The form-hipaa-notice uses --text-xs which at the low end of its clamp range could approach 12px on mobile — small but not illegible. The submit button ("Request Appointment") is btn--primary btn--full-width at min-height 52px — prominent and appropriately sized. — Screenshot: jordan-mobile-location-form.png

**Observation 6:** Doctor cards at mobile render as single-column flex-direction: column — photo on top (4:3 aspect ratio, full width), bio below. At 390px, the doctor photo is approximately 390px wide by 292px tall. `object-position: center top` ensures the face anchors to the top of the frame. This is correct behavior and the face visibility criterion is met in layout. Two doctor cards stack vertically with --space-12 (3rem) gap, which gives them clear separation. — Screenshot: jordan-mobile-about-doctors.png

---

## Final Score: 8.25 ((8.5 + 8.0) / 2)

---

## Top 3 Issues (ranked by impact)

1. **Hero uses practice interior photo rather than doctor face as primary visual** — Per the dental niche profile, "The first thing a patient needs to see is who will be treating them." The current hero leads with an interior-only photo plus text copy introducing the doctors by name. Doctor photos appear in section 4 (About). A real doctor photo in the hero — either as the background or as a positioned element — would close the most important niche gap on this site. — Impact: Medium — Estimated fix effort: M (requires sourcing a hero-appropriate doctor photo and adjusting the hero layout or object-position)

2. **Stats bar fourth item ("Father & Son") breaks grid rhythm on both desktop and mobile** — The string value renders at a different visual weight than the three numeric stats, and wraps to more lines on mobile causing ragged bottom alignment in the 2x2 mobile grid. The fix is either replacing the fourth stat with a numeric (e.g. "2 Doctors, 1 Family") or adding a `min-height` constraint to `.stats__item` so all four cells maintain consistent height. — Impact: Low — Estimated fix effort: S (CSS min-height or copy change)

3. **Hero photo alt text marks the image as decorative (aria-hidden="true" on the bg-media div) while it contains the practice interior** — The hero background image div has `aria-hidden="true"` which is technically correct for a background image that is described by the headline copy. However the alt text on the `<img>` inside reads "Dental Solutions of Central Park practice interior, Aurora CO" — this is a non-empty alt on an image inside an aria-hidden container, which means screen readers will ignore the alt entirely. This is a minor inconsistency: either the container should not be aria-hidden (so the alt is read) or the alt should be empty (if purely decorative). Casey will likely flag this. — Impact: Low — Estimated fix effort: S (one-line HTML change)

---

## Hard Fails

**Hero image face crop — NOT triggered.** The hero background image is a practice interior, not a person photo. No face crop is possible or applicable. The doctor photos in the About section (assets/dr-blake-1.jpg and assets/dr-hunter.png) both use `object-position: center top` — correct behavior for ensuring face visibility at the top of the frame. No face crop hard fail.

**Additional hard fail checks (Section 7):**
- Broken CTA: Both hero CTAs are either anchor links (#location) or tel: links — no dead navigation. Phone CTA in nav is tel:3033991488. No broken CTA detected.
- Missing phone number: Phone is in nav CTA, hero secondary CTA, location section, footer — minimum three locations met.
- Missing address: Address present in location section and footer.
- Placeholder text: No lorem ipsum, [business name], or INSERT text found anywhere in the document.
- Fake or dead links: Privacy Policy and Accessibility Statement links not present in footer — this may be a hard fail for Morgan (missing footer compliance links). Flagging for Morgan's review. Footer links (Services, Meet the Doctors, Reviews, Insurance, Location) are all internal anchor links — functional.
- Missing alt text on hero/owner photo: dr-blake-1.jpg alt = "Dr. Blake Weber, DDS, founder of Dental Solutions of Central Park, smiling in his Aurora dental office" — descriptive and present. dr-hunter.png alt = "Dr. Hunter Weber, DDS, dentist at Dental Solutions of Central Park, smiling in the Aurora dental office" — descriptive and present. This hard fail is not triggered.
- Console errors: Out of scope for Jordan — Dev Inspector owns this.

**Hard Fails triggered by Jordan: None.**

**Cross-domain flag for Morgan:** No Privacy Policy link or Accessibility Statement link found in the footer legal section. The footer contains a HIPAA notice paragraph and a license line but no clickable links to a Privacy Policy page. Per the dental niche compliance notes, a HIPAA-compliant Privacy Policy link in the footer is required. This may constitute a Morgan hard fail (dead/missing link) depending on whether Morgan's rubric treats an absent page as equivalent to a dead link. Flagging proactively.
