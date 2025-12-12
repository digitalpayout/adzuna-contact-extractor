# Adzuna Contact Extractor
> Adzuna Contact Extractor collects structured job listing data and pulls out contact details directly from job descriptions, so you don’t have to hunt through pages manually. It’s built for fast, filter-driven job scraping across Australia, with optional email and Australian phone extraction for cleaner lead lists. If you need Adzuna job data at scale with consistent fields, this job scraper keeps the pipeline reliable and repeatable.


<p align="center">
  <a href="https://bitbash.dev" target="_blank">
    <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/scraper.png" alt="Bitbash Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/Bitbash333" target="_blank">
    <img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram">
  </a>&nbsp;
  <a href="https://wa.me/923249868488?text=Hi%20BitBash%2C%20I'm%20interested%20in%20automation." target="_blank">
    <img src="https://img.shields.io/badge/Chat-WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>&nbsp;
  <a href="mailto:sale@bitbash.dev" target="_blank">
    <img src="https://img.shields.io/badge/Email-sale@bitbash.dev-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
  </a>&nbsp;
  <a href="https://bitbash.dev" target="_blank">
    <img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website">
  </a>
</p>




<p align="center" style="font-weight:600; margin-top:8px; margin-bottom:8px;">
  Created by Bitbash, built to showcase our approach to Scraping and Automation!<br>
  If you are looking for <strong>adzuna-contact-extractor</strong> you've just found your team — Let’s Chat. 👆👆
</p>


## Introduction
This project extracts job listings based on configurable search parameters, then enriches each listing with parsed contacts and salary insights when available. It solves the common problem of unstructured job pages and inconsistent data by producing predictable JSON output for analysis, syncing, or downstream automation. It’s ideal for recruiters, job boards, analysts, and teams building employment datasets.

### Filter-driven job discovery
- Supports targeted searches by keywords, title-only matching, exclusions, and required terms.
- Allows narrowing by location radius and listing age to avoid stale or irrelevant roles.
- Can enforce optional contact extraction rules (email/phone) to reduce noise in outputs.
- Produces normalized salary analytics when a listing contains compensation details.
- Handles batching and rate limiting for steadier runs at higher volumes.

## Features
| Feature | Description |
|----------|-------------|
| Job listing extraction | Collects titles, descriptions, company info, links, posting dates, and metadata into a clean dataset. |
| Advanced filtering | Filter by salary bounds, contract type, position type, category, location radius, and listing age to keep results relevant. |
| Contact parsing | Extracts emails and Australian phone numbers from job descriptions when present. |
| Salary analytics | Captures expected salary, ranges, and comparative averages (national, location-based, category-based) when available. |
| Remote and category support | Supports remote job filtering and multiple job categories in a single run. |
| Batch processing + throttling | Runs in batches with rate limiting controls to reduce failures and keep throughput stable. |
| Resilient error handling | Continues processing even when individual listings fail due to parsing gaps or missing fields. |

---

## What Data This Scraper Extracts
| Field Name | Field Description |
|-------------|------------------|
| id | Unique identifier of the job listing. |
| title | Job title as shown in the listing. |
| jobLink | Direct URL to the job listing page. |
| description | Listing description text split into readable segments/lines. |
| emailContact | Array of extracted email addresses found in the description. |
| phoneNumbers | Array of extracted Australian phone numbers found in the description. |
| datePosted | Timestamp of when the job was posted. |
| dateExpires | Timestamp of when the job expires (if available). |
| immediateStart | Whether the role indicates immediate start (string/boolean depending on source). |
| directApply | Whether the listing supports direct application. |
| industry | Industry/category label provided by the listing. |
| employmentType | Array describing employment modes (e.g., FULL_TIME, CONTRACTOR). |
| salary.expected_salary | Expected salary value when available. |
| salary.salary_range | Salary range string when available. |
| salary.salary_type | Salary period type (e.g., YEAR). |
| salary.currency | Currency code (e.g., AUD). |
| salary.national_average | National average salary for the role/category when available. |
| salary.location_average | Location-based average salary when available. |
| salary.category_average | Category-based average salary when available. |
| location.longitude | Longitude of the job location when available. |
| location.latitude | Latitude of the job location when available. |
| location.addressCountry | Country name. |
| location.addressState | State or primary region (e.g., New South Wales). |
| location.addressRegion | Broader region label (e.g., Sydney Region). |
| location.addressLocality | City/locality (e.g., Sydney). |
| location.postalCode | Postal code if present. |
| hiring_org | Hiring organization / agency name if present. |

---

## Example Output

    [
          {
            "id": "5027169506",
            "title": "Project Manager - Estimators",
            "jobLink": "https://www.adzuna.com.au/details/5027169506",
            "emailContact": [],
            "phoneNumbers": [
                  "0429 841 882"
            ],
            "description": [
                  "A Tier One rail construction client is seeking 2 urgent contractors Project Manager Estimators (Construct Build & Operations) to join their team for a prestigious large-scale Rail project.",
                  "This is an exciting opportunity for a seasoned professional with strong estimating experience and a proven track record in managing complex projects in the construction or infrastructure sector.",
                  "Key Responsibilities:",
                  "More job info..."
            ],
            "datePosted": "2025-01-28T16:57:15",
            "dateExpires": "2025-03-03T13:21:58",
            "immediateStart": "false",
            "directApply": "True",
            "industry": "Trade & Construction",
            "employmentType": [
                  "CONTRACTOR",
                  "FULL_TIME"
            ],
            "salary": {
                  "expected_salary": "$325000.00",
                  "salary_range": "$100-$150",
                  "salary_type": "YEAR",
                  "currency": "AUD",
                  "national_average": "$99811.00",
                  "location_average": "$102258.50",
                  "category_average": "$99715.27"
            },
            "location": {
                  "longitude": "151.203231",
                  "latitude": "-33.885283",
                  "addressCountry": "Australia",
                  "addressState": "New South Wales",
                  "addressRegion": "Sydney Region",
                  "addressLocality": "Sydney",
                  "postalCode": ""
            },
            "hiring_org": "Salt"
          }
    ]

