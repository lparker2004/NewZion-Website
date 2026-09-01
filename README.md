# New Zion Baptist Church — Website

15 pages (12 public + 3 members-only), burgundy/gold design system, hosted on GitHub Pages at newzionbaptist.org.

## Public Pages
| File | Purpose |
|---|---|
| `index.html` | Home |
| `about.html` | Mission, vision, the four-step progression, link to the full Roadmap graphic |
| `history.html` | Pastor-by-pastor story: founding, present, incoming |
| `leadership.html` | Current pastoral leadership cards |
| `worship.html` | Sunday livestream, online-worshipper info, service times, links to the Sunday Worship YouTube playlist |
| `events.html` | Google Calendar (2/3 width) + Announcements/flyers column (1/3 width) |
| `teaching.html` | Current sermon series, segmented sermon archive (separate Sunday Worship and Bible Study YouTube playlists side by side), teaching resources |
| `give.html` | Givelify link and giving info |
| `visit.html` | Address, map, service times, what to expect, visitor form |
| `connect.html` | MailerLite signup, prayer request, membership interest, general contact, testimony submissions |
| `lifeline.html` ("Need Help?") | Crisis/pastoral support form, prominent 911/988 emergency banner, explicit statement of what the church offers vs. medical care, links to Path to Salvation |
| `romanroad.html` | The Roman Road to Salvation — dedicated gospel page, with a testimony-sharing CTA |

## YouTube playlists
The archive is segmented into two playlists rather than one mixed feed:
- **Sunday Worship:** `https://www.youtube.com/playlist?list=PLS5Uqnbsv-jI`
- **Bible Studies:** `https://www.youtube.com/playlist?list=PLOMcjaopCp3o`

`teaching.html` embeds both side by side. `worship.html`'s archive links point specifically at the Sunday Worship playlist. New videos need to be manually added to the correct playlist in YouTube Studio when uploaded.

## Members-Only Pages
Reachable via the small gold cross-in-circle icon in the main nav (right after "Need Help?" on every public page), or by typing the URL directly. None of these three are linked in the main public nav or footer, by design.

### members.html — the hub
A welcome page, not just a form. Structure: welcome photo + greeting, a "Get Connected" card grid (Update My Info, Church Calendar, Support Request, Teen Corner, Children + Parents), a "Useful Links" row (Give via Givelify, Bible Study playlist, Sunday Sermons playlist), then the member info update form itself further down the same page (anchored at `#update-info`).

**Still intentionally not included:** a Ministries page and a photo Gallery, neither exists yet. Per an earlier design decision, the hub avoids shipping empty "coming soon" placeholder cards, add a card only once its destination page is real.

**Member Info Update Form:** embedded at `#update-info`. Backed by a Google Form (ID `1LouyGlf3NNJuyqqueFGzJuC-XAf77PwAITV1qZXG5bs`) linked to a Google Sheet in your Workspace, covering Full Name, Address, Mobile Phone, Email Address, Date Joined, and Shirt Size.

**Data flow (lives entirely outside this repo, in your Google Workspace):** every submission lands in the Sheet's default "Form Responses" tab as a raw, append-only change log. A separate "Member Log" tab is the actual formal roster. An AI Executive Assistant (not part of this website) compares each new submission against the Member Log by matching Name + Mobile Phone, updates the matching row if found, or adds a new row if not.

### teens.html — Teen Corner
Its own gated page (same password/hash as members.html), reachable only from the Members hub. Bible resource links, and a private question form (FormSubmit, goes to info@newzionbaptist.org) where a teen can ask anything, optionally anonymously, framed as safe and judgment-free, explicitly not a public forum. Simplified header/footer (Members Home / Main Site / Need Help links only, not the full public nav).

### children.html — Children + Parents
Also its own gated page. Bible resource links, and a question-submission form that **requires** a parent's name and email (child's name is optional), so a parent is structurally part of every submission, not just assumed. Coloring pages and crossword puzzles are marked "coming soon", no downloadable assets exist yet. When ready, they can be added as simple downloads directly on this page; since the whole page already sits behind the password gate, they don't need any separate gating.

