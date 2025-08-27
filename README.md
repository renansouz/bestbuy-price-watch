# BestBuy Price Watch (Canada) 🍁

A lightweight price-alert service for BestBuy.ca products. Users submit a SKU or product URL and a target price; the system checks prices once per day and sends email alerts when the target is met.

## Main topics

* **Overview**

  * Purpose: Notify users when a Best Buy Canada product reaches a specified price.
  * Source: Best Buy Products API (preferred). Avoid scraping unless you have written permission.

* **Features**

  * Create alerts by SKU or URL
  * Daily, batched price checks
  * Email notifications with unsubscribe links
  * Minimal user data stored (email, sku, target price)

* **Tech stack (suggested)**

  * Frontend: Next.js + React + TypeScript
  * Backend: Node.js + TypeScript (API routes / serverless)
  * Database: Firestore or Supabase
  * Email: SendGrid or Mailgun
  * Scheduler: GitHub Actions cron or Cloud Scheduler

* **Quick setup (summary)**

  1. Clone repo and install dependencies.
  2. Add required environment variables (BESTBUY\_API\_KEY, SENDGRID\_API\_KEY, DB credentials, APP\_HOST).
  3. Run dev server: `npm run dev`.
  4. Deploy and configure scheduler to run the daily job.

* **Environment variables (example)**

  * `BESTBUY_API_KEY`, `SENDGRID_API_KEY`, `EMAIL_FROM`, `APP_HOST`, plus DB credentials.

* **Scheduler**

  * Run once per day. Batch SKUs to reduce API calls. Use GitHub Actions or a cloud scheduler.

* **Legal**

  * Use the Best Buy API where possible. Do not scrape BestBuy.ca without explicit permission. Comply with privacy rules when storing emails.

* **Contributing & License**

  * Fork, create a feature branch, open a pull request.
  * MIT License.

* **Contact**

  * Open an issue or contact the repository owner.
