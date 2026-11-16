# UX / AX Review: Thawscope landing site

## Executive Summary

**Outcome: PASS** (audit coverage, not product quality): every aspect outside `skip-checks` has evidence. 8 findings (1 medium, 7 low), 9 plan tasks. No critical or high issues.

Strengths: one clear hero, AA contrast on every text token, landmarks, skip link and visible focus, no horizontal scroll from 320 to 1280 px, a very light page (about 56 KB first view on mobile, LCP 52–152 ms unthrottled lab, CLS 0), FAQ that answers the real objections (free, offline, no data), and a well-formed local llms.txt and JSON-LD.

Top three priorities:
1. **T2 (P2, F1)**: there is no way to keep the game for launch. Both "Coming soon to the App Store" elements are inert spans styled like the primary button. Add a share/copy-link button in the existing `.btn2` style now, and turn the pill into a real App Store link at launch.
2. **T6 (P2, F5)**: the JSON-LD Offer says `PreOrder`, but no pre-order exists.
3. **T3 (P3, F2)**: the alt text and caption of the "won" screenshot describe a stars result sheet the image does not show.

## Scope and Evidence

- Orchestrated by: `design-optimizer`. Evidence dir: `/home/lam/Documents/projects/thawscope-site/.claude/worktrees/s9-site/.reports/design-optimizer/evidence`, captured 2026-11-16T00:05:42Z (lab/capture evidence, not field data).
- Mode: evidence-only, plus one live lab run in headless Chrome (E5, E6) for metrics the manifest lacked.
- Audience (assumption, owner away): adults who play daily word puzzles on iPhone. Primary goal (assumption): understand the game and remember it for launch. There is no store link yet.
- Sample: home (live and local), support and privacy (local; live returns 200), 404 (local only), llms.txt (local; live 404). Excluded: no other routes exist.
- Sources: the local checkout is newer than live. It adds robots, sitemap, llms.txt, a 404 page, `@graph` JSON-LD and Twitter tags, with the same look and copy. Each finding states whether it came from local or live.
- Tool limits: headless google-chrome on Linux (viewport emulation, not devices). The Linux machine does not have the declared brand fonts. There was no screen reader and no field data. No external validator was run.
- Repo sync: no sync or stash was run. The orchestrator chose an output dir inside the worktree, under the untracked `.reports/` folder, and the brief allows writing only there. This is recorded as an assumption. The checkout was snapshotted (sha256 of all files outside `.git` and this output dir) before inspection and compared afterwards.
- `skip-checks`: clarity, robots-sitemap, markdown-pages, crawler-access.

| ID | Source | Method | Observation |
|---|---|---|---|
| E1 | evidence/manifest.json | manifest | Live home is 200. robots, sitemap, llms.txt and 404 at the site path return 404 on live because they are not deployed yet. |
| E2 | local index.html:143-146, 252-259 (live page.html:129, 242) | source | Both App Store elements are `<span class="soon">`. The page has no share, copy, notify or bookmark action. |
| E3 | screenshots mobile.png 390, desktop.png 1280 (live) | render | `.soon` renders as a dark filled pill with the Apple logo. It is the largest action-shaped element in the hero. |
| E4 | assets/won.webp; index.html:219-220 | image + source | The image shows HONEY thawed, best 100°, 20 of 30 probes left, and no stars. The alt and caption mention a stars result sheet. |
| E5 | CDP lab run, live, 2026-11-16, no throttling | lab | LCP 52–152 ms, CLS 0, 55–60 KB at mobile widths, 99 KB at 1280. No horizontal scroll at 320–768. |
| E6 | CDP keyboard walk at 1280 | scripted | Tab order is logical with a visible focus ring at every stop. Landmarks and headings are in order. Alt text is present. No motion. |
| E7 | tokens at index.html:43-44 | contrast calc | ink3 on frost 5.41:1, orange-ink on white 5.47:1 and on frost 5.0:1. All text pairs reach AA. |
| E8 | index.html:51, 64, 91; live page.html | source + runtime | Instrument Sans and IBM Plex Mono are named in the CSS but never loaded: no @font-face and `document.fonts` is empty. |
| E9 | index.html:111-118 | source + computed | The nav is `display:none` at widths up to 820 px with no substitute. The won.webp figure is hidden at 600 and 768. |
| E10 | assets/icon-256.png | file size | 25,515 B, displayed at 40×40 CSS px. |
| E11 | index.html:30-40; head.json (live) | JSON parse | The JSON-LD parses. The Offer `availability` is PreOrder. FAQ text matches the page. Live still has the older single VideoGame node. |
| E12 | local llms.txt:1-17 | source | The file is well formed. Line 3 says "on the App Store as …" and "Coming soon" in the same sentence. |
| E13 | site-path/llms.txt, origin llms.txt | saved files | The site-path file is 404 on live. The origin llms.txt has no Thawscope entry. |
| E14 | support.html, privacy.html, 404.html | source | Same tokens and system font on every sub-page. The 404 page uses the thermal ramp, root-absolute links and noindex. |

