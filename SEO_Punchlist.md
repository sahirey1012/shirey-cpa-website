# SEO Punchlist — Shirey CPA Quiet Rebrand

**Date:** April 30, 2026
**Scope:** Every SEO-relevant change triggered by the IA restructure (DIY-AI Training as a parallel service line; AI consulting product pages retired; Breckenridge → Salida; nationwide-remote framing for CPA work + regional in-person framing for DIY-AI training).
**Legend:** ✅ = completed in codebase. 🟡 = requires external action by Scott (Search Console, Google Business Profile, third-party directory, etc.).

---

## 1. Page-level meta titles and descriptions

| Page | Status | Was | Now |
|---|---|---|---|
| `/` (index.html) | ✅ | "Scott Shirey CPA \| Fractional Accounting & AI Consulting" / "CPA and fractional finance director helping small businesses and nonprofits with accounting services and customized AI work environments on Anthropic's Claude." | "Shirey CPA & DIY-AI Trainer \| Fractional Accounting and In-Person AI Training" / "Shirey CPA, LLC. Fractional CPA and finance director services delivered remotely across the U.S. In-person DIY-AI training for small business teams across central and western Colorado. Based in Salida." |
| `/services` | ✅ | "Services \| Shirey CPA" / generic accounting description | "Fractional Accounting & Finance Director Services \| Shirey CPA" / description updated to reflect remote-nationwide delivery |
| `/diy-ai-training` | ✅ | (page did not exist) | "DIY-AI Training \| Shirey CPA" / description naming Salida base + service area |
| `/about` | ✅ | Old bio focused on Breckenridge + AI consulting | New description: Salida base, two practices, named regional service area |
| `/contact` | ✅ | "Get in touch with Shirey CPA for fractional accounting services or AI consulting. Based in Breckenridge, Colorado, serving clients across the U.S." | Updated to Salida + DIY-AI training framing |
| `/ai-consulting` | ✅ retired | indexed product page | Files moved to sibling folder `C1_Website_Final_ARCHIVED_AI_PAGES/` (outside the deployed directory). 301 redirect in `netlify.toml` keeps any old inbound link routing to `/diy-ai-training`. `noindex,nofollow` retained on the archived files as belt-and-suspenders. |
| `/ai-consulting/teams` | ✅ retired | indexed product page | Same — file moved to sibling archive folder; 301 redirect in place; noindex retained. |
| `/ai-consulting/you` | ✅ retired | indexed product page | Same — file moved to sibling archive folder; 301 redirect in place; noindex retained. |

---

## 2. sitemap.xml

**✅ Updated.** Was 7 URLs, now 5 URLs.

- Removed: `/ai-consulting`, `/ai-consulting/teams`, `/ai-consulting/you`
- Added: `/diy-ai-training` (priority 0.9, changefreq monthly)
- All `<lastmod>` values updated to `2026-04-30`.

🟡 **External action required:** Resubmit the sitemap in Google Search Console (`https://search.google.com/search-console`) under Sitemaps → enter `https://shirey-cpa.com/sitemap.xml` and click **Resubmit**. This signals to Google to recrawl with the new structure rather than waiting for natural discovery.

🟡 **External action required:** If you are using Bing Webmaster Tools, resubmit the sitemap there as well.

---

## 3. robots.txt

**✅ No change required.** The current file is permissive (allow all crawlers, points at the canonical sitemap). The `noindex` meta tags on the retired AI consulting files plus the 301 redirects in `netlify.toml` are doing the right work. No need to add explicit `Disallow` lines for the retired paths — `noindex` is the cleaner mechanism because it allows Google to crawl the file once and acknowledge the noindex, whereas `Disallow` blocks crawl entirely and can leave stale entries in the index.

---

## 4. Open Graph and Twitter card tags

**✅ Updated** on every active page (`/`, `/services`, `/diy-ai-training`, `/about`, `/contact`).

- `og:title`, `og:description`, `og:url`, `og:type` all align with the new positioning.
- No Twitter-specific cards (`twitter:card`, etc.) currently exist on the site. The OG tags will be picked up by Twitter as fallback per Twitter's spec, so this is acceptable.

🟡 **Optional enhancement:** Add an Open Graph image (`og:image`) to each page for richer social previews. Recommended: a single 1200x630 image with the new "Shirey CPA. And DIY-AI trainer." lockup. Place it at `/og-image.png` and reference from each page's head. Not blocking for launch.

---

## 5. Canonical URLs

**✅ Updated.** Each page declares its own canonical URL pointing at the clean (no `.html`) form.

- `/` → `https://shirey-cpa.com/`
- `/services` → `https://shirey-cpa.com/services`
- `/diy-ai-training` → `https://shirey-cpa.com/diy-ai-training`
- `/about` → `https://shirey-cpa.com/about`
- `/contact` → `https://shirey-cpa.com/contact`

The retired pages still declare canonicals to their own URLs, but with `noindex` set those tags will not influence the index.

