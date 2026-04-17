# Claude SEO Skill

A comprehensive SEO research and auditing system for [Claude Code](https://docs.claude.com/en/docs/claude-code). Runs full site audits with 12 specialized sub-skills and 7 subagents — covering technical SEO, content quality, schema markup, Core Web Vitals, image optimization, hreflang, and Generative Engine Optimization (GEO) for AI Overviews, ChatGPT, and Perplexity.

## What it does

Drop a URL in and get back a structured audit across:

- **Technical SEO** — crawlability, indexability, robots.txt, canonicals, URL structure
- **Content quality** — E-E-A-T signals, depth, thin content detection, AI citation readiness
- **Schema markup** — JSON-LD detection, validation, gap analysis
- **Core Web Vitals** — LCP, INP, CLS with fix recommendations
- **Images** — alt text, compression, format, lazy loading, CLS prevention
- **Hreflang** — international SEO, language/region codes, common mistakes
- **Sitemaps** — validation and generation
- **GEO / AI search** — AI crawler accessibility (GPTBot, ClaudeBot, PerplexityBot), llms.txt, passage-level citability, brand mention signals
- **Competitor pages** — "X vs Y" layouts, alternatives pages, feature matrices
- **Programmatic SEO** — template engines, URL patterns, thin content safeguards
- **Single-page deep dive** — full on-page + technical analysis for any URL
- **Strategic planning** — industry-specific templates, content strategy, roadmap

Industry detection for SaaS, e-commerce, local business, publishers, agencies.

## Output

A typical full audit produces:

- Health score (0–100) across 7 weighted categories
- Top 5 priority issues with business impact
- Critical issues (fix this week)
- Prioritized action plan (critical → high-impact → quick wins → long-term)
- Evidence + specific fix for every finding

## Install

### Option A — Claude Cowork (Pro / Max / Team / Enterprise)

1. Download the skill zips from the [`dist/`](./dist) folder. Start with `seo.zip` (the orchestrator) — it's all you need for most audits. Add the others later if you want focused sub-skills.
2. In Claude Cowork: **Settings → Features → Custom Skills → Upload**. Upload each `.zip` file.
3. Toggle the skill on.
4. Ask Cowork: *"Run a comprehensive SEO audit on example.com"* and it will trigger the skill automatically.

### Option B — Claude Code (CLI / desktop)

1. Install [Claude Code](https://docs.claude.com/en/docs/claude-code)
2. Clone this repo:
   ```bash
   git clone https://github.com/tbcreator-nl/claude-seo-skill.git
   ```
3. Copy skills and agents into your Claude config:
   ```bash
   cp -r claude-seo-skill/skills/* ~/.claude/skills/
   cp -r claude-seo-skill/agents/* ~/.claude/agents/
   ```
4. Restart Claude Code. Trigger with any of:
   - "Run an SEO audit on example.com"
   - "Audit this page for SEO"
   - "Check schema markup on X"
   - "Analyze Core Web Vitals"
   - "How do I rank better for Y"

## How to use

**Full site audit:**
```
Run a comprehensive SEO audit on example.com
```
Orchestrator dispatches the relevant subagents in parallel, compiles findings into a single report with a health score and prioritized action plan.

**Targeted:**
```
Check schema markup on stripe.com/pricing
Audit hreflang implementation on my multilingual site
Analyze AI search readiness for example.com
```

**Single page deep-dive:**
```
Deep SEO analysis of https://example.com/blog/post-slug
```

## Requirements

- Claude Code (any recent version)
- Works best with these MCPs for live data: Firecrawl (page scraping), Chrome (JS-rendered schema detection), DataForSEO (rankings, competitor data). Not required — the skill degrades gracefully to WebFetch.

## Structure

```
skills/
├── seo/                    # Orchestrator — dispatches sub-skills and subagents
├── seo-audit/              # Full-site audit framework
├── seo-content/            # E-E-A-T and content quality
├── seo-geo/                # AI search optimization (AI Overviews, ChatGPT, Perplexity)
├── seo-hreflang/           # International SEO
├── seo-images/             # Image optimization
├── seo-page/               # Single-page deep analysis
├── seo-plan/               # Strategic SEO planning
├── seo-programmatic/       # Programmatic SEO at scale
├── seo-schema/             # Structured data detection and generation
├── seo-sitemap/            # XML sitemap analysis and generation
├── seo-technical/          # Technical SEO (crawlability, indexability, CWV)
└── seo-competitor-pages/   # Comparison and alternatives pages

agents/
├── seo-content.md          # Content quality reviewer
├── seo-geo.md              # GEO and AI search specialist
├── seo-performance.md      # Core Web Vitals analyzer
├── seo-schema.md           # Schema markup expert
├── seo-sitemap.md          # Sitemap architect
├── seo-technical.md        # Technical SEO specialist
└── seo-visual.md           # Visual analyzer (Playwright screenshots, mobile rendering)
```

## License

MIT
