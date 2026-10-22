# Uluwatu Property — Bali ROI Simulator

Interactive ROI simulator for villa / house investments in Bali.
Live site: https://uluwatupropertyroicalculator.netlify.app/

It is a single static page: all calculations run in the visitor's browser. There is no server, database or build step.

## Two tabs

| Tab | Link | What it includes |
| --- | --- | --- |
| Classic simulation (home page) | `/` | The original simulator: rental income and running costs only. No tabs are shown. |
| Full simulation (hidden for now) | `/#full` | OTA commission, direct bookings, maintenance plan, management services (website + Instagram). Opening this link also shows the tabs. |

Both tabs share the same code. Elements marked `class="full-only"` only show in the Full tab; in the Classic tab the OTA commission is 0, there is no maintenance plan and no management services.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole simulator: layout (HTML), styling (CSS) and calculations (JavaScript) |
| `logo.jpg` | Uluwatu Property logo, shown in the header and embedded in downloaded simulations |
| `netlify.toml` | Netlify settings: no build, publish the repo as-is |

## Making a change

1. On GitHub, open `index.html` and click the pencil icon (Edit).
2. Make the change, then click **Commit changes**.
3. Netlify redeploys the live site automatically within a few seconds.

To undo a change, open the commit history and revert the commit, or redeploy a previous version from the Netlify **Deploys** tab.

## Where things are in `index.html`

| To change… | Look for… |
| --- | --- |
| Default input values (price, rates, occupancy…) | the `value="…"` attribute on each `<input>` (e.g. `id="price"`, `id="r_low"`) |
| Season lengths (14 / 93 / 258 days) | `const DAYS` in the script, and the matching numbers in the HTML table |
| Notary fees (1%) | `const FEES` |
| Seasonal uplifts (+20% high, +40% peak) | `rLow * 1.2` and `rLow * 1.4` in `recalc()` |
| Per-bedroom costs ($120 housekeeper, $50 laundry, $60 electricity) | `const cH`, `cL`, `cE` in `recalc()` |
| ROI rating thresholds ("Excellent return"…) | `heroMsg` in `recalc()` |
| Residual lease value scenarios | the "Residual lease value — 3 scenarios" block in `recalc()` |
| Maintenance plan prices (IDR / month, extra bedroom) and perks | `const PLANS` in the script |
| Default maintenance plan | `checked` on the plan radio buttons (`id="plan_standard"`) |
| USD / IDR exchange rate (17,900) | `id="fx"` |
| OTA commission (15%) | `id="ota"` |
| Management fee base (after OTA or gross) | `id="mgmt_base"` |
| Default tab, hidden Full tab | `let TAB` and the `setTab()` function at the end of the script |
| Downloaded simulation layout | `downloadSim()` |
| Disclaimer text | `class="footer"` (page) and `<footer>` inside `downloadSim()` |

## Preview locally

Open `index.html` in a browser. Everything works offline except that a downloaded simulation will link to the logo instead of embedding it.
