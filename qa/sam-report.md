## Sam — Conversion

Niche: Dental

---

### Desktop (1440x900)
Score: 8.5 / 10

**Observation 1:** Above-fold test passes on all three counts. The hero eyebrow reads "Aurora's Father & Son Dental Team," the H1 is "The Only Dentist You'll Actually Look Forward to Visiting," and the subhead names Dr. Blake and Dr. Hunter Weber caring for Central Park families for over 30 years. Service is clear (general/family dentistry). Location is clear (Aurora, Central Park). Two CTAs are present above the fold: gold "Book Your Visit" button (min-height 52px, links to #location form) and "Call (303) 399-1488" as a secondary white-border button. Phone number also appears in the sticky nav as an accent-gold button. All three above-fold questions answered without scrolling. — Screenshot: sam-desktop-hero.png

**Observation 2:** Trust signals in the first two sections are strong. The hero subheadline calls out "30 years" and "no judgment, no rush, no anxiety" — directly addressing the pain/anxiety objection without being clinical about it. Immediately below the hero, a dark-green stats bar shows 5.0★ Google Rating, 551+ Patient Reviews, 30+ Years of Care, and names both doctors. This is a high-confidence trust signal sequence. Doctor photos with full bios appear in the About section (third scroll), which is slightly late for first-visit conversion but not critical given the hero subhead already humanizes them. One gap: there is no "Accepting New Patients" badge or message anywhere above the fold or in the hero area — a new patient searching Google cannot immediately confirm they can get in, which is a meaningful friction point for a practice with limited hours (Mon–Thu only, 7AM–3PM). — Screenshot: sam-desktop-trust.png

**Observation 3:** The primary CTA "Book Your Visit" in the hero links to `#location` which scrolls to the appointment request form. The form is well-structured (name, phone, email, service dropdown, message, HIPAA notice, submit button). The service dropdown includes "Emergency Appointment" which handles urgency cases. Insurance objection is addressed in a dedicated Financing section (Delta Dental, Cigna, Aetna, MetLife, United Concordia named explicitly plus CareCredit financing). Emergency same-day appointments are called out as a featured service card with a direct phone CTA. However, there is no new patient offer, no "first visit discount," and no explicit welcome message for new patients — this is a missed conversion opportunity for a new patient arriving from Google who needs a reason to choose this practice over the next Google result. Six testimonials are present, four attributed to named patients (Justin A., Sierra T., Kaylan W., Alexis-by-name), with specific and believable copy — this is high quality. No placeholder text found. — Screenshot: sam-desktop-form.png

---

### Mobile (390x844)
Score: 7.5 / 10

**Observation 1:** Above-fold test on mobile (390x844): The sticky nav is present and shows the logo on the left and a hamburger toggle on the right — but the phone number and "Book" CTA that appear in the desktop nav are NOT visible in the mobile nav. At 390px, the nav collapses to logo + hamburger only; the gold "Call (303) 399-1488" nav button is hidden. A user at this viewport sees no phone number or booking CTA in the nav bar. They must scroll into the hero to find the two CTA buttons. The hero CTAs ("Book Your Visit" and "Call (303) 399-1488") are stacked vertically and appear below the eyebrow + H1 + 3-line subhead, which on a 390px viewport likely pushes them into the lower half of the first screen or just below fold depending on font rendering and image height. This is a moderate conversion risk — not a hard fail, but the phone number is absent from the sticky nav on mobile, which is below the expected standard for this niche. — Screenshot: sam-mobile-nav.png

**Observation 2:** There is no sticky bottom bar or sticky CTA on mobile. Once a user scrolls past the hero, there is no persistent way to call or book without scrolling back up or scrolling to the bottom. Competitors in the dental space commonly use a fixed bottom "Call Now" bar on mobile. Its absence is a meaningful gap — a user reading through the Services or About section who decides they want to call has no thumb-reachable escape route without scrolling. The hero CTAs are stacked full-column and tap targets meet the 44px minimum (both set to min-height 52px), so touch usability within the hero is fine. But the lack of persistent mobile CTA across the scrollable page is the single biggest conversion friction on mobile. — Screenshot: sam-mobile-scroll.png

**Observation 3:** The appointment request form in the #location section is the primary online booking action. On mobile it renders as a single-column stacked form which is appropriate. The form has 5 fields (name, phone, email, service dropdown, textarea) plus a HIPAA notice and a full-width submit button. The field count is acceptable for dental — not excessively long. However, the hours (Mon–Thu 7AM–3PM only, Fri–Sun closed) are not visible until a user reaches the location section, which is far down the page. A new patient visiting on a Friday evening or weekend who doesn't know these hours may fill out a form expecting a callback that won't come for days, creating a trust/friction issue. The hours are repeated in the footer which helps, but they should appear earlier — ideally in the hero badge or trust bar. The why-us section mentions "7:00 AM Monday through Thursday" which partially addresses this, but it's framed as a positive differentiator rather than a heads-up about limited availability. — Screenshot: sam-mobile-form.png

---

### Final Score: 8.0 ((8.5 + 7.5) / 2)

---

### Top 3 Issues (ranked by impact)

1. Mobile nav has no phone number or book CTA — users on 390px viewport see logo + hamburger only; phone number is hidden and "Book" button is absent from sticky header — Impact: High — Estimated fix effort: S

2. No "Accepting New Patients" signal and no new patient offer anywhere above the fold or in the hero — a new patient from Google cannot confirm availability, and there is no first-visit incentive to choose this practice — Impact: High — Estimated fix effort: S

3. No sticky mobile CTA (bottom bar "Call Now" or floating "Book") — once a user scrolls past the hero on mobile, there is no persistent conversion path without scrolling back up — Impact: Medium — Estimated fix effort: M

---

### Hard Fails

None. No placeholder text found. Phone number present in hero, nav (desktop), location section, financing section, and footer. Physical address present in location section and footer. Emergency appointments addressed. No broken CTAs detected from code review (all `tel:` links use proper protocol, form submit button is type="submit"). Doctor photos are present with descriptive alt text.
