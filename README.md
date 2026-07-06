# 2027 Family Week Poll

A single-file HTML app for finding the weeks in 2027 that work for all of your families. No server, no accounts, no database — just one `index.html`.

## How it works

The app has two tabs:

1. **Fill Out Poll** — a family enters their name, checks every week of 2027 that works for them (each week starts on a Monday, e.g. *Monday, June 28, 2027*), and hits **Submit**. They get a short **response code** and one-click buttons to email it back to the organizer or copy a share link.
2. **View Results** — the organizer pastes the response codes (or opens the share links) as they come in. The app aggregates everything and highlights:
   - 🟢 weeks where **all** families are available
   - 🟡 weeks where all but one family is available
   - a bar + count for every other week, with a "sort by most available" option

Responses are saved in the organizer's browser (localStorage), so you can add them as they trickle in over days or weeks.

## Getting started

### Option A: GitHub Pages (recommended)

1. In this repo's settings, enable **GitHub Pages** (Settings → Pages → deploy from branch).
2. Send the resulting URL to your 10 families.
3. Families fill it out and email you their code (the **Email it** button opens a pre-addressed email), or send you the share link.
4. Open the same URL yourself, go to **View Results**, and paste in codes as they arrive. Opening a family's share link imports their response automatically.

### Option B: No hosting at all

Email the `index.html` file itself to each family. They open it locally in any browser, fill it out, and email you the response code. You open your own copy and paste codes into the Results tab.

## Configuration

Open `index.html` and edit the constants at the top of the `<script>` block:

- `ORGANIZER_EMAIL` — where the **Email it** button sends responses
- `YEAR` — change to run the same poll for a different year

## Why response codes instead of live syncing?

A pure HTML file can't share a database between 10 different households. Instead, each family's checked weeks are packed into a tiny code (a hex bitmask of the 52 weeks). Sending that code back to the organizer *is* the submission. The organizer's Results tab decodes and aggregates all of them locally.

If a family submits twice, just paste the new code — a response with the same family name replaces the old one.
