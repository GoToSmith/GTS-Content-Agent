---
name: seo-optimizer
description: 25-point on-page SEO checklist. Pass/fail per item with specific fixes. Run after article-writer, before geo-optimizer.
allowed-tools: [Read]
---

# Skill: seo-optimizer

## When to use

Automatically after `article-writer`. Do not ask the user. Iterate.

## Computational verification instructions

Before running the checklist, perform these actual counts on the article text. Do not estimate. Count precisely.

### Word count
Count every word in the article body (excluding metadata blocks). Record the number.

### Keyword density
1. Count the number of times the primary keyword appears in the article body.
2. Divide by total word count.
3. Multiply by 100.
4. Record as: "[X] occurrences / [Y] words = [Z]% density"

### Sentence length audit
1. Split the article text by sentence-ending punctuation (periods, question marks, exclamation marks).
2. Count the words in each sentence.
3. List every sentence that exceeds 25 words, with its word count.
4. Record as: "[X] sentences over 25 words out of [Y] total sentences"

Report these numbers at the top of the SEO Optimizer Report before the checklist results.

## Checklist: 25 items

Check each one. For each: PASS / FAIL + fix if FAIL.

### Title Tag (H1)
1. Maximum 60 characters?
2. Primary keyword within the first 3 words?
3. Click-worthy without clickbait?
4. Unique, not duplicating other articles on the blog?

### Meta Description
5. Maximum 155 characters?
6. Contains primary keyword (naturally)?
7. Contains a benefit for the reader?
8. Has a soft CTA (e.g. "Learn how", "See examples")?

### Header Structure
9. Exactly one H1?
10. H2s cover the main subtopics (minimum 4)?
11. H2s contain keyword variations / LSI terms (not verbatim primary keyword)?
12. Hierarchy H1 > H2 > H3 is maintained?

### Keyword Placement
13. Primary keyword in the first paragraph (first 100 words)?
14. Primary keyword in at least one H2?
15. Primary keyword density: 1.0-1.5% (not over-optimized)?
16. Secondary keywords woven in naturally, minimum 2 occurrences each?

### Internal Links
17. Minimum 3 internal links?
18. Pillar page is linked?
19. Anchor text is natural (not "click here" or "learn more")?
20. No broken links (links point to existing pages)?

### External Links / Citations
21. Minimum 2 links to credible external sources (with name in text)?
22. Sources are specific: not "according to research" but "according to [Name] [Year] report"?

### Technical On-Page
23. URL slug contains primary keyword, is short, and has no stop words?
24. Images (if present) have alt text with keyword?
25. Schema JSON-LD is defined (Article + FAQ minimum)?

## Output format

```markdown
## SEO Optimizer Report

**Computed Metrics:**
- Word count: [X]
- Keyword density: [X] occurrences / [Y] words = [Z]%
- Sentences over 25 words: [X] of [Y] total

**Pass:** X/25 | **Fail:** X/25

### Issues (FAIL items only)

| # | Criterion | Problem | Fix |
|---|-----------|---------|-----|
| X | [name] | [what is wrong] | [specific change] |
| X | [...] | [...] | [...] |

### Applied fixes

[List of specific changes to make in the article. Not "fix the title" but "change title from X to Y"]
```

If all criteria PASS: write "SEO check: 25/25 PASS" and proceed to geo-optimizer.
If any FAIL: apply fixes directly to the article, then proceed to geo-optimizer.
