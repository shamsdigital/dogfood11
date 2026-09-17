# Stellan Eoin Builders — Developer Punch List
**For:** Adam Melcher, New Line Web Design
**From:** Alianza Connects
**Date:** September 16, 2026
**Source:** full production crawl of www.stellaneoin.com (102 sitemap URLs plus llms.txt, robots.txt, sitemap.xml), Lighthouse run on the homepage and /services/residential, and raw-HTML inspection of every page below. Every item names what was observed on production and what the corrected state must be.

**How this is organized.** P0 items are factual or broken and go first. P1 items are metadata and structure. P2 items are performance and hygiene. Each item has an acceptance test. When the list is worked, tell us which items shipped and we re-fetch production and confirm; nothing is accepted on a claim.

**Ground rules for all copy changes:** no em dashes in visible copy, no sentence over 30 words, and the replacement text below is final copy, not a suggestion. Do not paraphrase it.

---

## P0 — Factual errors and broken URLs (ship today if possible)

### 1. llms.txt has three unfinished editorial notes live on production
**URL:** https://www.stellaneoin.com/llms.txt
**Observed:** three bracketed placeholders are published:
- line ~30: `- Hours: [CONFIRM published office hours with Jennifer, or delete this line]`
- line ~72: `...RightStart deliverables include Site Intelligence Briefs and Conceptual Cost Books. [CONFIRM with John that the two deliverable names may be published; they are not yet on the live site]`
- line ~175: `- Google Business Profile: [CONFIRM canonical Maps URL once the listing is verified to carry 11 Willow Street, Ste. 11 and (615) 212-9005]`

**Change:**
- Delete the Hours line entirely.
- Line 72: end the sentence at `...connects clients with architects who fit their project type.` Delete from `RightStart deliverables include` to the end of the bracket.
- Line 175: delete the Google Business Profile line entirely.

**Acceptance:** `curl -s https://www.stellaneoin.com/llms.txt | grep -c "CONFIRM"` returns 0.

### 2. Retired company address published on the Terms of Use page
**URL:** https://www.stellaneoin.com/terms-of-use
**Observed:** `Stellan Eoin Builders is located at: 1865 Air Lane Dr Nashville, TN 37210 United States`
**Change:** `Stellan Eoin Builders is located at: 11 Willow Street, Ste. 11, Nashville, TN 37210, United States.`
**Acceptance:** "Air Lane" returns zero matches sitewide. Check /privacy-policy for the same string while you are in there.

### 3. A service-area page is published in the sitemap but returns 404
**URL:** https://www.stellaneoin.com/service-areas/murfreesboro → HTTP 404
**Observed:** the URL is in sitemap.xml, is linked from the /service-areas hub ("Murfreesboro (Rutherford County)... Murfreesboro →"), and is named in the JSON-LD `areaServed` on /services/residential. The page does not exist.
**Change:** remove the URL from the sitemap, remove the Murfreesboro block and link from the /service-areas hub, and remove Murfreesboro from the Residential schema (see item 6). We will tell you if and when the page gets written.
**Acceptance:** the URL appears in zero places in the rendered HTML and zero places in sitemap.xml.

### 4. Two different price guidances published on the same site
**URL:** https://www.stellaneoin.com/guides/how-much-does-it-cost-to-build-a-home-in-nashville
**Observed:** the page publishes `Basic Construction: $120–$200 per square foot / Custom Homes: $200–$350+ per square foot / Luxury Builds: $400+ per square foot`, while /services/residential publishes "around $350 per square foot" as the company's guidance.
**Change:** replace the entire three-tier block with:

> Every home lands differently, and right now a custom home in this market commonly comes in around $350 per square foot. Finish selections move that number more than anything else, then land and site conditions. Our custom homes page walks through what drives it.

Link "custom homes page" to https://www.stellaneoin.com/services/residential. Leave the rest of the page as is.
**Acceptance:** `$120`, `$200 per square`, and `$400+` return zero matches sitewide. `$350` appears only on /services/residential and this page.

### 5. Homepage FAQ states what the company does not do
**URL:** https://www.stellaneoin.com/ (FAQ block and the FAQPage JSON-LD)
**Observed (both places, identical text):** "Yes, in two ways. We don't sell lots, but we're glad to connect you with a reputable realtor..."
**Change (replace in the visible FAQ and in the JSON-LD answer, verbatim, so they match):**

