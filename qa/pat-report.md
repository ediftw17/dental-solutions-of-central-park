## Pat — Niche Expert

Niche: dental
Persona: Practicing general dentist, 12 years in clinical practice, own Aurora-area practice
Niche profile loaded: yes

---

### Desktop (1440x900)
Score: 8.0 / 10

Observation 1: Hero background is an office interior photo (assets/hero.jpg), not a doctor photo. The niche profile is unambiguous: "the first thing a patient needs to see is who will be treating them." The doctors are not visible above the fold on first load. The eyebrow text "Aurora's Father & Son Dental Team" and the hero headline are strong, but the visual is a room, not a face. Every competitive Aurora/Denver practice in this market that has a good site leads with the doctor or team in the hero. The doctor cards don't appear until the About section (scroll 4-5 on desktop). This is the site's biggest credibility miss for a dental niche — patients are choosing a person, and this site delays that moment by several full scrolls. — Screenshot: pat-desktop-hero.png

Observation 2: No ADA membership badge, state dental board membership, or any certification badge is present anywhere on the page. The About section lists DDS credentials and dental schools (both University of Tennessee — good specificity, passes the smell test), but the niche profile specifically calls out the ADA member badge as "the single most recognized credential" and notes "state dental board license number should be in the footer." The footer has a HIPAA notice and a "Colorado Licensed Dental Practice" disclosure with both doctor names and DDS designations — that is correct and present. However no ADA badge, no AGD notation, and no state dental association membership is displayed. In the Aurora/Denver market, top-rated practices (e.g. Aspen Dental, dedicated independents in Stapleton/Central Park) routinely display ADA membership. This is a one-line fix in the About section but it's a visible gap to any patient who has been to a well-credentialed practice before. — Screenshot: pat-desktop-about.png

Observation 3: Section order matches the niche profile almost exactly: Hero → Stats → Services → About/Meet the Doctors → Reviews → Why Us → Financing → Location → Footer. The Stats bar is correctly placed immediately after the hero with 5.0★, 551+ reviews, 30+ years, and the father-son callout. Reviews appear in scroll 3-4 on desktop — within the first two full scrolls on a large monitor — which passes the niche requirement for social proof visibility. The reviews section leads with "5.0 stars across 551 Google reviews" in the subtitle and the aggregate rating widget, so even a quick scanner gets the number immediately. The link to all 551 Google reviews is present. This structure is correct and competitive. — Screenshot: pat-desktop-reviews.png

---

### Mobile (390x844)
Score: 7.5 / 10

Observation 1: Emergency use case evaluation — a patient with a toothache at 8pm who finds this site on their phone. The nav CTA "Call (303) 399-1488" is present in the header and is a tappable tel: link. However, on mobile at 390px the nav shows the hamburger toggle, and the "Call (303) 399-1488" button in the nav is set to display alongside the toggle — need to verify it doesn't collapse behind the toggle. Based on the CSS, `.nav__cta` has `flex-shrink: 0` and remains visible even on mobile (the toggle is added alongside the CTA, not in place of it). The phone number CTA is therefore present and tappable in the header at all times on mobile — this passes the emergency use case. The hero also has a secondary "Call (303) 399-1488" button. Emergency same-day care is featured as a prominent card in the services section with its own "Call for Same-Day Care" tel: button. The mobile emergency path works. — Screenshot: pat-mobile-hero.png

Observation 2: The hero section on mobile delivers zero doctor presence. At 390x844, the first full viewport shows an office interior background photo, a text overlay with the headline and CTAs, and no human face at all. The niche profile calls this "the most important trust opportunity on the entire site" and the common mistakes section specifically flags "Missing doctor photo above fold" as a critical error. Patients arriving on mobile from "dentist near me" searches are making a snap judgment. The father-son differentiator — which is genuinely compelling and rare in this market — is buried in text ("Dr. Blake and Dr. Hunter Weber") but not shown visually until About (scroll 6+ on mobile). This is a meaningful gap on the most important viewport for local dental search traffic. — Screenshot: pat-mobile-hero-fold.png

