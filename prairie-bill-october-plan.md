Prairie Specialty Billing: Audit + October Plan

Oct 6, 2026 · @Nathan · Internal

Engagement state

6 new specialty pages went live around Oct 3 and the on-site facts are disciplined, but the business barely exists off its own domain and Yelp carries an old address. Live crawl run Oct 6, 2026 against prairiebilling.com (16 URLs, all 200).


Holds

Founders: /ai-instructions and llms.txt name Blackburn and Vollers as founders; schema names only Blackburn as founder and Vollers as employee. [CONFIRM] which is right.
Karl Vollers credentials: "APRN, FNP" here vs "APRN, CWOCN" on prairiefoot.com. [CONFIRM] full string; both may be true.
Years in business: a third party roundup says "over 10 years"; llms.txt tells AI not to state a founding year. [CONFIRM] the real year so it can be published and the roundup corrected.

Next 3

Fix the leaked meta and the Yelp address.
Retype the entity off MedicalBusiness so it stops overlapping the clinic at the same address.
Build the off-site footprint: audit the existing GBP, add a LinkedIn company page and 3 billing directories.

Executive summary

The site's content is the strongest of the 2 Prairie properties, but Google has indexed only 4 pages and almost nothing else on the web confirms the company exists.


Biggest risks

Entity typed MedicalBusiness at the same street address as Prairie Foot & Ankle. Machines can read the billing company as a second clinic.
A third party article (MediBillMD Omaha list) is currently the strongest outside description, and it asserts a tenure the company has not confirmed.
3 competing entity nodes: the Squarespace auto Organization and LocalBusiness blocks, the custom #organization node, and a second LocalBusiness with its own @id on /contact-us.

Strengths to protect: disambiguation lines in llms.txt (names 3 look alike companies), a clear "do not claim" list, author bylines from Dr. Blackburn on every new page, and specific payer content (Heritage Health, Q7 to Q9 modifiers, Method II) no generic competitor page has.

Search Console findings

Google has indexed only 4 pages of this site, and nobody searched the company's name in 3 months. Data covers Jul 5 to Oct 4, 2026; the indexing report predates the Oct 3 pages.

Totals: 43 clicks, 1,590 impressions, 2.7% CTR, average position 13.9. No query contains "prairie specialty billing". The only name searches are for the founders: "dr blackburn grand island ne" 20 impressions, "karl vollers" 18, "corey blackburn" 9.

Indexing: 4 indexed (home, /about, /contact-us, /who-we-serve), 8 not indexed (3 redirects, 2 not found, 2 alternate canonical, 1 noindex). /services, /faqs, /blog, the blog post and /ai-instructions had zero impressions in 3 months.

Split homepage: http://www.prairiebilling.com/ still drew 622 impressions at position 5.0, beside 809 for the https version at 21.2. The http URL 301s today, so Google is holding a stale copy. An old /new#services URL also still shows and returns 404.

Queries already ranking with 0 clicks


The credentialing queries rank in the top 4 already and the new /credentialing page is an orphan with a broken meta. Fixing both is the cheapest win on the site.