> Yes, in two ways. We connect you with a reputable realtor who knows the market. Then we evaluate any lot you are considering before you buy it. Site conditions drive a large share of what a home costs to build, and that is worth knowing while you can still choose a different lot.

**Acceptance:** the visible FAQ answer and the `acceptedAnswer.text` in the JSON-LD are byte-identical, and "don't sell lots" returns zero matches.

### 6. Service-area list in schema contradicts the company entity
**URL:** https://www.stellaneoin.com/services/residential, the `Service` node `areaServed`
**Observed:** lists Nashville, Clarksville, Murfreesboro, Franklin, Middle Tennessee. The organization node on every page lists Nashville, Franklin, Brentwood, Davidson County, Williamson County, Middle Tennessee.
**Change:** use this array on the Residential `Service` node and on every other `Service` node sitewide that carries a general area list (the city pages keep their own single-city arrays):

```json
"areaServed": [
  { "@type": "City", "name": "Nashville" },
  { "@type": "City", "name": "Franklin" },
  { "@type": "City", "name": "Brentwood" },
  { "@type": "AdministrativeArea", "name": "Davidson County, TN" },
  { "@type": "AdministrativeArea", "name": "Williamson County, TN" },
  { "@type": "State", "name": "Middle Tennessee" }
]
```

**Acceptance:** "Murfreesboro" appears in zero JSON-LD blocks sitewide.

### 7. Old page URLs from the previous site return 404 with no redirect
**Observed:** these are still listed in Google's index and return 404: `/nashville/`, `/franklin/`, `/custom-homes/`. (`/blog/` already redirects correctly to `/blogs`.)
**Change:** add 301 redirects:
- `/nashville/` and `/nashville` → `/service-areas/nashville`
- `/franklin/` and `/franklin` → `/service-areas/franklin`
- `/custom-homes/` and `/custom-homes` → `/services/residential`

If you have a list of other pre-migration URLs from the old WordPress install, send it and we will map the rest.
**Acceptance:** each returns a single 301 to the target, and the target returns 200.

### 8. Broken and malformed internal links
**Observed:**
- `/blogs`, `/guides`, and `/plans` each contain a link to `/component/tags/tag/:` which returns 404. This looks like an empty tag module rendering a broken href.
- `/services` renders eleven links as `/./services/commercial`, `/./services/residential`, and so on. They resolve, but the `/./` segment creates a second crawlable path for every service page.

**Change:** remove or fix the empty tag link on the three listing pages, and correct the `/services` links to plain `/services/<slug>`.
**Acceptance:** zero occurrences of `href="/./` and zero occurrences of `component/tags/tag/:` sitewide.

---

## P1 — Metadata, structure, and schema

### 9. Three individual leadership pages are orphaned from the sitemap and carry no person schema
**URLs:** /leadership/john-hochstetler, /leadership/josh-hendrick, /leadership/aric-catlett (all return 200, all linked from /leadership, none in sitemap.xml)
**Change:**
- Add all three to the sitemap.
- Each page carries a `Person` JSON-LD node using the same `@id` already used on /leadership, so the entity stays unified. John's:

```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "@id": "https://www.stellaneoin.com/leadership#john-hochstetler",
  "name": "John Hochstetler",
  "jobTitle": "Founder and CEO",
  "url": "https://www.stellaneoin.com/leadership/john-hochstetler",
  "image": "[the actual headshot URL already on the page]",
  "worksFor": { "@id": "https://www.stellaneoin.com/#organization" },
  "knowsAbout": ["General contracting", "Preconstruction planning", "Framing", "Finish carpentry"]
}
```
Repeat for Josh Hendrick (Chief Operations Officer) and Aric Catlett (Project Technical Director) with their own `@id`s from /leadership.
- John's page opens "Founder John founded Stellan Eoin Builders in 2018..." Change the first two sentences to: `I founded Stellan Eoin Builders in 2018. I have been building since 1993.` Leave the rest of the bio.
- John's meta description is 210 characters and truncated mid-sentence. Replace with: `John Hochstetler founded Stellan Eoin Builders in 2018 and has been building since 1993, learning framing, roofing, and finish carpentry by hand.`

**Acceptance:** all three URLs in sitemap.xml, each returns exactly one `Person` node with the matching `@id`, John's description is under 160 characters.

