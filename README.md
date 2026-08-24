# New Zion Baptist Church — Website

12 pages, burgundy/gold design system, hosted on GitHub Pages at newzionbaptist.org.

## Pages
| File | Purpose |
|---|---|
| `index.html` | Home |
| `about.html` | Mission, vision, the four-step progression |
| `history.html` | Pastor-by-pastor story: founding, present, incoming |
| `leadership.html` | Current pastoral leadership cards |
| `worship.html` | Sunday livestream, online-worshipper info, service times |
| `events.html` | Google Calendar embed (see "Updating the calendar" below) |
| `teaching.html` | Current sermon series, sermon archive, teaching resources |
| `give.html` | Givelify link and giving info |
| `visit.html` | Address, map, service times, what to expect, visitor form |
| `connect.html` | MailerLite signup, prayer request, membership interest, general contact |
| `lifeline.html` ("Need Help?") | Crisis/pastoral support form, links to Path to Salvation |
| `romanroad.html` | The Roman Road to Salvation — dedicated gospel page |

`style-v2.css` is the one shared stylesheet for all 12 pages. Every image referenced by the HTML files must stay in this same folder — don't move things into subfolders, or the site will render unstyled ("shell page" look).

## Site-wide elements baked into every page
These three pieces are **duplicated in every single HTML file** rather than pulled from one shared file (this is a plain static site, no templating). If you ever want to change one of them, you need to edit it in all 12 files, not just one:

1. **Header/nav** — logo, nav links, mobile hamburger menu
2. **Footer** — logo, Navigate links, address/service times, copyright
3. **Bottom-of-page script block** — powers three things on every page:
   - The **lightbox** (click-to-enlarge on images tagged `class="lightbox-trigger"`)
   - The **floating "Path to Salvation" button** (bottom-right, hidden only on `romanroad.html`)
   - The mobile nav toggle and auto-updating copyright year

## Updating the calendar
Events are **not edited in these files at all**. The church's Google Calendar (the one shared with Claude when this was built) is the source of truth — add, edit, or delete events directly in Google Calendar and `events.html` reflects it automatically. No re-upload needed for routine calendar changes.

## Updating the current sermon series
When the series changes, edit the text and graphic in `teaching.html` — search for "Current Series" near the top of the file. The archive itself (past sermons/studies) pulls live from the YouTube channel embed, so that never needs manual updating.

## Key embeds and IDs (for reference if anything needs reconnecting)
- **YouTube channel:** `@NewZionBaptistChurch-DC` (channel ID `UCikwbnKH4tXgvRiSC5sIkOQ`)
- **Givelify:** `https://giv.li/5e28vt`
- **MailerLite account:** `2591296` — two separate forms: `ZeXFLS` (Stay Connected, on `connect.html`) and `wmf85O` (Prayer Request, also on `connect.html`)
- **Lifeline private message form:** Google Form ID `1FAIpQLSeteKXvgcA6kc_3dLxLyKvsEX2_I9eeAePcsgtYcRd352gr8w`, embedded on `lifeline.html`
- **Zoom (Wednesday Bible Study):** link appears on `worship.html` and `teaching.html`
- **Google Calendar (Events):** calendar ID `c_d55e8604353038a9c5b3f100e73ed22a15018a358ee84ace83188ab5f539ce88@group.calendar.google.com`

## Adding a new photo
1. Drop the image file into this same folder (no subfolders).
2. In the relevant page, find the `.arch-frame` div you want to fill and add `<img src="your-file.jpg" alt="...">` inside it.
3. Add `class="lightbox-trigger"` to that same `.arch-frame` div if the image has small text that should be viewable full-size on click.

## Hosting
Live on GitHub Pages, custom domain `newzionbaptist.org` (no `www`, which redirects to the bare domain). DNS is configured at GoDaddy with four A records pointing to GitHub's IPs. See GitHub repo Settings → Pages for domain/HTTPS status.
