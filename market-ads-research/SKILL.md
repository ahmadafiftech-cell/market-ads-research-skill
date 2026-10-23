---
name: market-ads-research
description: How to collect competitor ads for ANY market (clinics, restaurants, real estate, gyms, e-commerce, agencies) with the Apify Facebook Ad Library scraper, and turn them into a competitor paid-ads research report. Teaches the student step by step how to pull the ads, then exactly what the report must contain, in what order, how each finding is written (found / means / do / example), how to be honest about what the data can and cannot say, and what to check before delivering. Use whenever someone gives you competitor ads (an Apify export, a CSV/JSON file, or ads pasted from the Meta Ad Library) or says "research the market", "competitor ads report", "what are competitors running", "find market gaps", "who is doing something new", "make me the research report", "how do I collect competitor ads". Works with any AI tool. Not for analysing your own ad account.
---

# Market Ads Research: collect the ads, then write the report

Two jobs in this skill:
1. **Teach the student to collect the ads** with Apify (Step 1). If they have no data yet, start here.
2. **Write the report** to the spec below (Steps 2 to 4).

The goal of the report: someone who has never done ads research reads it in 10 minutes and knows **what the
market does, who is worth watching, and what to test first**.

Build the report from `assets/report-template-ar.md`. `assets/example-report-ar.md` is a finished report
(Dental clinics, Dubai): use it **for tone and look only**. It was written before some rules below. Where it
differs from this spec (vague sample size, findings without "X of Y", no gaps section, no concepts table), **this
spec wins**.

## Language and tone

- Default **Arabic**, simple, light Levantine. If the student writes in another language, use theirs.
- Short sentences. One idea per sentence. No jargon without a one-line explanation.
- Brand and advertiser names stay in Latin script. Numbers are digits.
- No em dashes. Use commas, colons or full stops.
- One number format everywhere, including the summary: **X من Y (Z%)**, for example **7 من 383 (2%)**.
  Never "most", "almost all", "many" or "few" without the count next to it.

---

## Step 1: Collect the ads with Apify (teach the student this)

If the student has no ads yet, walk them through this, one step at a time. Wait for them to confirm each step.

**What it is:** Apify runs a ready-made scraper that copies ads from the Meta Ad Library into a file.
Scraper: https://apify.com/curious_coder/facebook-ads-library-scraper?fpr=9lmok3

**Cost:** pay per ad, about **0.75 USD per 1,000 ads**. Apify's free plan includes a small monthly credit,
which covers a normal market (a few hundred to a few thousand ads). Leave "Scrape ad details" OFF, it is
slower and not needed.

### 1.1 Make an account
Open the link above, sign up (Google login works), then click **Try for free** / **Start** on the scraper page.

### 1.2 Pick search keywords
List 3 to 6 words people would use for this market, **in English AND the local language**. Searching only in
English biases the sample.
- Dental, Dubai: `dental clinic`, `dentist`, `veneers`, `invisalign`, `عيادة أسنان`, `تقويم أسنان`
- Restaurant, Riyadh: `restaurant`, `burger`, `مطعم`, `توصيل`

### 1.3 Build one Ad Library link per keyword
Go to facebook.com/ads/library and set:
- **Country:** the market's country (UAE = `AE`, Saudi = `SA`, Kuwait = `KW`, Qatar = `QA`, Jordan = `JO`)
- **Ad category:** All ads
- **Active status:** **Active ads**
- Type the keyword and press Enter. Copy the link from the browser bar.

The link looks like this. Swapping the keyword (`q=`) and country is enough:
```
https://www.facebook.com/ads/library/?active_status=active&ad_type=all&country=AE&q=dental%20clinic&search_type=keyword_unordered&media_type=all
```
For Arabic keywords, just type them into the Ad Library search and copy the link, the browser encodes them.

**Bonus:** you can also paste a competitor's Facebook page link to get all of that one page's ads.

### 1.4 Fill the scraper input
On the scraper page, in the **Input** tab:
- **URLs:** paste one link per line (one per keyword).
- **Limit per input URL:** `300` is a good start. (Blank = everything, which can be thousands.)
- **Total number of records required:** leave empty, or set a cap like `1500` to control cost.
- **Scrape ad details:** OFF.
- The "Date range", "Active status", "Sort" and "Country" fields below apply to **page links**. For search
  links, the filters come from the link itself (step 1.3), so set them there.