## Human UX

| Aspect | Status | Rationale | Refs |
|---|---|---|---|
| clarity | not-tested | skipped — owned by dont-make-me-think | — |
| brand | issues | Palette, ramp and tone are consistent across all pages. The two declared typefaces never load, so the rendered type depends on the OS. | E3, E8, E14, F8 |
| responsive | issues | No overflow at 320–768 and a clean stack at 390. The header nav disappears at 820 px and below. Hiding the third screenshot at 421–820 px is a deliberate grid choice and is not filed. Zoom and orientation were not tested. | E3, E5, E9, F3 |
| accessibility | issues | Landmarks, headings, skip link, focus ring, contrast and the lack of motion pass on the sample. One alt text is inaccurate. Screen readers were not tested (T1). | E4, E6, E7, F2 |
| performance | issues | Fast in the lab. One oversized icon. Unthrottled lab run only, no field CWV. | E5, E10, F4 |
| conversion | issues | Value and objections are covered. The remember-for-launch goal has no action. | E2, E3, F1 |

## AI/Search AX

| Aspect | Status | Rationale | Refs |
|---|---|---|---|
| robots-sitemap | not-tested | skipped — owned by website-agent-readiness | — |
| structured-data | issues | Local `@graph` parses and the FAQ matches visible text. The `PreOrder` Offer is not true. Google limits FAQ rich results to authoritative government and health sites, so FAQPage helps parsers but is not an expected rich result. Live serves the older markup until deploy. | E11, F5 |
| markdown-pages | not-tested | skipped — owned by website-agent-readiness | — |
| llms-txt | issues | Good format and accurate links. It states a present App Store listing, and it is not live or listed at the origin yet. llms.txt is a proposal; no claim is made that any provider reads it. | E12, E13, F6, F7 |
| crawler-access | not-tested | skipped — owned by website-agent-readiness | — |
| ai-actions | issues | There is no copy-link or share action. That action serves the launch goal, so it is merged into F1. Open-in-AI buttons are optional and not recommended. | E2, F1 |

## Prioritized Findings

| ID | Aspect | Kind | Sev / Conf | Source | Restyle | Finding → Recommendation |
|---|---|---|---|---|---|---|
| F1 | conversion (+ai-actions) | observed | medium / high | local + live | no | The page offers no way to save or share the game for launch, and the button-styled `span.soon` does nothing (E2, E3). → Add a "Share Thawscope" button in `.btn2` style that uses `navigator.share` with a clipboard fallback and an aria-live "Link copied" message. At launch, make `.soon` an `<a>` to the App Store and add the `apple-itunes-app` meta. |
| F2 | accessibility | observed | low / high | local index.html:219-220, live | no | The won.webp alt and caption claim a stars result sheet that is not in the image (WCAG 2.2 SC 1.1.1) (E4). → Describe what the image shows (HONEY thawed, best 100°, 20 of 30 left), or swap in a capture that shows the stars sheet. |
| F3 | responsive | observed | low / high | local index.html:116, live | no (layout only) | `header.top nav {display:none}` at widths up to 820 px with no replacement (E9). → Keep FAQ and Support visible and hide only "How it plays" below about 420 px. |
| F4 | performance | observed | low / high | local assets/icon-256.png | no | A 25.5 KB 256 px PNG is shown at 40 px (E10). → Serve 80 px and 120 px files through `srcset`. |
| F5 | structured-data | observed | low / high | local index.html:32, live | no | `offers.availability` is PreOrder, but no pre-order exists (E11). → Remove `offers` or its availability until launch, then add InStock with the store `url` and `sameAs`. |
| F6 | llms-txt | observed | low / medium | local llms.txt:3 | no | Present-tense "on the App Store as …" for an unreleased app (E12). → Reword to "to be listed as …" and add the real URL on launch. |
| F7 | llms-txt | observed | low / high | live + origin | no | llms.txt returns 404 live, and the origin llms.txt has no Thawscope entry (E13). → Deploy the branch and add one entry to the root llms.txt. |
| F8 | brand | observed | low / medium | local index.html:51, 64, 91, live | **restyle — needs owner** | Instrument Sans and IBM Plex Mono are declared but never loaded (E8). → The owner chooses: self-host WOFF2 files (the look changes to the intended fonts), or remove the names so the CSS matches the system-font look that ships. |

