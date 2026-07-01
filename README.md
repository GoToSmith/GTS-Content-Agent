# SEO Content Engine

**Your articles rank on page 3. AI search doesn't cite you. This fixes both.**

A context layer for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) that turns AI into a specialized content engine. Every article is optimized for Google ranking AND AI search citation (Perplexity, ChatGPT Search, AI Overviews).

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Works with Claude Code](https://img.shields.io/badge/Works%20with-Claude%20Code-blueviolet)](https://docs.anthropic.com/en/docs/claude-code)

---

## What This Does

- **SEO + GEO in one pass.** Articles are optimized for traditional search (25-point SEO checklist) and generative AI search (12-point GEO checklist). Most content tools ignore GEO entirely.
- **Automated quality gate.** Every article is scored 0-100 across 5 dimensions. Below 80, the engine self-corrects up to 3 times. Nothing reaches you without passing.
- **Two human review gates.** You approve the brief (5 min) and the final draft (10 min). The engine handles everything between.

---

## Try It in 2 Minutes

```bash
# Clone and open the demo
git clone https://github.com/gotosmith/content-engine.git
cd content-engine/examples/routemaster

# Tell Claude Code to write an article
claude "Write an article about last mile delivery cost reduction"
```

The RouteMaster demo includes pre-filled context files so you can see the full workflow immediately.

---

## Set Up for Your Company

Fill 3 files. Takes about 2 hours one time.

| File | What it contains | Time |
|------|-----------------|------|
| `context/client.md` | Company, product, UVP, 3+ case studies with numbers | 45 min |
| `context/icp.md` | Reader persona, 10+ search queries, pain points | 30 min |
| `context/tone-of-voice.md` | Voice attributes, style rules, good/bad examples | 30 min |

**Recommended** (adds depth to every article):

| File | What it contains | Time |
|------|-----------------|------|
| `context/domain-expertise.md` | Industry terminology, myths to debunk, authority sources | 45 min |

Copy templates from `context/*.template` and fill in the brackets. Use `examples/routemaster/` as reference.

**Auto-generated** (the engine creates these):

| File | Created by |
|------|-----------|
| `context/competitors.md` | SERP analysis during article brief |
| `context/topic-clusters.md` | Keyword discovery workflow |

---

## How It Works

```
You say: "Write an article about [keyword]"

1. Load Context ........... reads your 6 context files
2. Generate Brief ......... keyword analysis, SERP gaps, outline, EEAT plan
3. REVIEW GATE #1 ......... you approve the brief (~5 min)
4. Write Article .......... 1500-4000 words, structured for SEO+GEO
5. SEO Optimize ........... 25-point checklist, auto-fix
6. GEO Optimize ........... 12-point checklist, auto-fix
7. Quality Gate ........... score 0-100, auto-iterate if <80 (max 3x)
8. REVIEW GATE #2 ......... you read the final draft (~10 min)
9. Publish ................ push to CMS as draft, or Markdown package
```

Total: ~45 min Claude, ~15 min you.

![Article Production Workflow](assets/workflow.png)

---

## Quality System

Every article is scored across 5 dimensions before it reaches you:

| Dimension | Weight | What it measures |
|-----------|--------|------------------|
| EEAT Signals | 25 pts | Experience, expertise, authority, trust markers |
| SEO Fundamentals | 25 pts | Title, meta, headings, keyword density, links, schema |
| GEO Signals | 20 pts | Direct answers, structured claims, FAQ, citations, tables |
| Content Quality | 20 pts | Originality, depth, actionability, readability |
| Brand Alignment | 10 pts | Voice match, banned phrase check, style consistency |

**Thresholds:**
- **>= 80:** Passes to you for Review Gate #2
- **65-79:** Auto-iterates with specific diagnosis (you never see this)
- **< 65:** Escalates with full explanation
- Max 3 auto-iteration rounds, then escalates

---

## What is GEO?

**Generative Engine Optimization** is SEO for AI search. When someone asks Perplexity "how do I reduce last mile delivery costs?", GEO determines whether YOUR article gets cited in the answer.

Traditional SEO gets you ranked. GEO gets you cited. This engine does both.

**GEO signals the engine optimizes for:**
- Direct answer to the query in the first 100 words
- Structured claims: "[Claim] because [mechanism], which means [implication]"
- FAQ sections (5+ questions) that match natural language queries
- Data tables that AI can extract and reference
- Named sources with year for every data point
- Entity-first sentences that AI parsers can extract

---

## MCP Connectors

The engine works without connectors (via WebSearch and manual workflows). With connectors, it produces better keyword data, publishes directly to CMS, and pulls real analytics.

| Connector | What it adds | Without it |
|-----------|-------------|------------|
| Ahrefs MCP or SEMrush MCP | Real keyword difficulty, search volume, SERP features | WebSearch-based estimation (less precise) |
| Webflow MCP or WordPress MCP | Publish drafts directly to CMS with metadata and schema | Markdown + metadata package for manual upload |
| Google Search Console MCP | Real ranking data, clicks, CTR for performance review | Manual GSC export or WebSearch-based checks |

Each connector is optional and independent. To set up:

1. Copy the example config:
   ```bash
   cp .claude/mcp.json.example .claude/mcp.json
   ```
2. Fill in your API keys (remove connectors you don't need)
3. Restart Claude Code

See `.claude/mcp.json.example` for the full configuration template.

---

## Commands

| What you say | What happens |
|---|---|
| `Write an article about [keyword]` | Full article production workflow |
| `Find new keywords for [topic]` | Keyword discovery with priority scoring |
| `How is my content performing?` | Performance review with content decay detection |

---

## Article Rules (Hard-coded)

Every article follows these rules automatically:

**Opening:** Start with a number, cost, or specific problem. Never a definition.

**First 100 words:** Direct answer to the primary query.

**Structure:** FAQ (5+ questions), at least 1 data table, internal link to pillar page.

**Claims format:** "[Claim] because [mechanism], which means [implication for reader]."

**Style:** Max 25 words per sentence. 2-4 sentence paragraphs. Active voice. Numbers as digits.

**Banned phrases:** "In today's world", "comprehensive", "it's worth noting", "holistic", "game-changer", "landscape", "leverage" (as verb), "elevate".

**Sources:** Every data point has a named source and year. No exceptions.

---

## Project Structure

```
.
├── CLAUDE.md                          # Engine brain (routing, rules, validation)
├── context/
│   ├── client.md.template             # Your company context
│   ├── icp.md.template                # Reader persona
│   ├── tone-of-voice.md.template      # Voice and style
│   ├── domain-expertise.md.template   # Industry depth (recommended)
│   ├── topic-clusters.md.template     # Keyword map (auto-managed)
│   ├── competitors.md.template        # SERP analysis (auto-generated)
│   └── seo-standards.md               # Quality rubric (shared)
├── .claude/skills/
│   ├── keyword-research/              # Keyword expansion + priority scoring
│   ├── article-brief/                 # Brief generation + SERP analysis
│   ├── article-writer/                # Article writing with measurable checks
│   ├── seo-optimizer/                 # 25-point SEO checklist
│   ├── geo-optimizer/                 # 12-point GEO checklist
│   ├── quality-gate/                  # 0-100 scoring across 5 dimensions
│   └── cms-publisher/                 # CMS publishing or Markdown export
├── .claude/
│   └── mcp.json.example               # MCP connector configuration template
├── workflows/
│   ├── 01-article-production.md       # Keyword to published draft
│   ├── 02-keyword-discovery.md        # Seed topics to keyword map
│   └── 03-performance-review.md       # Monthly content audit
├── examples/
│   ├── routemaster/                   # Full demo (route optimization SaaS)
│   │   └── context/                   # Pre-filled context files
│   └── sample-output/                 # Example brief, article, quality report
└── assets/
    ├── workflow-bpmn.html             # Interactive workflow diagram
    └── workflow.png                   # Workflow diagram (embedded in README)
```

---

## Example Output

See `examples/sample-output/` for a complete production run:

- **`brief.md`** - Article brief for "last mile delivery cost reduction"
- **`article.md`** - Full 2500-word article following all engine rules
- **`quality-report.md`** - Quality gate report scoring 87/100

---

## FAQ

**Do I need MCP connectors to use this?**
No. The engine works with WebSearch for keyword research and produces Markdown for manual CMS upload. Connectors make it better, not possible.

**What languages does it support?**
The engine detects your prompt language and writes in that language. If you write in Spanish, the article is in Spanish. Context files and SEO standards are language-agnostic.

**How long does one article take?**
About 45 minutes of Claude processing and 15 minutes of your time (two review gates). You review the brief and the final draft.

**Can I skip the keyword discovery workflow?**
Yes. Bring your own keywords from any tool. Just say "write an article about [keyword]" and the engine starts immediately.

**What if I don't have case studies yet?**
The engine warns you that articles will lack proof and authority signals, but it proceeds. Fill in case studies when you have them.

**How is this different from other AI writing tools?**
Two things: GEO optimization (most tools ignore AI search entirely) and the automated quality gate (score, diagnose, self-correct loop). The engine also maintains persistent context about your company, readers, and voice across articles.

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on reporting bugs, suggesting features, and submitting pull requests.

---

## License

[MIT](LICENSE)

---

Built by [GoToSmith](https://gotosmith.eu)