Click **Start**. A few hundred ads take a few minutes.

### 1.5 Export
When the run says **Succeeded**: open **Output** / **Storage**, click **Export**, choose **CSV** (opens in
Excel / Google Sheets) or **JSON**. Download the file.

### 1.6 Give the file to the AI
Upload the file to the chat and say: "This is the Apify export for [market], [city]. Make the report."

**If the file is big:** keep only the useful columns before uploading: page name, start date, end date or
active flag, number of versions (often called `collation_count`), format (often `display_format`), ad text
(body), title, CTA text, and the ad's link. Column names can differ between runs: check the file's headers
and map them, don't assume.

### Manual fallback (no Apify)
Copy at least **30 ads from 10 different advertisers** by hand from the Ad Library. For each ad: advertiser
name, "Started running on" date, number of versions ("X ads use this creative"), format, ad text and headline,
button. Fine for a first look, too small for strong claims.

---

## Step 2: Prepare the data (before writing anything)

Do these in order and write the numbers in a scratch table first. Every number in the report must come from
that table, never from memory.

**Data date:** write down the date the ads were collected. "Days running" = collection date minus start date,
not the day the report is written.

1. **Clean the list.** Remove: advertisers that are not the market (other industries, product brands,
   agencies), other cities or countries the student does not target, ads in languages you will not cover,
   and duplicates. **Keep the counts**: raw ads in, removed by reason, left. These go in the title block.
2. **Raw ads vs unique creatives.** Apify returns one row per ad. The same text from the same advertiser is
   **one idea, many ads**. Count both: total ads and different ideas per advertiser.
3. **Days running** per ad. Write the oldest and newest per advertiser.
4. **Tag every unique idea:** format; hook type (price, result, doctor/expert, fear/pain, education, brand);
   offer (free consult, discount, package, financing, guarantee); price shown yes/no and the amount; button.
   If the text is hidden (dynamic ads) or the price is only in the image, write **"not shown"**. Never guess.
5. **Compare groups:** all ads vs ads running 60+ days vs ads started in the last 14 days vs ads with 3 or more
   versions. The differences are your best findings.
6. **Count the services or products** advertised (see "Adapting to the market"). Note which are advertised
   most and which almost never.
7. **Look for absences.** For each idea nobody seems to use (insurance, guarantee, a specific audience, a fear,
   a proof type), count how many ads mention it. Then **read those ads**. Keywords lie: the same word can mean
   two things. A gap needs a count and a reason it is open.
8. **Check where each finding comes from.** If most of a count comes from one advertiser, or from an
   advertiser outside the target city, say so inside the finding and give the count without them. Example: "20
   ads mention insurance, all from one clinic in Al Ain. Inside Dubai: 0 من 350."

---

## Step 3: Write the report, section by section

Total length: 4 to 7 pages. Follow `assets/report-template-ar.md`. Use headings, short tables, and the labels
below.

### Title block
Market, place, **data date**, source (Meta Ad Library, active ads only, collected with Apify or by hand),
and the exact sample: **N ads, U different ideas, from M advertisers (languages). Removed: R (reasons).**
Never "more than 380" or "about 60". If the sample is under 30 ads or 10 advertisers, say so here and call
every finding a hint.

### 1. The summary in three sentences
(1) the main pattern in the market as **X من Y**, (2) the biggest surprise, (3) the strongest opportunity.

### 2. Part one: the competitors

**2a. Who has the most ads.** Table of the top 10 advertisers:

| # | Advertiser | Active ads | Different ideas | Oldest ad | What they do |
|---|---|---|---|---|---|

Use the same unit in every row ("different ideas" = unique texts or creatives). If an advertiser's text is
hidden, write "not readable" and say how many.

Under it, write found / means / do. The key point to make: **number of ads is not strength**. An advertiser
with 41 ads and 1 idea is repeating, an advertiser with 36 ads and 36 ideas is testing. Spending data is not
available, so never call the biggest advertiser "the biggest spender".

**2b. Who is doing something new.** Pick 4 to 6 advertisers with a new or smart move (newest launches, unusual
offers, filtering the customer, price comparisons, guarantees, testing many hooks on one text, bilingual ads).
For each: **what they do** (quote their actual line and numbers), **why it matters**, **what to take**.

**2c. Interesting things.** 5 to 8 short items. Each: the observation, who does it, one action for the reader.

