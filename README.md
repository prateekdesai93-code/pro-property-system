# Property Management System (single-file pages)

A premium, dark-mode dashboard for landlords — properties, tenants, leases,
rent tracking with automatic reminders, and maintenance requests. Runs
entirely in your browser. No build step, no npm, no server, and — this
time — **no separate folders to lose during upload.**

## What's in this folder

Just 6 files. That's the whole app:

```
index.html          ← Dashboard (open this one first)
properties.html      ← Properties list, add/edit, assign tenants
tenants.html         ← Tenant directory
rent.html            ← This period's rent status + full payment history
maintenance.html     ← Maintenance request tracker
settings.html        ← Profile, currency, due-day defaults, accent color, backup
README.md            ← This file
```

Each `.html` file is fully self-contained — its styling and code are built
directly into the file itself (no `css/` or `js/` folder involved). That
was the cause of the blank white page you saw last time: GitHub's upload
box silently dropped the `css` and `js` folders, so the pages had no
styling or code to run. That can't happen anymore, because there's nothing
left to drop — every file carries everything it needs on its own.

## Try it on your computer right now

Double-click `index.html`. It opens in your browser and works
immediately — add a property, assign a tenant, record rent, everything
saves automatically as you go.

## Publish it for free on GitHub Pages

1. Open your repository on GitHub (the one you already made — e.g.
   `pro-property-system`).
2. If old files are still in there from before, delete them first: open
   each old `css` or `js` folder link (if any exist) and remove it, or
   just delete the whole repo and create a fresh one — either is fine.
3. Click **Add file → Upload files**.
4. Drag in all 6 files from this folder at once — `index.html`,
   `properties.html`, `tenants.html`, `rent.html`, `maintenance.html`,
   `settings.html`, and `README.md`. Make sure the box shows exactly 7
   files listed before committing (6 `.html` + this `README.md`) — no
   folders should appear this time, since there aren't any.
5. Click **Commit changes**.
6. Go to **Settings → Pages**. Under "Build and deployment", set
   **Source** to **Deploy from a branch**, branch **main**, folder
   **/ (root)**, then **Save**.
7. Wait about a minute, then visit
   `https://<your-github-username>.github.io/<repository-name>/`.

**To update the site later:** edit a file, then drag that same file back
into **Add file → Upload files** to replace it, and commit. GitHub Pages
picks up the change within a minute or so.

## How rent reminders work

Every time you open the app, each active lease's current rent period is
checked against today's date. Anything overdue or due within your
configured lead time (Settings → Rent Defaults) shows up on the Dashboard
and Rent page, where one click opens a pre-filled email to that tenant in
your own email app.

## Data & privacy

All data lives only in *your* browser's local storage — nothing is sent
anywhere, no account, no login.

- Data does **not** sync between devices or browsers automatically.
- Clearing your browser's site data for this page will erase it.
- Use **Settings → Backup & Restore** to download a `.json` backup
  regularly, and to restore it later or move it to another device.

## Customizing

Since everything is inline, each page's `<style>` block near the top
holds all the colors and spacing, and the `<script>` blocks near the
bottom hold the logic. Open any file in a text editor to tweak it — no
tools required beyond a plain text editor.
