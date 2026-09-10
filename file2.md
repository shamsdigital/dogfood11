Hey,

Attached is the September plan for the HVAC site. First, thank you. I checked the live site today and the cleanup from Saturday is mostly there. The fallback shells are gone, the blog is in the sitemap once, and the Plano and Rockwall city pages have descriptions now.

Two things came loose in the cleanup and they go first.

STEP 0. TWO THINGS TO PUT BACK

1. Three of the five pages that went live Saturday are no longer in any sitemap. sitemap-services.xml lists only the six June pages. Please add these three to it and to the Services section of llms.txt:
   /emergency-ac-repair/
   /heat-pump-installation-dallas/
   /furnace-tune-up-dallas/

2. The buyer guides are split. Four live at root (carrier-or-trane, rheem-vs-american-standard, carrier-vs-rheem, carrier-vs-american-standard). /which-is-best/carrier-vs-goodman/ is live at the old path and in no sitemap. /which-is-best/york-vs-american-standard/ and /which-is-best/goodman-vs-american-standard/ return 404 and Google still indexes both. There were nine guides in May. I need a full list from WordPress of every guide that exists, published or not, with its current URL. From that list we build a one to one map: restore at the root slug, or 301 the old path to the live page. One hop, no chains. Every guide ends up in sitemap-learn.xml.

Send me the list first and I'll send the map back the same day.

THE BATCH A TICKET (with the pages, live by Thu Sep 10)

3. Rebuild /privacy-policy/ and confirm /terms/. Both are linked in the footer and privacy is a 404 today.
4. Remove /hello-world/ and /sample-page/ from the sitemaps and unpublish them.
5. Meta description on /about-us/.
6. Give me the sitewide count of pages still missing a description so we know where the 104 stands.

THE THREE BATCHES (a week behind Staggs so you get one site per week)

Batch A: to you Tue Sep 8, live by Thu Sep 10. Four pages plus five city rewrites.
  /furnace-repair-cost-dallas/
  /emergency-heating-repair-dallas/
  /heat-pump-vs-furnace-dallas/
  /fall-allergy-season-hvac-dallas/
  Rewrites (same URLs, new body copy): /service-area/addison/, /richardson/, /plano/, /carrollton/, /farmers-branch/

Batch B: to you Thu Sep 17, live by Mon Sep 21. Four pages.
  /furnace-replacement-dallas/
  /smart-thermostat-installation-dallas/ (the nav links a smart thermostat service today. Tell me where that link goes.)
  /goodman-vs-american-standard/ (restored, old URL 301s here)
  /york-vs-american-standard/ (restored, old URL 301s here)
  Plus Article schema with a byline on all nine guides in one pass, and a real edit to /preparing-your-hvac-system-for-winter/

Batch C: to you Fri Sep 25, live by Wed Sep 30.
  /about-us/ rebuilt
  /reviews/ rebuilt with a live Google reviews embed, no hand typed quotes
  Two Job Notes posts, slugs to follow (fallback page is in the plan if Randy's techs don't send material)

I verify every batch on the live domain within 48 hours of publish.

URL PATTERNS, LOCKED

Service pages and articles: root level slugs, the way the June rebuild works
City pages: /service-area/{city}/
Buyer guides: root level, with the old /which-is-best/ path 301'd one hop

RULES THAT CAN'T BREAK

1. Phone is 972-423-0012 everywhere. If you see 214-710-2515 or 945-468-7191 in anything you're editing, flag it to me. Don't reproduce it.
2. No license number, warranty term, founding date, or price goes on a page unless it's in the package I send. No placeholders.
3. aggregateRating stays on the homepage only. Star rating reads "4.8 stars" with the count wording in the package.
4. FAQPage schema text matches the on page wording character for character. Regenerate from the final file.
5. Every ticket lists its sitemap and llms.txt changes. A page that isn't in both isn't done. That's how we lost the three Saturday pages.

Each package comes with preview.html, README-developer-brief.md and the zip. Reply with the guide list and a date for Step 0 and I'll send Batch A on Tuesday.



# Dallas Heating and Air Conditioning Master Plan: September 2026