---

## 6. Internal link audit

**✅ All internal links updated.** Audit results:

- Nav across all 5 active pages now shows: Home / DIY-AI Training / Fractional Accounting / About / Contact. Old `/ai-consulting` link removed.
- Homepage: hero CTAs now point at `/services` and `/diy-ai-training`. Two-card service snapshot replaces three-card layout. Old `Your Brain on AI` mention in the bio teaser removed.
- About page: bio rewritten; old `Your Brain on AI` paragraph removed.
- Services page: new cross-link section pointing at `/diy-ai-training` ("Looking for in-person AI training for your team?"). No broken links.
- DIY-AI Training page: cross-link section pointing at `/services` ("Need senior-level financial leadership?").
- 404 page: nav updated.
- Retired pages (`ai-consulting*.html`) still contain in-page nav and cross-links to each other; this does not matter because the pages are unreachable via public URLs and `noindex` is set.

No broken internal links detected.

---

## 7. Redirect map

**✅ Implemented in `netlify.toml`.**

| From | To | Status |
|---|---|---|
| `/ai-consulting` | `/diy-ai-training` | 301 (force) |
| `/ai-consulting.html` | `/diy-ai-training` | 301 (force) |
| `/ai-consulting/teams` | `/diy-ai-training` | 301 (force) |
| `/ai-consulting-teams` | `/diy-ai-training` | 301 (force) |
| `/ai-consulting-teams.html` | `/diy-ai-training` | 301 (force) |
| `/ai-consulting/you` | `/diy-ai-training` | 301 (force) |
| `/ai-consulting-you` | `/diy-ai-training` | 301 (force) |
| `/ai-consulting-you.html` | `/diy-ai-training` | 301 (force) |
| `/diy-ai-training.html` | `/diy-ai-training` | 301 |
| `/services.html` | `/services` | 301 (existing) |
| `/about.html` | `/about` | 301 (existing) |
| `/contact.html` | `/contact` | 301 (existing) |
| `/index.html` | `/` | 301 (existing) |

The `force = true` flag on the AI consulting redirects ensures Netlify intercepts them even though static files exist at those paths.

🟡 **External action required:** After deployment, spot-check the redirect chain by visiting `https://shirey-cpa.com/ai-consulting` and confirming a single 301 hop to `/diy-ai-training`. Redirect chain depth matters for SEO equity preservation.

---

## 8. Schema markup

**✅ LocalBusiness/ProfessionalService JSON-LD added to `/`.**

The schema declares:
- `@type: ProfessionalService`
- Name: "Shirey CPA, LLC" + alternate names
- Full Salida postal address: 10199 W. Cheyenne Circle, Salida, CO 81201, US
- `areaServed`: United States (for the CPA practice) + 8 named Colorado counties (Chaffee, Eagle, Lake, Summit, Pitkin, Fremont, Clear Creek, Saguache) for the DIY-AI training
- `hasOfferCatalog` listing both service lines with their respective service areas
- `knowsAbout`: CPA + AI training competencies
- `sameAs`: LinkedIn

This was a meaningful gap on the prior site — there was no schema markup at all. The new schema gives Google an unambiguous statement of what you do, where you do it, and which counties you serve in person.

🟡 **External action required:** Run the new homepage through Google's [Rich Results Test](https://search.google.com/test/rich-results) after deployment. Confirm the LocalBusiness object parses without errors.

🟡 **Optional enhancement:** Add a separate `Service` schema block to `/diy-ai-training` and `/services` referencing the parent business by URL. Useful for service-specific rich results but not blocking.

---

## 9. Location-based keyword adjustments

**✅ Updated site-wide.**

- "Breckenridge, Colorado" replaced with "Salida, Colorado" everywhere (footer on every page; about page bio; contact info block; all meta descriptions).
- The county list updated: was "Summit, Eagle, Lake, Clear Creek, Grand, and Chaffee." Now reflects the new spec — Chaffee, Eagle, Lake, Summit, Pitkin, Fremont, Clear Creek, Saguache, plus the Colorado Springs to Gunnison corridor framing.
- The fractional CPA practice is now framed as remote-nationwide rather than Colorado-regional. The "high country" framing was demoting the CPA work; the new "served remotely across the United States" language opens the discoverable funnel.
- The DIY-AI training is the regional/local SEO surface. That page carries the county names and the corridor language.

🟡 **External action required — Google Business Profile:** Update the GBP listing.
1. Change the business address from Breckenridge to Salida (use the new physical address).
2. Adjust the "service area" to the named counties + corridor.
3. Update the business description to mention both service lines.
4. Add `/diy-ai-training` as a featured service.
5. Re-verify the listing if Google requires it for the address change (postcard or video verification).

🟡 **External action required — local directories:** Audit any directory listings (Yelp, Bing Places, Apple Maps, BBB, Yellow Pages, professional CPA directories) for the old Breckenridge address and update each. If you don't know which directories carry your listing, run a free scan at brightlocal.com or moz.com/local for a discovery report.

