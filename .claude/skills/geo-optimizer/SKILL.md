---
name: geo-optimizer
description: 12-point GEO (Generative Engine Optimization) checklist for AI search engines (Perplexity, ChatGPT Search, Google AI Overviews). Run after seo-optimizer, before quality-gate.
allowed-tools: [Read]
---

# Skill: geo-optimizer

## When to use

Automatically after `seo-optimizer`. Do not ask the user. Iterate.

## What is GEO and why it matters

AI search engines (Perplexity, ChatGPT Search, Google AI Overviews) cite pages that:
1. Have direct, extractable answers to a question
2. Use structured claims (claim + mechanism + implication)
3. Have tables, lists, FAQ sections: formats that an LLM can extract
4. Cite sources with specific names and dates
5. Define key terms (entity optimization)

An article optimized for GEO is an article that an LLM can cite without reading the whole thing.

## Checklist: 12 items

Score each item as PASS or FAIL. For each FAIL, apply the fix before proceeding.

### Direct Answer
1. **Direct answer in first 100 words.** Is there a direct answer to the primary query within the first 100 words?
   - Format: "[Primary topic] is/means/involves [answer]. [Key detail]."
   - Test: could an LLM extract these 2 sentences and use them to answer the question?
   - PASS: a clear, extractable answer exists in the first 100 words.
   - FAIL: the opening is background, history, or context without answering the query.

2. **TL;DR / Key Takeaways section exists with 3-5 points.**
   - Each point is one falsifiable claim.
   - Test: would someone who reads only the TL;DR understand the main thesis?
   - PASS: TL;DR section exists with 3-5 specific, self-contained points.
   - FAIL: no TL;DR, or points are vague ("this topic is important").

### Structured Claims
3. **At least 3 structured claims in the format "[Claim] because [mechanism], which means [implication]."**
   - Claim: specific and falsifiable (not "this is important").
   - Mechanism: explains WHY (not "because it is").
   - Implication: what this means for the reader.
   - PASS: 3 or more complete structured claims found in the article body.
   - FAIL: fewer than 3, or claims missing mechanism or implication.

4. **Every statistical claim has specific attribution.**
   - Correct: "According to the 2024 Semrush report, 65% of queries..."
   - Incorrect: "Research shows that..."
   - PASS: every number or percentage has a named source and year.
   - FAIL: any statistic lacks named attribution.

### FAQ Section
5. **FAQ section exists with at least 5 questions.**
   - PASS: FAQ section present with 5 or more Q&A pairs.
   - FAIL: missing FAQ, or fewer than 5 questions.

6. **Questions phrased as natural queries (sourced from icp.md).**
   - Correct: "How do you calculate ROI on manufacturing automation?"
   - Incorrect: "What is manufacturing automation ROI?"
   - PASS: questions read like real search queries a human would type.
   - FAIL: questions are keyword-stuffed or unnaturally phrased.

7. **Each FAQ answer starts with a direct answer (maximum 2 sentences).**
   - PASS: every answer opens with a concrete, direct response.
   - FAIL: any answer starts with background or hedging before the actual answer.

### Tables and Structured Lists
8. **At least one table with data or a comparison.**
   - PASS: article contains a Markdown table with real data, comparisons, or specifications.
   - FAIL: no table, or table is decorative without meaningful data.

9. **At least one numbered list of steps (process/instructions).**
   - PASS: article contains a numbered list describing a process, workflow, or set of instructions.
   - FAIL: no numbered list, or only bullet lists without sequential logic.

### Entity Optimization
10. **Key terms defined at first use.**
    - Test: could an LLM that knows nothing about this topic understand the article without external context?
    - PASS: every technical or industry-specific term has a short contextual explanation at first mention.
    - FAIL: any term is used without explanation, assuming reader knowledge.

11. **Client company name used at least 3 times in context of expertise (not just in the footer).**
    - Format: "[Company X] deploys / observes / recommends / measures..."
    - This builds entity association: company name paired with article topic.
    - PASS: company name appears 3 or more times in active, expert context.
    - FAIL: company name appears fewer than 3 times, or only in boilerplate.

### Freshness Signals
12. **Article contains a date or reference to "current data as of [year]."**
    - AI search prefers fresh content.
    - If data is from a prior year, mark that clearly.
    - PASS: at least one explicit date or year reference in the article body.
    - FAIL: no date references; content could be from any year.

## Output format

```markdown
## GEO Optimizer Report

**Pass:** X/12 | **Fail:** X/12

### Critical Issues (affect citability)

| # | Criterion | Verdict | Problem | Fix |
|---|-----------|---------|---------|-----|
| 1 | Direct Answer | FAIL | [problem] | [add sentence: "..."] |
| 3 | Structured Claims | FAIL | [problem] | [in section X, rewrite to format: ...] |

### Applied fixes

[List of specific changes, citing fragments before and after]

**Before:** "[original fragment]"
**After:** "[corrected fragment]"
```

If all 12 PASS: write "GEO check: 12/12 PASS" and proceed to quality-gate.
If any FAIL: apply fixes directly to the article, then proceed to quality-gate.
