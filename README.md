# WiDS Zürich — Attendee Card Generator

A simple browser-based tool that lets conference attendees generate a personalised, branded card to share on LinkedIn before the WiDS Annual Conference.

---

## What it does

Attendees visit the page, upload their photo, enter their name and a short line about themselves, and download a ready-to-post 1200×1200px PNG. A suggested LinkedIn caption is provided with a one-click copy button to encourage tagging and sharing.

---

## How to use it

1. Open `wids_card_post.html` in a browser (must be served via a web server — see note below)
2. Upload a photo or paste a LinkedIn photo URL
3. Enter your name and anything else you'd like to share
4. Click **Download PNG**
5. Copy the suggested LinkedIn caption if wanted and post!

---

## File structure

```
wids_card_post.html             ← the entire application
logos/
    QRT.png
    AXA.png
    Swiss_Re.png
    Deloitte.png
    Migros.png
    Finyon.png
    WiDS_Logo_Transparent.png   ← WiDS Zürich logo
```

All files must be in this structure for the logos and branding to appear correctly in the downloaded PNG.

---

## Hosting

The tool is a single HTML file with no backend, no database, and no server-side code. To deploy it, a web developer simply needs to place the files in the correct folder structure on the WiDS website.

**Important:** the tool must be accessed via `http://` or `https://` — it will not work if opened directly from a desktop as a local file. To test locally, run a simple web server from the project folder:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/wids_card_post.html` in your browser.

---

## Technical details

- Runs entirely in the browser — no data is sent to any server
- Photos are processed locally and never uploaded or stored
- PNG export uses [html2canvas](https://html2canvas.hertzen.com/) v1.4.1
- Fonts loaded from Google Fonts: League Spartan, DM Sans, Montserrat, Arimo
- Output: 1200×1200px PNG matching the WiDS Canva branding

---

## Customisation

To update for future conferences, the following values can be edited directly in the HTML file:

| What | Where in the code |
|---|---|
| Conference date | `ac-event-meta` div in the HTML |
| Venue | `ac-event-meta` div in the HTML |
| Gradient colours | `background` in `.attendee-card` CSS |
| Sponsor logos | `logos/` folder + `ac-sponsors` div in the HTML |
| LinkedIn caption | `caption-text` paragraph in the HTML |
| Hardcoded tagline | `ac-name` div in the HTML |

---

## Credits

Built by Heather Driver for WiDS Zürich 2026.