Prairie Foot & Ankle: Audit + October Plan

Oct 6, 2026 · @Nathan · Internal

Engagement state

The site moved a long way since August, but the NAP gate is still open because Yelp and BBB list an old street address. Live crawl run Oct 6, 2026 against prairiefoot.com (31 sitemap URLs, all 200).


Holds

Karl Vollers credential string: site says "APRN, CWOCN"; billing site says "APRN, FNP". [CONFIRM] full credentials with the clinic.
Legal name form: "Prairie Foot & Ankle, PC" (schema, BBB) vs "Prairie Foot & Ankle P.C." (llms.txt). [CONFIRM] Nebraska SOS filing.
1932 Aspen Cir: [CONFIRM] whether it is a former office or a mailing address. If it is a residence, removal is also a privacy fix.

Next 3

Fix Yelp and BBB addresses, then lock NAP.
Clean the sitewide schema injection on Squarespace.
Build the client skill and stand up crawl telemetry.

Executive summary

Machines can read the site and the core facts are strong; the two things holding it back are an old address on Yelp and BBB, and sitewide schema that contradicts itself.


Biggest risks

Yelp is listed in the site's own sameAs while showing 1932 Aspen Cir. The schema formally points machines at a contradicting record.
The full 21 KB custom JSON-LD graph, including FAQPage and the /locations CollectionPage, loads on all 31 pages. FAQ markup appears on pages where those questions are not visible.
Squarespace's auto blocks publish Friday close at 16:30 and a malformed phone "(308) 6460077". The custom block and visible footer say Friday 4:00pm.

Strengths to protect: clean single phone across site and schema, NPI in Physician schema, 7 outreach locations each with its own MedicalClinic node and parentOrganization link, and a disciplined llms.txt.

Search Console findings

Search Console changes the top priority: 13 old URLs return 404 with no redirect, and 5 newer pages (including /ai-information and the blog post) have never been crawled. Data covers Jul 5 to Oct 4, 2026; indexing as of Sept 20.

Totals: 542 clicks, 15,200 impressions, 3.6% CTR, average position 7.1. The homepage takes 446 of the 542 clicks, almost all from brand and provider name searches ("prairie foot and ankle" 112 clicks, "dr blackburn grand island ne" 27).

Indexing: 25 indexed, 25 not indexed.

404, no redirect (13): /foot-problems, /ankle-problems, /skin, /prevention, /foot-types, /deformities, /sports-injuries, /heel-pain, /woundcare, /nail-problems, /vascular-problems, /new-patients-3, /survey. The service pages moved under /services/ and the old URLs were dropped. Confirmed 404 by curl today.
Discovered, never crawled (5): /ai-information, /blog/why-does-my-heel-hurt-in-the-morning, /careers, /locations/broken-bow-ne, /locations/st-paul-ne. None of these has had a single impression.

