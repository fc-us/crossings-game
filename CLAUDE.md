# Crossings — Project CLAUDE.md

## Purpose
Mario-style platformer about the international student experience — identity, belonging, and finding home in a new place. Forked from Goers (faith/missions theme) with entirely new content layer. Same engine, new audience.

## Stack
- Single-file static site: `index.html` (HTML + Canvas + vanilla JS)
- No dependencies, no build step
- Hosting: GitHub Pages or Cloudflare Pages (static)
- Audio: Web Audio API chiptune (no external assets)

## Deployment
1. Push to `main` branch on GitHub
2. Serve `index.html` from any static host — zero config needed
3. No env vars, no API keys, no backend

## Architecture
- Everything in `index.html` (~3978 lines)
- Game loop: `update()` → `draw()` at 60fps via `requestAnimationFrame`
- State machine: MENU → PLAYING → DECISION → LEVEL_COMPLETE → PLAYING (L2) → END (+ PAUSED overlay)
- Level data built by `buildLevel()` / `buildLevel2()` functions
- Forked from Goers — engine is identical, only content layer changed

## Thematic Mapping (from Goers)
- Meters: Heart→Connection, Faith→Identity, Money→Resources (variable names unchanged, display text changed)
- L1 Zones: HOME→ARRIVAL, SCHOOL→CAMPUS, CAREER→CULTURE, CALLING→BELONGING
- L2 Zones: DOUBT→HOMESICK, PRESSURE→PRESSURE, COMMUNITY→BRIDGE, COURAGE→ROOTS
- Enemies: expectation→stereotype, comfort→bureaucracy, overwork→burnout, isolation→isolation, comparison→homesick, scarcity→visa, pleaser→imposter, distraction→assimilate
- Collectibles: heart→handshake icon, cross→passport icon, globe→globe (same), trophy→trophy (same)
- Backgrounds: drawWealth→drawBubble (isolation), drawFaith→drawBridge (integration), drawBgCrossSymbol→drawBgFlagSymbol
- All Bible verses replaced with secular quotes (Morgenstern, Proust, Maya Angelou, Tolkien, etc.)
- All missions/church/faith language replaced with identity/belonging/culture language

## Key Decisions
- **2026-02-19**: Initial fork from Goers. Full content reskin — 16 decisions rewritten, 10 life events, 7+7 pit challenges, 3 gauntlet timed decisions, 8 end-screen narratives, zone quotes, gate labels, enemy types, background art functions, collectible icons, HUD colors. Engine untouched.
- **2026-02-20**: ISM contextualization pass. Reviewed Lausanne Global Classroom ISM User Guide through 3 lenses (ISM leader, international student, pastor). Identified 7 gaps and rewrote 5 decisions + 2 life events:
  - CAMPUS Easy: accent coaching → language-as-identity (ISM: language exhaustion)
  - CULTURE Hard: "be more local" → cross-cultural dating (ISM: missing relationship dimension)
  - BELONGING Easy: lead orientation → host family weekly dinners (ISM Ep3: power of hospitality)
  - HOMESICK Easy: scrolling photos → spiritual/existential seeking (ISM Ep2: faith questions abroad)
  - ROOTS Easy: company sponsorship → re-entry/reverse culture shock (ISM Ep8: re-entry)
  - Life event: Thanksgiving invite → campus counseling visit (mental health stigma gap)
  - Life event: laptop dies → racist encounter on bus (racism beyond stereotypes gap)

## Gotchas
- Internal variable names (`heart`, `faith`, `money`, `cross`, etc.) are PRESERVED from Goers to avoid breaking engine logic. Only display text/labels changed.
- If engine bugs are found, patch both Goers and Crossings (rare — engine is stable).
- `drawBubble()` replaces `drawWealth()` — isolation progression (small room → TV → takeout → headphones → co-national group → food shop → flag → video call)
- `drawBridge()` replaces `drawFaith()` — integration progression (coffee chat → potluck → cultural festival → community center with mural → rainbow)
- `drawBgFlagSymbol()` replaces `drawBgCrossSymbol()` — flags instead of crosses on buildings
