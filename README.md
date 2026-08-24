# New Zion Baptist Church — Website

12 pages, burgundy/gold design system, hosted on GitHub Pages at newzionbaptist.org.

## Pages
| File | Purpose |
|---|---|
| `index.html` | Home |
| `about.html` | Mission, vision, the four-step progression, link to the full Roadmap graphic |
| `history.html` | Pastor-by-pastor story: founding, present, incoming |
| `leadership.html` | Current pastoral leadership cards |
| `worship.html` | Sunday livestream, online-worshipper info, service times |
| `events.html` | Google Calendar embed (see "Updating the calendar" below) |
| `teaching.html` | Current sermon series, sermon archive, teaching resources |
| `give.html` | Givelify link and giving info |
| `visit.html` | Address, map, service times, what to expect, visitor form |
| `connect.html` | MailerLite signup, prayer request, membership interest, general contact, testimony submissions |
| `lifeline.html` ("Need Help?") | Crisis/pastoral support form, prominent 911/988 emergency banner, explicit statement of what the church offers vs. medical care, links to Path to Salvation |
| `romanroad.html` | The Roman Road to Salvation — dedicated gospel page, with a testimony-sharing CTA |

`style-v2.css` is the one shared stylesheet for all 12 pages. Every image referenced by the HTML files must stay in this same folder — don't move things into subfolders, or the site will render unstyled ("shell page" look).

## Known open item
The Home page's "Someone Is Here" section still has an older version of a story that was intentionally removed from `lifeline.html`. Leadership is reviewing the site and this will be reconciled along with their other feedback.

## Site-wide elements baked into every page
These pieces are **duplicated in every single HTML file** rather than pulled from one shared file (this is a plain static site, no templating). If you ever want to change one of them, you need to edit it in all 12 files, not just one:

1. **Header/nav** — logo, nav links, mobile hamburger menu
2. **Footer** — logo, Navigate links, address/service times, copyright
3. **Bottom-of-page script block** — powers three things on every page:
   - The **lightbox** (click-to-enlarge) — works two ways: automatically on any image inside a `class="lightbox-trigger"` wrapper, or from any button/link with `data-lightbox-src="filename.png"` (used for the "See the Full Roadmap" buttons on `about.html`)
   - The **floating "Path to Salvation" button** (bottom-right, hidden only on `romanroad.html`)
   - The mobile nav toggle and auto-updating copyright year

## Style notes
- No em dashes are used anywhere on the site (converted to commas sitewide per house style preference).
- The homepage hero eyebrow line (`#hero-eyebrow` in `index.html`) uses a `.eyebrow.no-mark` variant that removes the small decorative gold bar the eyebrow style normally shows before text — used only where that mark would look cluttered against a multi-part line.

## Updating the calendar
Events are **not edited in these files at all**. The church's Google Calendar (the one shared with Claude when this was built) is the source of truth — add, edit, or delete events directly in Google Calendar and `events.html` reflects it automatically. No re-upload needed for routine calendar changes.

## Updating the current sermon series
When the series changes, edit the text and graphic in `teaching.html` — search for "Current Series" near the top of the file. The archive itself (past sermons/studies) pulls live from the YouTube channel embed, so that never needs manual updating.

## Testimonies from the Roman Road page
The "Share My Testimony" button on `romanroad.html` links to the general contact form on `connect.html` (anchored to `#contact`), with "I Accepted Christ — I Want to Share My Testimony" pre-added as a subject option in that form's dropdown. Submissions arrive as regular emails via FormSubmit — same inbox as all other general contact messages.

## Key embeds and IDs (for reference if anything needs reconnecting)
- **YouTube channel:** `@NewZionBaptistChurch-DC` (channel ID `UCikwbnKH4tXgvRiSC5sIkOQ`)
- **Givelify:** `https://giv.li/5e28vt`
- **MailerLite account:** `2591296` — two separate forms: `ZeXFLS` (Stay Connected, on `connect.html`) and `wmf85O` (Prayer Request, also on `connect.html`)
- **Lifeline private message form:** Google Form ID `1FAIpQLSeteKXvgcA6kc_3dLxLyKvsEX2_I9eeAePcsgtYcRd352gr8w`, embedded on `lifeline.html`
- **Zoom (Wednesday Bible Study):** link appears on `worship.html` and `teaching.html`
- **Google Calendar (Events):** calendar ID `c_d55e8604353038a9c5b3f100e73ed22a15018a358ee84ace83188ab5f539ce88@group.calendar.google.com`

## Hosting
Live on GitHub Pages, custom domain `newzionbaptist.org` (no `www`, which redirects to the bare domain). DNS is configured at GoDaddy with four A records pointing to GitHub's IPs. See GitHub repo Settings → Pages for domain/HTTPS status.