AI features (Google's generative AI report): 75 impressions total; home 61, /contact-us 16, /about 14.

GA4: the site carries tag G-Q1FER38SN5, but that property is not in the Google account I could reach in Chrome. Lead events and AI referral traffic are unmeasured until access is granted.

Entity and NAP verification

The hard contact facts agree on every owned surface; the drift is off site and in who founded the company.


Confirmed consistent: phone (308) 675-3401, email info@prairiebilling.com and M to F 8:30 to 4:30 match on footer, schema, llms.txt and /ai-instructions.

Name collisions already handled in llms.txt: Prairie Billing & Consulting Services (CA), Prairie Health Care Billing and Consulting (IL), Prairie Lakes Healthcare System. Add Prairie Flower Billing, which surfaced in today's exact name search.

Shared address with the clinic: both businesses publish 3016 West Faidley Ave, and both Yelp listings carry the same old address. If the billing office has a suite or separate entrance, publish it. If not, keep the GBP category distinctly "Medical billing service" and never "Podiatrist".

Technical and crawl readiness

No access problems; the gap is that nobody can see whether AI bots have found the 6 pages that went live on Oct 3.


Readiness verdict: the live pages are reachable, but Google has indexed only 4 of them and the 3 orphans are reachable only through the sitemap. Fix linking and request indexing first. The specialty pages are 263 to 467 words, which is enough to be quoted but short for the payer depth they promise.

On-page and schema findings

Schema is scoped per page better than the clinic site, but the root entity type is wrong and 1 meta description shipped a drafting note to production.

Schema

Root #organization node is typed MedicalBusiness. A billing company is not a medical business. Retype to Organization + ProfessionalService, keep knowsAbout, and add a sameAs or relatedTo link to the clinic's @id so the 2 entities are related, not merged.
/contact-us adds a second LocalBusiness with @id #localbusiness, its own founder object ("Founder, DPM" as a jobTitle) and priceRange "$$". Delete it and reference #organization instead.
Squarespace auto Organization and LocalBusiness blocks load on every page with a 10 digit phone and malformed hours. Align or blank the Business Information fields.
Founder: set founder to both people only after the [CONFIRM] resolves. Today schema and copy disagree.
FAQPage blocks on home, /services, /faqs and each specialty page: [CONFIRM] each block's questions are visible on that page before the next QA pass.
Add hasCredential or alumniOf on the Person nodes using the education already stated on /ai-instructions (Des Moines University, UNMC).

Titles, metas, headings


Content and AEO gaps

On-site content is ahead of the off-site footprint; October should split effort about evenly between finishing the specialty set and earning outside mentions.

On-site gaps

Primary care, chiropractic and telehealth billing are promised on /who-we-serve with H2 answers but have no pages. Build 1 per month, starting with whichever the keyword export favors.
Cost of outsourced billing is the question every prospect asks first. /faqs touches it. A standalone page that explains how pricing is structured, with no invented percentages, would be the most quotable page on the site. [CONFIRM] what pricing facts the owners will publish.
Switching billing companies is covered inside /denials-and-ar-recovery. Promote it to its own H2 and link it from home.
Blog: 1 post. Move to 2 a month, each written from Dr. Blackburn's practice side (the physician owned angle is the moat).
Specialty pages: deepen each from about 300 words to 600 to 800 with 1 worked claim scenario per page (no client data, no outcome numbers).

Off-site (Q4) gaps


Who owns the Grand Island billing results today: ASP RCM Solutions runs programmatic Grand Island pages per specialty, and PRG runs a Nebraska page. Neither is local. Prairie's local, physician owned position beats both on substance; it simply is not visible yet.

Portrayal check

The live assistant check has not been run; the open web already carries 3 incidents an assistant could repeat. Observations only, no scores.

Observed in web search results (Oct 6)

Exact name search ("Prairie Specialty Billing" Grand Island) returned no Prairie page in the top 9. It returned "Prairie Flower Billing" and ASP RCM pages. Incident: entity not retrievable by name in that engine. Source type: absence.
A longer descriptive query did return the site, /about, /services and Yelp. The entity is findable when the query carries context.
Yelp listing title shows 1932 Aspen Cir. Incident: wrong address. Source type: directory.
MediBillMD says "providing affordable and accurate billing support for over 10 years." Incident: unverified tenure and a price positioning ("affordable") the company does not use. Source type: third party listicle.

To run in October (manual, 1 session each in ChatGPT, Perplexity, Gemini, Google AI Mode)

"What is Prairie Specialty Billing?"
"Is Prairie Specialty Billing the same company as Prairie Foot & Ankle?"
"Who offers podiatry billing services in Nebraska?"

Log: whether the company is described as a clinic, which founders and credentials are named, the address, whether it is confused with the CA or IL look alikes, and which sources were cited.

October action plan

October fixes the leaked meta and the entity type in week 1, closes the NAP gate by mid month, and puts the company on at least 5 outside surfaces by Oct 31.


Not in October: the cost of billing page waits on the owners' pricing decision; review requests to client practices start after GBP is audited.

Sources

Live crawl of prairiebilling.com, sitemap.xml, llms.txt, robots.txt (raw HTML, Oct 6, 2026)
Yelp listing (address from search result title; page blocks fetch)
MediBillMD: Top 10 medical billing companies in Omaha
PRG Nebraska page
ASP RCM Solutions Grand Island page
