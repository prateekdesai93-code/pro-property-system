# Property Management System (plain HTML version)

A premium, dark-mode dashboard for landlords — properties, tenants, leases,
rent tracking with automatic reminders, and maintenance requests. Everything
runs directly in the browser; there is **no build step, no npm, and no
server**. Your data is saved privately on your own device using the
browser's local storage.

## Files in this folder

```
index.html          ← Dashboard (open this one first)
properties.html      ← Properties list, add/edit, assign tenants
tenants.html         ← Tenant directory
rent.html            ← This period's rent status + full payment history
maintenance.html     ← Maintenance request tracker
settings.html        ← Profile, currency, due-day defaults, accent color, backup

css/styles.css        ← All styling (one file, easy to tweak colors/spacing)
js/store.js           ← Data layer — reads/writes your data to local storage
js/ui.js               ← Shared sidebar, modals, and toast notifications
js/dashboard.js        ← Logic for index.html
js/properties.js       ← Logic for properties.html
js/tenants.js          ← Logic for tenants.html
js/rent.js             ← Logic for rent.html
js/maintenance.js      ← Logic for maintenance.html
js/settings.js          ← Logic for settings.html

assets/favicon.svg    ← The little icon shown in the browser tab
```

Every page is a normal HTML file that loads `css/styles.css` and a couple of
`.js` files with plain `<script>` tags — no bundler, no compiling, nothing
to install. You can open `index.html` straight from your computer (double
click it) and the whole app works.

## Try it on your computer right now

Just double-click `index.html`. It opens in your browser and works
immediately — add a property, assign a tenant, record rent, everything
saves automatically as you go.

## Publish it for free on GitHub Pages (so you have a real web address to share)

1. Create a new, empty repository on GitHub (or use one you already have) —
   for example `property-dashboard`.
2. On the repository page, click **Add file → Upload files**, then drag
   this entire folder's contents in (`index.html`, `properties.html`,
   `css/`, `js/`, `assets/`, everything) and commit them to the `main`
   branch.
3. Go to **Settings → Pages**. Under "Build and deployment", set
   **Source** to **Deploy from a branch**, choose branch **main** and
   folder **/ (root)**, then click **Save**.
4. Wait about a minute, then visit
   `https://<your-github-username>.github.io/<repository-name>/`.

That's the whole process — no GitHub Actions, no build workflow, and no
`docs/` folder needed. GitHub just serves the files exactly as you
uploaded them, so whatever you see on your computer is exactly what your
visitors will see.

**To update the live site later:** edit the files, then upload the changed
ones again (or drag the whole folder in again) and commit — GitHub Pages
picks up the change automatically within a minute or so.

## How rent reminders work

Since there's no server running in the background, reminders work by
checking, every time you open the app, whether each active lease's current
rent period is due soon or overdue (based on the "Reminder lead time" you
set in Settings). Anything that needs attention shows up on the Dashboard
and Rent page, and a single click opens a pre-filled email to that tenant
in your own email app.

## Data & privacy

All data lives only in *your* browser's local storage — nothing is sent
anywhere, and there is no account or login. That also means:

- Data does **not** sync between devices or browsers automatically.
- Clearing your browser's site data/history for this page will erase it.
- Use **Settings → Backup & Restore** to download a `.json` backup
  regularly, and to restore it later or move it to another device.

## Customizing

- **Colors / spacing:** everything is in `css/styles.css`, using plain CSS
  custom properties (`--accent`, `--bg`, `--text`, etc.) near the top of
  the file.
- **App name / branding:** edit the `<title>` tag and the "Property
  Manager" text near the top of `js/ui.js` (`renderShell` function).
- **Currencies:** add more options to the `CURRENCIES` list in
  `js/settings.js` and `CURRENCY_LOCALE` in `js/store.js`.
