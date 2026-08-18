# Property Management System (single-file, black &amp; white, password-locked)

A stark black-and-white dashboard for landlords — properties, tenants,
leases, rent tracking with automatic reminders, and maintenance requests.
Runs entirely in the browser, no build step, no npm, no server. Locked
behind a simple access code you set yourself.

## What's in this folder

Just 6 files — no folders, nothing to lose during upload:

```
index.html          ← Dashboard (open this one first)
properties.html      ← Properties list, add/edit, assign tenants
tenants.html         ← Tenant directory
rent.html            ← This period's rent status + full payment history
maintenance.html     ← Maintenance request tracker
settings.html        ← Profile, currency, due-day defaults, backup
README.md            ← This file
```

## Setting your customer's access code — do this before you hand it over

Every visitor has to type a code before they can see anything. Right now
that code is set to `changeme-2026`, and you need to change it before
publishing, or anyone who has this README can get in.

1. Open `index.html` in a plain text editor (Notepad, TextEdit, VS Code —
   anything works).
2. Press Ctrl+F / Cmd+F and search for `changeme-2026`.
3. Replace it with whatever code you want to give this customer — for
   example `"smith-jan-2026"`. Keep the quote marks around it.
4. **Repeat this in all 6 `.html` files** — each page checks its own copy
   of the code, so if you skip one, that page will still ask for the old
   code. (This is quick to do with your editor's "Find in Folder / Replace
   in Files" feature if it has one — search for `changeme-2026` across all
   6 files at once and replace every occurrence.)
5. Save all 6 files, then upload them to GitHub as normal.

Give your customer the web address plus the code you chose. The first
time they visit, they'll see an "Enter Access Code" screen; once they type
it correctly, that browser stays unlocked (it won't ask again on that
device unless they clear their browser data).

**Be honest with yourself about what this does and doesn't do:** this app
has no server, so the code lives right inside the page. Anyone who opens
their browser's "View Page Source" can read it in plain text. It's a real
deterrent against a customer sharing the link casually or a stranger
stumbling onto it — not a lock that would stop someone determined to get
in. Don't put anything you'd consider truly sensitive behind it. If you
ever want a version that can't be bypassed this way, that needs a small
server component (a real login) — let me know and I can help you plan
that out.

## Try it on your computer right now

Double-click `index.html`, type in whatever code is currently set (the
default is `changeme-2026` until you change it per the steps above), and
you're in.

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

## Customizing

Each page carries its own `<style>` and `<script>` blocks — open any file
in a text editor to tweak colors, wording, or logic. No build tools
needed.
