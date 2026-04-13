# teq-niq.github.io — Strategy & Design Notes
_Last updated: April 13, 2026_

---

## Purpose of This Site

Personal portfolio/article showcase for Raghuraman Ramaswamy.  
--

## Article Card Design Decisions

### Card structure
- Cards are `<div class="article-card">` — **not** `<a>` wrappers.
- Reason: each card has two links in the footer (DZone + GitHub). Nesting `<a>` inside `<a>` is invalid HTML.

### Two links per card
Each card footer has:
1. **📄 DZone Article** — solid blue filled button, primary CTA. Opens the DZone article in a new tab.
2. **⌥ GitHub Repo** — muted plain text link, secondary. Opens the repo (or specific branch) in a new tab.

### Why DZone is the primary link (for now)
- DZone is the primary way to attract readers right now.
- The homepage audience is small and specific; DZone gets the broad organic search traffic.
- Keeping DZone as primary helps grow view counts (53K, 112K, 119K reads are credibility signals).

### "First published on DZone" badge
- Small italic grey text above the card title on every card.
- Gives DZone credit without needing a separate link.
- When local article copies are added, this badge inside the card (and inside each article) handles attribution — no DZone link needed on the card itself at that point.

### GitHub links — branch-specific for older articles
Cards 4, 5, 6 point to specific branches of the `sample` repo:
- Card 4 (Extending Swagger): `tree/documented-custom-validators-updated1`
- Card 5 (Doing More): `tree/springdoc-openapi-doingmore-updated1`
- Card 6 (OpenAPI 3 Intro): `tree/springdoc-openapi-intro-update1`

Cards 2 & 3 (both MCP articles) share the same repo: `mcp-stdio-logging`

---

## Thumbnail / Image Decisions

### Aspect ratio
- All cards: `aspect-ratio: 1.6 / 1` on `.card-thumb-wrap`
- Original was `1.92 / 1` (too short for the GIFs). `1.2 / 1` was tried but too tall.
- `1.6 / 1` is the sweet spot — GIFs look good, static images fill nicely.

### object-fit
- All thumbnails: `object-fit: cover` — fills the frame, crops rather than letterboxes.
- `object-fit: contain` was tried for static images but caused white padding/letterboxing — reverted.

### GIF-specific (cards 1 & 2)
- `object-position` overrides were tried (`top`, `center 10%`, `center 15%`) to trim top/bottom.
- All were reverted — the default `center center` crop at `1.6 / 1` ratio is optimal.
- If further trimming is needed in future, physically crop the GIF files (e.g. ezgif.com) rather than CSS — CSS cropping on animated GIFs is too blunt.

---

## Future Plans

### When local article copies are added
- Add a **📖 Read Article** link as the new primary CTA (filled blue button).
- Demote DZone to a small secondary text link — "Also on DZone" — or remove from card entirely (attribution is already inside the article copy).
- GitHub link stays as secondary muted text.
- The "First published on DZone" badge stays on the card and is also mentioned prominently at the top of each article copy.

### DZone traffic consideration
- People finding articles via DZone search are a completely separate audience from homepage visitors.
- Removing the DZone card link will not meaningfully reduce DZone traffic — that traffic comes from Google/DZone search, not from this homepage.
- The 119K/112K/53K read counts are already captured as credentials on the cards and won't diminish.

---

## CSS Classes Reference

| Class | Purpose |
|---|---|
| `.article-card` | Card wrapper (`div`, not `a`) |
| `.card-thumb-wrap` | Aspect-ratio container for thumbnail |
| `.card-thumb` | Thumbnail image (`object-fit: cover`) |
| `.card-badge` | "First published on DZone" italic text |
| `.card-title` | Article title |
| `.card-source` | Date |
| `.card-desc` | Description text |
| `.card-tags` | Tag chip row |
| `.card-views` | Read count (👁 112,000+ reads) |
| `.card-footer` | Footer row holding the two links |
| `.card-link` | Base link pill style |
| `.card-link-dzone` | Primary filled blue button |
| `.card-link-github` | Muted plain text link |
