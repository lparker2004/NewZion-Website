# New Zion Baptist Church — Website

19 pages (13 public + 6 members/special-access), burgundy/gold design system, hosted on GitHub Pages at newzionbaptist.org.

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
| `faq.html` | Full FAQ: address, office email, directions, inviting a friend, sharing your faith, service times, online vs. in-person, biblical giving, connecting to Givelify |

## YouTube playlists
- **Sunday Worship:** `https://www.youtube.com/playlist?list=PLS5Uqnbsv-jI`
- **Bible Studies:** `https://www.youtube.com/playlist?list=PLOMcjaopCp3o`

`teaching.html` embeds both side by side. `worship.html`'s archive links point specifically at the Sunday Worship playlist.

## Members-Only Pages (password gated)
Reachable via the small gold cross-in-circle icon in the main nav, or by typing the URL directly. Not linked in the main public nav or footer.

### members.html — the hub
Welcome photo + greeting, a "Get Connected" card grid (Update My Info, Church Calendar, Support Request, Teen Corner, Children + Parents, + Add Member), a "Useful Links" row (Give, Bible Study playlist, Sunday Sermons playlist), then the member info update form itself at `#update-info`.

### teens.html — Teen Corner
Its own gate, own password (see below). Bible resources, a private question form to Pastor Parker (FormSubmit).

### children.html — Children + Parents
Its own gate, shares the members.html password. Bible resources, a question form requiring a parent's name and email. Coloring pages/crosswords marked "coming soon," no assets yet.

### addmember.html — Add New Member
**No password gate of its own right now, by deliberate choice.** Lloyd wants any member to be able to help out here in the near term, so this page relies entirely on being reachable only from within the already-gated members hub, it is not linked anywhere on the public site. Linked from three places on members.html: a nav menu item, a doorway card, and a bottom-of-page link. Embeds a Google Form ("Add New Member") with Name, Birthday, Phone, Email, and a Status field (New Member/Returning Member/Visitor/Other). Feeds a Google Sheet tab that Lloyd's own ChatGPT-based automation polls to trigger a welcome email with the link to welcomehome.html.

### family-directory.html — Family Directory
Its own gate, shares the members.html password. Linked from Step 3 of welcomehome.html ("Meet Your Family"). **Currently a placeholder**, no real member photos or names exist yet. The intent, per Lloyd, is a directory of the whole congregation by face and name, not just leadership, specifically to address the same representation concern raised earlier about the Church Life gallery (existing photos overrepresenting a few visible families). Building this out means collecting photos and names from a broad cross-section of actual members, not something Claude can build without that real data. Consider pairing this with the photo-submission mechanism already discussed for the Church Life gallery, since both need the same kind of broad member participation to work well.

**Lloyd has said he'll want to add a password here later.** When that happens, ask Claude to add a gate (the same pattern used on teens.html/children.html/members.html works) and generate a hash for whatever password he chooses at that time.

**Passwords summary:**
- `members.html` and `children.html` share `NewZion2026!`
- `teens.html` has its own separate password, `NZT4Christ2026!`
- `addmember.html` currently has no password at all (see above)

Each gated page has its own separate sessionStorage key, so entering one password never unlocks another.

**Important honesty note:** because this GitHub repo is public, these files are technically visible in the repo's file list. This is a soft privacy gate, not real security. No highly sensitive info belongs on any of these pages.

## welcomehome.html — New Member Experience (special access, no password)
No password gate at all, instead a `noindex, nofollow` meta tag keeps it out of search engines. Not linked anywhere on the public site or the members hub, the only way in is a direct link or QR code Lloyd hands out personally, or the automated welcome email triggered by addmember.html.

**Page flow, in order (reordered per Lloyd's request):** (1) "What Just Happened?", the decision explained personally plus the biblical concept of the local church, comes first now, meaning before the paperwork, (2) Member Info Update Form, "let's make it official", includes an "Areas You'd Like to Assist" field covering the "where do you feel led to serve" question, (3) "Meet Your Family", now links to family-directory.html (see above) rather than showing individual leadership photos, (4) Mission and Vision, illustrated with the Roadmap graphic, (5) three training video modules (Now That I'm a Believer / What We Believe / Where Do I Fit In), currently placeholder slots, no videos recorded yet, (5b) a compact FAQ (service times, location, inviting a friend, sharing your faith, online vs. in-person, connecting to Givelify), with a link to the full faq.html, (6) a completion checkpoint ("Let Us Know You're Done"), currently a placeholder card pending a dedicated Google Form, (7) "Connect With Me Personally", a live MailerLite form (`data-form="fxQmIn"`) going straight to Lloyd.

**Note on leadership visibility:** Lloyd asked to deemphasize Rev. Major L. Certain's visibility going forward and be more prominent himself, since he needs to assert his role as the only Senior Pastor. Claude flagged that this is a direct reversal of an earlier explicit decision (waiting until after the Sept 19, 2026 installation specifically to avoid overshadowing the sitting Senior Pastor) and did not apply this broadly. The only change made was removing her individual photo from the Welcome Home family trio, a natural consequence of that section becoming a link to the family directory instead of a leadership photo spread, not an independent editorial choice about her prominence. `history.html` and `leadership.html` were deliberately left untouched, since they exist to accurately document who currently holds the role. This is worth a direct conversation with Lloyd about scope before touching those pages, rather than assuming either direction.

