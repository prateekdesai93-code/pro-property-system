# Property Management System (single-file, black &amp; white, password-locked)

A stark black-and-white dashboard for landlords — properties, tenants,
leases, rent tracking with automatic reminders, bank statement import, and
maintenance requests. Runs entirely in the browser, no build step, no npm,
no server. Locked behind a simple access code you set yourself.

## What's in this folder

Just 6 files — no folders, nothing to lose during upload:

```
index.html          ← Dashboard (open this one first)
properties.html      ← Properties list, add/edit, assign tenants
tenants.html         ← Tenant directory
rent.html            ← This period's rent status, payment history, bank import
maintenance.html     ← Maintenance request tracker
settings.html         ← Profile, currency, theme, due-day defaults, backup
README.md            ← This file
```

## The access code for this app

Right now every page in this folder is set to the code **`property2026`**.
Give this code to whoever you're sharing this app with. If you want a
different code (recommended — especially before selling to a real
customer), see below.

### Changing it

1. Open `index.html` in a plain text editor (Notepad, TextEdit, VS Code —
   anything works).
2. Press Ctrl+F / Cmd+F and search for `property2026`.
3. Replace it with your new code — for example `"smith-jan-2026"`. Keep
   the quote marks around it.
4. **Repeat this in all 6 `.html` files** — each page checks its own copy,
   so if you skip one, that page keeps asking for the old code. Most text
   editors have a "Find in Folder / Replace in Files" feature — use it to
   change all 6 files in one go.
5. Save all 6 files, then upload them to GitHub as normal.

**Be honest with yourself about what this does and doesn't do:** this app
has no server, so the code lives right inside the page. Anyone who opens
their browser's "View Page Source" can read it in plain text. It's a real
deterrent against a customer sharing the link casually or a stranger
stumbling onto it — not a lock that would stop someone determined to get
in. Don't put anything you'd consider truly sensitive behind it.

## Currency &amp; theme (Settings page)

- **Currency** — the dropdown now lists 47 currencies, each showing its
  symbol right in the list (e.g. "INR (₹)", "EUR (€)") so you can see what
  you're picking.
- **Custom symbol override** — if your currency isn't listed, or you just
  want a different symbol, type it into "Custom symbol override" in
  Settings → Rent Defaults. Once set, it replaces the symbol everywhere in
  the app. Leave it blank to use the standard symbol for whatever currency
  you picked above.
- **Theme** — Settings → Theme has two buttons: Dark (black background,
  the default) and Light (white background). Both are still pure black
  and white — just inverted — so pick whichever is easier to read. This
  is a per-browser setting stored with the rest of your data.

## Importing a bank statement to fill in rent (Rent page)

Click **Import Bank Statement** at the top of the Rent page and upload a
file exported from your bank. The app looks through it for deposits and
suggests which tenant each one belongs to — **it never marks anything
paid on its own**. You always see a review screen first and have to click
"Confirm & Record Payments" before anything is saved.

**What to upload:**

- **CSV or Excel export** (recommended, most reliable) — almost every
  bank's online portal has a "Download transactions" or "Export" button
  that produces one of these. The app looks for a date column, a
  description/memo column, and either an "Amount" column or separate
  "Credit"/"Debit" columns — it's flexible about exact column names and
  order, as long as the first row is the headers.
- **PDF statement** — works too, but PDF layouts vary wildly bank to
  bank, so treat every row it finds as a rough guess and double-check the
  date, amount, and tenant before confirming. It cannot read a scanned or
  photographed statement — only a real, text-based PDF export.

**How matching works:**

- A deposit is suggested for a tenant when either the tenant's name shows
  up in the transaction description, or the deposit amount exactly
  matches that tenant's current rent balance and no other active tenant
  shares that same balance.
- If a deposit's amount matches more than one tenant and there's no name
  to go on, it's marked **"Needs your pick"** — pick the right tenant
  from the dropdown in that row before it can be applied. This is on
  purpose: guessing wrong on a same-amount collision would silently mark
  the wrong tenant's rent as paid.
- Anything already recorded (matching tenant, period, and amount) shows as
  **"Already recorded"** and is skipped automatically, so re-uploading
  the same statement twice by mistake won't double-count a payment.
  Deposits that don't match any active tenant's rent amount at all are
  simply left out of the review list (the summary line at the top tells
  you how many were skipped).
- Every payment you confirm shows up in the normal Payment History list
  below, tagged "Bank Transfer" with a note that it came from an import,
  exactly like one you'd record by hand.

The CSV/Excel path runs with plain JavaScript already in this file. The
PDF path loads a PDF-reading library from a CDN the first time you pick a
PDF file, so it needs an internet connection (the CSV/Excel path does
not).

## Try it on your computer right now

Double-click `index.html`, type `property2026` (or whatever you changed
it to), and you're in.

## Publish it for free on GitHub Pages

1. Open your repository on GitHub.
2. Click **Add file → Upload files**.
3. Drag in all 6 `.html` files plus this `README.md`. Check the box shows
   exactly those files before committing — no folders.
4. Click **Commit changes**.
5. Go to **Settings → Pages**. Set **Source** to **Deploy from a branch**,
   branch **main**, folder **/ (root)**, then **Save**.
6. Wait about a minute, then visit
   `https://<your-github-username>.github.io/<repository-name>/`.

**To update the site later:** edit a file, drag it back into **Add file →
Upload files** to replace it, and commit.

## How rent reminders work

Every time the app opens, each active lease's current rent period is
checked against today's date. Anything overdue or due within your
configured lead time (Settings → Rent Defaults) shows up on the Dashboard
and Rent page, with a one-click button that opens a pre-filled email to
that tenant.

## Data & privacy

All data lives only in *that visitor's* browser local storage — nothing
is sent anywhere, no account, no login beyond the access code.

- Data does **not** sync between devices, browsers, or visitors — each
  person who unlocks the app has their own separate data.
- Clearing browser site data erases it.
- **Settings → Backup & Restore** downloads/restores a `.json` backup.
- The bank statement file you upload is read entirely in your browser and
  never leaves it — only the matched transactions you confirm are saved,
  into the same local storage as everything else.

## Customizing

Each page carries its own `<style>` and `<script>` blocks — open any file
in a text editor to tweak colors, wording, or logic. No build tools
needed.
