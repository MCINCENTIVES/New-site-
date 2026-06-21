# Handoff: MC Incentives — Strategic Workforce Performance Consultancy Website

## Overview
A 14-page marketing/lead-gen website for **MC Incentives**, repositioning the business from an incentive-travel provider into a premium **Strategic Workforce Performance consultancy** for the AI era. The site sells two core engagements (a 3-week **Strategy Diagnostic** and a custom **Workforce Performance System Rollout**), a five-category **Consulting Services** offering, and converts via a **Book a call** scheduler and an **AI advisor chatbot** that also captures contact leads.

## About the Design Files
The files in this bundle are **design references created in HTML** — working prototypes that show the intended look, content, and behaviour. They are **not** production code to ship directly.

These prototypes are authored as "Design Components" (`*.dc.html`) that depend on a bespoke client-side runtime (`support.js`) plus a build step that inlines everything into the `*.bundled.html` files you can open in a browser. **Do not port that runtime.** The task is to **recreate these designs in the target codebase's environment** (this is best built as a React/Next.js site, or Vue/Astro — whatever the team standardises on), using its established component patterns, styling system, routing, and form/CRM integrations. If no codebase exists yet, **Next.js + React with CSS Modules or Tailwind** is the recommended choice given the static, content-driven nature of the site.

Read the `.bundled.html` files for the *rendered* truth (open in a browser), and the `.dc.html` files for structure/content/logic. Ignore `support.js` and the `<x-dc>`, `<sc-for>`, `<sc-if>`, `{{ }}` template constructs — they are runtime scaffolding; reimplement their effect with normal components, loops, and conditionals.

## Fidelity
**High-fidelity (hifi).** Final colours, typography, spacing, imagery, copy, and interactions are all specified and present. Recreate the UI pixel-faithfully using the codebase's libraries. Exact tokens are listed under **Design Tokens**.

---

## Site Map & Routing

| Page | Source file | Suggested route |
|---|---|---|
| Homepage | `MC Incentives Homepage.dc.html` | `/` |
| What We Do | `What We Do.dc.html` | `/what-we-do` |
| Strategy Diagnostic (Offer 01) | `Strategy Diagnostic.dc.html` | `/strategy-diagnostic` |
| Workforce Performance System Rollout (Offer 02) | `Rollout.dc.html` | `/rollout` |
| Insights | `Insights.dc.html` | `/insights` |
| Who We Work With | `Who We Work With.dc.html` | `/who-we-work-with` |
| About | `About.dc.html` | `/about` |
| Contact | `Contact.dc.html` | `/contact` |
| Book a Call (scheduler) | `Book a Workforce Review.dc.html` | `/book` |
| Consulting: Pay Strategy | `Pay Strategy.dc.html` | `/consulting/pay-strategy` |
| Consulting: Reward Optimisation | `Reward Optimisation.dc.html` | `/consulting/reward-optimisation` |
| Consulting: Total Reward & Experience | `Total Reward.dc.html` | `/consulting/total-reward` |
| Consulting: Performance & Incentive Design | `Performance Incentive Design.dc.html` | `/consulting/performance-incentives` |
| Consulting: AI & Workforce Strategy | `AI Workforce Strategy.dc.html` | `/consulting/ai-workforce-strategy` |

> In the prototypes, links point at `*.bundled.html` filenames (URL-encoded, e.g. `Book%20a%20Workforce%20Review.bundled.html`). Replace all of these with the real routes above.

---

## Global Design Tokens

These are declared as CSS custom properties on each page's root element. Centralise them as a theme.

```
--bg:        #FFFFFF   /* page background (white base) */
--blush:     #FFEFEC   /* primary soft-pink panel/card fill */
--blush2:    #FFF6F3   /* secondary blush (chat message area) */
--peach:     #FFD0C7   /* image placeholder / deeper pink */
--ink:       #232222   /* near-black text + dark panels */
--soft:      rgba(35,34,34,.60)  /* secondary text */
--ghost:     rgba(35,34,34,.24)  /* "ghosted" 2nd half of headlines */
--line:      rgba(35,34,34,.12)  /* hairline borders/dividers */
--orange:    #FF5522   /* brand accent (CTAs, highlights) */
--r:         26px      /* large card radius */
--rsm:       16px      /* small card radius */
```

