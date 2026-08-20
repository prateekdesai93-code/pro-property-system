# Property Management System (single-file, black &amp; white, password-locked)

A stark black-and-white dashboard for landlords — properties, tenants,
leases with security deposits and renewal reminders, rent tracking with
automatic reminders and bank statement import, numbered tenant invoices
and statements (with quantity/unit-price line items, credit notes, and
paid/unpaid tracking), professional letterhead-style
invoices/statements/receipts, a finances tracker for every dollar spent
per property, full-portfolio and per-tenant Excel exports, and
maintenance requests. Runs entirely in the browser, no build step, no
npm, no server. Locked behind a simple access code you set yourself.

## What's in this folder

Just 7 files — no folders, nothing to lose during upload:

```
index.html          ← Dashboard (open this one first)
properties.html      ← Properties list, add/edit, assign tenants, deposits, renewals
tenants.html         ← Tenant directory, invoices, statements, per-tenant Excel export
rent.html            ← This period's rent status, payment history, bank import
maintenance.html     ← Maintenance request tracker (with cost tracking)
finances.html        ← Expense log + income/expense summary per property
settings.html         ← Profile, currency, charge items, invoicing, lease renewals, backups
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
  picking. Amounts always show two decimal places (e.g. R100.09) — no
  rounding to whole units, so real balances and invoice totals are never
  hidden by the display.
- **Custom symbol override** — if your currency isn't listed, or you just
  want a different symbol, type it into "Custom symbol override" in
  Settings → Rent Defaults. Once set, it replaces the symbol everywhere in
  the app, including invoices, statements, receipts, and the Finances page.
- **Theme** — Settings → Theme has two buttons: Dark (black background,
  the default) and Light (white background). Both are still pure black
  and white — just inverted — so pick whichever is easier to read.

## Charge items &amp; quantity on invoices (Settings + Tenants page)

Settings → **Charge Items** is where you set up the things you bill
often — Rent, Water, Electricity, Refuse, Sewerage, or anything else —
each with its own fixed unit price. Add, edit, or delete as many as you
want; a new install starts with five common presets already there
(prices set to 0 until you fill them in).

When you invoice a tenant, each line now has a **Preset** dropdown next
to the description — pick one and it fills in the description and unit
price for you. Set the **Qty** (quantity) and the **Amount** calculates
itself as quantity × unit price. You can still type over the description,
quantity, unit price, or amount by hand at any time — the preset is a
shortcut, not a requirement, so one-off or custom charges work exactly as
before. Printed invoices show the Qty and Unit Price columns whenever a
line item has them; older invoices without that detail still print
cleanly with just Description and Amount.

## Security deposits &amp; deposit receipts (Properties page)

When you assign a tenant to a property, there's a "Security deposit"
field. Once set, the property card shows **"Deposit held: [amount]"** for
as long as the lease is active. Click **Edit Lease** any time to update
the rent, due day, lease end date, or deposit amount, or to check the box
marking the deposit as **returned** (with the amount and date you gave
back) — the card then shows "Deposit … returned [date]" instead. If a
lease ends before you've marked the deposit returned, the property card
keeps reminding you with a note like "Still owe [tenant] [amount] deposit
back" even though the unit now shows vacant, so it doesn't get forgotten.

Whenever a lease has a deposit on it, the Edit Lease modal has a **Print
Deposit Receipt** button — it prints a signed-and-dated-style receipt
(with signature lines for you and the tenant) confirming either that you
received the deposit, or, once you've checked "returned," that you gave
it back. Good for handing to a tenant on move-in or move-out day.

## Lease renewals (Properties &amp; Dashboard)

Give a lease an optional **lease end date** — when you assign a tenant,
or later via Edit Lease — and this app will start reminding you as that
date approaches:

- The property card shows **"Lease renews in N days"** once you're inside
  the lead time, or a red **"Lease ended N days ago — still marked
  active"** warning if the date has already passed and you haven't
  renewed or ended it.
- The Dashboard gets a **Renewals Due** stat and a **Leases Renewing
  Soon** list.
- How far ahead you get warned is configurable in Settings → Rent
  Defaults → **Lease renewal lead time** (default 60 days).

Leave the end date blank for a month-to-month lease with no fixed term —
nothing renewal-related shows up for those, exactly as before.

## Vacancy tracking (Properties &amp; Dashboard)

Every vacant property card now shows **"Vacant · N days"** — counted from
whenever its last lease ended (or since you added the property, if it's
never been leased). The Dashboard adds a **Longest Vacancy** stat and a
**Vacant Units** list so you can see at a glance which unit has been
sitting empty the longest.

## Maintenance costs (Maintenance page)

Every maintenance request has an optional **Cost** field — log what a
repair actually cost when you create the request, or click **Edit** on
any existing request to add or update it later. Costs you log here
automatically show up on the Finances page under the "Maintenance"
category, no extra data entry needed.

## Finances (page) — track spending per property

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

Each tenant row has these actions (Invoice/Statement enabled once they
have a lease):

- **Invoice** — opens an itemized invoice starting with a "Rent" line
  pre-filled from their lease. Add as many extra lines as you want —
  pick from your Charge Items presets or type your own, set a quantity,
  and the amount fills in automatically (still editable by hand) — each
  line has its own editable description, quantity, unit price, and
  amount, and remove any line you don't need. Every invoice is
  automatically given a sequential **invoice number** (`INV-0001`,
  `INV-0002`, …) — the modal shows you which number it'll be before you
  save. Saving records the invoice in that tenant's history and opens
  your browser's print dialog with a clean, professional letterhead-style
  invoice — choose "Save as PDF" there to get a file to email, or print
  it directly. No external software or internet connection needed for
  this.
- **Statement** — pick a date range and see every invoice charged (shown
  with its invoice number), every rent payment received, and every
  **credit note** issued to that tenant in that window, with a running
  balance, plus totals for charged / paid / credited / balance due. Each
  invoice line has a **Paid / Unpaid** pill you can click to toggle — a
  quick way to track which invoices are settled without it affecting
  your recorded rent payments. Credit note rows have their own **Edit**
  button right there in the ledger. Use **Print** the same way as
  invoices (browser print → Save as PDF), or **Export to Excel** for a
  spreadsheet version (needs internet the first time, same as the
  Finances export above).
- **Credit Note** — records a credit against a tenant's account (a
  deposit refund, a discount, a billing correction, a write-off, or
  anything else) that reduces what they owe without touching your
  invoice or rent-payment records. Pick a reason from the suggestions
  (or type your own), an amount, a date, and an optional note. It shows
  up immediately on that tenant's Statement, subtracted from the running
  balance, and can be edited or deleted at any time from either the
  Tenants page or directly from the Statement ledger.
- **Export (download icon)** — downloads a single Excel workbook with
  this tenant's full profile, lease and deposit history, every rent
  payment, every invoice (with line items on their own sheet), and every
  credit note — a complete record for one tenant, separate from the
  date-ranged statement above.

### Credit notes and the "needs review" items from an imported backup

If your data was imported from another system (see Backups below), some
historical entries may not have been fully classified — was it a deposit
refund, a discount, a write-off, something else? Rather than leaving
those in a separate spreadsheet you'd have to cross-reference by hand,
they're imported as ordinary credit notes with a reason of **"Needs
Review"** and a note explaining exactly what the old system recorded and
why it was ambiguous. Open the tenant's Statement, find the flagged
entry (its date and amount will match the old record), and use the Edit
button to correct the reason, adjust the amount, or delete it if it
doesn't apply — once you're done, it's an ordinary credit note like any
other.

### Invoiced rent amounts feed the Rent page

If you invoice a tenant for the current period — say Rent plus an
Electricity line — the Rent page and Dashboard now show that invoice's
total as what's owed for the period, instead of just the flat lease rent.
You'll see a small **"Amount from invoice"** note next to that period so
it's clear where the number came from. Skip invoicing entirely and
nothing changes — the flat lease rent is used exactly as before.

### Invoice numbering (Settings → Invoicing)

Invoice numbers are assigned automatically and never reused, even if you
delete an invoice later — each one just gets the next number in line. In
Settings you can:

- Change the **prefix** (default `INV-`) — e.g. use your company initials
  or a property code instead.
- Set the **next invoice number** — useful if you're switching from paper
  invoices or another tool and want to continue an existing sequence
  instead of restarting at 1.

One thing worth knowing: since all data lives in your browser only (see
Data & privacy below), if you invoice tenants from more than one browser
or computer, each keeps its own separate counter and could produce
duplicate numbers. If that matters to you, invoice from one browser/
computer, or export/import a backup to keep one running sequence.

## Backups (Settings page)

There are two different kinds of backup, for two different purposes:

- **Export backup (.json)** — this is the one that matters for safety.
  It's the exact copy of your data used to **restore** everything if you
  clear your browser, switch computers, or something goes wrong. Download
  this regularly and keep it somewhere safe.
- **Export full backup (.xlsx)** — a human-readable Excel workbook of
  your entire portfolio, with a cover sheet showing your company name and
  the date it was generated, then a sheet each for Properties, Tenants,
  Leases & Deposits, Rent Payments, Invoices, Invoice Line Items, Credit
  Notes, and Expenses. This is for opening in Excel or Google Sheets — to
  hand to an
  accountant, a new property manager, or just to have a readable record.
  **It is not used to restore data** — use the .json backup for that.

Both need an internet connection the first time you generate an .xlsx
file in a browser session (it loads a small spreadsheet library); the
.json backup works fully offline. One honest limitation: the free
spreadsheet library this app uses can't apply bold text or colored cells,
so the .xlsx files are clean and well-organized with readable column
widths, but not visually styled the way the printed invoices/statements/
receipts are — those get the full letterhead treatment because they're
built as plain HTML instead.

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
  including deposits, lease end dates, expenses, invoice history (with
  paid/unpaid status), charge item presets, and the invoice counter —
  see Backups above for how this differs from the Excel export.
- Any file you upload (bank statement, backup) is read entirely in your
  browser and never leaves it.

## Customizing

Each page carries its own `<style>` and `<script>` blocks — open any file
in a text editor to tweak colors, wording, or logic. No build tools
needed.