### 3. Part two: what I found and what to do
5 to 9 findings. Each finding uses exactly these labels, in this order:

- **لقيت (Found):** one number as **X من Y (Z%)**. One sentence. A percentage alone is not allowed.
- **يعني (Means):** what it means for the customer or the market. One or two sentences.
- **اعمل (Do):** one specific action, not a list.
- **مثال حقيقي (Real example):** an advertiser and a line from their ad. If you have none, write a model line
  and label it "مثال" (model).
- **انتبه (Careful):** only when something must be checked before acting.

Order findings from most to least important. Typical findings: how people are sent to buy (WhatsApp,
website), which offers dominate, price visibility by product, old ads vs new ads, proof and guarantees, missing
audiences, missing education, missing formats.

### 4. The gaps (required, its own section)
5 openings at most. For each: **why it is open** (with the count), **which customer it attracts**, **one angle
to test**. Then pick **the single strongest** and give **3 reasons**. A gap is an opening only if the count is
zero or near zero AND it fits a real customer need. A missing topic is not automatically a good one.

### 5. Concepts to test (required)
4 to 6 ideas as a table: **customer | angle | offer | format | one hook line**. Concept = who + what argument +
what offer. Give hook lines and ideas, not full scripts. Test one idea at a time, about 10 ads per idea, and
judge by qualified leads, not raw leads.

### 6. Start here: 3 steps
Three tests in order, each one sentence, each linked to a finding or gap number.

### 7. What I am not sure about (required)
Include at least:
- No spend or impressions: "running a long time" and "many versions" are hints, not proof.
- Only active ads: stopped ads are invisible.
- Demand is untested: "nobody advertises it" can mean nobody wants it.
- Only paid ads, not organic posts.
- Which advertisers are off-market or in another city and slipped into the sample, and which findings they
  affect.
- How many ads had hidden text or prices only inside images.
- If the market is regulated (health, finance, real estate, education): check the platform and authority
  rules before using any price, before/after, guarantee or claim.
- Numbers come from keyword counting and are approximate by a point or two.
- Anything you got wrong earlier and corrected.

---

## Writing rules for every finding

1. A number first, an opinion second.
2. One real example from an actual ad, with the advertiser name.
3. **Zero claims are dangerous.** Never write "nobody does X" unless you counted zero AND read the ads AND
   checked the near cases. Example: "no ad sells a female dentist as a benefit" is only true if you also note
   that a female doctor who markets herself is not the same thing. Otherwise: "X من Y ads mention it".
4. Never call an ad "winning". Use "likely working, because it ran N days with M versions".
5. Separate the signals: (1) running 90+ days AND 3+ versions = strongest; (2) an advertiser with many ideas
   over a long time = a content engine; (3) new ads with many versions = a test, too young to judge.
6. Explain every term a beginner may not know the first time you use it (dynamic ad, versions, CTA).
7. Every "do" must be something the reader can start this week.

## Checklist before delivering

- [ ] Title block has the data date, exact N / U / M, and how many were removed and why
- [ ] Every number, including the summary, is written as "X من Y"
- [ ] Top-10 table shows ads AND different ideas, same unit in every row
- [ ] Every finding has Found / Means / Do / Example
- [ ] Findings driven by one advertiser or an off-market advertiser say so, with the count without them
- [ ] At least 4 advertisers are named with a real quote
- [ ] Gaps were checked by reading ads, not only counting words, and zero claims checked for near cases
- [ ] Gaps section with one strongest opportunity and 3 reasons
- [ ] Concepts table with hook lines, no full scripts
- [ ] "What I am not sure about" section is complete
- [ ] No em dashes, no unexplained jargon
- [ ] Saved as one final file (and PDF if asked). Older drafts are moved to an archive, not deleted

## Adapting to the market

Same report, different things to count:

| Market | Count these | Typical gaps to check |
|---|---|---|
| Clinics | treatments, prices, financing | guarantee, insurance, aftercare, fear, female/male doctor, results over time |
| Restaurants and cafes | dishes, combos, delivery, events | halal, family, view, loyalty, catering |
| Real estate | property types, areas, payment plans | handover plans, yield, visa, risk of off-plan |
| Gyms and wellness | programs, trials, trainers | women-only, results timeline, no contract |
| E-commerce and brands | product lines, bundles, discounts | guarantee, subscription, comparison, proof |
| Services, agencies, courses | offers, niches, lead magnets | case studies, guarantees, qualification |