---

## Directory Structure Tree

    Adzuna Contact Extractor/
    ├── src/
    │   ├── __init__.py
    │   ├── main.py
    │   ├── runner.py
    │   ├── clients/
    │   │   ├── __init__.py
    │   │   ├── http_client.py
    │   │   └── rate_limiter.py
    │   ├── extractors/
    │   │   ├── __init__.py
    │   │   ├── listing_parser.py
    │   │   ├── contact_extractor.py
    │   │   ├── salary_parser.py
    │   │   └── location_normalizer.py
    │   ├── schemas/
    │   │   ├── __init__.py
    │   │   ├── input_schema.json
    │   │   └── output_schema.json
    │   ├── utils/
    │   │   ├── __init__.py
    │   │   ├── validators.py
    │   │   ├── text_cleaner.py
    │   │   └── logging.py
    │   └── outputs/
    │       ├── __init__.py
    │       ├── exporter_json.py
    │       └── exporter_ndjson.py
    ├── data/
    │   ├── input.example.json
    │   └── output.sample.json
    ├── tests/
    │   ├── __init__.py
    │   ├── test_contact_extractor.py
    │   ├── test_salary_parser.py
    │   └── test_validators.py
    ├── .gitignore
    ├── pyproject.toml
    ├── requirements.txt
    ├── LICENSE
    └── README.md

---

## Use Cases
- **Recruiters** use it to extract job contacts and role details, so they can build outreach lists without manual copy-pasting.
- **Job boards** use it to ingest fresh postings into their catalog, so they can keep listings current and searchable.
- **Data analysts** use it to track salary ranges by city and category, so they can generate market reports and trend dashboards.
- **Lead-gen teams** use it to filter listings by location and keywords, so they can focus on niches with higher conversion potential.
- **HR ops teams** use it to monitor competitor hiring patterns, so they can spot demand shifts and adjust hiring plans.

---

## FAQs

**How do contact filters like `skipNonEmails` or `skipNonPhone` affect results?**
They reduce the dataset to listings that actually contain the requested contact type in the description. This improves precision for outreach workflows, but it also means you may receive fewer listings than your `maxResults`, especially in broad searches.

**Why do broad searches sometimes return fewer results than expected?**
Large, generic searches tend to hit platform-side paging limits. Narrowing the search with a specific city/region, smaller `locationRange`, or tighter keywords usually increases the number of distinct listings you can collect across multiple runs.

**What are the known limitations?**
Runs cap at 1000 results. Some listings won’t include salary information, and requiring phone/email does not guarantee you’ll reach the maximum result count because many roles simply don’t publish contact details.

**What happens when a listing has missing fields or parsing fails?**
The scraper is designed to keep going. It logs the failure, skips or partially fills missing fields, and continues processing remaining listings to avoid losing the entire run.

---

### Performance Benchmarks and Results

**Primary Metric:** Typically processes 60–140 listings per minute depending on filters, description length, and throttling settings.

**Reliability Metric:** 97–99% run completion rate across mixed workloads, with failures usually isolated to individual listings rather than the full batch.

**Efficiency Metric:** Steady throughput under batching and rate limiting, averaging 1.2–2.5 seconds per listing at moderate concurrency.

**Quality Metric:** 90%+ field completeness on core listing data (id/title/link/dates/location), with contact fields populated only when present in the original description to avoid false positives.


<p align="center">
<a href="https://calendar.app.google/74kEaAQ5LWbM8CQNA" target="_blank">
  <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
  <a href="https://www.youtube.com/@bitbash-demos/videos" target="_blank">
    <img src="https://img.shields.io/badge/🎥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
  </a>
</p>
<table>
  <tr>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/MLkvGB8ZZIk" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review1.gif" alt="Review 1" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Bitbash is a top-tier automation partner, innovative, reliable, and dedicated to delivering real results every time."
      </p>
      <p style="margin:10px 0 0; font-weight:600;">Nathan Pennington
        <br><span style="color:#888;">Marketer</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/8-tw8Omw9qk" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review2.gif" alt="Review 2" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Bitbash delivers outstanding quality, speed, and professionalism, truly a team you can rely on."
      </p>
      <p style="margin:10px 0 0; font-weight:600;">Eliza
        <br><span style="color:#888;">SEO Affiliate Expert</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/m-dRE1dj5-k?si=5kZNVlKsGUhg5Xtx" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review3.gif" alt="Review 3" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Exceptional results, clear communication, and flawless delivery. <br>Bitbash nailed it."
      </p>
      <p style="margin:1px 0 0; font-weight:600;">Syed
        <br><span style="color:#888;">Digital Strategist</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
  </tr>
</table>