**Completion tracking, deliberate design choice:** Lloyd decided against per-module tracking or any unlock-gating between videos, all three stay watchable in any order at any time, matching the page's "no rush, no deadline" promise. Instead there's one lightweight self-reported checkpoint after all three, just name, email, and an optional note, no comprehension questions, specifically to avoid the course feeling like "work" rather than an easing-in.

**Three outstanding items:**
- The three video modules need to be recorded and embedded once ready, swap each placeholder `.arch-frame` block for a real `<iframe>`, same pattern used elsewhere on the site.
- A dedicated Google Form for the completion checkpoint needs to be created (Name, Email, optional note field) and linked to a Sheet, same pattern as every other form on this site. Once it exists, share the embed code and it replaces the placeholder card.
- The `addmember.html` password, when Lloyd decides on one.

## The full new-member pipeline (mostly lives outside this website)
1. Someone tells a member or staff (in person) they want to join.
2. That person opens `addmember.html` (from the members hub, no separate password currently) and fills in the "Add New Member" Google Form (Name, Birthday, Phone, Email, Status).
3. That form feeds a dedicated tab in the same Google Sheet as the Member Log.
4. Lloyd's own ChatGPT-based automation polls that sheet (a few times a day) and automatically emails the new person a welcome message containing the direct link to `welcomehome.html`.
5. The person visits `welcomehome.html` on their own time and works through the full experience, including the self-reported completion checkpoint at the end of the three video modules.

Only step 2 involves this repository. Steps 3 to 5 are Lloyd's Google Workspace and his own automation, not part of this website's code.

## Announcements on the Events page
The right-hand column on `events.html` holds announcement/flyer cards. To add one, copy the Installation Service card's HTML block and swap in the new flyer, title, date, and blurb.

`style-v2.css` is the one shared stylesheet for all pages. Every image referenced by the HTML files must stay in this same folder.

## Site-wide elements baked into every public page
Duplicated in every public HTML file (no templating on a static site): header/nav, footer, and a bottom-of-page script block (lightbox, floating "Path to Salvation" button, mobile nav toggle, copyright year). The members-only and special-access pages each have their own simpler scripts and don't include the public site's lightbox or floating button.

## Known open item
The Home page's "Someone Is Here" section still has an older version of a story that was intentionally removed from `lifeline.html`. Leadership is reviewing the site and this will be reconciled along with their other feedback.

## Future roadmap (discussed, not yet built)
See conversation history / Claude's memory of this project for full detail. Summary: a Ministries page (shared interest form with a ministry dropdown), a custom Spiritual Gifts inventory (5 modules) as a separate optional deeper track, a rule-based FAQ widget (explicitly not an AI chatbot), and a member-side photo Gallery (with a planned photo-submission mechanism to address representation balance across the congregation). Individual member logins/portals were explicitly deferred indefinitely.

## FAQ (faq.html and the mini-FAQ on welcomehome.html)
`faq.html` is a full accordion-style FAQ page on the main site, six questions: address, office email, directions, inviting a friend, sharing your faith (links to the Roman Road page), and service times. Uses native HTML `<details>/<summary>` elements, no JavaScript needed for the expand/collapse itself, just CSS. Linked from the footer Navigate list on every public page, deliberately kept out of the top nav to avoid crowding it, same treatment Roman Road got.

A shorter 4-question version (service times, location, inviting a friend, sharing your faith) lives directly on `welcomehome.html`, styled to match that page's own design language, with a link through to the full FAQ page for anything more. This is the "rule-based FAQ" approach decided on earlier in the project: pre-written, pastor-approved answers only, with an easy path to reach Lloyd directly for anything deeper, explicitly not an AI chatbot.

## Style notes
- No em dashes anywhere on the site (converted to commas sitewide).
- Every `.eyebrow` label shows a small gold cross icon, except the homepage hero eyebrow line (`.eyebrow.no-mark`).
- Main nav is burgundy background with white text; "Need Help?" is a solid gold box; the header logo uses `logo-dark.png` so it blends into the nav.

## Testimonies from the Roman Road page
"Share My Testimony" links to `connect.html#contact`, with "I Accepted Christ, I Want to Share My Testimony" as a subject option.

## Key embeds and IDs
- **YouTube channel:** `@NewZionBaptistChurch-DC`
- **YouTube playlists:** Sunday Worship `PLS5Uqnbsv-jI`, Bible Studies `PLOMcjaopCp3o`
- **Givelify:** `https://giv.li/5e28vt`
- **MailerLite account:** `2591296` — forms `ZeXFLS` (Stay Connected) and `wmf85O` (Prayer Request) on `connect.html`; `fxQmIn` (Connect With Me Personally) on `welcomehome.html`
- **Lifeline private message form:** Google Form ID `1FAIpQLSeteKXvgcA6kc_3dLxLyKvsEX2_I9eeAePcsgtYcRd352gr8w`
- **Member Info Update Form:** Google Form ID `1LouyGlf3NNJuyqqueFGzJuC-XAf77PwAITV1qZXG5bs`
- **Add New Member Form:** Google Form ID `1FAIpQLScIT35K-5jBwaDJbRGwbAUSNiGQ7Td2P6MOeLd4FqlBLd-mIg`
- **Zoom (Wednesday Bible Study):** on `worship.html` and `teaching.html`
- **Google Calendar (Events):** `c_d55e8604353038a9c5b3f100e73ed22a15018a358ee84ace83188ab5f539ce88@group.calendar.google.com`

## Hosting
Live on GitHub Pages, custom domain `newzionbaptist.org` (no `www`). DNS at GoDaddy with four A records pointing to GitHub's IPs.
