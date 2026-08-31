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
Reachable two ways: the small gold cross-in-circle icon in the main nav (right after "Need Help?" on every public page), or by typing `newzionbaptist.org/members.html` directly. Not listed in the footer's Navigate list, to keep it low-key.

**Important honesty note:** because this GitHub repository is public (required for free GitHub Pages), `members.html` is technically visible to anyone who browses the repo's file list on GitHub itself. The password gate on the page is a **soft privacy gate**, not real security: the page content still exists in the file, and someone technically determined could view it via browser dev tools before entering the password. Do not put highly sensitive info (SSNs, financial details, etc.) on this page. It's appropriate for keeping casual visitors out of member-only content, not for protecting truly confidential data.

**How the gate works:** the password is stored as a SHA-256 hash in the page's JavaScript (never in plain text), so casual view-source doesn't reveal it. The password is currently set to `NewZion2026!`.

**To change the password:** ask Claude to generate a new SHA-256 hash for your chosen password, then swap the `GATE_HASH` value near the bottom of `members.html`. This is a one-line edit, no automation involved — exactly the "reset it myself from time to time" workflow requested.

**Member Info Update Form:** live and embedded directly on the page. Backed by a Google Form (ID `1LouyGlf3NNJuyqqueFGzJuC-XAf77PwAITV1qZXG5bs`) linked to a Google Sheet in your Workspace, covering Full Name, Address, Mobile Phone, Email Address, Date Joined, and Shirt Size. Responses land in that Sheet automatically, no manual re-entry needed.

## Announcements on the Events page
The right-hand column on `events.html` holds announcement/flyer cards. The Installation Service flyer is the first entry — clicking it opens the full flyer via the site's lightbox. To add a new announcement, copy that card's HTML block, swap in the new flyer image (drop the file in this same folder), title, date, and blurb.

`style-v2.css` is the one shared stylesheet for all pages. Every image referenced by the HTML files must stay in this same folder — don't move things into subfolders, or the site will render unstyled ("shell page" look).

## Site-wide elements baked into every public page
These pieces are **duplicated in every single HTML file** rather than pulled from one shared file (this is a plain static site, no templating). If you ever want to change one of them, you need to edit it in all pages, not just one:

1. **Header/nav** — logo, nav links, the members-login icon, mobile hamburger menu
2. **Footer** — logo, Navigate links, address/service times, copyright
3. **Bottom-of-page script block** — powers three things on every page:
   - The **lightbox** (click-to-enlarge) — works two ways: automatically on any image inside a `class="lightbox-trigger"` wrapper, or from any button/link with `data-lightbox-src="filename.png"` (used for the "See the Full Roadmap" buttons on `about.html`)
   - The **floating "Path to Salvation" button** (bottom-right, hidden only on `romanroad.html`)
   - The mobile nav toggle and auto-updating copyright year

`members.html` has its own separate script (the password gate) and does not include the floating salvation button or lightbox, since it's a standalone gated page.

## Known open item
The Home page's "Someone Is Here" section still has an older version of a story that was intentionally removed from `lifeline.html`. Leadership is reviewing the site and this will be reconciled along with their other feedback.

## Style notes
- No em dashes are used anywhere on the site (converted to commas sitewide per house style preference).
- Every `.eyebrow` label sitewide (small gold caps text) shows a small gold cross icon before it, except the homepage hero eyebrow line, which uses a `.eyebrow.no-mark` variant with no icon and forced single-line display.

## Updating the calendar
Events are **not edited in these files at all**. The church's Google Calendar (the one shared with Claude when this was built) is the source of truth — add, edit, or delete events directly in Google Calendar and the calendar portion of `events.html` reflects it automatically. No re-upload needed for routine calendar changes. Announcements/flyers (the right-hand column) are separate and are edited directly in the HTML as described above.

## Updating the current sermon series
When the series changes, edit the text and graphic in `teaching.html` — search for "Current Series" near the top of the file. The archive itself (past sermons/studies) pulls live from the YouTube channel embed, so that never needs manual updating.

## Testimonies from the Roman Road page
The "Share My Testimony" button on `romanroad.html` links to the general contact form on `connect.html` (anchored to `#contact`), with "I Accepted Christ — I Want to Share My Testimony" pre-added as a subject option in that form's dropdown. Submissions arrive as regular emails via FormSubmit — same inbox as all other general contact messages.

## Key embeds and IDs (for reference if anything needs reconnecting)
- **YouTube channel:** `@NewZionBaptistChurch-DC` (channel ID `UCikwbnKH4tXgvRiSC5sIkOQ`)
- **Givelify:** `https://giv.li/5e28vt`
- **MailerLite account:** `2591296` — two separate forms: `ZeXFLS` (Stay Connected, on `connect.html`) and `wmf85O` (Prayer Request, also on `connect.html`)
- **Lifeline private message form:** Google Form ID `1FAIpQLSeteKXvgcA6kc_3dLxLyKvsEX2_I9eeAePcsgtYcRd352gr8w`, embedded on `lifeline.html`
- **Member Info Update Form:** Google Form ID `1LouyGlf3NNJuyqqueFGzJuC-XAf77PwAITV1qZXG5bs`, embedded on `members.html`
- **Zoom (Wednesday Bible Study):** link appears on `worship.html` and `teaching.html`
- **Google Calendar (Events):** calendar ID `c_d55e8604353038a9c5b3f100e73ed22a15018a358ee84ace83188ab5f539ce88@group.calendar.google.com`

## Hosting
Live on GitHub Pages, custom domain `newzionbaptist.org` (no `www`, which redirects to the bare domain). DNS is configured at GoDaddy with four A records pointing to GitHub's IPs. See GitHub repo Settings → Pages for domain/HTTPS status.