AI features (Google's generative AI report): 3,000 impressions. Top pages: home 843, /services/foot-problems 661, /services/ankle-problems 270, /services/sports-injuries 268, /services/woundcare 266, /services/skin 212. The legacy service pages I graded weakest are the ones Google's AI answers already draw from. Restructure them in place: keep the URLs and the body facts, add headers and answers, cut nothing.

High impressions, almost no clicks


Local demand: "podiatrist grand island ne" 295 impressions at position 2.3; "podiatrist hastings ne" 129 at 8.5; Kearney 18 total. Condition searches are small: heel and plantar 112 impressions, ingrown 90, wound 86, diabetic 46. That moves the /locations hub and the Hastings page ahead of new condition pages.

GA4: the site carries tag G-VJVVW1NNF0, but that property is not in the Google account I could reach in Chrome. AI referral traffic and lead events remain unmeasured until access is granted.

Entity and NAP verification

The entity is positively identified; 6 facts drift between sources. Canonical value is the site's visible footer unless marked [CONFIRM].


Confirmed consistent: phone 308-646-0077 on site, schema, llms.txt, BBB and Mary Lanning. Founding 2017 matches BBB start date of Oct 2, 2017. Email podiatry@prairiefoot.com matches everywhere.

Stale copy: the /locations meta description still names "Sutton" and "St Francis Wound Care". Neither appears in the current footer or location pages. The Grand Island Regional wound center page exists but is missing from the footer location list.

Shared address note: Prairie Specialty Billing uses the same street address and its schema is typed MedicalBusiness. Google can merge or suppress 2 GBPs at one address with near identical names. Check that each GBP has a distinct category and, if one exists, a suite number.

Technical and crawl readiness

The starting line is strong on access and weak on measurement: every page is reachable and server rendered, but nobody can yet see which AI bots fetch which pages.


Readiness verdict: live pages have no Q1 blocker, but Search Console shows 13 dead URLs without redirects and 5 pages Google has never crawled (see Search Console findings). The 7 location pages and the hub are the thinnest money pages on the site and are the first things an assistant would fetch for "podiatrist near Hastings" style questions.

On-page and schema findings

Pages rewritten since August carry strong titles; the 10 legacy service pages still look like 2017 templates, and the schema is injected once for the whole site instead of per page.

Schema (every page loads 14 JSON-LD blocks)

3 Squarespace auto blocks (WebSite, Organization, LocalBusiness) duplicate the custom #organization node with worse data. Turn off or blank the Business Information fields that generate them, or make them match exactly.
The custom graph (21 KB) sits in sitewide header code injection. It loads the FAQPage, the /locations CollectionPage and all 7 MedicalClinic nodes on every URL. Move each node to its own page: FAQPage on /faq-1 only, each MedicalClinic on its location page, CollectionPage on /locations.
The blog post has its own Article block, but its visible FAQ has no matching FAQPage. The sitewide FAQPage on that URL carries the clinic FAQ questions instead.
Root entity is typed LocalBusiness + MedicalBusiness + Organization. Use MedicalClinic (with Podiatric as medicalSpecialty) to match the location nodes and llms.txt.
priceRange "$" and paymentAccepted listing insurers are misuse. Insurers belong in visible copy and llms.txt; drop priceRange.
Enrich: add hasCredential or memberOf (APMA, Nebraska Podiatric Medical Association) for Dr. Blackburn if [CONFIRM]; add sameAs for Healthgrades provider page and Mary Lanning provider page to the Physician node.

Titles, metas, headings


Content and AEO gaps

The AI page question is settled (llms.txt and /ai-information are both live); the content gap now is depth on high intent conditions and on the 7 location pages.

Blog verdict (open since August): yes, keep the blog, at 2 posts a month. The heel pain post proves the format. Each post should answer 1 patient question and link to 1 service page. No calendar filler.

Gaps ranked by likely patient intent

Diabetic foot care has no page of its own. It is named in the H1 area copy, schema and FAQ, and it is the bridge to the wound care line. Build a standalone page.
Ingrown toenails live inside a 398 word nail page. Split into its own answer page; it is the most common same week podiatry need.
Bunions and hammertoes sit inside a 1,371 word deformities page with no H2s. Restructure with statement headers, or split.
Neuropathy appears in llms.txt but has no page. Mid Nebraska Foot Clinic leads with laser therapy for neuropathy, so this topic is contested.
Location pages run 85 to 115 words and share a template. Each needs unique facts: which provider, which days the outreach clinic runs, how booking works through the host hospital. [CONFIRM] schedules with the clinic before writing.
/locations hub needs real body copy: a short answer on where patients can be seen and a list linking all 7 sites.

Demand gate: items 1 to 4 are condition pages, not a city or service matrix, so they can proceed. Pull a keyword export for Grand Island, Hastings and Kearney before adding any more location pages.

Competitors seen in the same towns


Prairie's differentiator against both is wound care inside 2 hospital wound centers plus rural outreach. That angle should lead the diabetic foot and location pages.

Portrayal check

The live assistant portrayal check has not been run yet; what the open web hands an assistant today already contains 1 wrong fact. Observations only, no scores, per the Sept 10 ruling.

Observed in web search results (Oct 6)

Yelp's listing title for Prairie Foot & Ankle shows 1932 Aspen Circle. Any engine that grounds on Yelp (Perplexity and ChatGPT commonly do) can repeat it. Incident: wrong address. Source type: directory.
A broad "Prairie Foot & Ankle reviews" query surfaced Healthline provider pages for Karl Vollers and a competitor before the clinic's own pages. Source type: health directory.
The /ai-information page ranks for the clinic name plus "Blackburn", so the canonical facts page is being indexed.

To run in October (manual, 1 session each in ChatGPT, Perplexity, Gemini, Google AI Mode)

"Tell me about Prairie Foot & Ankle in Grand Island, Nebraska."
"Who are the providers at Prairie Foot & Ankle and what are their credentials?"
"Where can I see a podiatrist for wound care near Hastings, NE?"

Log for each: address given, hours given, provider credentials, which sources were cited, and whether Prairie Foot & Ankle and Prairie Specialty Billing are confused. Comparison set: Foot & Ankle Clinic of Central Nebraska, Mid Nebraska Foot Clinic.

October action plan

October starts with redirects and indexing (Search Console shows both are broken), closes the NAP gate, fixes the schema, and ships the /locations hub plus 1 condition page by Oct 31. Ingrown toenails moves to November because Search Console shows little demand.


Not in October: new city pages (wait for keyword export), review velocity program (start once NAP locks in November).

Sources

Live crawl of prairiefoot.com, sitemap.xml, llms.txt, robots.txt (raw HTML, Oct 6, 2026)
BBB profile
Mary Lanning provider page
Yelp listing (address from search result title; page blocks fetch)
Foot & Ankle Clinic of Central Nebraska
Mid Nebraska Foot Clinic
