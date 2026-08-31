# New Zion Baptist Church — Website

13 pages (12 public + 1 members-only), burgundy/gold design system, hosted on GitHub Pages at newzionbaptist.org.

## Public Pages
| File | Purpose |
|---|---|
| `index.html` | Home |
| `about.html` | Mission, vision, the four-step progression, link to the full Roadmap graphic |
| `history.html` | Pastor-by-pastor story: founding, present, incoming |
| `leadership.html` | Current pastoral leadership cards |
| `worship.html` | Sunday livestream, online-worshipper info, service times |
| `events.html` | Google Calendar (2/3 width) + Announcements/flyers column (1/3 width) |
| `teaching.html` | Current sermon series, sermon archive, teaching resources |
| `give.html` | Givelify link and giving info |
| `visit.html` | Address, map, service times, what to expect, visitor form |
| `connect.html` | MailerLite signup, prayer request, membership interest, general contact, testimony submissions |
| `lifeline.html` ("Need Help?") | Crisis/pastoral support form, prominent 911/988 emergency banner, explicit statement of what the church offers vs. medical care, links to Path to Salvation |
| `romanroad.html` | The Roman Road to Salvation — dedicated gospel page, with a testimony-sharing CTA |

## Members-Only Page: members.html
Reachable via the small gold cross-in-circle icon in the main nav (right after "Need Help?" on every public page), or by typing `newzionbaptist.org/members.html` directly.

**Important honesty note:** because this GitHub repository is public (required for free GitHub Pages), `members.html` is technically visible to anyone who browses the repo's file list on GitHub itself. The password gate on the page is a **soft privacy gate**, not real security: the page content still exists in the file, and someone technically determined could view it via browser dev tools before entering the password. Do not put highly sensitive info (SSNs, financial details, etc.) on this page.

**How the gate works:** the password is stored as a SHA-256 hash in the page's JavaScript (never in plain text). The password is currently set to `NewZion2026!`.

**To change the password:** ask Claude to generate a new SHA-256 hash for your chosen password, then swap the `GATE_HASH` value near the bottom of `members.html`. One-line edit, no automation involved.

**Member Info Update Form:** live and embedded directly on the page. Backed by a Google Form (ID `1LouyGlf3NNJuyqqueFGzJuC-XAf77PwAITV1qZXG5bs`) linked to a Google Sheet in your Workspace, covering Full Name, Address, Mobile Phone, Email Address, Date Joined, and Shirt Size. Responses land in that Sheet automatically.

## Nav bar styling
The main navigation bar is burgundy with white text (previously white background with dark text). The header logo uses `logo-dark.png` (the burgundy-background logo variant) specifically so it blends seamlessly into the burgundy nav bar rather than sitting in a white box — this is what creates the "floating logo" look. If the nav background color ever changes back to a light color, the logo should be swapped back to `logo-light.png` to match. The "Need Help?" link is styled as a solid gold box for emphasis; the members-login icon uses a lighter gold outline to stand apart from it.

## Announcements on the Events page
The right-hand column on `events.html` holds announcement/flyer cards. The Installation Service flyer is the first entry, clicking it opens the full flyer via the site's lightbox. To add a new announcement, copy that card's HTML block, swap in the new flyer image (drop the file in this same folder), title, date, and blurb.

`style-v2.css` is the one shared stylesheet for all pages. Every image referenced by the HTML files must stay in this same folder, don't move things into subfolders, or the site will render unstyled ("shell page" look).

## Site-wide elements baked into every public page
These pieces are **duplicated in every single HTML file** rather than pulled from one shared file (this is a plain static site, no templating). If you ever want to change one of them, you need to edit it in all pages, not just one:

1. **Header/nav** — logo, nav links, the members-login icon, mobile hamburger menu
2. **Footer** — logo, Navigate links, address/service times, copyright
3. **Bottom-of-page script block** — powers three things on every page:
   - The **lightbox** (click-to-enlarge)
   - The **floating "Path to Salvation" button** (bottom-right, hidden only on `romanroad.html`)
   - The mobile nav toggle and auto-updating copyright year

`members.html` has its own separate script (the password gate) and does not include the floating salvation button or lightbox.

## Known open item
The Home page's "Someone Is Here" section still has an older version of a story that was intentionally removed from `lifeline.html`. Leadership is reviewing the site and this will be reconciled along with their other feedback.

## Style notes
- No em dashes are used anywhere on the site (converted to commas sitewide).
- Every `.eyebrow` label sitewide shows a small gold cross icon before it, except the homepage hero eyebrow line, which uses `.eyebrow.no-mark` with no icon.

## Updating the calendar
Events are **not edited in these files at all**. The church's Google Calendar is the source of truth, add, edit, or delete events directly in Google Calendar and the calendar portion of `events.html` reflects it automatically.

## Updating the current sermon series
Edit the text and graphic in `teaching.html`, search for "Current Series." The sermon archive pulls live from the YouTube channel embed.

## Testimonies from the Roman Road page
The "Share My Testimony" button on `romanroad.html` links to `connect.html#contact`, with "I Accepted Christ, I Want to Share My Testimony" as a subject option in that form's dropdown.

## Key embeds and IDs
- **YouTube channel:** `@NewZionBaptistChurch-DC` (channel ID `UCikwbnKH4tXgvRiSC5sIkOQ`)
- **Givelify:** `https://giv.li/5e28vt`
- **MailerLite account:** `2591296` — forms `ZeXFLS` (Stay Connected) and `wmf85O` (Prayer Request), both on `connect.html`
- **Lifeline private message form:** Google Form ID `1FAIpQLSeteKXvgcA6kc_3dLxLyKvsEX2_I9eeAePcsgtYcRd352gr8w`
- **Member Info Update Form:** Google Form ID `1LouyGlf3NNJuyqqueFGzJuC-XAf77PwAITV1qZXG5bs`
- **Zoom (Wednesday Bible Study):** on `worship.html` and `teaching.html`
- **Google Calendar (Events):** `c_d55e8604353038a9c5b3f100e73ed22a15018a358ee84ace83188ab5f539ce88@group.calendar.google.com`

## Hosting
Live on GitHub Pages, custom domain `newzionbaptist.org` (no `www`). DNS at GoDaddy with four A records pointing to GitHub's IPs.
