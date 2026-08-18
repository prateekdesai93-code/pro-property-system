# Property Management System (single-file, black &amp; white, password-locked)

A stark black-and-white dashboard for landlords — properties, tenants,
leases with security deposits, rent tracking with automatic reminders and
bank statement import, tenant invoices and statements, a finances tracker
for every dollar spent per property, and maintenance requests. Runs
entirely in the browser, no build step, no npm, no server. Locked behind a
simple access code you set yourself.

## What's in this folder

Just 7 files — no folders, nothing to lose during upload:

```
index.html          ← Dashboard (open this one first)
properties.html      ← Properties list, add/edit, assign tenants, deposits
tenants.html         ← Tenant directory, invoices, statements
rent.html            ← This period's rent status, payment history, bank import
maintenance.html     ← Maintenance request tracker (with cost tracking)
finances.html        ← Expense log + income/expense summary per property
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
4. **Repeat this in all 7 `.html` files** — each page checks its own copy,
   so if you skip one, that page keeps asking for the old code. Most text
   editors have a "Find in Folder / Replace in Files" feature — use it to
   change all 7 files in one go.
5. Save all 7 files, then upload them to GitHub as normal.

**Be honest with yourself about what this does and doesn't do:** this app
has no server, so the code lives right inside the page. Anyone who opens
their browser's "View Page Source" can read it in plain text. It's a real
deterrent against a customer sharing the link casually or a stranger
stumbling onto it — not a lock that would stop someone determined to get
in. Don't put anything you'd consider truly sensitive behind it.

## Currency &amp; theme (Settings page)

- **Currency** — the dropdown lists 47 currencies, each showing its symbol
  right in the list (e.g. "INR (₹)", "EUR (€)") so you can see what you're
  picking.
- **Custom symbol override** — if your currency isn't listed, or you just
  want a different symbol, type it into "Custom symbol override" in
  Settings → Rent Defaults. Once set, it replaces the symbol everywhere in
  the app, including invoices, statements, and the Finances page.
- **Theme** — Settings → Theme has two buttons: Dark (black background,
  the default) and Light (white background). Both are still pure black
  and white — just inverted — so pick whichever is easier to read.

## Security deposits (Properties page)

When you assign a tenant to a property, there's a "Security deposit"
field. Once set, the property card shows **"Deposit held: [amount]"** for
as long as the lease is active. Click **Edit Lease** any time to update
the rent, due day, or deposit amount, or to check the box marking the
deposit as **returned** (with the amount and date you gave back) — the
card then shows "Deposit … returned [date]" instead. If a lease ends
before you've marked the deposit returned, the property card keeps
reminding you with a note like "Still owe [tenant] [amount] deposit back"
even though the unit now shows vacant, so it doesn't get forgotten.

## Maintenance costs (Maintenance page)

Every maintenance request has an optional **Cost** field — log what a
repair actually cost when you create the request, or click **Edit** on
any existing request to add or update it later. Costs you log here
automatically show up on the Finances page under the "Maintenance"
category, no extra data entry needed.

## Finances (new page) — track spending per property

The **Finances** page is where every dollar in and out per property comes
together:

- **Filters** — pick a property (or "All properties") and a date range.
- **Summary** — Income (rent collected), Total Expenses, and Net for that
  property and date range.
- **Expenses by Category** — a breakdown of everything you've spent,
  grouped by category.
- **Log Expense** — record anything that isn't rent or a maintenance
  request: insurance, property tax / levy, a bank loan payment,
  utilities, management fees, or anything else. The category field
  suggests common ones but you can type whatever you want — there's no
  fixed list, add as many custom categories as you need.
- **Export to Excel** — downloads a real `.xlsx` file with every line
  item (rent payments, maintenance costs, and logged expenses) in the
  selected date range and property, ready to open in Excel or Google
  Sheets. This needs an internet connection the first time you use it in
  a given browser session (it loads a small spreadsheet library).

## Tenant invoices &amp; statements (Tenants page)

Each tenant row now has two buttons (enabled once they have a lease):

- **Invoice** — opens an itemized invoice starting with a "Rent" line
  pre-filled from their lease. Add as many extra lines as you want —
  Electricity, Water, a late fee, anything — each with its own editable
  description and amount, and remove any line you don't need. Saving it
  records the invoice in that tenant's history and opens your browser's
  print dialog with a clean, professional-looking invoice — choose "Save
  as PDF" there to get a PDF you can email, or print it directly. No
  external software or internet connection needed for this.
- **Statement** — pick a date range and see every invoice charged and
  every rent payment received for that tenant in that window, with a
  running balance, plus totals for charged / paid / balance due. Use
  **Print** the same way as invoices (browser print → Save as PDF), or
  **Export to Excel** for a spreadsheet version (needs internet the first
  time, same as the Finances export above).

## Try it on your computer right now

Double-click `index.html`, type `property2026` (or whatever you changed
it to), and you're in.

## Publish it for free on GitHub Pages

1. Open your repository on GitHub.
2. Click **Add file → Upload files**.
3. Drag in all 7 `.html` files plus this `README.md`. Check the box shows
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

## Importing a bank statement to fill in rent (Rent page)

Click **Import Bank Statement** at the top of the Rent page and upload a
CSV/Excel export (most reliable) or a text-based PDF from your bank. The
app suggests which tenant each deposit belongs to and shows a review
screen — nothing is ever marked paid without you clicking "Confirm &
Record Payments". Deposits already recorded are automatically flagged and
skipped so re-uploading a statement by mistake won't double-count a
payment.

## Data & privacy

All data lives only in *that visitor's* browser local storage — nothing
is sent anywhere, no account, no login beyond the access code.

- Data does **not** sync between devices, browsers, or visitors — each
  person who unlocks the app has their own separate data.
- Clearing browser site data erases it.
- **Settings → Backup & Restore** downloads/restores a `.json` backup,
  including deposits, expenses, and invoice history.
- Any file you upload (bank statement, backup) is read entirely in your
  browser and never leaves it.

## Customizing

Each page carries its own `<style>` and `<script>` blocks — open any file
in a text editor to tweak colors, wording, or logic. No build tools
needed.
