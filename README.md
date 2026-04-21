# Xing Scraper

Extract structured data from [xing.com](https://xing.com) — structured job listings from xing.com API.

**[Xing.com Jobs Scraper on Apify →](https://apify.com/blackfalcondata/xing-scraper?fpr=1h3gvi)**

---

## Key features






**Detail enrichment** — Fetch full job descriptions, salary data, contact information for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Change classification** — Track unchanged, expired, cross-run repost detection across runs. Build audit trails of how listings evolve over time.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings (up to 10.000). Set to 0 for the full catalog.

**Proxy support** — Route traffic through Apify Proxy or your own proxy group to avoid regional blocks and rate limits.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases






**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from Xing.com on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from Xing.com.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Compensation benchmarking**
Aggregate salary ranges across roles, industries, and locations on Xing.com to inform pricing decisions, hiring plans, or candidate negotiations.

**Lead generation**
Extract employer contact details alongside listings to build outreach lists for recruiters, staffing agencies, or B2B sales teams.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "query": "software engineer",
  "maxResults": 50,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job search keywords (e.g. 'software engineer', 'data analyst'). |
| `location` | string | — | City or region to search in (e.g. 'Berlin', 'Wien', 'Zürich'). |
| `locationRadius` | integer | `30` | Radius around the location in kilometers. |
| `maxResults` | integer | `50` | Maximum total results (0 = unlimited). |
| `includeDetails` | boolean | `true` | Include full job description in output. |
| `descriptionMaxLength` | integer | `0` | Truncate description to N chars. 0 = no truncation. |
| `compact` | boolean | `false` | Core fields only (for AI-agent/MCP workflows). |
| `incrementalMode` | boolean | `false` | Compare against previous run state — only output new/changed jobs. |
| `stateKey` | string | — | Stable identifier for tracked universe. |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape xing.com?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->


## Output fields

Every listing returns the same 38-field schema. Missing values are `null` — never omitted.

- `jobId`
- `xingId`
- `slug`
- `title`
- `company`
- `companyId`
- `companySize`
- `companyIndustry`
- `companyLogoUrl`
- `location`
- `locations`
- `countryCode`
- `employmentType`
- `remoteOption`
- `careerLevel`
- `discipline`
- `industry`
- `salaryCurrency`
- `salaryMin`
- `salaryMax`
- `salaryMedian`
- `salaryType`
- `description`
- `applyUrl`
- `portalUrl`
- `postedDate`
- `refreshedAt`
- `activeUntil`
- `language`
- `keywords`
- `isPaid`
- `isTopJob`
- `contentHash`
- `scrapedAt`
- `source`
- `isRepost`
- `repostOfId`
- `repostDetectedAt`


## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "jobId": "152604739.9d36ca",
  "xingId": "152604739.9d36ca",
  "slug": "berlin-software-ingenieur-linux-kernel-152604739",
  "title": "Software Ingenieur - Linux / C / Kernel (m/w/d)",
  "company": "Workwise GmbH",
  "companyId": "1969208.99ecd5",
  "companySize": "201-500 employees",
  "companyIndustry": "Personaldienstleistungen",
  "companyLogoUrl": "https://www.xing.com/imagecache/public/scaled_original_image/eyJ1dWlkIjoiMDEzMWM5OTUtZTc1Yy00Y2Q4LWEzMDQtMDZmZjUxMzMzMWRlIiwiYXBwX2NvbnRleHQiOiJlbnRpdHktcGFnZXMiLCJtYXhfd2lkdGgiOjk…",
  "location": "Berlin",
  "locations": [
    {
      "city": "Berlin",
      "zipCode": "10178",
      "street": null,
      "region": "Berlin",
      "countryCode": "DE"
    }
  ],
  "countryCode": "DE"
}
```

*Truncated — full records contain 38 fields. See Output fields for the complete schema.*


**[Try Xing Scraper now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/xing-scraper?fpr=1h3gvi)**


## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/xing-scraper?fpr=1h3gvi) for current pricing.

---

## Related products by Black Falcon Data






- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal

---


## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---

## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) — $5 credit included
2. Open the actor and paste your input
3. Click Start — results download as JSON, CSV, or Excel

Need more volume? [See pricing](https://apify.com/pricing?fpr=1h3gvi).

---

---

*Last updated: 2026 03*
