# Site notes (for future sessions)

## What this site is
Agents4Academia umbrella site on GitHub Pages. Root = general community site
(hackathons + ongoing open-source agent development). Each event is archived
as a self-contained snapshot under `events/`.

## Structure (since July 2026 restructure)
- Root: `index.html` (mission), `events/index.html` (event list),
  `projects.html` + `people.html` (living, community-wide), `contribute.html`.
- `events/2026-oxford-sg/` — frozen snapshot of the June 2026 Oxford–NUS–NTU
  hackathon site (its own `assets/` copy, so root redesigns never restyle it).
  Its navs got a "Main site" back-link.
- `assets/css/style.css` shared by root pages only; linked with `?v=2`
  cache-buster (bump on CSS changes).

## Key decisions & why
- GitHub org is `Agents4Academia-AI` (the lowercase `agents4academia` org only
  holds this Pages repo).
- Projects page fetches org repos + per-repo contributors client-side from the
  GitHub API. Responses cached in localStorage (10 min TTL, stale fallback)
  because the unauthenticated limit is 60 req/hour/IP — dev testing exhausted
  it once.
- `EXTRA_CONTRIBUTORS` map in projects.html force-adds people hidden by
  squashed history (prior's history was squashed; real history in private
  archived repo `prior-history`). Currently: prior → harit7.
- People page: photos are HOTLINKED from personal homepages (Harit's explicit
  rule: never download photos into the repo). GitHub avatars as fallback;
  `onerror` hides broken images. All URLs verified 200 image/* on 2026-07-07.
- Team membership came from the IDEAS deck rosters (Google Slides, linked in
  the org profile README) cross-checked with repo commit authors.

## Data sources
- Org profile README: `Agents4Academia-AI/.github/profile/README.md` (links
  white paper, schedule, introductions deck, IDEAS deck).
- Introductions deck (participants) and IDEAS deck (team rosters) are Google
  Slides; export as text via `.../export/txt`.

## Open items
- "Shiqi Chen" in auto-reviewer roster but not in intro deck — excluded from
  People page pending confirmation.
- Tom Rainforth, Freddie Bickford Smith, Nele Quast have no team/project tag.
- Debolina Paul: no homepage/photo found (Scholar link + initials placeholder).
- Representative project images: agreed approach is GitHub social-preview
  (`https://opengraph.githubassets.com/1/Agents4Academia-AI/<repo>`) — NOT yet
  implemented on the projects page.
- Org GitHub Discussions not enabled; contribute.html points to issues/email.
- Nothing committed yet as of the restructure session.
- `cover_test.html` at root is leftover scratch; ask before deleting.

## Local preview
`python3 -m http.server 8000` from repo root.

## July 2026: root aligned with new org README
The org profile README was rewritten community-first (goals, five principles,
social channels, "Oxford–Singapore Hackathon" as the official event name).
Root `index.html` now mirrors it: new tagline, learn/build goals, condensed
Principles section, Channels row (Discord discord.gg/fEDXaSWwj, X and
Bluesky @agents4academia), all six organisers, institutional thanks under
the Anthropic logo. `contribute.html` "Get in touch" leads with the channels.
Site text stays condensed on purpose — don't paste the README verbatim.

## July 2026 redesign (v4, "lightweight, minimal, classy")
Full restyle after Harit rejected: the original cream/serif template, a graph-paper
background, gray-tinted backgrounds, boxed cards/pills, heavy margin-rule
marginalia, multi-color thread systems, and dark themes. What stands:
- Pure white, single centered ~47rem column ("think research papers"), header
  on a wider 64rem measure so the nav stays one line.
- Archivo (display) + IBM Plex Sans/Mono. Accent #c85c45 (from banner's "4"),
  working blue #1c56c6.
- Icon sprite INLINED into every page (Safari can't <use> external files);
  drawn 1.6px-stroke set incl. lifecycle stages, principles, channels, institution.
- Hero = banner rethought as the page: motto, wordmark (terracotta 4), tagline,
  channel links. fig-vision.svg under it: the workflow line with an agent
  docked at each of the seven areas named in the org README (verbatim labels).
- ALL headings/body text verbatim from the org profile README — Harit: "don't
  try to do much writing on your own; use same titles as in the github org page".
- Principles = separate principles.html (exact README text), never on the home page.
- Anthropic appears ONLY in hackathon contexts (cohort paragraph + event pages),
  not as a site-wide supporter. Footer logos = the three universities
  (Wikimedia-hotlinked, grayscale, color on hover).
- Event snapshot events/2026-oxford-sg/ now SHARES the theme (its css is a copy
  of root style.css; fonts patched; cover = lifecycle_strip.png retinted cool).
  Keep the copies in sync on future restyles.
- designs/ folder = rejected candidates from the exploration (b-manuscript,
  c-threads, d-constellation + index). DELETE before deploying; not linked.
- lifecycle_strip.png lives in root assets + event assets (same file).

## Final polish before first deploy (10 Jul 2026)
- Dark/light theme: toggle button in every header (accent-colored, 38px),
  preference in localStorage, default = system. Palette via CSS vars;
  dark gets --paper #0f151d etc. Figures: vision figure is INLINE svg using
  var() colors; lifecycle strip has a _dark.png variant swapped via
  .light-only/.dark-only; logos sit on white plates in dark.
- Brand mark + favicon: "graduate agent" (blue robot head, LED eyes,
  mortarboard, terracotta tassel) — v1 with round eyes/smile read as a
  Halloween pumpkin at 16px; squared shapes fixed it. Same svg inline in
  every header (theme-aware via var()) and as favicon on all 11 pages.
- Logos row (main + event pages): Anthropic wordmark 17px + Oxford horizontal
  lockup (Commons) + NUS univ-level (assets/img/nus.png — cropped from the
  NUS Computing lockup, local because you can't hotlink a crop) + NTU. One
  row, always full color (no grayscale).
- Event snapshot: h1/titles say "Oxford–Singapore Hackathon" (brand name is
  the community, not the event); README-verbatim organisers/advisors with
  homepage links; cover strip below the title; brand icon links to main site
  (no "Main site" nav item).
- projects.html EXCLUDE += media, example-agents.
- contribute.html: CTA button row (GitHub primary + socials); tagline is the
  README welcome sentence (Harit vetoed the "research grind" line).
- designs/ (rejected candidates) deleted before this deploy.
