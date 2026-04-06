## Alex — Performance Audit

### Desktop (1440x900)
Score: 6.5 / 10

Observation 1: Google Fonts loaded via CSS `@import` inside inline `<style>` block (line 82) — `@import url('https://fonts.googleapis.com/css2?...')` is render-blocking. The browser cannot proceed past the `<style>` tag until the imported file resolves. This is functionally identical to a CSS `@import` in a linked file. Correct approach is a `<link rel="stylesheet">` tag in `<head>` with `display=swap` already in the URL. Impact: blocks initial render, hurts FCP and LCP on every load. — Screenshot: alex-desktop-fonts-import.png

Observation 2: No `<link rel="preconnect" href="https://fonts.googleapis.com">` anywhere in `<head>`. With Google Fonts in use, the preconnect is required to eliminate the DNS lookup and TCP handshake latency on the font origin before the CSS `@import` resolves. Missing preconnect adds measurable latency to font load and increases risk of FOIT on slower connections. — Screenshot: alex-desktop-preconnect.png

Observation 3: Hero `<img>` at line 1915 (`src="assets/hero.jpg"`) has `loading="eager"` (correct) but is missing `width` and `height` attributes entirely. Without explicit dimensions the browser cannot reserve layout space before the image loads, causing Cumulative Layout Shift (CLS). Hero image CLS is especially penalised by Lighthouse because it happens above the fold during initial paint. Additionally, doctor photo at line 2064 (`src="assets/dr-blake-1.jpg"`), doctor photo at line 2080 (`src="assets/dr-hunter.png"`), and office photo at line 2098 (`src="assets/office.png"`) are all also missing `width` and `height` attributes — four images total missing dimension attributes. — Screenshot: alex-desktop-hero-img.png

### Mobile (390x844)
Score: 6.5 / 10

Observation 1: Same `@import` render-blocking issue applies on mobile. On a mobile network the latency impact of a blocking `@import` for Google Fonts is amplified further — slower connections mean longer render-blocking windows. The `@import` blocks the CSS parser on both viewports identically, but mobile users on 4G/LTE feel this more acutely. — Screenshot: alex-mobile-fonts-import.png

Observation 2: `og:image` is set to a relative path: `content="assets/about-team.jpg"` (line 16). Open Graph images must be absolute URLs (e.g., `https://dental-solutions-of-central-park.nule.io/assets/about-team.jpg`) to render correctly when the page is shared on social platforms. A relative path will fail to resolve in most social scrapers and messaging apps, resulting in no preview image. Twitter Card image at line 22 has the same relative-path issue. — Screenshot: alex-desktop-og-image.png

Observation 3: Schema.org JSON-LD (lines 25-72) is missing the `geo` field (`latitude` and `longitude`). The rubric requires `geo` with `GeoCoordinates` for local business schema. Its absence means Google cannot pin the business to precise map coordinates via structured data, which is a low-to-medium signal loss for local pack ranking. All other required schema fields are present: `name`, `address` (full PostalAddress), `telephone`, `openingHoursSpecification`, `aggregateRating`. — Screenshot: alex-mobile-schema.png

### Final Score: 6.5 ((6.5 + 6.5) / 2)

### Top 3 Issues (ranked by impact)

1. Google Fonts loaded via CSS `@import` inside inline `<style>` block — render-blocking, hurts FCP/LCP on all connections — Impact: High — Estimated fix effort: S
2. Four `<img>` tags missing `width` and `height` attributes (hero, dr-blake-1, dr-hunter, office) — causes CLS above and below fold — Impact: High — Estimated fix effort: S
3. `og:image` and `twitter:image` use relative paths instead of absolute URLs — social sharing previews will be blank on all platforms — Impact: Medium — Estimated fix effort: S

### Hard Fails
None. Alex does not own any hard fail conditions. No hard fail conditions owned by other auditors were observed during this code review.
