# Summer 2027 Family Week Poll

A single-file HTML app for finding the summer week (June, July, or August 2027) that works for all of your families. No server, no accounts, no database — just one `index.html` you share as a link.

## The flow

**Families** (you send everyone the same link):

1. **Enter family name** — the poll is gated behind a name so every response is identified.
2. **Pick weeks** — all 13 weeks of June–August 2027, each labeled by its Monday (e.g. *Monday, June 28, 2027*). Selections auto-save in their browser.
3. **Send it in** — submitting shows a big **Email my response** button (pre-addressed to the organizer), plus copy-able response link/code as a fallback.
4. **Make adjustments** — reopening the link (or tapping *Make adjustments*) brings back their saved picks. They edit, resubmit, and send the new response — it replaces their old one on the organizer's side automatically (matched by family name).

**Organizer** (you):

- Open the same link with `#admin` on the end (or the small *organizer view* link in the footer).
- When a family emails you their **response link**, just open it — it auto-imports into your dashboard. Or paste response codes into the box, one per line.
- The dashboard shows who's responded (x / 10), a 🎉 banner listing weeks that work for **all** families, green/yellow highlighting for full and near-full availability, and a "sort by most available" option.
- Everything is saved in your browser, so responses can trickle in over weeks.

## Hosting

**GitHub Pages (recommended):** enable it in this repo's settings (Settings → Pages → deploy from branch), then send the resulting URL to your families. Your admin view is that same URL + `#admin`.

**No hosting:** email `index.html` itself to each family; they open it locally and email you the response code, which you paste into your own copy's admin view.

## Configuration

Edit the constants at the top of the `<script>` block in `index.html`:

- `ORGANIZER_EMAIL` — where the **Email my response** button sends responses
- `MONTHS` — which months to offer (0-based; `[5, 6, 7]` = June–August)
- `YEAR`, `TOTAL_FAMILIES` — self-explanatory

## Why response links instead of live syncing?

A pure HTML file can't share a database between 10 households. Instead, each family's picks are packed into a tiny code (a hex bitmask over the 13 weeks) embedded in a link. Opening that link *is* the submission — your admin view decodes and aggregates them all locally.
