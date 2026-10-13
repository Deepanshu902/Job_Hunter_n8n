# Job_Hunter_n8n

> First time trying n8n, and learning it by building something real with it.

A small n8n workflow that checks company career pages, filters for relevant roles, and emails me the matching jobs with direct apply links.

## Screenshots

**Workflow canvas**

![Workflow canvas](https://github.com/user-attachments/assets/ba39d5d2-3692-4a38-b988-03e1169e0230)

**Email digest received**

![Email digest](https://github.com/user-attachments/assets/ec80eddc-f221-4f87-b7b2-2178706a30c7)

## How it works

1. Trigger (currently manual)
2. Firecrawl node scrapes a careers page to markdown
3. JavaScript Code node parses job title, location and link, then filters by keywords (backend, node, mern, sde, intern, fresher...) and drops senior/lead/sales roles
4. Edit Fields normalises the fields; Remove Duplicates dedupes by link
5. A Code node builds one HTML digest; Send Email (Gmail SMTP) delivers it

**Note:** Before running the workflow, configure your own sender and recipient email addresses in the **Send an Email** node and set up your SMTP credentials in n8n. The exported workflow uses placeholder email addresses; replace them with your own.

## Tested on

- Razorpay (Greenhouse board): 28 listings scraped, 2 matched my filters

## Run it yourself

- Run n8n with Docker (see n8n's official Docker docs)
- Import `Job Hunter.json` into n8n
- Add your own Firecrawl and SMTP credentials in n8n
- No secrets are stored in this repo

## Limitations / next steps

- Only one company so far; per-company parsing may need tweaks
- Greenhouse and Lever have public job APIs that I plan to use instead of scraping where available
- Add a schedule trigger and "only new jobs" tracking
