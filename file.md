Hey,

Attached is the September content plan for Staggs. Fifteen new pages in three batches, each batch arriving as one consolidated package the way the slab season file did. Here is what you need from it and the order to do it in.

High level. Lets get this in play before the end of Sept.

STEP 0. THE SLAB SEASON PACKAGE FROM AUG 27

I checked the live site today. /slab-leaks/ still shows "Updated: July 14, 2026" and has no fall season section, so the Aug 27 package has not landed. Randy was told it would be live by Aug 31. It ships first. Please confirm a date before anything below starts.

THE THREE BATCHES

Batch A: to you Wed Sep 2, live by Fri Sep 4. Five pages. - or your call on dates these are just suggestd.
  /water-heaters/attic-water-heater-replacement/
  /learn/leak-detection/slab-leak-or-sprinkler-leak/
  /learn/slab-leaks/foundation-watering-and-slab-leaks/
  /service-area/rockwall-tx/emergency-plumber/
  /learn/costs-hiring/what-counts-as-a-plumbing-emergency/
  Plus one refresh: /learn/leak-detection/high-water-bill-causes/ (new section, date moves)

Batch B: to you Mon Sep 14, live by Wed Sep 16. Five pages.
  /plumbing-services/sewer-line-repair/
  /learn/drain-sewer/tree-roots-sewer-lines-after-drought/
  /service-area/richardson-tx/drain-cleaning/
  /service-area/rockwall-tx/drain-cleaning/
  /learn/water-heaters/attic-water-heater-checklist/
  Plus one refresh: /learn/water-heaters/water-heater-maintenance-dfw/

Batch C: to you Thu Sep 24, live by Mon Sep 28. Five pages.
  /learn/costs-hiring/emergency-plumber-cost-plano/
  /learn/winter-prep/gas-line-check-before-heating-season/
  /service-area/allen-tx/emergency-plumber/
  Two Learn posts, slugs to follow (a pilot with Randy, fallback page already written into the plan)

I verify every batch on the live domain within 48 hours of publish. Randy gets his month end list on Sep 30.

FIXES THAT RIDE WITH BATCH A

1. Ten city pages are live but missing from the sitemap and from llms.txt. The five burst pipe pages at /service-area/{city}-tx/burst-pipe-repair/ (Richardson, Garland, Rockwall, Carrollton, Mesquite) and the five water heater replacement pages at /service-area/{city}-tx/water-heater-replacement/ (Frisco, McKinney, Allen, Richardson, Rockwall). Add all ten to sitemap-service-area.xml and to the Service Areas section of llms.txt.

2. The Rockwall hub page at /service-area/rockwall-tx/ says "we average 45 minutes or less for emergency calls" in the FAQ. Remove that line. The 45 minute claim is only approved for Plano, Allen, Frisco and McKinney. Then link the two new Rockwall pages from that hub when they go live.

3. From this month on, sitemap and llms.txt additions are part of the same ticket as the pages. No follow ups.

URL PATTERNS, LOCKED

City plus service pages: /service-area/{city}-tx/{service}/ (this is where the live burst pipe and replacement pages already sit, so it is the standing pattern now)
Learn articles: /learn/{cluster}/{slug}/ inside an existing cluster
Service pillars: /plumbing-services/{service}/
Water heater pillars: /water-heaters/{service}/
Slab leak city pages stay at /slab-leaks/{city}-tx/

THREE RULES THAT CAN'T BREAK

1. FAQPage schema text matches the on page wording character for character. Regenerate schema from the final file in each package, never from a draft.

2. The HOLD list is hard. No changes to any star rating or review count anywhere (pages, schema, llms.txt, ai-information), no change to legalName, no change to the areaServed list. If a ticket item seems to touch those, stop and ask.

3. Phone is 682-284-0966 everywhere. If you see any other number in anything you're editing, flag it to me. Don't reproduce it.

Each package comes with preview.html, README-developer-brief.md and the zip, same as July. Reply with a date for Step 0 and I'll send Batch A on Wednesday.

Thanks,
Nathan





# Staggs Plumbing Content Strategy & Plan: September 2026

