---
name: quality-gate
description: Scores an article 0-100 across 5 dimensions. Hard threshold of 80 to pass. Below that, diagnose and loop back. No article reaches the CMS without passing this gate.
allowed-tools: [Read]
---

# Skill: quality-gate

## When to use

Always after `geo-optimizer`. Automatically. Do not ask the user.

## Core principle: Fresh Evaluator

Evaluate the article as if you are seeing it for the first time. You do not know the process behind it, you do not know the brief, you do not know the author's intentions. You see only the finished text and the scoring criteria. This is intentional: Quality Gate must catch what the author cannot see because they are too close to the material.

If the article could be better, say so. Do not round up "to make it pass." The threshold of 80 is a minimum, not a target.

## Measurable verification (mandatory)

Before scoring, actually count these metrics. Do not estimate.

1. **Word count:** Count every word in the article body.
2. **Keyword density:** Count primary keyword occurrences. Divide by total words. Multiply by 100.
3. **Sentence lengths:** Split text by sentence-ending punctuation. Count words per sentence. List any exceeding 25 words.
4. **Internal links:** Count them. Verify pillar page is linked.
5. **FAQ questions:** Count them. Minimum 5.
6. **Tables:** Count them. Minimum 1.

Record these numbers in the report. They inform the SEO and Content Quality scores.

## Required input

- Article (after passing seo-optimizer and geo-optimizer)
- Output from both optimizers (list of issues found)
- `context/client.md` (for EEAT verification)
- `context/icp.md` (for ICP fit verification)
- `context/tone-of-voice.md` (for brand alignment verification)

## Scoring Rubric

Score EVERY item individually. Do not round up. If there is no evidence, score 0.

---

### EEAT Signals: max 25 points

**Experience (5 pts):**
- 5: Article contains 2+ concrete examples from client experience (case studies with numbers from client.md)
- 3: 1 concrete example or data point
- 1: General references without numbers
- 0: No examples from practice

**Expertise (5 pts):**
- 5: Article demonstrates deep understanding, not surface-level content, with new angles and mechanisms
- 2: Solid knowledge but nothing that is not in the first 3 Google results
- 1: Surface-level, Wikipedia depth
- 0: Factual errors or lack of substance

**Authoritativeness (5 pts):**
- 5: Cites external sources by name (study X, report Y with date), client data with numbers
- 3: Some data but incomplete attribution
- 1: "Research shows" without names
- 0: No external sources at all

**Trust signals (5 pts):**
- 5: Article acknowledges limitations, contexts where the approach does NOT apply, trade-offs
- 3: Presents topic honestly without overselling
- 1: One-sided but not dishonest
- 0: Pure marketing, promises without backing

**Originality (5 pts):**
- 5: Unique angle, proprietary framework, data not found at competitors
- 2: Good quality but no unique perspective that could not be found elsewhere
- 1: Respin of what is already in the SERP
- 0: Near-copy of competitor content

---

### SEO Fundamentals: max 25 points

**Title tag (5 pts):**
- 5: Max 60 characters, primary keyword in first 3 words, click-worthy without clickbait
- 3: Keyword present but too long OR uncompelling
- 1: Keyword present, everything else is weak
- 0: No keyword or exceeds 70 characters

**Header structure (5 pts):**
- 5: One H1, H2s cover primary subtopics, H3 sub-sections where needed, keyword variations used naturally
- 3: Good hierarchy but no keyword variations in headers
- 1: Headers present but random
- 0: No header structure

**Keyword placement (5 pts):**
- 5: Primary keyword in H1, first paragraph, at least one H2; density 1.0-1.5%; secondary keywords used naturally
- 3: Keyword present but density above 2% or below 0.5%
- 1: Keyword only in the title
- 0: Keyword absent from body text

**Internal links (5 pts):**
- 5: 3+ internal links including pillar page; natural anchor text
- 3: 2 internal links or pillar link missing
- 1: 1 internal link
- 0: No internal links

**Schema + meta (5 pts):**
- 5: Meta description max 155 characters with keyword and CTA; Article + FAQ schema JSON-LD
- 3: Meta OK but no schema, OR schema without FAQ
- 1: Meta only, no schema
- 0: Neither present

---

### GEO Signals: max 20 points

