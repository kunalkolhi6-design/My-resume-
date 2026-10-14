# CRIMINAL RECORD — the complete manual

Your portfolio is **one self-contained file: `index.html`** (plus `cover.jpg`,
the social-share card). No build step, no dependencies, no internet needed.
Everything below — editing, passwords, eggs, deploy — is inside that file.

Files in this folder:

| File | What it is |
|---|---|
| `index.html` | **The deliverable.** Edit this, host this. |
| `cover.jpg` | 1200×630 share card shown when the link is posted anywhere. |
| `README.md` | This manual. |
| `archive-paper-v2.html` | Backup: the paper theme before the editor existed. |
| `archive-dark-fbi.html` | Backup: the original dark FBI draft. |

Local preview: `python3 -m http.server 8080` in this folder, then open
`http://localhost:8080`.

---

## 1. Officer mode (editing) — passwords & keys

**How to enter:** click `· officer access ·` at the very bottom of the page,
or press **Ctrl+Shift+E** (Mac: **Cmd+Shift+E**). A password box appears.

| Thing | Value |
|---|---|
| **Default password** | `case-officer` |
| Change it | Officer panel → **Password** button (asks old, then new, twice). |
| Where the password lives | Only in *your* browser (`localStorage` key `cr-pass-v2`). Visitors' browsers use the default until they change it — which they can't, because only the unlocked browser shows the panel. |
| Session unlock | `sessionStorage` key `cr-unlocked-v2` — stays unlocked until the tab closes. |
| Your edits | `localStorage` key `cr-content-v2` — per browser, until you **Export file**. |
| Exit | Panel → **Exit officer mode**, or Ctrl/Cmd+Shift+E again. |

> Honest security note: this is a portfolio lock, not a bank vault. The point
> is that visitors never *see* edit controls. Someone determined with devtools
> on their own machine could poke it — but it's their machine, and your real
> content ships inside the exported file anyway.

### Editing once you're in

- **Any text:** click it and type. Click away to save ("Saved in this browser").
  Enter also saves; Esc cancels.
- **Controls never cover text** — every card's buttons sit in a footer bar
  under it: ↑ ↓ move · ⧉ duplicate · ✕ delete · ▣ swap image · ⤢ open case file.
- **Images (▣):** mugshot, every exhibit hero, every gallery plate, tool
  logos, fingerprint frames, and the seal/your logo. Uploads are compressed
  automatically (max 1400 px, paper-white background for transparent PNGs).
- **Links (✎):** social rows and list links ask for a URL (`https://…` or
  `mailto:…`).
- **Add buttons** (dashed): add favourites, charges, jobs, exhibits, plates,
  results, quotes, tools, statements, timeline rows…
- **Your logo:** ▣ on the seal (top-left), or panel → **Logo**. Replaces the
  drawn bureau seal *and* the browser-tab icon. ↺ restores the drawn seal.
- **Software logos:** ▣ on any tool card uploads the real icon (Ai, Ps, Ae…).
  ↺ restores the drawn one.
- **Fingerprint PNGs:** ▣ per frame, or the dashed button under the grid to
  load up to 10 at once, left to right. ↺ per frame restores the scribble.
- **Availability status:** click the badge under the header (or panel →
  **Status**) to cycle: Open for work → Booked this month → On a job — back soon.
- **Sound:** panel → **Sound: off/on**. Typewriter clacks while you type, ink
  thud on stamps. Off by default, remembered per browser.
- **Save now** forces a save; **Reset all** wipes this browser's edits back to
  the built-in placeholders.
- **Export file** (the important one): downloads a fresh `index.html` with all
  your edits, logo, prints and images baked in. **That file is what you
  deploy.** Upload it anywhere as `index.html`.

---

## 2. What visitors see (feature list)

Paper theme: white scanned paper, black ink, red only for stamps. Sections:
01 Tools used to conduct crime · 02 Charges filed · 03 Criminal record (job
history accordion) · 04 Classified exhibits (projects) · 05 Physical evidence
(skill bars) · 06 Modus operandi (services) · 07 Witness statements ·
08 Known movement (timeline) · 09 Agent's notes · 10 Submit a lead.

- **Project case files:** click any exhibit card → popup file with role,
  client, timeline, tools, story, plates, results, quote. ← → buttons move
  between cases with neighbour titles shown.
- **Discipline filters:** chips above Exhibits (All / Brand / Motion /
  Illustration / Print / Paint / Build) with live counts; remembered.
- **Availability badge + IST clock** under the header; clock ticks every 30 s.
- **Case index:** `INDEX` in the top strip or **Ctrl/Cmd+K** — searchable
  drawer of every section, project, tool, charge, arrest, witness, year.
- **Minimap:** thin tick rail on the right edge (wide screens) — where you
  are, click to jump.
- **Lightbox:** click a hero image or plate inside a case file. Arrows / ← →
  move, wheel zooms 1–3×, drag pans, double-click 1×/2×, Esc closes.
- **Darkroom:** ◐ button (bottom-right) flips to a negative-dark theme;
  remembered. A warm safelight follows the cursor in darkroom.
- **Share card:** link previews show `cover.jpg`. On deploy, make the
  `og:image` URL absolute (see §5).
- **Brief builder:** the lead form adds budget band, deadline and how-they-
  found-you to the email it drafts.