🟡 **External action required — NAP consistency:** Once the address is updated everywhere, ensure Name / Address / Phone consistency across all online mentions. Inconsistent NAP is the single largest preventable local-SEO drag for a solo practice.

---

## 10. Analytics / tag manager

**✅ No code changes required.** GA4 (`G-R3M9ESG5H5`) is intact on every active page. The retired pages still carry the GA4 snippet, but since traffic is 301'd before reaching them no events fire there.

🟡 **External action required — GA4 housekeeping:**
- In GA4, set up a custom event or audience for traffic to `/diy-ai-training` so you can monitor adoption of the new positioning.
- If you have configured GA4 conversion events tied to old `/ai-consulting` URLs, update or rename them.
- If you've published any custom Search Console reports referencing the old URLs, refresh them.

🟡 **External action required — Search Console:**
- Use the URL Inspection tool on each retired URL to confirm Google sees the 301 + noindex (request indexing on the new `/diy-ai-training` URL while you're there).
- Check for any "Excluded" errors flagged after redeployment.

---

## 11. Other items relevant to the codebase

| Item | Status | Notes |
|---|---|---|
| Hero headline rewrite | ✅ | "The CPA who builds your AI." → "Shirey CPA. And DIY-AI trainer." with subhead distinguishing remote CPA from regional in-person AI training. |
| Three-card homepage layout | ✅ retired | Replaced with two-card layout matching the new two-service-line IA. The third card (`AI for Individuals`) and its CSS class `.service-card-icon.ai-individual` are no longer in use; the class definition stays in `css-additions.css` as inert code (no harm, no broken pages). |
| Bio teaser on homepage | ✅ | Updated to reference Salida + the two practices; the prior "Your Brain on AI" sentence removed. |
| Existing testimonials | ✅ kept | Ellen Reid (Summit Foundation) and Rob Goodell (Loveland) preserved on homepage. Ellen's mention of AI is reframed under the new positioning — it speaks to past collaborative work, not architecture design. |
| Contact form interest dropdown | ✅ added | New `<select>` field on contact form lets visitors flag whether they're reaching out about CPA, DIY-AI, both, or other. Helps you triage inbound. |
| Google Search Console verification meta tag | ✅ kept | Untouched on `/`. |
| Headshot reference (`/SS%20headshot.jpg`) | ✅ kept | Path unchanged. |
| `css-additions.css` | ✅ kept | Existing rules for breadcrumb, gateway-grid, callout-box, cross-link, faq-item all still used by either active or retired pages. No deletion needed. |

---

## 12. Items that explicitly come down publicly per spec

| What | Where | Status |
|---|---|---|
| Detailed pricing schemes ($4,500, $8,000 + travel, $2,500, $200/month) | `/ai-consulting`, `/ai-consulting/teams`, `/ai-consulting/you` | ✅ unreachable via 301 redirects |
| Discovery / build / handoff process visualization | `/ai-consulting/teams` | ✅ unreachable |
| Anthropic subscription sizing tables | `/ai-consulting/teams` | ✅ unreachable |
| Four-step engagement flow (discovery / build / walkthrough / follow-up) | `/ai-consulting/you` | ✅ unreachable |
| `Your Brain on AI` product naming | site-wide | ✅ removed from index, about, services |

---

## 13. What is NOT in this punchlist (intentional)

- **Phone number / GBP phone updates** — Scott is getting a new Colorado number; until then the site remains email-only. Once the new number is in hand, add a `telephone` field to the LocalBusiness schema and surface it on the contact page.
- **Pricing on `/diy-ai-training`** — published as "starting at $1,000 per day plus mileage" with a follow-up note that shorter session formats will be added once Scott is settled. No fully-fleshed-out pricing table to maintain.
- **In-person training format details** (venue, materials, session length) — left out of the page per spec; Scott fills these in post-relocation.
- **A blog or content marketing surface** — not in scope for this rebrand. The site is a stake-the-flag move, not a discovery funnel.

---

## 14. Punchlist summary

**In codebase, complete:** 1, 2 (file), 3, 4, 5, 6, 7, 8 (file), 9 (site), 10 (no change), 11 (site), 12.

**Requires external action by Scott:**
1. Resubmit sitemap in Google Search Console (and Bing if applicable).
2. Test homepage through Google Rich Results Test after deployment.
3. Spot-check the redirect chain post-deployment (single 301 hop, no chains).
4. Update Google Business Profile (address, service area, description, services, possibly re-verify).
5. Audit and update third-party directory listings for the old Breckenridge address.
6. URL Inspection in Search Console for retired pages and the new `/diy-ai-training` URL.
7. GA4 — add a custom event/audience for `/diy-ai-training`; refresh any reports referencing old AI consulting URLs.

These external items are the difference between deploying clean code and actually moving the search index. None of them is technically hard, but each one needs a real human action that I cannot perform from inside the codebase.