**Direct answer (5 pts):**
- 5: Within first 100 words, a concrete answer to the primary query, extractable, in 1-2 sentences
- 3: Answer exists but buried in 200-300 words or too vague
- 1: Answer somewhere in the article but not at the beginning
- 0: No direct answer to the query

**Structured claims (5 pts):**
- 5: 3+ claims in "[Claim] because [mechanism], which means [implication]" format
- 3: 1-2 structured claims
- 1: Claims present but incomplete (missing mechanism or implication)
- 0: No structured claims

**FAQ section (5 pts):**
- 5: 5+ Q&A pairs, questions in reader language (from icp.md), direct answers
- 3: 3-4 questions or questions not in reader language
- 1: 1-2 questions
- 0: No FAQ section

**Tables and structured lists (5 pts):**
- 5: At least 1 table + at least 1 numbered list (process/steps)
- 3: Only a table OR only a list
- 1: Bullet list but no table
- 0: Continuous text only

---

### Content Quality: max 20 points

**Originality (5 pts):**
- 5: Article adds something not found in the top 5 Google results: new angle, original data, unique synthesis
- 2: Good quality but no unique perspective
- 1: Respin of top results
- 0: AI-sounding generic content

**Depth (5 pts):**
- 5: Every section answers "why" and "how," not just "what"; mechanisms explained
- 3: Good depth in half the article
- 1: Surface-level across all sections
- 0: Definitions and obvious statements only

**Actionability (5 pts):**
- 5: Reader knows what to do after reading: concrete steps, applicable examples
- 3: General guidance
- 1: Knowledge only, no guidance
- 0: Theoretical with no actionable content

**Readability (5 pts):**
- 5: Sentences max 25 words, paragraphs 2-4 sentences, no banned buzzwords, active voice throughout
- 3: A few long sentences or banned phrases present
- 1: Many long sentences, passive voice dominates
- 0: Difficult to read

---

### Brand Alignment: max 10 points

**Tone of voice (5 pts):**
- 5: Article sounds like the "ideal author" persona from tone-of-voice.md; zero banned words
- 3: Close but a few deviations
- 1: Neutral: does not match but does not clash
- 0: Contradicts tone of voice or contains banned phrases

**ICP fit (5 pts):**
- 5: Article assumes exactly the knowledge level described in icp.md; uses reader language from icp.md
- 3: Close but occasionally too basic or too advanced
- 1: Generic: fits anyone
- 0: Wrong knowledge level for the ICP

---

## Workflow

1. Run measurable verification (word count, density, sentence lengths, link count, FAQ count, table count)
2. Score each item individually with a one-sentence justification
3. Sum the points
4. Apply threshold:

**Score >= 80:** Article passes. Present to the user for review with score summary + 3 strengths.

**Score 65-79:** Targeted revision. Identify exactly which criteria are not met. Send diagnosis to `article-writer` with a list of specific changes (not "improve EEAT" but "in section X, add a concrete example from client.md showing [specific data point]"). Iterate without asking the user.

**Score < 65:** Major revision required. Return to `article-brief` to verify the brief was correct. Inform the user with full diagnosis.

Maximum 3 auto-iteration rounds. After 3 failed rounds, escalate to the user with diagnosis.

## Output format

```
## Quality Gate Report

**Score: [X]/100** - [PASS >=80 / REVISION 65-79 / REWRITE <65]

### Measured Metrics
- Word count: [X] (target: [Y])
- Keyword density: [X]% (target: 1.0-1.5%)
- Sentences over 25 words: [X]
- Internal links: [X] (minimum: 3)
- FAQ questions: [X] (minimum: 5)
- Tables: [X] (minimum: 1)

### Breakdown
| Dimension | Score | Max | Diagnosis |
|-----------|-------|-----|-----------|
| EEAT Signals | X | 25 | [one sentence] |
| SEO Fundamentals | X | 25 | [one sentence] |
| GEO Signals | X | 20 | [one sentence] |
| Content Quality | X | 20 | [one sentence] |
| Brand Alignment | X | 10 | [one sentence] |
| **TOTAL** | **X** | **100** | |

### Strengths
1. [Specific strength]
2. [Specific strength]

### Required fixes [only if score < 80]
1. [Specific change with location in article: section X, paragraph Y]
2. [Specific change]
3. [...]
```
