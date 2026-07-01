# Workflow 01: Article Production

**Goal:** Produce one SEO+GEO-optimized article from keyword to published draft.

**Claude time:** ~45 minutes (non-interactive)
**User time:** ~15 minutes (2 review gates)

**Trigger:**
```
Write an article about [keyword]
```

---

## Prerequisites

Before starting, verify these files exist:

- [ ] `context/client.md` (filled in)
- [ ] `context/icp.md` (filled in)
- [ ] `context/tone-of-voice.md` (filled in)
- [ ] `context/topic-clusters.md` (keyword listed as `queued`, or keyword will be added after publishing)

If any file is missing, list which ones and point to `examples/routemaster/` as reference. Do not block if at least `client.md` exists.

---

## Step 1: Generate Brief

Invoke skill `article-brief` with the chosen keyword.

**Input:** keyword + `context/client.md` + `context/icp.md` + `context/tone-of-voice.md`

**Output:** A structured brief containing: keyword, search intent, target reader, word count range, full outline (H1 through H3), EEAT plan, GEO signals plan, internal link targets, meta description, and 3 differentiating angles.

---

## REVIEW GATE #1: Approve the Brief (~5 minutes)

Present the brief to the user. Wait for approval.

Message to user:
```
The brief is ready. Before I write the article, I need your sign-off.

Check:
1. Does the outline cover what you want to say?
2. Are the differentiating angles aligned with your perspective?
3. Are the EEAT signals (examples from client.md) accurate?

Type "OK" to continue, or describe what to change.
```

**If the user requests changes:** Update the brief and return to this gate.

---

## Step 2: Write the Article

Invoke skill `article-writer` with the approved brief.

**Input:** approved brief + `context/client.md` + `context/icp.md` + `context/tone-of-voice.md` + `context/domain-expertise.md` (if available)

**Output:** Full article in Markdown, 1500-4000 words, with complete structure (H1-H3, FAQ, TL;DR, data table, internal links).

---

## Step 3: SEO Optimization

Invoke skill `seo-optimizer` automatically.

Run the SEO checklist against the article. If any items fail, apply fixes directly. Do not ask the user.

---

## Step 4: GEO Optimization

Invoke skill `geo-optimizer` automatically.

Run the GEO signals checklist against the article. If any items fail, apply fixes directly. Do not ask the user.

---

## Step 5: Quality Gate

Invoke skill `quality-gate` automatically.

- **Score >= 80:** Proceed to Review Gate #2.
- **Score 65-79:** Pass the diagnosis to `article-writer` with a list of specific changes. Iterate automatically, maximum 3 rounds. Do not ask the user.
- **Score < 65:** Escalate to the user with the full diagnosis.
- **After 3 rounds still below 80:** Escalate to the user with the diagnosis and current score.

---

## REVIEW GATE #2: Read the Final Draft (~10 minutes)

Present to the user:
- Quality Gate score (e.g. "92/100")
- The full article in Markdown
- 3 strengths and any notes from the quality report

Message to user:
```
The article is ready. Quality Gate score: [X]/100.

[Full article in Markdown]

Read the draft and respond:
- "Publish" to push it to CMS as a draft (or receive the Markdown package)
- Describe changes if something needs correction
- "Stop" if you don't want to publish
```

**If the user requests changes:** Apply them, re-run quality-gate. If score >= 80, return to Review Gate #2.

---

## Step 6: Publish

After user approval:

**With CMS connector (Webflow MCP, WordPress MCP):** Invoke skill `cms-publisher`. Output: draft in CMS with full metadata and schema markup. Provide the preview URL to the user.

**Without CMS connector:** Output a complete Markdown package with frontmatter (title, meta description, slug, schema type, publish date) ready for manual upload. Notify the user that the package is ready.

---

## Step 7: Update topic-clusters.md

Change the keyword status in `context/topic-clusters.md`:
- `queued` or `in-progress` changes to `published`
- Add the publish date and article URL

If the keyword was not in topic-clusters.md (ad-hoc article), add it now with status `published`.

---

## Summary

```
Article "[title]" is ready as a DRAFT in [CMS / Markdown output].

Preview: [URL or file path]
Quality Gate: [score]/100
Next step: Open the preview, check formatting, and hit Publish.

Next article in the queue: [keyword] (or tell me which one to write next)
```

---

## Enhancement: MCP Connectors

The core flow above works without any connectors. Adding MCP connectors improves the workflow in these ways:

| Connector | Enhancement |
|---|---|
| Ahrefs/SEMrush MCP | Real search volume and difficulty data in the brief |
| Webflow/WordPress MCP | Direct CMS publishing in Step 6 instead of Markdown output |
| Google Search Console MCP | Real ranking data to inform keyword selection |

See `CLAUDE.md` for connector setup instructions.