**Brand:** Staggs Plumbing ([staggsplumbing.co](https://staggsplumbing.co))  
**Focus:** Slab Season, Attic Tanks, and the East Side  
**Scope:** 15 New Pages in 3 Batches (13 Firm, 2 Pilot with Fallback) | 2 Real Refreshes | 6 Decisions Needed  
**Prepared Date:** August 31, 2026  
**Target Audience:** Prepared for Nathan; Hand-off sections for Shams and Randy  

---

## Executive Summary & High-Level Metrics

Fifteen new pages in three batches, timed to what actually breaks in North Texas in September, each built with a thesis a competitor couldn't copy. The first five go live the week Randy was told they would. Nothing goes to Shams until the slab-season package he already has is confirmed live.

### Key Deployment Statistics
- **15 New Pages:** 13 Firm, 2 Pilot with a Fallback option.
- **3 Deploy Batches:** September 4, September 16, and September 28.
- **2 Real Refreshes:** Refreshes that move the "Updated" date honestly.
- **6 Decisions Needed:** Decisions required from Randy, one needing an email.

---

## Current Site Audit & Baseline (As of Aug 31, 2026)

Before planning new pages, live-site checks were run to establish the baseline:

| Item | Status | Key Observations & Defects |
| :--- | :--- | :--- |
| **Slab-Season Package** *(sent Aug 27)* | **NOT LIVE** | `/slab-leaks/` still shows *"Updated: July 14, 2026"* and has no fall-season section. Randy was told this lands by Aug 31. **This is Step 0 for everything below.** |
| **Burst Pipe City Pages (5)** | **LIVE, ORPHANED** | Load fine at `/service-area/{city}-tx/burst-pipe-repair/`. Missing from `sitemap-service-area.xml` and from `llms.txt`. |
| **Water Heater Replacement City Pages (5, July batch)** | **LIVE, ORPHANED** | Frisco, Allen, and Rockwall confirmed live at `/service-area/{city}-tx/water-heater-replacement/`. Same defect: not in the sitemap or `llms.txt`. **Ten finished pages are invisible to Google and AI crawlers.** |
| **Learn Hub Freshness** | **STALLED** | 39 articles; every date is June 12–14 except one July 14 spigot post. No author shown. The "Last updated" line and author block are in the Aug 27 ticket and unshipped. |
| **Rockwall Hub Page** | **CLAIM DRIFT** | FAQ says *"we average 45 minutes or less."* Rockwall is not in the locked core four (Plano, Allen, Frisco, McKinney). Fix in Batch A. |
| **llms.txt Facts** | **NEEDS RANDY** | Says *"4.7 stars, 536 reviews."* GBP read 545 on Aug 27. Under the **HOLD rule** until Randy confirms one number or agrees to drop counts. |
| **Score & Traffic Metrics** | **GOOD** | Performance increased to **84/B** (from 67/D+ in May). Impressions roughly tripled since June; **62% of clicks non-branded**. Remaining gap is off-site roundup authority, not site quality. |

---

## Strategic Recommendation: Three Content Lanes

1. **Slab Season, Extended:**
   - The nine-page seasonal update covers money pages.
   - September adds two critical homeowner questions right after the August water bill arrives:
     - *Is it my sprinklers or my slab?*
     - *Does foundation watering actually prevent this?*
   - Addresses gaps currently unfulfilled by the Learn hub.

2. **Attic Tanks Before the Cold:**
   - Water heaters work hardest and fail most once incoming water turns cold. September is the last calm month for the *"50 gallons over your ceiling"* conversation.
   - Staggs has five replacement city pages and Navien/Rinnai certification, but lacks a page owning the **attic-tank-to-tankless conversion** by name. This represents the biggest single opening on the site.

3. **The East Side and Sewer Lines:**
   - Rockwall is Staggs's second office and its weakest entity.
   - Sewer line repair is a five-figure service living as an anchor inside the drain page.
   - Late-summer drought pushes roots into old joints; a sewer pillar and two Rockwall service pages land in the month demand spikes.

### Deliberate Exclusions
- **No Templated City Pages:** Avoid patterns like *"What We Do for Richardson Customers"* headings. Every page must carry a unique thesis and signature element.
- **No Pre-Winter Freeze Content Yet:** The Learn hub already has freeze content; October is when it earns its refresh.

---

## September 2026 Content Slate

### Batch A: The Promise Batch
* **To Shams:** Wed Sep 2 | **Live by:** Fri Sep 4 | **QA by:** Tue Sep 8 *(Labor Day: Mon Sep 7)*
* **Focus:** Five pages with minimal dependencies on Randy to ensure delivery on the committed date.

| Page Name & URL | Strategic Thesis | Signature Element | Dependencies |
| :--- | :--- | :--- | :--- |
| **Attic Water Heater Replacement & Tankless Conversion**<br>`/water-heaters/attic-water-heater-replacement/` | Builders put tanks in DFW attics to save floor space; at year 10, that tank is the most expensive water risk in the house. Conversion removes standing 50 gallons entirely. Pan, drain line, and venting justify licensed work. | Risk table by home build era (late-80s post-tension through 2000s Frisco/McKinney) with tank-age window. | **NONE** (Facts in Brand Profile §1 & §3) |
| **Slab Leak or Sprinkler Leak? Reading a September Water Bill**<br>`/learn/leak-detection/slab-leak-or-sprinkler-leak/` | Late-summer bills peak due to irrigation. Method to isolate: meter test with irrigation valve isolated (everything off, photo meter, wait 30–60 mins, read again). | Three-step isolation test sequence. Links to 8 slab-leak city pages. | **NONE** |
| **Foundation Watering and Slab Leaks: What a Plumber Will and Won't Tell You**<br>`/learn/slab-leaks/foundation-watering-and-slab-leaks/` | Blackland Prairie clay shrinks in summer and swells with fall rain; this swing stresses under-slab copper. Soaker hoses 12–18" out reduce swing. Structural/crack issues go to an engineer. | Plain explanation of seasonal moisture swing in first 60 words. | **NONE** (Engineer referral boundary from §6) |
| **Emergency Plumber in Rockwall, TX**<br>`/service-area/rockwall-tx/emergency-plumber/` | Staggs has an actual office east of Lake Ray Hubbard (709 W Rusk Street). Focus on 24/7 reality for Rockwall homeowners hour-by-hour. No 45-minute claim. | *"The first hour"* sequence: shut off, photograph, truck arrival steps. | **ROCKWALL HUB FIX** (Ships in same ticket) |
| **What Counts as a Plumbing Emergency (and What Can Wait Until Morning)**<br>`/learn/costs-hiring/what-counts-as-a-plumbing-emergency/` | Solves PAA gap from May audit. Active un-shutoff leak, sewage backup, gas smell = NOW. Slow drain or running toilet = MORNING. Includes locked shutoff & Atmos scripts. | Call-now vs. morning triage table. | **NONE** (Gas script verbatim from §3) |

> **Batch A Mandatory Ticket Inclusions:**
> 1. Add 10 orphaned city URLs (5 burst pipe, 5 water heater replacement) to `sitemap-service-area.xml` and `llms.txt`.
> 2. Remove *"45 minutes or less"* from Rockwall hub FAQ and link new emergency page.
> 3. Confirm Aug 27 slab-season package is live with updated dates. (**Step 0 Rule:** Slab package ships with or before Batch A).

---

### Batch B: Sewer, Drains, and the Attic Checklist
* **To Shams:** Mon Sep 14 | **Live by:** Wed Sep 16 | **QA by:** Fri Sep 18

| Page Name & URL | Strategic Thesis | Signature Element | Dependencies |
| :--- | :--- | :--- | :--- |
| **Sewer Line Repair & Replacement**<br>`/plumbing-services/sewer-line-repair/` | New pillar page. Camera first, always: jetting rotted cast iron makes it worse. Repair vs. replace decided by pipe material and era, not clog severity. | Material decision table: Cast iron (pre-1970s) vs. PVC. Clay tile included if common. | **RANDY:** Confirm trenchless / pipe bursting is offered before listing. |
| **Why Tree Roots Find Sewer Lines After a North Texas Summer**<br>`/learn/drain-sewer/tree-roots-sewer-lines-after-drought/` | Roots chase moisture into wet pipe joints during droughts. Pre-1970s Garland, Mesquite, and East Dallas stock hit hardest. | Cabling vs. jetting explained by impact on pipe walls. | **NONE** |
| **Drain Cleaning in Richardson, TX**<br>`/service-area/richardson-tx/drain-cleaning/` | Richardson's 1970s–80s stock sits where cast iron meets PVC under pinhole-prone slabs. Camera inspection prevents breaking rotted cast iron. | *"What's under a Richardson house"* era-specific cutaway section. | **NONE** |
| **Drain Cleaning in Rockwall, TX**<br>`/service-area/rockwall-tx/drain-cleaning/` | 2000s stock: failures stem from grease, wipes, fixture traps. Restaurant grease lines are jetting jobs. Expands entity around W Rusk St office. | Residential vs. restaurant grease-line section (feeds commercial). | **NONE** (No 45-min claim) |
| **Five Things to Check on an Attic Water Heater Before the First Cold Snap**<br>`/learn/water-heaters/attic-water-heater-checklist/` | Inspect label age, pan water, pan drain exit, fitting rust, TPR discharge. 10 mins in attic in Sept beats ceiling repair in Dec. Pairs with Batch A conversion page. | Five-item liftable checklist with visual indicator of failure. | **RANDY:** Opinion #3 (*"50 gallons waiting over ceiling"*) requires approval. |

---

### Batch C: Cost, Gas, Allen, and the Pilot
* **To Shams:** Thu Sep 24 | **Live by:** Mon Sep 28 | **QA by:** Wed Sep 30 *(Randy's month-end list Wed Sep 30)*

| Page Name & URL | Strategic Thesis | Signature Element | Dependencies |
| :--- | :--- | :--- | :--- |
| **How Much Does an Emergency Plumber Cost in Plano?**<br>`/learn/costs-hiring/emergency-plumber-cost-plano/` | Highest-intent query from May audit with no local answer. Written using approved facts: $69 service call credited, flat-rate written quote. | *"What you'll know before we start"* sequence. | **RANDY:** Price ranges unlock strong version; ships either way. |
| **Check Your Gas Lines Before You Turn the Heat On**<br>`/learn/winter-prep/gas-line-check-before-heating-season/` | Furnace & gas water heater season starts in October. Covers smell, hiss, dead grass. Locked script: leave, call Atmos (866-322-8667), call Staggs for pressure test. | Atmos script verbatim under H1. Red flag: "No permit needed". | **NONE** |
| **Emergency Plumber in Allen, TX**<br>`/service-area/allen-tx/emergency-plumber/` | Allen is core-four lacking an emergency page. Late-80s to 2000s post-tension stock + hard water = failed tanks & slab lines. 45-min average allowed. | Post-tension safety paragraph as differentiator. | **NONE** |
| **Job Notes Pilot (2 Posts)**<br>`/learn/{cluster}/job-notes-{slug}/` | First-hand evidence E-E-A-T reward. Two short posts: city, home era, findings, actions, one photo. No customer names/addresses. | Randy's words lightly edited with license in byline. | **RANDY:** 10-min call or two voice memos. |
| **Fallback for Pilot:**<br>**Post-Tension Slabs: Why Your Plumber Won't Cut First**<br>`/learn/slab-leaks/post-tension-slab-repair/` | Locate cables before cutting; tensioned cable break damages walls. Reroutes with lifetime warranty are default. | Spot repair vs. reroute vs. repipe framework. | **NONE** (Runs opinion #1 if approved) |

---

## Content Refreshes (Honest Date Advancement)

Real edits required to move the "Updated" date:
1. `/learn/leak-detection/high-water-bill-causes/`: Add September irrigation-vs-leak section and meter test; link new sprinkler article. *(Ships in Batch A)*
2. `/learn/water-heaters/water-heater-maintenance-dfw/`: Add *"descale your tankless before winter"* with certified-installer maintenance point; link attic pages. *(Ships in Batch B)*
3. `/service-area/rockwall-tx/`: Remove 45-minute claim; link two new Rockwall pages. *(Batch A Ticket)*

---

## Execution Workflow Standard

1. **Brief from Plan:** Thesis and signature element fixed before drafting.
2. **Draft from Brand Profile:** One H1, four question-shaped H2s, 40–60 word answer under H1, 5-question FAQ matching schema exactly, JSON-LD with `@id` to homepage business node, author block with Randy (License M-17697).
3. **Scrub Pass:** Run through `ai-tell-scrub` for plain, second-person, numbers-over-adjectives voice.
4. **Programmatic Validation:** No 972 numbers, no dev URLs, no review counts/aggregateRating, 45-min claim restricted to Plano/Allen/Frisco/McKinney, clean schema parser.
5. **Package Delivery:** `preview.html`, `README-developer-brief.md`, and `.zip` sent to Shams.
6. **Production QA:** `production-launch-qa` executed within 48 hours of publish.
7. **Month-End Reporting:** Comprehensive summary delivered to Randy on Sep 30.

### URL Structure Standards
- **City x Service:** `/service-area/{city}-tx/{service}/`
- **Learn Articles:** `/learn/{cluster}/{slug}/`
- **Service Pillars:** `/plumbing-services/`
- **Water Heater Pillars:** `/water-heaters/`
- **Slab Leak City Pages:** `/slab-leaks/{city}-tx/`

---

## Key Decisions Required from Randy

| Decision | Strategic Importance | Unblocks |
| :--- | :--- | :--- |
| **1. Ballpark Price Ranges (Yes/No)** | High-intent query resolution. Currently only $69 credited call and flat-rate quote approved. | Batch C: Cost page (strong version), Attic conversion cost H2. |
| **2. Proposed Opinions Approval** | Profile §5 contains 4 proposed plumber opinions. Unlocks E-E-A-T positioning. | Batch B: Attic checklist; Batch C: Post-tension fallback. |
| **3. Job Notes Voice Memos** | Two 5-minute voice memos or a 10-minute call to generate pilot posts. | Batch C: Job Notes pilot. |
| **4. Review Count / llms.txt Sync** | Sync GBP count (545 on Aug 27) vs `llms.txt` (536) or remove count across surfaces. | Fact pass across all batches. |
| **5. Rockwall GBP Phone Line** | Clarify `972-379-4000` vs primary `682-284-0966`. | Rockwall entity consistency. |
| **6. Trenchless / Pipe Bursting Offering** | Confirm capability before publishing on sewer pillar. | Batch B: Sewer pillar. |

---

## Off-Site Strategy & Definition of Success

### Off-Site Link Building & Entity Authority
- Submit Plano and Rockwall profiles to **Expertise.com** and **ThreeBestRated**.
- Pitch fall slab-leak explainer to Plano/Rockwall community outlets and neighborhood groups.
- Maintain review acquisition push (target: 4.7+ rating).

### Definition of Success (by October 5, 2026)
- **15 new pages live and QA'd**, indexed in sitemap and `llms.txt`.
- **10 orphaned August pages integrated**.
- **Updated dates moved** with verified edits across 9 slab pages, 2 refreshes, and Rockwall hub.
- Search Console showing new impressions within 30 days.
- Measured movement on target AI search queries (*best plumber Plano*, *emergency plumber cost Plano*, *attic water heater replacement DFW*, etc.).
- Complete delivery report handed to Randy on Sep 30.

---

## Non-Negotiable Operating Rules

- **Primary Phone Number:** `682-284-0966` on ALL pages. Any other number is a critical defect.
- **Review Counts & Ratings:** Kept OFF pages until explicit approval; no `aggregateRating` in page schema.
- **Testimonials:** Verbatim from sourced reviews only. Never pair real names with written quotes.
- **Technical Boundaries:** Foundations referred to structural engineers. Insurance messaging strictly framed as *"often covers access damage; confirm with your carrier."* Gas messaging MUST use Atmos script verbatim.
- **Entity Scope:** Plano-first entity layout. City pages anchor their respective cities only and never list the entire service area.
- **Date Integrity:** "Updated" dates advance ONLY on substantive manual edits.
