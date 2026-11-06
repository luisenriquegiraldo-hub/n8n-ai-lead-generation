# AI Lead Generation + Personalized Cold Email (n8n + GPT-4.1)

Finding prospects and writing to each one by hand doesn't scale. I **adapted and extended an n8n template** into two daily workflows that run in production:

- **7 AM — Scraper:** picks a niche and city from Google Sheets, finds businesses with Google Places, reads their websites and saves validated, deduplicated emails.
- **8 AM — Icebreaker:** GPT-4.1 reads each lead's website and writes a personal email with anti-spam rules and a real signature, sent by SMTP from the company domain. A lead is marked *sent* only if delivery succeeds.

![Pipeline](docs/pipeline-diagram.png)

## Workflow 1 — Scraper

![Scraper workflow](docs/n8n-workflow-1-scraper.png)

## Workflow 2 — Icebreaker

![Icebreaker workflow](docs/n8n-workflow-2-icebreaker.png)

## A real email it wrote

Business name and recipient blurred.

![Real email](docs/email-real-2.png)

## What I added to the original template

- Google Sheets as the control panel: niches and cities editable without touching n8n
- Website scraping with browser-like headers
- Email validation and deduplication
- Anti-spam copy rules, real signature, 130-word limit
- Own SMTP from the company domain
- Fault tolerance: one failed send never stops the run

## Import

The workflow JSON files are in [`workflows/`](workflows/). In n8n: **Workflows → Import from file**, then connect your own credentials (Google Sheets, Google Places API key, OpenAI, SMTP). No credentials are included.

## Stack

n8n · Google Places API · Google Sheets · OpenAI GPT-4.1 · SMTP

---

Built by **Luis E. Giraldo** — n8n & AI automation engineer (Digitrion). Available on Upwork.
