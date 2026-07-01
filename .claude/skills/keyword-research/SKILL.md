---
name: keyword-research
description: Expands a seed keyword into 60-100 phrases with intent classification, difficulty scoring, and pillar/cluster grouping. Output updates topic-clusters.md.
allowed-tools: [Read, Write, WebSearch, WebFetch]
---

# Skill: keyword-research

## When to use

In workflow `02-keyword-discovery` (monthly/quarterly) or when topic-clusters.md is empty/incomplete.

## Required input

- Seed keyword or topic area (from user)
- `context/client.md` (for business context)
- `context/icp.md` (for understanding reader language)
- `context/domain-expertise.md` (if available, for LSI terms and industry vocabulary)

## Data sources (in priority order)

### PRIMARY: MCP connectors (Ahrefs / SEMrush)

If an MCP connector for Ahrefs or SEMrush is available, use it as the primary data source:
- Pull real search volume, keyword difficulty (KD), trend data, and SERP features
- Extract "also rank for" and "questions" reports
- Use KD score directly (Low: KD < 30, Medium: KD 30-60, High: KD > 60)

### FALLBACK: WebSearch

If no MCP connector is available, use WebSearch to gather keyword ideas:
- Search `[seed keyword] site:alsoasked.com` or `[seed keyword] people also ask`
- Search `[seed keyword] autocomplete suggestions`
- Search `[seed keyword] related searches`
- Search `[seed keyword] forum questions site:reddit.com OR site:quora.com`
- Estimate difficulty based on SERP logic (see Step 3 below)

## Workflow

### Step 1: Seed keyword expansion

Generate variants of the seed keyword in 5 categories:

1. **Exact + near-exact** - [seed keyword], [keyword synonym], [keyword with qualifier]
2. **Question keywords** - "how [seed]", "why [seed]", "when [seed]", "what is [seed]"
3. **Comparison keywords** - "[seed] vs [alternative]", "best [seed]", "[seed] ranking"
4. **Problem keywords** - "[problem that seed solves]", "how to fix [problem]"
5. **Longtail specifics** - "[seed] for [industry/role]", "[seed] step by step", "[seed] examples"

### Step 2: Intent classification

For each phrase:
- **Informational (INFO):** wants to understand, learn, find out
- **Commercial Investigation (COMM):** considering a purchase, comparing options
- **Transactional (TRANS):** ready to buy or take action
- **Navigational (NAV):** looking for a specific page

### Step 3: Difficulty estimation

**With MCP data:** Use the Keyword Difficulty score directly:
- Low: KD < 30
- Medium: KD 30-60
- High: KD > 60

**Without MCP (WebSearch fallback):** Estimate based on SERP logic:
- **Low:** longtail (4+ words), niche topic, few high-authority results
- **Medium:** 2-3 words, industry topic, mixed SERP
- **High:** head term (1-2 words), dominated by big brands, featured snippets present

### Step 4: Business fit scoring

Rate each phrase for client fit (1-5):
- 5 = Perfect fit: article naturally leads to the client's product/service
- 4 = Strong fit: directly related topic, clear path to conversion
- 3 = Good fit: related topic, generates awareness
- 2 = Weak fit: tangentially related
- 1 = Poor fit: too generic or unrelated to the offering

### Step 5: Priority scoring

Calculate a priority score for each keyword using this formula:

```
Priority = (Business Fit x 3) + (Inverse Difficulty x 2) + (Intent Weight x 2)
```

Where:
- **Business Fit:** 1-5 score from Step 4
- **Inverse Difficulty:** Low = 5, Medium = 3, High = 1
- **Intent Weight:** TRANS = 5, COMM = 4, INFO = 3, NAV = 1

**Priority ranges:**
- 28-35: Top priority (publish first)
- 20-27: High priority
- 14-19: Medium priority
- 7-13: Low priority (defer or skip)

### Step 6: Pillar + cluster grouping

Group keywords into 3-5 pillar topics:
- Pillar = broad topic, 1500+ words, covers multiple search intents
- Cluster = specific subtopic, 800-2500 words, supports pillar
- Each cluster should link to its pillar page

## Output format

Update `context/topic-clusters.md`:

```markdown
# Topic Clusters

Last updated: [date]

---

## Pillar 1: [Pillar name]

**Pillar page:** [keyword] | Intent: INFO | Difficulty: [L/M/H] | Fit: [1-5] | Priority: [score] | Status: [queued/in-progress/published]

### Cluster keywords:

| Keyword | Intent | Difficulty | Fit | Priority | Status |
|---------|--------|------------|-----|----------|--------|
| [phrase 1] | INFO | Low | 5 | 31 | queued |
| [phrase 2] | COMM | Medium | 4 | 24 | queued |
| [phrase 3] | INFO | Low | 3 | 23 | queued |

---

## Pillar 2: [Pillar name]

[...]

---

## Production queue (recommended order)

1. [Keyword 1] - pillar, low difficulty, high fit, priority: 33
2. [Keyword 2] - cluster Pillar 1, longtail, quick win, priority: 29
3. [...]
```

After generating the output, present a summary to the user (top 10 keywords with reasoning) and wait for approval of the production queue.