### 10. Two duplicate title tags cover 21 pages
**Observed:**
- `Custom Home Plans | Stellan Eoin Builders` on all 13 /plans pages
- `Projects | Custom Home & Commercial Construction | Stellan Eoin` on /projects and all 7 project detail pages

**Change:** unique, page-specific titles. Use these for the project pages:

| URL | Title |
|---|---|
| /projects | Our Work: Custom Homes and Commercial Projects in Nashville |
| /projects/commercial | Commercial Construction Projects in Nashville, TN |
| /projects/residential | Custom Home and Renovation Projects in Middle Tennessee |
| /projects/commercial/the-bedford-nashville-event-venue | The Bedford: Historic Restaurant to Nashville Event Venue |
| /projects/commercial/rome-records-cafe | Rome Records and Cafe: Nashville Retail and Venue Buildout |
| /projects/commercial/the-moringa-tree-restaurant-cafe | The Moringa Tree: Residential to Cafe Conversion, Nashville |
| /projects/commercial/5-11-tactical | 5.11 Tactical: Fast Track Retail Franchise Buildout, Nashville |
| /projects/residential/dickson-tn-custom-home | Custom Home in Dickson, TN | Stellan Eoin Builders |
| /projects/residential/multifamily-gallatin | Multi Family Renovation in Gallatin, TN | Stellan Eoin |
| /projects/residential/accessible-age-in-place-projects | Accessible and Aging in Place Projects | Nashville, TN |

For the plans pages use the pattern `[Style] House Plans | Custom Home Builder Nashville | Stellan Eoin` (for example `Modern Farmhouse House Plans | Custom Home Builder Nashville`). Keep each under 62 characters.
**Acceptance:** zero duplicate title tags across the site.

### 11. Meta descriptions out of range
**Over 160 characters (will truncate in results):** /about (167), /services/commercial (164), /services/restaurants (182), /services/adaptive-reuse (175), /services/historic-preservation (191), /services/tenant-improvements (189), /services/event-venues (187), /leadership/john-hochstetler (210, fixed in item 9).
**Under 70 characters (wasting the slot):** /projects, /projects/commercial, /projects/residential, /projects/residential/accessible-age-in-place-projects (all 25 chars), /rightstart (26 chars).
**Missing entirely:** /terms-of-use, /privacy-policy, /service-areas/murfreesboro (resolved by item 3).
**Change:** trim the long ones to 150 to 158 characters without dropping the license number or the city. Write 150 to 158 character descriptions for the short and missing ones. Send us the drafts for the five project and RightStart pages if you would rather we write them.
**About page, replace with this exact text** (it also removes a third-person founder reference): `Licensed Tennessee general contractor, BC 73150, building since 1993. Our team learned the trades by hand before managing projects. Nashville and Middle Tennessee.`
**Acceptance:** every indexable page has a description between 120 and 160 characters.

### 12. Legacy copy on the About page
**URL:** https://www.stellaneoin.com/about
**Observed and replace, exactly:**

| Current | Replace with |
|---|---|
| `Every build is more than a project — it's a promise to deliver excellence through thoughtful design, expert execution, and meaningful client relationships.` | `Every build gets planned before it gets built. Scope, budget, and schedule are settled in writing, the trade partners are ones we have worked with for years, and one team answers for the outcome.` |
| `Every Stellan Eoin project runs through our team of licensed trade partners — people we've vetted, contracted, and managed on job after job across Middle Tennessee.` | `Our trade partner team took years to build. Onboarding and vetting the best subcontractors in the area produced one of the strongest trade partner teams in Middle Tennessee, and we manage it directly.` |

### 13. Same legacy trade partner line on the homepage
**URL:** https://www.stellaneoin.com/
**Current:** `Every Stellan Eoin project runs through our team of licensed trade partners — people we've vetted, contracted, and managed on job after job across Middle Tennessee. We answer for...`
**Replace with:** `Years of onboarding and vetting the best subcontractors in the area have built one of the strongest trade partner teams in Middle Tennessee. Our team manages that team directly on every project, and we answer for the result.`
(The wording differs from the About page version on purpose. Do not make them match.)

### 14. Em dashes and two lines to rewrite on the pages published today
**URL:** /services/renovations

