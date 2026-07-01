---
name: article-brief
description: Generates a 2-page brief per keyword with H1-H3 outline, EEAT plan, internal links, schema type, word count, and 3 differentiating angles. Output goes to Review Gate #1 for user approval.
allowed-tools: [Read, WebSearch, WebFetch]
---

# Skill: article-brief

## When to use

After the user selects a keyword (from `context/topic-clusters.md` or directly). Always before article-writer.

## Required input

- Target keyword (primary)
- `context/client.md`
- `context/icp.md`
- `context/topic-clusters.md` (for internal link plan)
- `context/domain-expertise.md` (if available, for differentiating angles and LSI terms)

Note: `context/competitors.md` is NOT required as user input. It is auto-generated during this skill via SERP analysis (see Step 2).

## Workflow

### Step 1: Search intent analysis

Identify:
- **Intent type:** Informational / Commercial Investigation / Transactional / Navigational
- **Who is asking:** Which profile from icp.md best matches
- **What they actually want to achieve:** Not "learn more" but what they will do with this knowledge
- **Knowledge level:** What they already know, what they do not know

### Step 2: SERP analysis and competitor content mapping

**Default path (WebSearch):**
Search for the primary keyword and analyze the top 5 results:
- What structure do the top-ranking articles use?
- What do they do well (understand why, do not copy)?
- What do they miss or do poorly (this is your opportunity)?
- Are there featured snippets or AI Overviews (format to beat)?
- What word count range do the top results fall in?

**If MCP available (Ahrefs/SEMrush):**
Use the MCP connector for deeper SERP data:
- Content gap analysis
- Backlink profiles of top results
- SERP feature opportunities
- Traffic estimates for top-ranking pages

**Auto-generate competitors.md:**
Write findings to `context/competitors.md` with the following structure:
```markdown
# SERP Analysis: [Primary Keyword]
Generated: [date]

## Top 5 Results
1. [URL] - [Title] - Strengths: [...] - Gaps: [...]
2. [...]

## Content Gaps (opportunities)
- [What top results miss]

## SERP Features Present
- [Featured snippet / AI Overview / People Also Ask / etc.]
```

### Step 3: Outline H1-H3

Rules:
- H1: primary keyword + angle that differentiates from competition
- H2: main subtopics (4-8 sections), each answering a distinct question from icp.md
- H3: specific sub-points (only when the section requires them)
- Every H2 must have a "delivery promise" (what the reader gains from it)

### Step 4: EEAT Plan

Specify concretely for each section:
- What proof/example from client.md to weave in
- What external data to cite (with source name)
- Where to acknowledge a limitation or context (Trust signal)

### Step 5: GEO Signals Plan

- **Direct Answer location:** First paragraph. Draft it already in the brief.
- **Structured claims:** Which sections will have "[Claim] because [mechanism]" format
- **FAQ questions:** 5-7 questions sourced from icp.md
- **Table location:** Which section needs a table + what it compares
- **TL;DR placement:** Top of article (always)

### Step 6: Internal Links

From `context/topic-clusters.md`:
- 1x pillar page (mandatory) with suggested anchor text
- 2x cluster pages with suggested anchor text
- If pillar page does not exist yet, note that it must be created

### Step 7: Schema + Meta plan

- **Schema type:** Article / FAQ / HowTo / listicle, matched to format
- **Meta description draft:** Max 155 characters with primary keyword + benefit + soft CTA
- **Slug suggestion:** keyword-primary-angle (no stop words)

### Step 8: Word count + format

Match word count to intent:
- Informational (how/what/why): 2000-3500 words
- Commercial Investigation (comparison/selection): 2500-4000 words
- Quick answer / Definition: 800-1500 words
- Process / Tutorial (steps): 1800-3000 words

Format: standard article / listicle / step-by-step guide / comparison. Match to intent.

### Step 9: Differentiating angles

Define 3 concrete angles that set this article apart from the competition:
1. [e.g. "Implementation perspective: what happens in weeks 2-4, not just what to choose"]
2. [e.g. "Real cost data from actual deployments, not vendor pricing pages"]
3. [e.g. "Honest limitations section covering when this approach fails"]

Reference `context/domain-expertise.md` for unique angles rooted in deep industry knowledge (if available).

## Output format

```markdown
# Brief: [Primary Keyword]

**Keyword:** [primary keyword]
**Related:** [secondary keyword 1], [secondary keyword 2], [secondary keyword 3]
**Intent:** [type + one-sentence description]
**Target reader:** [profile from icp.md]
**Word count:** [number] words
**Format:** [article / listicle / guide / comparison]
**Schema:** [Article + FAQ / HowTo / etc.]

---

## Direct Answer (first 100 words)

[Draft it now. article-writer will rewrite in proper tone.]

---

## Outline

**H1:** [Title, max 60 characters, primary keyword, differentiating angle]

**H2: [Section 1]** - Delivery: [what the reader gains]
- H3: [sub-point] (optional)
- EEAT: [what proof/example from client.md to include]
- GEO: [structured claim / table / list]

**H2: [Section 2]** - Delivery: [what the reader gains]
- EEAT: [...]
- GEO: [...]

[...]

**H2: FAQ**
1. [Question 1 from icp.md]
2. [Question 2]
3. [Question 3]
4. [Question 4]
5. [Question 5]

---

## Internal Links

- **Pillar:** [URL] - anchor: "[anchor text]"
- **Cluster 1:** [URL or "to be created"] - anchor: "[anchor text]"
- **Cluster 2:** [URL or "to be created"] - anchor: "[anchor text]"

---

## Meta Description

[Max 155 characters with primary keyword + main benefit + soft CTA]

**Slug:** [keyword-angle]

---

## TL;DR (to be placed at the top of the article)

- [Takeaway 1]
- [Takeaway 2]
- [Takeaway 3]

---

## Differentiating Angles

1. [Angle 1: what this article has that top 5 results do not]
2. [Angle 2]
3. [Angle 3]

---

**[AWAITING USER APPROVAL]**
```

After generating the brief: stop and wait for user approval (Review Gate #1).
