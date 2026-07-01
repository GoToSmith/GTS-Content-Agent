# Workflow 03: Performance Review

**Goal:** Monthly audit of published content. Detect ranking changes, content decay, AI citation gaps, and new keyword opportunities.

**Claude time:** ~20 minutes
**User time:** ~10 minutes (review refresh plan)

**Trigger:**
```
How is my content performing?
```

---

## Prerequisites

- [ ] Blog has at least 5 published articles
- [ ] `context/topic-clusters.md` tracks published articles with URLs
- [ ] Google Search Console access (via MCP or manual export)

---

## Step 1: Collect Performance Data

### Primary: GSC via MCP (if available)

Pull from Google Search Console for each published article:
- Average Position (ranking)
- Clicks, Impressions, CTR (last 28 days vs. previous 28 days)
- Top queries per URL
- New queries driving impressions

### Fallback: Manual GSC Export

If no GSC MCP connector is available, ask the user:
```
I need Google Search Console data to run the performance review.

Option A: Export from GSC
  1. Go to Search Console > Performance
  2. Set date range: last 3 months
  3. Click Export > Download CSV
  4. Share the file with me

Option B: Skip GSC data
  I'll run the review using WebSearch-based checks only.
  This is less precise but still useful for AI citation auditing.
```

---

## Step 2: Content Decay Detection

Flag articles showing content decay based on these signals:

| Signal | Threshold | Action |
|---|---|---|
| Ranking drop | >5 positions vs. previous period | High priority refresh |
| CTR drop | >20% drop with stable impressions | Rewrite title + meta description |
| Content age | >6 months without an update | Review for freshness |
| Outdated references | Dates, stats, or tools that have changed | Update specific sections |
| Broken internal links | Links pointing to removed pages | Fix immediately |

For each flagged article, note:
- Which decay signal triggered the flag
- Current ranking vs. previous ranking
- Specific sections that need updating

---

## Step 3: AI Citation Audit

Check whether published articles appear in AI search results. This measures GEO effectiveness.

**Method: WebSearch**

For the top 10 published articles (by traffic or strategic importance):
1. Search the primary keyword as a question (e.g., "how do I reduce last mile delivery costs?")
2. Check if the article or its claims appear in search results
3. Note whether AI-generated snippets reference the article's data or claims

**Record for each article:**
- Cited / Not cited / Partially cited
- Which AI platforms show the content (if identifiable from search results)
- Missing GEO signals that may explain non-citation (no FAQ, no structured claims, no direct answer)

If an article ranks well in traditional search but is not cited by AI, it likely needs stronger GEO signals. Add it to the refresh list.

---

## Step 4: Content Gap Analysis

Using GSC query data (or WebSearch observations):

1. **High impressions, low CTR:** The article ranks but the title/meta don't compel clicks. Rewrite the title and meta description.
2. **Position 8-20 keywords:** The article is close to page 1. Strengthen with internal links, content refresh, or expanded sections.
3. **Uncovered queries:** Search queries generating impressions but no matching article. Add these as new keywords to the production queue.

---

## Step 5: Build the Refresh Priority List

Create a prioritized action plan:

| Article | Problem | Action | Priority |
|---|---|---|---|
| [title/URL] | Ranking dropped 8 positions | Full refresh: new data + GEO signals | High |
| [title/URL] | No AI citation despite top-5 ranking | Add FAQ + structured claims | High |
| [title/URL] | CTR at 1.2% in top 5 | Rewrite title + meta description | Medium |
| [title/URL] | Content 9 months old, no updates | Review for outdated sections | Medium |
| [title/URL] | New queries not covered | Consider new cluster article | Low |

---

## REVIEW: User Approves the Refresh Plan (~10 minutes)

Present to the user:
- Monthly summary: what is growing, what is declining
- Content decay list with specific articles and signals
- AI citation status for top articles
- Refresh priority list with recommended actions
- New keyword suggestions from gap analysis

Wait for approval. The user may:
- Reprioritize the refresh list
- Skip certain articles
- Add articles they want refreshed regardless of data

---

## Step 6: Update topic-clusters.md

After approval:
- Change status of flagged articles from `published` to `needs-refresh`
- Add new keywords from gap analysis with status `queued`
- Add notes on specific refresh actions needed per article

---

## Step 7: Save Insights

Record performance data in a format that informs future content decisions:

```
## Performance Snapshot: [Month YYYY]

Published articles: [X]
Average position: [X]
Average CTR: [X]%
AI citations: [X]/[total] articles cited

Articles flagged for refresh: [X]
New keywords added to queue: [X]

Key insight: [One sentence about the most important finding]

Next review: [date, one month from now]
```

Append this snapshot to `context/topic-clusters.md` under a "Performance History" section.