**Brand:** Dallas Heating and Air Conditioning ([dallasheatingac.com](https://dallasheatingac.com))  
**Focus:** Recover the Guides, then Own the First Cold Front  
**Scope:** 12 New Pages in 3 Batches (10 Firm, 2 Pilot with Fallback) | 5 City Pages Rewritten with Real Local Material | 7 Decisions Needed  
**Prepared Date:** August 31, 2026  
**Target Audience:** Prepared for Nathan; Hand-off sections for Shams and Randy  

---

## Executive Summary & High-Level Metrics

Twelve new pages in three batches, staggered a week behind Staggs so Shams gets one site per week. The first ticket is a recovery job, not a content job: the June rebuild left the site's best-performing content split across old URLs that 404, and three of the five pages that went live Saturday are already missing from the sitemap. Fix that, then heating season.

### Key Deployment Statistics
- **12 New Pages:** 10 Firm, 2 Pilot with a Fallback option.
- **3 Deploy Batches:** September 10, September 21, and September 30.
- **5 City Pages Rewritten:** Rewritten with real local material.
- **7 Decisions Needed:** Decisions required from Randy, one needing an email.

---

## Current Site Audit & Baseline (As of Aug 31, 2026)

The August 29 site read scored the domain at **59 out of 100** with several technical items remaining:

| Item | Status | Key Observations & Defects |
| :--- | :--- | :--- |
| **Fallback-Shell Pages (14)** | **MOSTLY CLEARED** | `/testfoobar/`, `/reviews/`, `/areas-served/`, and `/privacy-policy/` return 404 instead of shell. `/service-area/` is a real hub with 30 city links. Privacy Policy is linked in footer but still dead. |
| **Meta Descriptions** | **MOVING** | Plano and Rockwall city pages carry real descriptions. About page still has none. Needs full-site recount. |
| **Sitemap Double-Listing** | **FIXED** | Learn sitemap is 18 unique URLs. Posts sitemap down to `/hello-world/` (junk entry and `/sample-page/` still ship). |
| **Aug 29 Pages (5)** | **3 ORPHANED** | `/emergency-ac-repair/`, `/heat-pump-installation-dallas/`, and `/furnace-tune-up-dallas/` are live with content but missing from sitemaps. |
| **Buyer Guides** *(Best Traffic)* | **FRAGMENTED** | 9 original guides at `/which-is-best/` fragmented. 4 live at root; `/which-is-best/carrier-vs-goodman/` live at old path (not in sitemap). `/york-vs-american-standard/` and `/goodman-vs-american-standard/` return 404 while indexed by Google. **York vs American Standard traffic down 41% due to 404.** |
| **City Pages (29)** | **TEMPLATED** | ~2,200 words each with identical H2 stacks and zero city-specific housing/climate facts. Invisible to information gain algorithms. |
| **Pricing Consistency** | **NEEDS RANDY** | AC repair cost page carries full ranges ($150–$700 common repairs, refrigerant $80–$150/lb). Tune-ups listed as $75–$150. Account note says "no tune-up prices." |
| **Authority Facts** | **NEEDS RANDY** | No license number anywhere. No founding year on About page. Reviews stated as "200+" (GBP was 231 on Aug 27). Primary phone is `972-423-0012`. |

---

## Strategic Recommendation: Three Content Lanes

1. **Recover the Guides:**
   - The brand comparison cluster is the primary content cited by AI assistants and shoppers.
   - Inventory all nine original guides, restore or 301 every old `/which-is-best/` URL, insert into Learn sitemap with Article schema and byline.
   - Add one new guide in the high-performing format.

2. **Own the First Cold Front:**
   - Furnace tune-up and heat pump pages went live late August.
   - September builds out the remaining heating shelf before the first cold front: emergency heating repair, furnace replacement, furnace repair cost, and heat pump vs furnace guide.

3. **Make Five Cities Real:**
   - Pick five cities closest to the Quorum Drive office: **Addison, Richardson, Plano, Carrollton, and Farmers Branch**.
   - Rewrite each with local context: 2000s builder-grade systems, attic air handlers, two-story zoning issues. Leave the remaining 24 templated city pages alone for initial testing.

### Deliberate Exclusions
- **No More Brand Matchups:** Avoid new brand matchups without fixing existing redirects first.
- **No Unverified Authority Claims:** Avoid leaning on license numbers, warranty terms, or founding years until supplied by Randy.

---

## September 2026 Content Slate

### Batch A: Recovery, Plus the Heating Twins
* **To Shams:** Tue Sep 8 *(Labor Day: Mon Sep 7)* | **Live by:** Thu Sep 10 | **QA by:** Mon Sep 14

> **Batch A Mandatory Technical Cleanup:**
> 1. Add `/emergency-ac-repair/`, `/heat-pump-installation-dallas/`, and `/furnace-tune-up-dallas/` to `sitemap-services.xml` and `llms.txt`.
> 2. Inventory 9 original buyer guides: restore at root slug or 301 redirect old `/which-is-best/` URLs; add all to `sitemap-learn.xml`.
> 3. Rebuild `/privacy-policy/` and confirm `/terms/`.
> 4. Remove and unpublish `/hello-world/` and `/sample-page/` from sitemaps.
> 5. Add meta description to About page and audit sitewide description count.

| Page Name & URL | Strategic Thesis | Signature Element | Dependencies |
| :--- | :--- | :--- | :--- |
| **What Does Furnace Repair Cost in Dallas? A 2026 Guide**<br>`/furnace-repair-cost-dallas/` | Twin to the AC cost page. Covers igniters, flame sensors, blower motors, control boards, and repair-vs-replace decision thresholds. | Common-repairs table using the same price basis as the AC cost page. | **RANDY:** Confirm AC cost ranges as approved basis. |
| **Emergency Heating Repair in Dallas, Around the Clock**<br>`/emergency-heating-repair-dallas/` | Mirror of emergency AC page for cold fronts. Defines heating emergencies (no heat with freeze coming, CO alarm, gas smell). Includes locked Atmos script. | *"Before we arrive"* sequence including Atmos 866-322-8667 step. | **NONE** |
| **Heat Pump vs Furnace for Dallas Homes**<br>`/heat-pump-vs-furnace-dallas/` | Buyer-guide format addressing backup heat, gas availability, and ductwork compatibility for mild DFW winters. | Decision table by home type: gas furnace present, all-electric, dual-fuel. | **NONE** (No tax-credit claims beyond existing heat pump page) |
| **Ragweed Season and Your HVAC: Filters, Ducts, and What Actually Helps**<br>`/fall-allergy-season-hvac-dallas/` | September–October North Texas allergy response. Covers filter ratings, replacement cadence, and duct cleaning limits. Equipment focused. | Filter-rating table (MERV ratings for typical residential blowers). | **NONE** (No health/medical claims) |

#### Batch A City Page Rewrites (Preserves URLs, Titles, FAQ Schema)
- `/service-area/addison/`: Focus on townhome/condo systems, shared walls, rooftop/closet units near Quorum Drive.
- `/service-area/richardson/`: Focus on 1970s–80s housing stock on 3rd/4th systems, undersized returns, original ductwork.
- `/service-area/plano/`: Focus on 1990s–2000s two-story west Plano stock and upstairs/downstairs temperature split.
- `/service-area/carrollton/`: Focus on late-80s to 90s build-outs with aging 2005–2012 replacement units.
- `/service-area/farmers-branch/`: Focus on older ranch stock vs. new infill, attic units, and split replacement timelines.

---

### Batch B: The Heating Shelf and the Guides
* **To Shams:** Thu Sep 17 | **Live by:** Mon Sep 21 | **QA by:** Wed Sep 23

| Page Name & URL | Strategic Thesis | Signature Element | Dependencies |
| :--- | :--- | :--- | :--- |
| **Furnace Replacement and Installation in Dallas**<br>`/furnace-replacement-dallas/` | Covers sizing and venting strategy in mild-winter markets where 80% vs high-efficiency AFUE rarely pays back on runtime alone. Links to R-410A page. | Sizing/venting section; *"replace both or one"* decision matrix. | **RANDY:** Warranty terms and financing partner details. |
| **Smart Thermostat Installation in Dallas**<br>`/smart-thermostat-installation-dallas/` | Resolves broken nav target. Covers C-wire issues, heat pump compatibility, and multi-stage configurations. | Compatibility checklist by system type. | **CONFIRM URL:** Nav target today. |
| **Goodman vs American Standard for Dallas Homes (Restored)**<br>`/goodman-vs-american-standard/` | Restores indexed 404 guide in updated format with Article schema and named byline. | Brand comparison table. | **BATCH A INVENTORY** |
| **York vs American Standard for Dallas Homes (Restored)**<br>`/york-vs-american-standard/` | Restores indexed 404 guide named in August audit drop report. Rebuilt with Article schema and named byline. | Brand comparison table. | **BATCH A INVENTORY** |

> **Batch B Additional Actions:** Apply Article schema with a named byline across all nine buyer guides. Update `/preparing-your-hvac-system-for-winter/` to link tune-up, emergency heating, and furnace replacement pages with updated September dates.

---

### Batch C: The Entity Pages and the Pilot
* **To Shams:** Fri Sep 25 | **Live by:** Wed Sep 30 | **QA by:** Fri Oct 2 *(Randy's month-end list Wed Sep 30)*

| Page Name & URL | Strategic Thesis | Signature Element | Dependencies |
| :--- | :--- | :--- | :--- |
| **About Us (Rebuilt Entity Page)**<br>`/about-us/` | Adds founding year, technician names, license, meta description, BBB rating, and Staggs relationship for local authority. | Facts block matching `llms.txt` line for line. | **RANDY:** License number, names, ownership statement. |
| **Reviews Page (Rebuilt)**<br>`/reviews/` | Replaces dead 404 page with live Google reviews embed block, eliminating typed quote text. Ratings listed as "4.8 stars". | Live Google review embed + review link and QR block. | **RANDY:** Review count wording confirmation. |
| **Job Notes Pilot (2 Posts)**<br>`/job-notes-{slug}/` | First-hand evidence E-E-A-T reward: technician photo and field notes from Dallas jobs without customer identifiers. | Photo + technician direct account with named byline. | **RANDY:** 10-minute call or two voice memos from tech. |
| **Fallback for Pilot:**<br>**Two-Stage vs Variable-Speed AC for Dallas Homes**<br>`/two-stage-vs-variable-speed-ac-dallas/` | Equipment-class buyer guide evaluating humidity control, extended cooling seasons, and part-load efficiency. | Runtime and humidity comparison table. | **NONE** |

---

## Execution Workflow Standard

1. **Brief from Plan:** Thesis and signature element fixed before drafting.
2. **Draft Inside Constraints:** No unverified license numbers, warranty terms, founding years, or prices. Phone locked to `972-423-0012`. One H1, alternating question/statement H2s, 40–60 word answer under H1, 5-question FAQ matching schema, Service/Article schema referencing homepage node.
3. **Scrub Pass:** Run through `ai-tell-scrub` for plain, second-person, non-fear-based voice.
4. **Programmatic Validation:** No 214 or 945 phone numbers, no dev URLs, no `aggregateRating` outside homepage, schema clean, unique meta description, single H1.
5. **Package Delivery:** Send `preview.html`, `README-developer-brief.md`, `.zip`, and explicit sitemap/`llms.txt` ticket to Shams.
6. **Production QA:** Execute `production-launch-qa` within 48 hours.
7. **Month-End Reporting:** Comprehensive summary delivered to Randy on Sep 30.

### URL Structure Standards
- **Service Pages & Articles:** Root-level slugs (`/slug/`)
- **City Pages:** `/service-area/{city}/`
- **Buyer Guides:** Root level (`/slug/`) with 301 redirects from old `/which-is-best/` paths.

---

## Key Decisions Required from Randy

| Decision | Strategic Importance | Unblocks |
| :--- | :--- | :--- |
| **1. Texas HVAC License Number** | Required for state regulatory compliance and schema `hasCredential` field. | Batch C: About page, `llms.txt`, Schema. |
| **2. Phone Consistency Check** | Verify `972-423-0012` against legacy `214-710-2515` on GBP/Yelp/Facebook. | All off-site directory listings. |
| **3. Pricing Basis Confirmation** | Confirm AC cost ranges as standard and clarify $150-off special status. | Batch A: Furnace repair cost; Batch B: Replacement. |
| **4. Review Count Wording** | Align site "200+" text with GBP actual count (231 on Aug 27). | Batch C: Reviews page, About page. |
| **5. Named Technicians as Authors** | Authorize technician names (Joe, Luis, Josh, Skyler) for guide/article bylines. | Batch B: Guide bylines; Batch C: Job Notes. |
| **6. Founding Year & Staggs Link** | Confirm BBB June 2020 date and approve cross-linking with Staggs Plumbing. | Batch C: About page entity mapping. |
| **7. Warranty Terms & Financing** | Provide current equipment warranty terms and preferred financing partners. | Batch B: Furnace replacement page. |

---

## Off-Site Strategy & Definition of Success

### Off-Site Link Building & Directory Sync
- Submit synchronized NAP to **Expertise.com**, **ThreeBestRated**, and **Angi** once phone line is resolved.
- Maintain review request QR codes with technicians post-service.
- Cross-link Staggs Plumbing and Dallas Heating & AC once ownership relationship statement is confirmed.

### Definition of Success (by October 5, 2026)
- **All 9 buyer guides live at single root URLs** in Learn sitemap with Article schema and zero 404s.
- **12 new pages live and QA'd**, fully indexed in sitemap and `llms.txt`.
- 3 orphaned August pages corrected in sitemap.
- Description gap fully resolved across service, city, and guide pages.
- Restored buyer guides and heating pages earning clicks and impressions in Search Console ahead of cold fronts.
- Overall site quality score improved from baseline of 59/100.
- Unified dated delivery report sent to Randy on Sep 30.

---

## Non-Negotiable Operating Rules

- **Primary Phone Number:** `972-423-0012` on ALL pages and files. Any other phone number is a defect.
- **Fact Verification:** Zero unverified license numbers, warranties, founding dates, or prices published without written confirmation.
- **Review Integrity:** Reviews presented as "4.8 stars" with approved count wording. `aggregateRating` restricted to homepage schema only. Real names never paired with written quotes.
- **Safety Messaging:** Gas leaks MUST use Atmos script word for word (`866-322-8667`). Medical/health claims for air quality strictly prohibited.
- **Deployment Requirement:** Every batch ticket MUST explicitly list sitemap and `llms.txt` additions. Pages not present in both are incomplete.
