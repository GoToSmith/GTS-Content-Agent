# Workflow 02: Keyword Discovery

**Goal:** Expand seed topics into a full keyword cluster map with priority scoring. Run monthly or when `topic-clusters.md` is empty.

**Claude time:** ~30 minutes
**User time:** ~15 minutes (review top 15 keywords)

**Trigger:**
```
Find new keywords for [seed topic or "refresh topic clusters"]
```

---

## Prerequisites

- [ ] `context/client.md` (filled in)
- [ ] `context/icp.md` (filled in, especially the "Search Queries" section)

---

## Step 1: Collect Seed Topics

If the user did not specify seed topics, ask:
```
Give me 3-5 topic areas that are strategically important for your business.
Example: "route optimization", "fleet management for SMBs", "last mile delivery costs"
```

If `topic-clusters.md` already exists, read the existing pillars and ask whether to expand them or add new ones.

---

## Step 2: Research Keywords

For each seed topic, invoke skill `keyword-research`.

### Data sources (in priority order):

**Primary: MCP connectors (if available)**
Use Ahrefs MCP or SEMrush MCP to pull real data:
- Search volume (monthly)
- Keyword difficulty score
- SERP features (featured snippets, People Also Ask, AI Overviews)
- Related keywords and questions

**Fallback: WebSearch**
If no MCP connector is available, use WebSearch to estimate:
- Relative search interest (autocomplete suggestions, People Also Ask)
- Competitor content covering this keyword
- SERP competition level (how many strong domains rank)

**User-provided data:**
The user can also paste keyword data exported from any external tool (Ahrefs, SEMrush, Ubersuggest, Google Keyword Planner). If provided, parse and integrate this data directly.

Run seed topics sequentially (not in parallel). Each seed informs the context for the next.

---

## Step 3: Deduplicate and Cluster

After collecting all keywords:
1. Remove duplicates (identical or near-identical phrases)
2. Identify overlapping topics (keyword cannibalization risk)
3. Confirm each cluster has at least 4 keywords (1 pillar + 3 cluster articles)
4. Group keywords by pillar topic

---

## Step 4: Priority Scoring

For each keyword, calculate a Priority Score (1-10):

```
Priority = (Business Fit x 3) + (Inverse Difficulty x 2) + (Search Intent Weight x 2)
```

- **Business Fit:** 1-5 (from client.md, how closely the keyword relates to the product/service)
- **Inverse Difficulty:** Low=3, Medium=2, High=1
- **Search Intent Weight:** COMM=3, INFO=2, TRANS=2, NAV=1

Sort keywords by Priority Score descending. Top 15 = recommended production order.

---

## REVIEW: User Approves the Keyword Map (~15 minutes)

Present to the user:
- Pillar topics (3-5) with one-sentence justification each
- Top 15 keywords ranked by Priority Score, showing: keyword, intent, difficulty, business fit, score
- Estimated production timeline (at 3 articles per week)

Wait for approval. Possible changes:
- Reprioritize keywords
- Remove topics too far from the business
- Add topics that the research missed

---

## Step 5: Save to topic-clusters.md

After approval, update or create `context/topic-clusters.md` with:
- All pillars and cluster keywords
- Priority scores
- Status set to `queued` for all new keywords
- Internal link plan (which cluster articles link to which pillar)
- Production queue in recommended order

---

## Summary

```
Keyword discovery complete.

Pillars: [count] | Keywords queued: [count]
Estimated production time at 3 articles/week: [X] weeks

Recommended first article: [keyword]
Run: "Write an article about [keyword]"
```
