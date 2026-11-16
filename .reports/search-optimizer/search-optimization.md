# Search optimization — Thawscope site (web branch, 2026-11-16)

Target: https://nguyenvanlamm.github.io/thawscope-site/ (repo `thawscope-site`). Store listing search was done at S8
by aso-marketing (`thawscope/store/aso-report.md`), so this run is web only.

Members: website-agent-readiness PASS (scan once, plan written, no issues filed by the owner's scope) ·
seo-ai-optimizer COMPLETE (fixes applied, audit 0 critical) · viral-product-evaluator — run once inside
design-optimizer right after this report (same site), not twice.

## Findings

| P | Check | Owner | Finding | Status |
|---|---|---|---|---|
| P1 | robots-sitemap | seo-ai-optimizer | no sitemap.xml; host-root robots.txt lacked this site's Sitemap line | sitemap.xml added; root line added in `nguyenvanlamm.github.io` at S9 (scan's robots check corroborates) |
| P1 | meta-tags | seo-ai-optimizer | home title 68 chars, description 232 | fixed (55 / 153) |
| P1 | structured-data | seo-ai-optimizer | privacy/support without JSON-LD or OG; home graph thin | fixed: WebPage, ContactPage, WebSite, VideoGame + MobileApplication, FAQPage |
| P2 | llms-txt | seo-ai-optimizer | no site llms.txt (the host root's lists other games) | added; root llms.txt line added at S9 |
| P2 | crawler-access | seo-ai-optimizer | no AI-bot directives under the site path | explicit allows in site robots.txt; host root already allows all with Content-Signal |
| P2 | markdown-pages | website-agent-readiness | Markdown for Agents not supported (P0 of the scan's plan) | not fixable on GitHub Pages (no content negotiation); planned only |
| P3 | agent-readiness-scan | website-agent-readiness | 2/5 Bot-Aware; 13 fails, 10 of them API/OAuth/MCP/A2A discovery for a site with no API | plan in `reports/website-agent-readiness/agent-ready-plan.md`; no issues filed |
| P3 | 404 | seo-ai-optimizer | no 404 page | added (`noindex`) |

## Skipped / not covered

- `ai-actions`: no web-branch member evaluates it; design-optimizer's ux-ax-review covers it next.
- The scan predates the fixes; a re-scan after deploy would be a new send to isitagentready.com.
