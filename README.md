# Cdeskspace

Cdeskspace is a lightweight workspace operations notebook for coworking teams. It brings customer records, desk and space subscriptions, payments, reports, and operational notes together in one place.

The initial interface is adapted from a single-file HTML prototype. It is designed to be easy to try without a build step, while leaving room to add account-based cloud sync with Supabase in a later phase.

## Current prototype

- Overview of received payments, active subscriptions, balances, and recent activity.
- Create subscriptions and record payments, including partial payments.
- Capture start and end times for bookings and hourly sessions.
- Start an open-ended session on any plan with time-based prices, keep it pending until checkout, then log its actual end time and calculate the charge using the shortest listed price tier that covers the elapsed time. If the session exceeds the largest tier, that tier repeats; for billing, a month is 30 days.
- Log non-subscription income, expenses, and cash counts with clear/held amounts.
- Keep corrections as signed adjustment records, separate from income and expenses, and save dated operational notes.
- Record whether subscription customers are new or returning, and note client status on other income records when relevant.
- Customer, subscription, and payment registers.
- Date-based reports and operational notes.
- JSON import and export.
- Optional privacy blur after inactivity, with a choice between a full-screen unlock popup and a less obstructive blur that leaves workspace navigation available; blur-only mode provides a header button to show details again.
- Local browser storage; no account or cloud sync is connected yet.

New workspaces start with no customer or activity records; only the default plans and payment methods are preconfigured. Use **Settings & data → Reset workspace** to clear all locally saved records and restore those defaults. Reset requires confirmation and cannot be undone, so export a JSON backup first if you may need the data. Do not enter real customer information into this prototype: browser storage is specific to the current browser profile and is not an authenticated or encrypted cloud database.

## Run locally

Open `index.html` in a modern browser. No package installation or build command is required. Changes are saved in that browser's local storage.

For a local web server, run:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Live preview

The public static prototype is available at <https://joelevic.github.io/cdeskspace/>.

## Data backup

Use **Export JSON** to download a backup and **Import JSON** to load a previously exported file. Imports replace the current local dataset, so export a backup before importing. Keep exported files private because they may contain customer and payment information.

## Planned next step: Supabase

Supabase is not configured in this prototype. The planned integration will add authentication and per-user cloud storage, with explicit sync status and safe handling for local drafts. Do not add Supabase credentials to this repository; public client configuration belongs in environment variables, and privileged service keys must never be shipped to the browser.
