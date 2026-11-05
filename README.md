# Cdeskspace

Cdeskspace is a lightweight workspace operations notebook for coworking teams. It brings customer records, desk and space subscriptions, payments, reports, and operational notes together in one place.

The initial interface is adapted from a single-file HTML prototype. It is designed to be easy to try without a build step, while leaving room to add account-based cloud sync with Supabase in a later phase.

## Current prototype

- Overview of received payments, active subscriptions, balances, and recent activity.
- Create subscriptions and record payments, including partial payments.
- Customer, subscription, and payment registers.
- Date-based reports and operational notes.
- JSON import and export.
- Optional privacy blur after inactivity.
- Local browser storage; no account or cloud sync is connected yet.

The starter data is fictional demo content. Do not enter real customer information into this prototype: browser storage is specific to the current browser profile and is not an authenticated or encrypted cloud database.

## Run locally

Open `index.html` in a modern browser. No package installation or build command is required. Changes are saved in that browser's local storage.

For a local web server, run:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Data backup

Use **Export JSON** to download a backup and **Import JSON** to load a previously exported file. Imports replace the current local dataset, so export a backup before importing. Keep exported files private because they may contain customer and payment information.

## Planned next step: Supabase

Supabase is not configured in this prototype. The planned integration will add authentication and per-user cloud storage, with explicit sync status and safe handling for local drafts. Do not add Supabase credentials to this repository; public client configuration belongs in environment variables, and privileged service keys must never be shipped to the browser.
