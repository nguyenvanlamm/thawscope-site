# Design Optimization: https://nguyenvanlamm.github.io/thawscope-site/

Run: design-optimizer 1.1.0 · 2026-11-16 (intake 00:05:42Z) · mode: audit
Evidence: evidence/manifest.json · AX ownership case: A (scan reused, owner-approved G1 earlier today, scannedAt 2026-11-16T00:02:34Z)
Members: dont-make-me-think √ (COMPLETE, thinking cost MODERATE) · ux-ax-review √ · website-agent-readiness ~ PARTIAL (G3 not approved, owner away; score 2/5) · viral-product-evaluator ~ PARTIAL (game code out of scope, repo sync skipped; 56/100)

Sources: "local" = /home/lam/Documents/projects/thawscope-site/.claude/worktrees/s9-site (newer than live); "live" = the deployed page and the headless-Chrome screenshots in evidence/screenshots/.
Safe = usability, accessibility, copy clarity, meta, no restyle, no new product claims. Needs owner = restyle, layout change, new UI/feature, or new copy/claims.

## Summary
- Thinking cost (dont-make-me-think): MODERATE, 6 issues (0 high, 3 medium, 3 low)
- Agent-readiness score: 2/5 Bot-Aware (scanned once, 2026-11-16T00:02:34Z; reused, not re-sent)
- Virality score: 56/100 (Needs work)
- Findings: 0 P0 · 2 P1 · 8 P2 · 13 P3 (3 cross-member duplicates merged: ux-ax-review F1 and viral V4 into D-01, dont-make-me-think DMMT-4 into D-03)

## Findings

