# Best Buy Canada Price Watch 🍁

A simple, focused service to notify users when a BestBuy.ca product reaches a target price. I built this to track SKUs or product URLs, run daily price checks against the Best Buy Products API, and send email alerts with unsubscribe links.

## Why

Many customers ask when an item will go on sale. This repo is a small, production-minded implementation that solves that exact need while staying compliant with Best Buy policies by using the public API.

## What it does

* Accepts alerts by SKU or BestBuy.ca URL.
* Stores minimal data: email, sku, target price, active flag.
* Runs a daily, batched check of active SKUs.
* Sends email notifications when price <= target.
* Provides an unsubscribe link that deactivates the alert.

## Tech choices

* Frontend: Next.js + React + TypeScript. Use API routes for server side operations.
* Backend: Node.js + TypeScript. Serverless functions or a small API server are fine.
* Database: Firestore or Supabase.
* Email: SendGrid or Mailgun.
* Scheduler: GitHub Actions cron or Cloud Scheduler.

## Quick start

1. Clone the repo and install dependencies.

```bash
git clone https://github.com/<you>/bestbuy-price-watch.git
cd bestbuy-price-watch
npm install
```

2. Create `.env.local` with these variables:

```
BESTBUY_API_KEY=
SENDGRID_API_KEY=
EMAIL_FROM=
APP_HOST=
# DB credentials depending on your choice
```

3. Run the dev server

```bash
npm run dev
```

4. Deploy and configure a daily scheduler to run the price check job.

## API endpoints (examples)

* `POST /api/alerts`  Create an alert. Body: `{ email, sku, targetPrice }`.
* `GET /api/unsubscribe?token=...`  Deactivate the alert linked to the token.
* Internal: `GET /api/bestbuy/price?sku=...`  Fetch product data from Best Buy API.

## Data model

`alerts` collection

* id: string
* userEmail: string
* sku: string
* targetPrice: number
* currency: string (default CAD)
* createdAt: timestamp
* active: boolean
* unsubscribeToken: string

Optional `trackedSkus` collection to cache lastPrice and lastChecked.

## Scheduler and batching

Batch SKUs to reduce API calls. The Best Buy API supports queries like `products(sku in(111,222))`. Run once per day unless you have a use case that needs higher frequency.

## Legal and privacy notes

* Use the Best Buy Products API where possible. Do not scrape BestBuy.ca without written permission.
* Store only what you need. If you plan to handle many users, add privacy, retention and data deletion policies.

## Contributing

If you want to contribute, open an issue or a pull request. Keep changes small and include tests for business logic where appropriate.

## License

MIT

## Contact

Open an issue or reach me at the contact on my GitHub profile.