## Password gate mechanism
All three members-only pages use the same underlying mechanism (SHA-256 hash stored in the page's JavaScript, never plain text), but **teens.html now has its own distinct password**, separate from members.html and children.html:
- `members.html` and `children.html` share one password: `NewZion2026!`
- `teens.html` has its own separate password: `NZT4Christ2026!`

Each page also has its own separate sessionStorage key (`nzbc_member_unlocked` vs `nzbc_teen_unlocked`), so entering one password does not also unlock the other, they're genuinely independent even though members.html and children.html happen to currently share the same password value.

To change any password: ask Claude to generate a new SHA-256 hash, then update the `GATE_HASH` value near the bottom of the relevant file(s). If you want members.html and children.html to keep sharing one password, update both together; teens.html can always be changed independently.

**Important honesty note:** because this GitHub repository is public (required for free GitHub Pages), these files are technically visible to anyone who browses the repo's file list on GitHub itself. This is a **soft privacy gate**, not real security. Do not put highly sensitive info (SSNs, financial details, etc.) on any of these pages.

## Announcements on the Events page
The right-hand column on `events.html` holds announcement/flyer cards. The Installation Service flyer is the first entry, click it to see the full flyer via the site's lightbox. To add a new announcement, copy that card's HTML block, swap in the new flyer image, title, date, and blurb.

`style-v2.css` is the one shared stylesheet for all pages. Every image referenced by the HTML files must stay in this same folder, don't move things into subfolders.

## Site-wide elements baked into every public page
Duplicated in every public HTML file (no templating on a static site):
1. **Header/nav** — logo, nav links, the members-login icon, mobile hamburger menu
2. **Footer** — logo, Navigate links, address/service times, copyright
3. **Bottom-of-page script block** — the lightbox, the floating "Path to Salvation" button (hidden only on `romanroad.html`), the mobile nav toggle, auto-updating copyright year

The three members-only pages each have their own simpler script (the password gate) and do not include the public site's lightbox or floating salvation button.

## Known open item
The Home page's "Someone Is Here" section still has an older version of a story that was intentionally removed from `lifeline.html`. Leadership is reviewing the site and this will be reconciled along with their other feedback.

## Future roadmap (discussed, not yet built)
See conversation history / Claude's memory of this project for full detail. Summary: a Ministries page (shared interest form with a ministry dropdown), a custom Spiritual Gifts inventory (5 modules, teach-then-assess, synchronized across Romans 12/1 Corinthians 12/Ephesians 4), a New Member Experience course (self-paced, form-based module unlocking, completion certificate, "right hand of fellowship"), a rule-based FAQ widget (explicitly not an AI chatbot), and a member-side photo Gallery. Individual member logins/portals were explicitly deferred indefinitely in favor of the current human-gatekeeper model.

## Style notes
- No em dashes anywhere on the site (converted to commas sitewide).
- Every `.eyebrow` label shows a small gold cross icon, except the homepage hero eyebrow line (`.eyebrow.no-mark`).
- Main nav is burgundy background with white text; "Need Help?" is a solid gold box; the header logo uses `logo-dark.png` (burgundy-background variant) so it blends into the nav rather than sitting in a white box.

## Testimonies from the Roman Road page
"Share My Testimony" links to `connect.html#contact`, with "I Accepted Christ, I Want to Share My Testimony" as a subject option in that form's dropdown.

## Key embeds and IDs
- **YouTube channel:** `@NewZionBaptistChurch-DC`
- **YouTube playlists:** Sunday Worship `PLS5Uqnbsv-jI`, Bible Studies `PLOMcjaopCp3o`
- **Givelify:** `https://giv.li/5e28vt`
- **MailerLite account:** `2591296` — forms `ZeXFLS` (Stay Connected) and `wmf85O` (Prayer Request), both on `connect.html`
- **Lifeline private message form:** Google Form ID `1FAIpQLSeteKXvgcA6kc_3dLxLyKvsEX2_I9eeAePcsgtYcRd352gr8w`
- **Member Info Update Form:** Google Form ID `1LouyGlf3NNJuyqqueFGzJuC-XAf77PwAITV1qZXG5bs`
- **Zoom (Wednesday Bible Study):** on `worship.html` and `teaching.html`
- **Google Calendar (Events):** `c_d55e8604353038a9c5b3f100e73ed22a15018a358ee84ace83188ab5f539ce88@group.calendar.google.com`

## Hosting
Live on GitHub Pages, custom domain `newzionbaptist.org` (no `www`). DNS at GoDaddy with four A records pointing to GitHub's IPs.