Hero gradient (pink): `linear-gradient(135deg,#FFF1ED 0%,#FFE2D9 52%,#FFD0C7 100%)`
Outer radius on big banded sections/hero/footer: **34px**.

### Typography
- **Font family:** `'Helvetica Neue', Helvetica, Arial, sans-serif` (system Helvetica/Arial stack — swap for the team's equivalent, e.g. Inter/Helvetica Now if licensed; keep it a neutral grotesque).
- **Headings:** weight **800**, `text-transform:uppercase`, tight tracking `letter-spacing:-.02em to -.03em`, line-height `.97–1.04`.
  - H1 hero: 50–62px. Section H2: 32–42px. Card H3: 16–25px.
- **Two-tone headline pattern (signature):** first clause in `--ink`, trailing clause wrapped in `<span style="color:var(--ghost)">…</span>` (light grey). On dark panels the trailing clause uses `--orange` instead. Reuse everywhere.
- **Body:** weight 400–500, 14–18px, line-height 1.5–1.65, colour `--soft`.
- **Eyebrows/labels:** 11–12px, weight 700, `text-transform:uppercase`, `letter-spacing:.12–.16em`, colour `--orange` (or `--peach` on dark).

### Spacing & layout
- Content max-width: **1280px** (1180px for the mega-menu inner). Side padding: **22px**.
- Vertical rhythm between sections: **80–100px** top margin.
- Cards: white or `--blush` fill, `--line` border (on white), radius `--r`/`--rsm`.

### Shadows
- Card hover lift: `transform:translateY(-4px to -6px)` + `box-shadow:0 24px 44px -30px rgba(35,34,34,.45)` (transition .25s ease).
- Dropdown panel: `box-shadow:0 30px 70px -28px rgba(35,34,34,.28)`.
- Floating chat launcher: `box-shadow:0 20px 40px -16px rgba(255,85,34,.7)`.

### The "swoosh" motif (brand device)
A concentric set of rounded bars (a fanned arc) drawn as SVG `<rect rx="29">` stacked at offsets, used as a large decorative element bleeding off the corners of hero bands, dark panels and CTAs. Recolours per context (white/peach/orange tints). Example markup:
```html
<svg viewBox="0 0 320 320" style="width:100%;height:100%;transform:rotate(176deg)">
  <g>
    <rect x="80" y="30"  width="204" height="58" rx="29" fill="rgba(255,255,255,.5)"/>
    <rect x="40" y="98"  width="204" height="58" rx="29" fill="rgba(255,208,199,.8)"/>
    <rect x="80" y="166" width="204" height="58" rx="29" fill="rgba(255,255,255,.55)"/>
    <rect x="40" y="234" width="204" height="58" rx="29" fill="rgba(255,122,69,.45)"/>
  </g>
</svg>
```
Place absolutely in a corner of a `position:relative; overflow:hidden; border-radius` container so it clips to the panel shape. Ship it as a reusable `<Swoosh tint rotation/>` component.

### Animations
- **Section reveal:** `@keyframes rise { from{transform:translateY(22px)} to{transform:none} }` applied as `animation:rise .8s cubic-bezier(.2,.7,.2,1) both`. (Translate only — no opacity — so content is always readable.) Reimplement as an on-scroll/intersection reveal.
- **Marquee** (homepage capability strip): `@keyframes marquee{from{transform:translateX(0)}to{transform:translateX(-50%)}}` on a duplicated row, 36s linear infinite, with edge mask `mask-image:linear-gradient(90deg,transparent,#000 12%,#000 88%,transparent)`.
- **Nav underline:** `.mc-link` pseudo-underline that wipes in left→right on hover (2px, `--orange`, `transition right .3s`).
- **Pulse** on the chat launcher dot: `@keyframes pulse{0%,100%{transform:scale(1);opacity:.5}50%{transform:scale(1.5);opacity:0}}`.

---

## Global Components

### Header / Nav (every page)
- Sits **inside** the hero band (transparent over the pink gradient), `padding:24px 36px 6px`, `display:flex; justify-content:space-between; align-items:center`.
- **Left:** MC Incentives logo (`uploads/logo.png`), height 30px, links to `/`.
- **Centre:** menu links — `What we do` · **Consulting Services ▾** · `Diagnostic` · `Rollout` · `Insights` · `Who we work with` · `About`. 13px, weight 600, colour `--ink`; active item is `--orange`. `white-space:nowrap`. Hover = left→right underline wipe.
- **Right:** solid `--orange` pill button **"Book a call"** → `/book`.
- **Consulting Services mega-menu (dropdown):** opens on hover. A fixed-position, full-width panel (max-width 1180px, centred, white, radius 22px, big soft shadow) with **5 columns** (`grid-template-columns:repeat(5,minmax(0,1fr))`, gap 18px, `white-space:normal`). Each column = an `--orange` uppercase header that links to the category landing page, then 5 plain item links (`--soft`, hover→`--ink`). Implementation notes that matter:
  - Use `minmax(0,1fr)` so long labels wrap instead of overflowing.
  - The panel must escape the hero band's `overflow:hidden` — in HTML this was solved with `position:fixed` + a transparent top padding "hover bridge". In a real app, render the dropdown in a portal/overlay layer and position under the trigger; you do not need the fixed-offset hack.

  Mega-menu data (column header → items):
  - **Pay Strategy** → Pay Benchmarking · Pay Structure Design · Executive & Leadership Remuneration · Pay Equity & Transparency · Job Evaluation & Role Architecture
  - **Reward Optimisation** → Reward Strategy Development · Reward Audits · Reward Advisory (On-Demand) · Reward Communication · Reward Governance & Policy
  - **Total Reward & Experience** → Employee Value Proposition · Employee Benefits Strategy · Recognition Programs · Wellbeing & Lifestyle · Flexible Work & Reward
  - **Performance & Incentives** → Bonus Scheme Design · Sales Incentive Programs · Executive Incentives · Performance Frameworks · KPI & Goal Alignment
  - **AI & Workforce Strategy** → AI Workforce Readiness · Workforce Performance Reviews · Role & Job Architecture · Skills-Based Planning · Future of Work Strategy

### Footer (every page)
- Dark (`--ink`) rounded block (radius 34px, padding 54px 48px), `max-width:1280px`.
- 4-column grid `1.6fr 1fr 1fr 1fr`: (1) white logo + 1-line positioning blurb; (2) **Consulting** links; (3) **Explore** links; (4) **Get in touch** (`contact@mcincentives.com.au`, `Sydney, Australia`). Bottom line: `© 2026 MC Incentives · Reward · Recognition · Performance · Workforce`.
- White logo = same logo with `filter:brightness(0) invert(1)`.

### Floating AI Advisor Chatbot (homepage; reusable site-wide)
Fixed bottom-right stack. Three states:
1. **Launcher button** — orange pill "Ask an advisor" with a pulsing green dot.
2. **Entry-point popover** (on launcher click) — "Advisory entry points" list:
   - *Workforce architecture* (icon WA)
   - *Reward systems* (icon RS)
   - **Contact the team** (dark row, envelope icon) — "Leave a message · reply in 4 hrs"
3. **Chat panel** (370px wide, 520px tall, white, radius 22px). Dark header with icon, title, subtitle, ✕ close. Two **modes**:
   - **Advisor mode:** tab switch between the two advisors; scrollable message thread (bot/user bubbles — bot = white, user = `--orange`); a "Suggested" footer with 3 canned prompt buttons that append a Q→A pair to the thread. A small "Contact the team →" shortcut sits in the suggested header.
   - **Contact mode:** header reads "Contact the team advisor / We reply within 4 hours". Body = a "We reply within 4 hours" reassurance chip + form fields **Full name, Company, Work email, "What are you working on?"** + orange **Send message** button → on submit shows a "Message received" confirmation ("a consultant will be in touch by email within 4 business hours").

The advisor replies are **canned/scripted** in the prototype (see `prompts` object in the homepage `.dc.html`). For production, either keep them scripted or wire to a real assistant; the **Contact mode form must POST to your CRM/email** and is the real lead-capture path. See **Interactions** for the exact scripted copy source.

---

## Page-by-Page Notes

> All pages share the Header, Footer, two-tone headline pattern, swoosh motif, and `rise` reveal. Below are the section structures unique to each. Pull exact copy from the corresponding `.dc.html` (it's plain text in the markup, or in the `renderVals()` data arrays in the trailing `<script data-dc-script>` block).

### Homepage (`MC Incentives Homepage.dc.html`)
Hero (two-column: headline + CTAs left; portrait image right with caption overlay + orange swoosh) → marquee **capability strip** → **The Shift** (3 cards) → **Business Problem** with big **16%** stat + 3 mini stat-bars (64% / 20% / 16%) → **What's Breaking** (dark quote + lettered A–D list) → **The Model** (3 pillar cards, middle one solid orange) → **Insight** (dark band, "explainability") → **Incentives reframe** (system nodes; incentives shown as one subordinate node) → **Why MC** (4 cards) → **Advisors** (2 cards opening the chatbot) → **Clarity Diagnostic** (interactive sliders + SVG gauge) → **FAQ** (accordion) → **CTA** → Footer. Plus the floating chatbot.
- **Interactive Clarity Diagnostic:** 4 sliders (Role clarity, Reward transparency, Progression visibility, Manager consistency, 0–100). `gap = 100 - average`. An SVG ring gauge animates to `gap%`. Tier label/desc thresholds: ≥58 "Structural risk", ≥40 "Elevated drift", ≥22 "Emerging gaps", else "Largely aligned". (Logic in `renderVals()`.)
- **Props exposed as theme knobs** (optional to keep): `accent` colour (default `#FF5522`), `cornerRadius` (default 26), `showMotif` (bool).

### Strategy Diagnostic (`Strategy Diagnostic.dc.html`)
Offer 01. Hero (headline + dark "why it matters" card) → 3-week structure (Week 1 discovery / Week 2 analysis / Week 3 synthesis) → **what's included** → **process map** → **Commercial Lens** (3 image cards: Revenue / Retention / Productivity) → outputs (prioritised opportunity map, risk report, 12-month roadmap, exec summary in 5 business days, 60-min debrief) → **gate notice** ("must complete before any Rollout") → pricing **From $3,500 + GST**, fee **credited toward implementation** → CTA. Tone: executive/commercial.

### Rollout (`Rollout.dc.html`)
Offer 02. Hero (headline + image) → **gate notice** ("Begins after the Diagnostic") → scope (system redesign, implementation & rollout support, systems & measurement, AI-era alignment, post-implementation, dedicated consultant) → **Outcome** (4 image cards: Revenue / Retention / Productivity / Clarity) → **pricing comparison** (custom-scoped, itemised after diagnostic, diagnostic fee credited) → CTA. Custom pricing, not packaged.

### What We Do (`What We Do.dc.html`)
Hero (headline + dark stat card: **5×** / **16%**) → positioning strip → full-bleed image band → **5 capability pillars** (each a wide card with Strategically / Commercially / In the system columns) → diagnostic CTA.

### Consulting category pages (5×, all same template)
`Pay Strategy`, `Reward Optimisation`, `Total Reward`, `Performance Incentive Design`, `AI Workforce Strategy`. Each: Hero (headline + dark "Why it matters" card with 3 proof bullets) → intro strip → **captioned image band** → **services grid** (3-col tiles, numbered badge, hover-lift) → **business outcomes** (4 `--blush` cards) → **Why MC** (dark band) → **Diagnostic CTA** with the `From $3,500 + GST` card (scoped to size/complexity · fee credited · exec summary in 5 business days) → Footer. Build ONE parametrised template + a data file with the per-page content (hero copy, services[], outcomes[], why copy, image). All content is in each file's `renderVals()`.

### Book a Call (`Book a Workforce Review.dc.html`)
Hero (two-column, headline + person image) → **Step 1: choose call type** (two selectable cards: *30-minute consultation* [complimentary] and *Strategy Diagnostic call* [From $3,500 + GST]; each has a "See what's included →" link to the relevant page) → **Step 2: pick a time** — a **calendar** (month grid, weekdays only, prev/next month nav, prev disabled on current month, up to ~6 months ahead) + **time slots 3:00–6:30 PM in 30-min increments** + a live **booking summary** panel collecting **Full name, Company, Phone, Work email** with a Confirm button → confirmation state. This is real scheduling UI — wire to your calendar/booking backend (Cal.com/Calendly/custom). Logic (month math, slot list, gating) is in `renderVals()`.

### Insights (`Insights.dc.html`)
Hero (headline + dark "Our perspective" card — qualitative, **no invented stats**) → "why this thinking matters" → **featured article** (dark) → article grid. Articles are placeholders; wire to CMS.

### Who We Work With (`Who We Work With.dc.html`)
Hero (headline + image) → org-type cards (Mid-market / Enterprise) → leaders we work with (HR & Reward Directors, **Chief Operating Officers**, People & Culture leaders) → industries → challenges (01–0n) → CTA.

### About (`About.dc.html`) & Contact (`Contact.dc.html`)
Positioning-led About (belief system, perspective, approach: diagnostic → system design → implementation). Contact page = decisive conversion layout (Book Strategy Diagnostic + 30-min consultation), minimal friction. Pull copy from the files.

---

## Interactions & Behavior (summary)
- **Nav mega-menu:** hover-open dropdown (portal/overlay in prod), keyboard-accessible; close on blur/escape. Active route highlights its nav item in `--orange`.
- **Section reveals:** `rise` translate-up on enter (IntersectionObserver), `.8s cubic-bezier(.2,.7,.2,1)`.
- **Card hovers:** translateY lift + soft shadow, .25s.
- **FAQ:** single-open accordion (`+` rotates 45° to ×).
- **Clarity Diagnostic:** live slider → recompute gap → animate SVG ring (`stroke-dashoffset`, .4s) + tier label.
- **Chatbot:** launcher → entry popover → advisor or contact mode (see component). Scripted advisor replies live in the homepage file's `prompts` object; contact form is the real lead path.
- **Calendar:** select call type → pick weekday (past/weekends disabled) → pick 30-min slot (3–6:30 PM) → fill details → confirm → success state. Month nav clears prior selection.
- **All forms** (chatbot contact, booking summary, Contact page): client-validate required fields, POST to CRM/email, show success state. Promise SLA copy: **"reply within 4 business hours via email."**

## State Management
- Global: active route (nav highlight), mega-menu open/hover state.
- Chatbot: `open`, `launcherOpen`, `mode` ('advisor'|'contact'), active advisor (`arch`|`reward`), per-advisor message `threads`, `contactSent`.
- Homepage diagnostic: 4 slider values → derived `gap`, `tierLabel`, `tierDesc`.
- Booking: `callType`, `selectedDate`, `selectedTime`, `monthOffset`, `booked`, contact fields.
- FAQ: `openIndex`.

## Assets
- **Logo:** `uploads/logo.png` (MC Incentives wordmark; invert for dark footer).
- **Photography:** in `assets/site/` — hero/section portraits and the consulting image bands (`cs-pay.jpg`, `cs-reward.jpg`, `cs-total.jpg`, `cs-perf.jpg`, plus `u-*.jpg`, `out-*.jpg`, etc.). These are licensed/stock + user-provided conference imagery; confirm licensing before production use and replace as needed. All are included in this bundle under `assets/`.
- **Icons:** inline SVG (search, chevrons, check, clock, envelope, calendar). Replace with the codebase's icon set.
- **Swoosh motif:** pure SVG (see Design Tokens) — rebuild as a component.

## Files
Design source (recreate these): the 14 `*.dc.html` files listed in the Site Map. Open the matching `*.bundled.html` in a browser to see each rendered. `assets/` and `uploads/logo.png` hold imagery. **Ignore** `support.js` and the `*.bundled.html` build artifacts for code reference (they're runtime/compiled output).

## Screenshots
`screenshots/` contains a top-of-page capture per page (numbered to match the site map). Two caveats: (1) they show the **hero/upper fold**, not the full scroll — open the matching `.bundled.html` in a browser for the complete page; (2) the capture engine renders inlined photos as flat **peach placeholders**, so judge imagery from the `.bundled.html` files / `assets/`, but typography, colour, layout and spacing are accurate.