| ID | Pri | Check | Finding | Evidence | Owner | Also reported by | Fix | Class |
|---|---|---|---|---|---|---|---|---|
| D-01 | P1 | clarity | Both "Coming soon to the App Store" pills are dark button-like `<span class="soon">` that do nothing; the launch plan ("This page will link to it on launch day") is only inside the last collapsed FAQ item | local index.html:144, :257, :247; live mobile.png/desktop.png | dont-make-me-think (DMMT-1, DMMT-2) | ux-ax-review F1 (conversion), viral V4 | Add one plain line under each `.cta`: "Not out yet. This page will link to the App Store on launch day." (reuses FAQ text). Changing the pill fill is restyle | safe |
| D-02 | P2 | conversion | No way to save or share the page for launch | local index.html:143-146, 252-259 | ux-ax-review F1 | viral V4 | Add a "Share Thawscope" button in the existing `.btn2` style (navigator.share, copy-link fallback with an aria-live "Link copied"); at launch make `.soon` a store link and add `apple-itunes-app` meta. An email list would be a new feature | needs owner (new UI/JS) |
| D-03 | P2 | responsive | Header nav is hidden at <=820px with no replacement; FAQ and Support reachable only from the footer | local index.html:116 `header.top nav{display:none}`; live checked 320-768px | ux-ax-review F3 | dont-make-me-think DMMT-4 | Keep FAQ and Support visible at narrow widths in the same style; hide only "How it plays" below about 420px | safe |
| D-04 | P2 | structured-data | JSON-LD `offers.availability` is `PreOrder`, but no pre-order exists | local index.html:32; live head.json | ux-ax-review F5 | — | Remove `availability` (or the whole `offers`) until launch; at launch set InStock + store `url` + `sameAs` | safe |
| D-05 | P2 | llms-txt | llms.txt says Thawscope is "on the App Store as \"Thawscope: Word Puzzle\"" although it is unreleased | local llms.txt:3 | ux-ax-review F6 | — | Reword to "to be listed on the App Store as ..." | safe |
| D-06 | P2 | llms-txt | Site llms.txt (and robots.txt, sitemap.xml, 404.html) return 404 on live; root llms.txt has no Thawscope entry | manifest site-path/*: 404 | ux-ax-review F7 | — | Deploy the s9-site branch; add one Thawscope line to the root llms.txt | safe |
| D-07 | P2 | meta-tags | Live head is out of date: description 237 chars, title 67 chars, no twitter:title/description/image | live head.json vs local head.local.json | viral-product-evaluator V2 | — | Deploy the s9-site head (152-char description, 55-char title, twitter:* tags already written) | safe |
| D-08 | P2 | accessibility | `won.webp` alt and caption describe a result sheet with stars; the image shows HONEY thawed, best 100°, 20 of 30 probes left (WCAG 1.1.1) | local index.html:219-220; live page.html | ux-ax-review F2 | — | Make alt/caption describe what is shown, or swap in a capture that shows the stars | safe |
| D-09 | P1 | meta-tags | `assets/share-card.jpg` has no wordmark or words and is about half empty; at feed size only the icon reads | local assets/share-card.jpg | viral-product-evaluator V1 | — | Redesign the card: headline "Every guess shows which way is warmer", wordmark, "Coming soon to iPhone", ramp as the only accent, content in the centre 630x630 | needs owner (asset redesign / restyle) |
| D-10 | P2 | meta-tags | privacy.html and support.html use `twitter:card=summary` with the 1200x630 card; a centre square crop is mostly empty frost (checked by cropping, not a platform preview) | local privacy.html:18, support.html:18 | viral-product-evaluator V3 | — | Add `twitter:image` = assets/icon-256.png, or use `summary_large_image` | safe |
| D-11 | P3 | brand | CSS names "Instrument Sans" and "IBM Plex Mono" but never loads them; visitors get each OS's system font | local index.html:51, 64, 91; live runtime | ux-ax-review F8 | — | Owner decides: self-host the fonts, or remove the names | restyle — needs owner |
| D-12 | P3 | clarity | Hero fact "A new Daily Core every day" uses a game term explained only later | local index.html:149 | dont-make-me-think DMMT-3 | — | "A new daily word (Daily Core)" | safe |
| D-13 | P3 | clarity | Home screenshot and its alt say "Expeditions"; page copy and caption say "Core sets" | local index.html:211; live desktop-full.png | dont-make-me-think DMMT-5 | — | Caption/alt: "today's Daily Core and your Core sets (Expeditions)" | safe |
| D-14 | P3 | clarity | At 390px the gameplay image starts about 720px down (visual estimate, not measured) | live mobile.png; `.hero` <=820px | dont-make-me-think DMMT-6 | — | Shorten the mobile lede to two sentences, or move `.phone` after the H1 | needs owner (layout reorder) |
| D-15 | P3 | performance | `assets/icon-256.png` is 25.5 KB but shown at 40px | local header.top img | ux-ax-review F4 | — | Serve 80px/120px versions via `srcset` | safe |
| D-16 | P3 | virality | Final section's second button is "Get help or send feedback"; nothing helps a visitor remember the game | local index.html:256-259 | viral-product-evaluator V4 | — | Make it "See how it plays" (anchor to the how-it-plays section) | safe |
| D-17 | P3 | virality | Hero `.lede` describes the mechanic, never the feeling | local `.lede` | viral-product-evaluator V5 | — | Open the lede with "No more blind guessing: even a cold word tells you where to turn." (h1 unchanged) | needs owner (new marketing copy) |
| D-18 | P3 | virality | In-app purchases are disclosed only in a collapsed FAQ item | local index.html FAQ | viral-product-evaluator V8 | — | Viral's fix ("120 free levels · no ads") already exists in `.facts` (index.html:148, 150); orchestrator note: the remaining gap is adding "Optional in-app purchases" to `.facts`, reusing the FAQ answer | safe |
| D-19 | P3 | virality | One section (index.html:187-224) packs five ideas plus the screenshots | local | viral-product-evaluator V6 | — | Give the screenshots their own section, or move the tools card into How it plays | needs owner (layout) |
| D-20 | P3 | virality | No comparison with the daily guess-the-word category | local | viral-product-evaluator V7 | — | One unbranded category line | needs owner (new comparative claim; App Store 4.3 copycat risk) |
| D-21 | P3 | virality | Other misses: orange accent not on the main button (#2); "about twice as close" needs the exact game value (#26, index.html:206); interactive sample, maker note, testimonials absent (#25, #15, #14/#29) | local | viral-product-evaluator | — | Owner supplies the exact Flare value; the rest is restyle or new content | needs owner |
| W-01 | P3 | markdown-pages | Scan `markdownNegotiation` fail (scan triage P0: gate to level 3). GitHub Pages cannot negotiate `Accept: text/markdown` | evidence/agent-readiness/scan.json | website-agent-readiness | — | Optional: publish a markdown alternate (e.g. index.md) linked with `<link rel="alternate" type="text/markdown">`; route to seo-ai-optimizer | safe |
| W-02 | P3 | agent-readiness-scan | 12 other fails: `linkHeaders` (GitHub Pages cannot set headers), `dnsAid` (github.io DNS not owner-controlled), 10 discovery checks (API catalog, OAuth, MCP/A2A cards, agent skills, WebMCP, ARD, auth.md, PAP) for a static page with no API or auth | scan.json; reports/website-agent-readiness/.agent-ready/triage.json | website-agent-readiness | — | No action recommended for a static pre-launch game page; record as accepted | safe (no action) |

## Check coverage (each canonical ID once)

| Check | Owner | Result |
|---|---|---|
| clarity | dont-make-me-think | D-01, D-12, D-13, D-14 |
| brand | ux-ax-review | D-11 |
| responsive | ux-ax-review | D-03 |
| accessibility | ux-ax-review | D-08 (contrast AA, keyboard, skip link, landmarks passed) |
| performance | ux-ax-review | D-15 (lab LCP 52-152 ms, no CLS, ~56 KB mobile) |
| conversion | ux-ax-review | D-02 |
| structured-data | ux-ax-review | D-04 |
| llms-txt | ux-ax-review | D-05, D-06 |
| ai-actions | ux-ax-review | no separate finding (tagged on F1 → D-02) |
| robots-sitemap | website-agent-readiness | pass (robotsTxt, sitemap) — scan read the origin root files; the site's own robots/sitemap are not deployed (D-06) |
| crawler-access | website-agent-readiness | pass (robotsTxtAiRules, contentSignals) |
| markdown-pages | website-agent-readiness | W-01 |
| agent-readiness-scan | website-agent-readiness | 2/5; W-02 |
| virality | viral-product-evaluator | D-16 to D-21 |
| meta-tags | viral-product-evaluator | D-07, D-09, D-10 |

## Skipped (owned elsewhere)
| Check | Skipped by | Owner |
|---|---|---|
| clarity | ux-ax-review | dont-make-me-think |
| robots-sitemap, markdown-pages, crawler-access | ux-ax-review | website-agent-readiness |

## Not covered
| Check | Reason |
|---|---|
| — | Every canonical check had an owner. Gaps inside members: no screen-reader/device run, no field speed data (ux-ax-review); privacy/support/404 not reviewed and no interactions clicked (dont-make-me-think); game codebase not reviewed (viral-product-evaluator). |

## Orchestrator note (not a member finding)
- Local index.html:266 footer reads "© 2026 Luong Nguyen" and the JSON-LD `author` is "Luong Nguyen"; the live page and the previous commit (7404a3f) read "© 2026 Thawscope". The repo's git author is `nguyenvanlamm`. Owner should confirm the intended publisher name before deploying. Needs owner.

## Member reports
- reports/dont-make-me-think/usability-review.md
- reports/ux-ax-review/UX_AX_REVIEW.md, reports/ux-ax-review/ux-ax-findings.json
- reports/website-agent-readiness/result.md, .agent-ready/ (scan.json, fixes.md, triage.json); no agent-ready-plan.md (G3 pending)
- reports/viral-product-evaluator/viral-evaluation.md

## Next step
Apply is opt-in. Reply with finding IDs to fix (e.g. "apply D-01, D-04"); each routes to one member and its own confirmation gate. AX/SEO-file fixes (D-04 to D-07, D-10, W-01) route to seo-ai-optimizer.
Pending member offers (recorded, not answered): ux-ax-review — "Would you like me to implement any of these fixes? Choose the finding/task IDs and scope."; website-agent-readiness — G3 (sync branch + write agent-ready-plan.md).