- **Redactions:** black bars reveal on hover. **R** reveals all at once.
- **Accessibility:** skip link, live-region toasts, focus outlines, popup
  focus trap-and-return, reduced-motion respected everywhere.
- No loading screen — the file opens straight onto page 01.

---

## 3. Keyboard & mouse cheat-sheet

| Input | Effect |
|---|---|
| Ctrl/Cmd + Shift + E | Officer mode in/out |
| Ctrl/Cmd + K | Open the case index |
| R | Declassify all redactions |
| Esc | Puts down stamp → closes tray → lightbox → case file → index → password box (in that order) |
| Enter / Space on a focused exhibit card | Opens its case file |
| ← → | Move between case files / lightbox images |
| Wheel in lightbox | Zoom 1–3× (drag to pan while zoomed) |
| Click text (officer mode) | Edit it |
| ↑ ↑ ↓ ↓ ← → ← → B A | See §4 🙂 |

---

## 4. Easter eggs & visitor toys (complete list)

1. **Konami code** — ↑ ↑ ↓ ↓ ← → ← → B A: redaction-bar confetti rains down,
   "Full declassification achieved."
2. **Seal triple-click** — click the agency seal (or your uploaded logo) three
   times within a second: margin-note toast + ink thud.
3. **Stamp tray (⊙ button, bottom-right rail)** — pick a rubber stamp
   (HIRE HIM / APPROVED / SEEN / NOT GUILTY), click the paper to slam it down
   at a random tilt. Stamps live in *that visitor's* browser only
   (`cr-stamps`), survive reloads, cap at 60, "wipe my stamps" clears them,
   and printed copies stay clean. Esc puts the stamp down.
4. **Fingerprint scan** — click any of the ten prints: red scan line sweeps,
   "MATCH 41 OF 41 — ID CONFIRMED".
5. **Height pin** — hover the mugshot: dashed measure line with live cm
   readout; click pins it to the record, click again removes.
6. **Card tilt** — exhibit & tool cards lean toward the cursor (fine pointers
   only).
7. **Hover redactions** — black bars leak their text on hover.
8. **Typewriter note** — the agent's note types itself when it scrolls in.
9. **Footer joke** — "( made with one html file )" plus the warning box that
   admits the whole thing is a joke made with love.
10. **Sounds (opt-in)** — panel → Sound: typewriter clacks while editing,
    stamp thuds on reveals. Off by default.

---

## 5. Deploy checklist

1. Officer mode → replace placeholders (list below) → swap logo/prints/photos.
2. **Export file** → you get the final `index.html`.
3. Open the exported file once, find `<meta property="og:image" content="cover.jpg">`
   and the `twitter:image` tag, and make them absolute, e.g.
   `https://yourdomain.com/cover.jpg`. Upload `cover.jpg` next to it.
4. Host: drag the folder onto **Netlify Drop**, or push to **GitHub Pages /
   Vercel / Cloudflare Pages** as the root `index.html`. Done.

### Placeholders still wearing fake names

- Your real name (header, placard, statements…) — click and type.
- OCR string / file numbers / record ID / DOB-ish fields.
- Email, phone, five social links (✎ for URLs).
- The nine projects, three jobs, charges, quotes — swap or delete (✕).
- Mugshot sketch → your photo (▣), project plates (▣ per card).
- Logo (▣ on seal / panel Logo), fingerprint PNGs, tool software logos.

---

## 6. Storage keys (per browser)

| Key | Holds |
|---|---|
| `cr-content-v2` | Your edits, until exported |
| `cr-pass-v2` | Officer password |
| `cr-unlocked-v2` (session) | Unlocked-this-tab flag |
| `cr-filter` | Last discipline filter |
| `cr-dark` | Darkroom on/off |
| `cr-sound` | Sounds on/off |
| `cr-stamps` | Visitor's rubber stamps |

Clearing site data resets everything to factory placeholders.

---

## 7. Troubleshooting

- **Page looks like empty paper / sections missing:** hard-reload
  (Ctrl/Cmd+Shift+R). If it persists, open the browser console and tell me the
  red line.
- **Edits "lost" on another machine:** edits live in the browser until you
  Export. Always deploy the *exported* file.
- **Preview boxes here block native dialogs/storage:** that's why the file
  uses in-page confirm/prompt boxes and storage guards — normal browsers are
  fine either way.
- **Want an old look back:** `archive-paper-v2.html` (pre-editor paper) and
  `archive-dark-fbi.html` (dark FBI draft) are untouched backups.

---

## 8. Version history, one line each

- v1 dark FBI draft → v2 paper theme per your reference image →
- v3 tools-as-crime-instruments with drawn SVG icons →
- v4 officer mode (password editor, no code) →
- v5 popup case files per project →
- v6 edit-controls layout fix (nothing overlaps text) →
- v6.5 print/PDF button removed →
- v7 the big batch: filters, availability + IST clock, brief builder, index
  drawer, minimap, lightbox, share card, darkroom, Konami + seal eggs,
  optional sounds, accessibility pass →
- v8 your-logo & fingerprint-PNG uploads, loading screen removed, software
  logos per tool →
- v9 the interactive layer: stamp tray, print scan, height pin, card tilt,
  darkroom safelight, lightbox zoom.

*End of document. The bureau thanks you for your cooperation.*
