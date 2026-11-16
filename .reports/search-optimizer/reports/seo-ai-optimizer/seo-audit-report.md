# SEO and AI-bot audit — thawscope-site (2026-11-16)

Orchestrated by search-optimizer. Repo: `thawscope-site` (worktree `s9-site`); live copy:
https://nguyenvanlamm.github.io/thawscope-site/ (evidence captured before the fixes). Fixes pre-authorized by the
game-clone pipeline (owner away; S9 scope).

## Before (audit_seo.py: 0 critical, 8 warning, 2 info)

| Severity | File | Finding | Fix applied |
|---|---|---|---|
| Warning | index.html | title 68 chars | 55: "Thawscope: a word puzzle that shows which way is warmer" |
| Warning | index.html | description 232 chars | 153 chars |
| Warning | privacy.html, support.html | no JSON-LD, no OpenGraph | WebPage / ContactPage JSON-LD linked to the site and game ids; OG and Twitter tags |
| Warning | project | no robots.txt under the site path | `robots.txt` with Sitemap and explicit AI-bot allows (documentary: crawlers read the host root, which already allows all and gets this site's Sitemap line at S9) |
| Warning | project | no sitemap.xml | `sitemap.xml`: home, support, privacy |
| Info | project | no llms.txt | `llms.txt`: rules, thaw stages, campaign, Daily, tools, what is free, privacy, pages; linked from index `<link rel="alternate">` |
| Info | index.html | one VideoGame block | `@graph`: VideoGame + MobileApplication (author, screenshot, players), WebSite, FAQPage mirroring the visible FAQ |
| — | project | no 404 page | `404.html`, `noindex`, links back home and to support |
| — | index.html footer | "© 2026 Thawscope" | "© 2026 Luong Nguyen", matching the App Store copyright line (docs/APP-STORE-CONNECT.md) |

## After (audit_seo.py: 0 critical)

index, privacy and support: no issues; all JSON-LD parses. Remaining warnings: `404.html` has no canonical, JSON-LD
or OG (intended for a `noindex` error page) and the evidence copy of the old page (pre-fix capture). Info:
no `.well-known/ai-plugin.json` (optional, nothing to describe: no API).

## Step 8 — agent readiness

REUSED: `evidence/agent-readiness/scan.json` from website-agent-readiness in this run, level 2/5 (Bot-Aware),
scanned 2026-11-16T00:02Z, before these fixes were deployed. A re-scan after the push is a new decision for the
owner.

## Not fixed (and why)

- Markdown for Agents, Link headers, DNS-AID: GitHub Pages serves static files and cannot negotiate content or add
  headers; see `reports/website-agent-readiness/agent-ready-plan.md`.
- API/OAuth/MCP/A2A discovery files: the site has no API, sign-in or agent tools to describe.