## Improvement Plan

| Task | Phase | Priority | Findings | Owner | Effort | Depends | Expected impact | Acceptance check |
|---|---|---|---|---|---|---|---|---|
| T1 VoiceOver pass on iPhone Safari | 0 | P3 | — (measurement) | QA/a11y | S | — | Closes the screen-reader evidence gap | VoiceOver reads the skip link, nav, h1, Coming soon text, FAQ states and every alt in order; notes recorded per page |
| T2 Share/copy-link now, App Store link at launch | 1 | P2 | F1 | frontend | S | — | Visitors can keep the game for launch (not measured, since there are no analytics) | The iPhone share sheet opens with the canonical URL. Desktop copies the URL and announces it. No colour or font values change. At launch, `.soon` is a focusable `<a>` |
| T3 Fix won.webp alt and caption | 1 | P3 | F2 | content | XS | — | Accurate description for all users | The text mentions only elements visible in the image |
| T4 Mobile header keeps FAQ and Support | 1 | P3 | F3 | frontend | XS | — | Faster mobile navigation | Links visible at 320, 375, 390 and 768 px, scrollWidth equals innerWidth, 1280 unchanged |
| T5 Right-sized header icon | 1 | P3 | F4 | frontend | XS | — | About 20 KB less in the first view (no timing claim) | Icon transfer under 6 KB at 390 px with cache disabled |
| T6 Align JSON-LD offers | 2 | P2 | F5 | frontend/SEO | XS | — | No false pre-order claim | JSON parses, no PreOrder while there is no store link, Schema.org validator shows no errors |
| T7 Reword the llms.txt store claim | 2 | P3 | F6 | content | XS | — | Assistants are not sent to a missing listing | Line 3 is future tense and matches "Coming soon" |
| T8 Deploy and list in the root llms.txt | 2 | P3 | F7 | site owner | XS | T6, T7 | Live site serves the new llms.txt and JSON-LD | `/thawscope-site/llms.txt` returns 200, the root llms.txt links it, live home has the `@graph` |
| T9 Font decision (restyle — needs owner) | 3 | P3 | F8 | owner + design | S | — | Rendered type matches the approved design | The owner confirms the look. Loaded fonts show status loaded with CLS 0, or no unloaded names remain in the CSS |

Phase notes: T1 is phase 0 as a measurement task. T8 waits for T6 and T7 so that one deploy carries all of the content fixes. No phase exceptions.

## Limitations and Next Step

- Evidence gaps: no field Core Web Vitals (the lab run was unthrottled and from one machine), no screen reader or iOS device run, screenshots at 390 and 1280 only, the approved mockup's fonts were not inspected (F8 needs the owner), and there is no analytics or user research. Human understanding is unconfirmed.
- Nothing here certifies WCAG conformance, search indexing, AI citations or conversion uplift.
- The skipped aspects (clarity, robots-sitemap, markdown-pages, crawler-access) belong to the orchestrator's other members. Every skip-check id was a valid aspect id.
- No finding restyles the approved look except F8, which is marked restyle — needs owner. The colours #F3F5F7, #24282C, #FF6A13 and #B84300 and the thermal ramp stay unchanged in every recommendation.
- State check: the snapshot comparison found no change to any site file. Two new files appeared during the run: `.reports/design-optimizer/reports/dont-make-me-think/usability-review.md` and `.../viral-product-evaluator/viral-evaluation.md`. They are reports from parallel members of the same orchestrator run, not written by this review, and no site file changed. Treated as resolved.
- Artifacts:
  - `/home/lam/Documents/projects/thawscope-site/.claude/worktrees/s9-site/.reports/design-optimizer/reports/ux-ax-review/UX_AX_REVIEW.md`
  - `/home/lam/Documents/projects/thawscope-site/.claude/worktrees/s9-site/.reports/design-optimizer/reports/ux-ax-review/ux-ax-findings.json`

Would you like me to implement any of these fixes? Choose the finding/task IDs and scope.