Observation 3: HIPAA compliance on mobile. The contact form in the Location section includes an inline HIPAA notice ("Your information is protected under HIPAA and will never be shared with third parties") directly above the submit button — this is correctly placed adjacent to the form that collects patient data. The footer also carries a HIPAA statement. On mobile both are present and readable. The form itself collects name, phone, email, and optionally service type — appropriate fields, none over-collecting. The footer also shows "Colorado Licensed Dental Practice. Dr. Blake Weber, DDS · Dr. Hunter Weber, DDS" which is the license disclosure analog. No state license numbers are listed (just the DDS designations and "Colorado Licensed" — Colorado does require dentists to be licensed but does not typically mandate the license number on advertising materials the way contractor licenses are required). This is acceptable but noting it. — Screenshot: pat-mobile-footer.png

---

### Final Score: 7.75 ((8.0 + 7.5) / 2)

---

### Top 3 Issues (ranked by impact)

1. No doctor photo above the fold on either desktop or mobile. The hero background is an office interior. The father-son duo — the strongest differentiator this practice has — is invisible on first load. Patients are choosing a person, and this site makes them scroll past hero, stats, and a full services grid before they see a face. In the Aurora/Denver dental market where every well-reviewed independent practice leads with a doctor photo, this is the gap that costs the most trust in the first 5 seconds. — Impact: High — Estimated fix effort: S (swap or overlay hero image with a doctor/team photo, or add a doctor photo panel alongside the text in the hero)

2. No ADA membership badge or state dental association credential displayed. The niche profile calls the ADA member badge "the single most recognized credential" in dental. Both doctors have real DDS credentials from credentialed dental schools listed in the About section, which is good — but no badge, no association callout, nothing that lets a patient immediately shortcut to "this is a legitimate, vetted practice." Top competitors in the Aurora/Stapleton market display these. A patient who has been to a credentialed practice before will notice the absence. — Impact: Medium — Estimated fix effort: S (add ADA badge image + link to About section, confirm membership is current with client)

3. Copy references "sedation dentistry" as a dropdown option in the appointment form (value="sedation") but no sedation service card exists in the services section and no mention of sedation appears anywhere in the visible copy. The niche profile warns: "If the practice offers sedation dentistry, some states require specific disclosures about who administers it." If sedation is offered, it needs to appear in services with proper copy. If it is not offered, remove it from the form dropdown — presenting it as an option and then having nothing on the site about it is a credibility gap. A nervous patient specifically searching for sedation options would be confused. — Impact: Medium — Estimated fix effort: S (either add sedation to services section with appropriate copy and disclosure, or remove from form dropdown)

---

### Hard Fails
None. Phone number appears in nav header (tappable tel: link), hero section (tappable tel: link in secondary CTA), location section (tappable tel: link in address block), financing section (tappable tel: link on CTA), and footer (tappable tel: link). Physical address appears in hero subheadline context ("Stanley Marketplace"), the location section (full address with suite number), and footer. HIPAA notice present inline on form and in footer. No placeholder text detected — all business names, addresses, doctor names, phone numbers, review content are fully populated. No "lorem ipsum" or "[business name]" anywhere.

---

### What a real dentist would think when they see this site

As someone who runs my own practice and has seen hundreds of dental sites built for colleagues, I'd look at this and say: the bones are genuinely good. The palette, the tone, the actual copy — especially that father-son angle and the "no judgment" framing — these are the right instincts and the copy avoids almost every mistake I see on templated sites. The 551 five-star reviews front and center, the DDS credentials called out in the About section, the early 7am hours as a differentiator — a real practice built this. What I'd wince at is never seeing Blake or Hunter's face until I've already scrolled past three sections. Patients don't book with a room, they book with a person, and the interior photo in the hero is a missed opportunity that every competitor with a polished site has already solved. I'd refer a colleague's nervous patient here — but I'd tell them to scroll to the About section first.