| Current | Replace with |
|---|---|
| `...before demolition or construction starts — so the surprises happen on paper, not on your kitchen floor.` | `...before demolition starts. Most surprises get found on paper that way, where changing course costs an hour instead of a week.` |
| `Renovation work exposes what was hidden — structure, mechanicals, and code issues that were not visible until walls opened.` | `Renovation work exposes what was hidden: structure, mechanicals, and code issues that were not visible until the walls opened.` |

**URL:** /services/ada-age-in-place

| Current | Replace with |
|---|---|
| `Accessibility and aging-in-place modifications built to work in daily life — not just on paper.` | `Accessibility and aging in place modifications planned during design and built to work in daily life.` |
| `...grab bars, wider doorways, and barrier removal — scoped to what the household actually needs.` | `...grab bars, wider doorways, and barrier removal, scoped to what the household needs.` |

**URLs:** /services/consulting and /services/project-management each contain one em dash in the first content section. Replace each with a period or a colon and adjust capitalization. No other change.

**Also carrying em dashes in visible copy** (lower priority, fix when you are in the file): /services, /services/commercial, /projects, /projects/residential, /projects/residential/accessible-age-in-place-projects, /service-areas/williamson-county, /plans/barndominiums, /plans/pool-houses-dadus-garages, /guides/10-essential-questions-to-ask-before-hiring-a-builder-in-nashville, /guides/top-rated-builders-in-nashville-tn-your-guide-to-a-trusted-contractor.

### 15. Two wording corrections on service-area copy
- **/services/residential**, where-we-build FAQ: `...and we're licensed across more than twenty Tennessee jurisdictions.` → `Our Tennessee license is valid statewide, and we have built and permitted projects in more than twenty Tennessee jurisdictions.`
- **/service-areas** hub, Clarksville block: `Our official headquarters, and a full-service market for custom homes and commercial construction.` → `Our official headquarters, inside the wider Middle Tennessee footprint we build across.`

### 16. Wrong locale tag on five pages
**Observed:** `<meta name="fb:locale" content="en_gb">` on /about, /contact, /leadership/john-hochstetler, /leadership/josh-hendrick, /leadership/aric-catlett. The site is en-US everywhere else.
**Change:** `en_US`, or remove the tag. Check the global template for where it is injected so it does not come back.
**Acceptance:** zero occurrences of `en_gb` sitewide.

