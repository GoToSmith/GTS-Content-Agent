# SEO Standards - Quality Rubric

Shared file (not client-specific). Defines quality standards that the engine enforces automatically.

> **Note:** Adapt examples, sources, and date formats to your target market. The standards below are language-agnostic; replace sample titles and meta descriptions with equivalents in your content language.

## Word Count per Intent

| Intent | Min | Optimal | Max |
|--------|-----|---------|-----|
| Informational (how/what/why) | 1500 | 2500 | 3500 |
| Commercial Investigation (comparison) | 2000 | 3000 | 4000 |
| Quick Answer / Definition | 600 | 1000 | 1500 |
| Process / Tutorial | 1500 | 2500 | 3500 |
| Pillar Page | 3000 | 4000 | 6000 |

## Title Tag Formula

**Format:** [Primary Keyword] - [Benefit or Angle] [(optional: year)]

**Rules:**
- Max 60 characters (including spaces)
- Primary keyword in the first 3 words
- No clickbait (only promise what the article delivers)
- Unique per article (check for duplicates)

**Good title examples:**
- "Production Automation: 5 Deployments That Cut Time by 40%"
- "CRM for Small Business - What Actually Works [2025]"
- "How to Calculate ROI on a MES System Implementation"

**Bad title examples:**
- "A Comprehensive Guide to Production Automation for Businesses" (too generic, "comprehensive")
- "Everything You Need to Know About CRM" (clickbait without substance)

## Meta Description Formula

**Format:** [Primary Keyword] [benefit/outcome]. [Specific detail: number, example, unique perspective]. [Soft CTA].

**Rules:**
- Max 155 characters
- Primary keyword naturally in the first sentence
- Include a specific detail, not "learn more"
- CTA: "See how", "Compare examples", "Get the framework"; not "Click here"

## Schema Types per Format

| Article format | Required schema | Optional schema |
|----------------|----------------|------------------|
| Standard article | Article + FAQ | BreadcrumbList |
| Step-by-step guide | Article + HowTo | FAQ |
| Comparison / Ranking | Article + FAQ | ItemList |
| Definition/Explanation | Article + FAQ | DefinedTerm |
| Case study | Article | Review |

## Internal Linking Minimum

- Minimum 3 internal links per article
- 1x pillar page (required)
- 2x cluster pages (topically related)
- Maximum 8 internal links (don't link to everything)
- Anchor text: a natural sentence fragment, not "click here"

## On-Page Checklist (25 items)

See: skill `seo-optimizer/SKILL.md`

## GEO Signals Checklist (12 items)

See: skill `geo-optimizer/SKILL.md`

## Quality Gate Scoring

See: skill `quality-gate/SKILL.md`

Hard threshold: 80/100 = minimum for publication.

## Banned SEO Practices (never)

- Keyword stuffing; naturalness over density
- Hidden text or links
- Duplicate content between articles
- Thin content (<600 words for any article)
- Buying links
- Clickbait titles that don't match the content
- Auto-generated content without human review (this engine has mandatory review gates)