### 17. og:image points at the homepage URL, not an image, on 24 pages
**Observed:** `<meta property="og:image" content="https://www.stellaneoin.com/">` on /rightstart, /service-areas and all five city/county pages, /services/hospitality, /services/retail, /services/restaurants, /services/adaptive-reuse, /services/historic-preservation, /services/tenant-improvements, /services/event-venues, all seven project detail pages, /blogs/what-changes-when-a-building-changes-use, /contact, /terms-of-use, /privacy-policy.
**Change:** point each at a real absolute image URL (the page's own header or hero image; the site logo is an acceptable fallback). This is almost certainly one template default to fix rather than 24 edits.
**Also:** /contact and the three leadership sub-pages emit no Open Graph tags at all. Add the standard set (og:title, og:type, og:url, og:image, og:site_name, og:locale, og:description).
**Acceptance:** every page's og:image resolves to an image file with a 200 status.

### 18. Duplicate breadcrumb schema on every page that has a hand-authored one
**Observed:** pages emit both the authored `#breadcrumb` node and a Joomla-generated `BreadcrumbList` with `@id` ending `#/schema/BreadcrumbList/17`. On service pages the Joomla version's last item has no URL.
**Change:** disable the Joomla breadcrumb schema output (template or plugin setting) so each page emits exactly one `BreadcrumbList`.
**Acceptance:** `grep -c BreadcrumbList` per page returns 1.

### 19. Heading structure
**Observed:** 16 pages emit two H1s (all seven project detail pages, all seven pre-2026 blog posts, both older guides, /terms-of-use, /privacy-policy) because the page title renders once in the hero and again above the body. Separately, many pages jump H1 → H3 with no H2 (all four batch 2 service pages, /services/residential, /services/commercial, /blogs, /guides, /plans, /gallery), and /contact jumps H1 → H4.
**Change:** one H1 per page (demote the duplicate to H2 or to a styled div), and no skipped levels. The visual design does not need to change; this is a tag-level fix.
**Acceptance:** every page has exactly one H1 and no skipped heading level.

### 20. Article schema and authorship on the older posts
**Observed:** only /blogs/what-changes-when-a-building-changes-use carries `BlogPosting`. The seven older posts and the two older guides carry none and name no author.
**Change:** add a `BlogPosting` block to each, following the pattern already on the August post, with the real publish date from Joomla and `author` pointing at `https://www.stellaneoin.com/leadership#john-hochstetler`:

```json
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "@id": "[page URL]#article",
  "headline": "[page H1]",
  "mainEntityOfPage": { "@type": "WebPage", "@id": "[page URL]" },
  "author": { "@id": "https://www.stellaneoin.com/leadership#john-hochstetler" },
  "publisher": { "@id": "https://www.stellaneoin.com/#organization" },
  "datePublished": "[real date]",
  "dateModified": "[real date of last substantive edit]",
  "inLanguage": "en-US"
}
```
Only move `dateModified` when the copy actually changes.
**Acceptance:** every /blogs and /guides page carries one `BlogPosting` with an author reference that resolves to a Person node.

### 21. Company entity node enrichment (homepage template, applies sitewide)
**Add to the existing `#organization` node. Do not create a second node.**

```json
"sameAs": [
  "https://www.facebook.com/stellaneoin",
  "https://www.linkedin.com/company/stellan-eoin-builders/",
  "https://www.instagram.com/stellaneoin/",
  "https://www.alignable.com/nashville-tn/stellan-eoin-builders-llc/custom-homes-commercial-buildings",
  "https://nashvillevoyager.com/interview/hidden-gems-meet-john-hochstetler-of-stellan-eoin-builders-llc/",
  "https://www.buildzoom.com/contractor/stellan-eoin-builders",
  "https://www.youtube.com/@StellanEoinBuilders"
],
"contactPoint": {
  "@type": "ContactPoint",
  "telephone": "+1-615-212-9005",
  "email": "quotes@stellaneoin.com",
  "contactType": "sales",
  "areaServed": "US-TN",
  "availableLanguage": "en"
},
"founder": { "@id": "https://www.stellaneoin.com/leadership#john-hochstetler" },
"employee": [
  { "@id": "https://www.stellaneoin.com/leadership#josh-hendrick" },
  { "@id": "https://www.stellaneoin.com/leadership#aric-catlett" }
]
```
Also extend `knowsAbout` to cover all eleven published service lines rather than the current seven: add "Home renovations and additions", "ADA and aging in place remodeling", "Retail construction and store buildouts", "Assembly and event space construction".
**Do not add** `aggregateRating` or `review` to this node under any circumstance.
**Acceptance:** the homepage passes Google's Rich Results Test with one organization entity and no rating markup.

### 22. Sitemap contents
**Observed:** 102 URLs, of which 37 are single-image gallery detail pages (`/gallery/black-granite-guest-sink` and similar). The three leadership sub-pages are missing (item 9).
**Change:** exclude the /gallery/ detail items from sitemap.xml so crawl attention goes to service, area, project, and content pages. Keep /gallery itself. Add the three leadership pages.
**Acceptance:** sitemap contains roughly 65 to 70 URLs, no /gallery/ detail items, no 404s. Validate with `curl -s .../sitemap.xml | grep -c "<loc>"`.

---

## P2 — Performance and hygiene

### 23. The homepage hero video is 6 MB and is the page
**Measured (Lighthouse, desktop):** homepage total weight 7,954 KB, of which `/images/hero/hero-video-02.mp4` is 6,096 KB. The next largest asset is 263 KB. Performance score 70; /services/residential, which has no video, is 1,302 KB total.
**Change, in order of preference:**
1. Re-encode the MP4 at a web bitrate and add a WebM version. Target under 1.5 MB total for the hero. Two-pass H.264 at roughly 1,500 kbps for 1080p is usually enough for a muted background loop, and trimming the loop to 8 to 12 seconds helps more than anything.
2. Add `preload="none"` to the `<video>` element so the poster image carries first paint.
3. Serve the poster image at the size it renders and keep it under 150 KB.
4. Do not autoplay the video on viewports under 768 px. Show the poster instead.

**Acceptance:** homepage total transfer under 2.5 MB and Lighthouse mobile performance above 80.

### 24. Render and caching details
- **No `preconnect` or `dns-prefetch` tags.** Add `<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>`, the same for `https://fonts.googleapis.com`, `https://www.googletagmanager.com`, and `https://ka-p.fontawesome.com`.
- **11 stylesheets and 31 script tags on the homepage.** Combine and minify where Joomla allows. Lighthouse flags 13.7 KB of unminified CSS and 5.5 KB of unminified JS as the quick wins.
- **Fonts: 475 KB across several Open Sans weight files.** Subset to the weights actually used and add `font-display: swap`.
- **`Cache-Control: no-store, no-cache, must-revalidate` is set on HTML.** That is defensible for a logged-in CMS, but it also disables back/forward cache for every visitor and adds latency. If the site has no logged-in front end, change HTML to a short public cache (for example `public, max-age=0, must-revalidate`) and set long cache headers on `/images/`, `/media/`, and font files.
- **`X-Powered-By: PHP/8.3.33` is disclosed.** Remove the header.

### 25. Images
- **Four homepage images have no width and height attributes** (right_start_logo.webp, site/about.jpg, the project management service image, Sonance_logo_thumb.png). Add intrinsic dimensions; /services/residential currently shows a CLS of 0.125, which is at the edge of passing.
- **Only 4 of 31 homepage images use `loading="lazy"`.** Lazy-load everything below the fold; never lazy-load the hero or poster.
- **19 images across the site are still .jpg or .png.** Convert to WebP; the rest of the site already uses it.

### 26. Accessibility items flagged on both pages tested
- Insufficient color contrast on body paragraphs in several modules (the muted gray on white in `p.mb-4`, `p.text-center` inside the "Two Ways We Build" and custom modules). Darken the muted text token until it passes 4.5:1.
- Touch targets below the minimum size and spacing on mobile.
- One iframe without a `title` attribute (the Hearth financing widget).
- One non-descriptive link: "Learn More" pointing at /services. Change to "Explore our services."

### 27. Search and AI indexing hand-off (needs your account access)
- **Confirm Google Search Console is verified for this property** and send us access. GA4 is installed (G-2HLQZ6X4CR), so GSC can be verified through it in a couple of minutes.
- **Set up Bing Webmaster Tools** and submit the sitemap. This matters more than it used to: Bing's index feeds Copilot and part of ChatGPT's live search.
- **Enable IndexNow.** There is no key file at /indexnow.txt today. Bing Webmaster Tools will generate the key and Joomla has extensions that ping it on publish.
- **Send us raw Apache access logs** (or set up log export) for September. There is no Cloudflare in front of the site, so server logs are the only way to see which AI crawlers are actually fetching which pages. This is the measurement we need to show progress, and it costs nothing.
- After the P0 items deploy, request indexing in GSC URL Inspection for /llms.txt, /terms-of-use, /guides/how-much-does-it-cost-to-build-a-home-in-nashville, and the homepage.

---

## Quick reference: what gets re-tested on acceptance

| # | Test | Passing result |
|---|---|---|
| 1 | `curl -s /llms.txt \| grep -c CONFIRM` | 0 |
| 2 | "Air Lane" sitewide | 0 matches |
| 3 | GET /service-areas/murfreesboro | not linked, not in sitemap |
| 4 | `$120`, `$400+` sitewide | 0 matches |
| 5 | Homepage FAQ text vs JSON-LD answer | byte-identical, no negative phrasing |
| 6 | "Murfreesboro" in JSON-LD | 0 matches |
| 7 | /nashville/, /franklin/, /custom-homes/ | single 301 to a 200 |
| 8 | `href="/./` and `component/tags/tag/:` | 0 matches |
| 9 | Three leadership URLs | in sitemap, one Person node each |
| 10 | Duplicate title tags | 0 |
| 11 | Meta descriptions | all 120 to 160 chars |
| 16 | `en_gb` | 0 matches |
| 17 | og:image values | all resolve to an image, 200 |
| 18 | BreadcrumbList blocks per page | 1 |
| 19 | H1 per page | 1, no skipped levels |
| 20 | BlogPosting on /blogs and /guides | present with resolving author |
| 21 | Rich Results Test, homepage | one organization, no rating markup |
| 23 | Homepage transfer weight | under 2.5 MB |

Send the list back with each item marked shipped or blocked. We re-fetch production and confirm before anything is called done.
