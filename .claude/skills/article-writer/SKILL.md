---
name: article-writer
description: Writes a full SEO+GEO article (1500-4000 words) from an approved brief. Built-in EEAT signals, GEO optimization, and client tone of voice. The most important skill in the engine.
allowed-tools: [Read, Write, WebSearch, WebFetch]
---

# Skill: article-writer

## When to use

After the user approves the brief (Review Gate #1). Never without a brief. Every word must have justification in the brief.

## Required input

Read in this order before writing:
1. `context/client.md` - who is writing and for which company
2. `context/icp.md` - who you are writing for, what they already know, what language they use
3. `context/tone-of-voice.md` - how you write, what to avoid
4. `context/domain-expertise.md` - (if available) LSI terms, industry depth, technical vocabulary
5. Brief (output from `article-brief` skill) - structure, outline, EEAT plan, target keyword

## Workflow

### Step 1: Understand the task

Before writing, answer internally (not out loud):
- What did the reader type into Google/AI? What is their problem right now?
- What do they want to accomplish after reading this article?
- What do they know and what do they not know about this topic?
- What does the client (the company) want the reader to understand or do?

### Step 2: Write the opening (first 100-150 words)

**This is the most important part of the article.**

Rule: the first sentence must contain either (a) a specific number, (b) a specific cost, or (c) a specific problem. Never start with a definition of the topic.

**Direct Answer (GEO signal):** Within the first 100 words, place a direct answer to the primary query before any background context. Perplexity and AI Overviews extract this answer as a citation.

Direct answer format: "[Primary keyword] is/means/involves [answer in 1-2 sentences]. [Key detail that separates a good answer from a generic one]."

### Step 3: TL;DR / Key Takeaways (GEO signal, mandatory)

Place immediately after the opening. Format:

```
**Key Takeaways:**
- [Takeaway 1: specific, falsifiable, with a number if possible]
- [Takeaway 2: mechanism or "why"]
- [Takeaway 3: practical implication]
- [Takeaway 4: optional]
```

**Why TL;DR at the top, not the bottom:** Perplexity and ChatGPT Search extract content from the beginning of a document first. An article with TL;DR at the top gets cited more frequently than an identical article with TL;DR at the bottom or without one.

Each TL;DR point must be self-contained. A reader who reads only the TL;DR should understand the main thesis of the article.

### Step 4: Write main sections (H2)

For each H2 section from the brief:

**Section structure (mandatory):**
1. **Thesis** (1 sentence): what this section proves or explains
2. **Mechanism** (2-4 sentences): how/why it works
3. **Evidence** (1-3 sentences): specific example, data, case study from client.md
4. **Implication** (1-2 sentences): what this means for the reader

**Structured claims (GEO signal):** In each section, include at least one claim in this format:
"[Factual claim] because [mechanism], which means [implication for the reader]."

This format is frequently cited by AI search engines.

### Step 5: Table AND numbered list (GEO + SEO signal)

Every article must contain at least one data table AND at least one numbered list. Both are required for full GEO marks.

**When to use a table:** comparisons, feature lists, pros/cons, specifications.
**When to use a numbered list:** processes, instructions, checklists.

Tables are cited by AI Overviews approximately 3x more often than continuous prose.

### Step 6: EEAT signals

Weave in naturally, not in a separate section:

- **Experience:** "In our deployments we observe..." or "Clients we work with report..." (data from client.md)
- **Expertise:** Use domain terminology (from domain-expertise.md if available), but explain when needed
- **Authority:** Reference case studies with numbers (from client.md)
- **Trust:** Acknowledge limitations or context: "This works when..., it does not work when..."

Minimum: 2 concrete examples from client.md (case studies) woven in as natural illustrations.

### Step 7: FAQ section (GEO signal, mandatory)

Minimum 5 questions. Format:

```
## Frequently Asked Questions

### [Question from icp.md, phrased as the reader actually asks]
[Answer: 2-4 sentences. Concrete, no hedging. Direct answer in the first sentence.]

### [Question 2]
[Answer]
```

Pull questions from `context/icp.md` (section with reader search queries). Supplement with longtail variants of the primary keyword.

### Step 8: Internal links

Follow the brief. Minimum 3:
- 1x to pillar page (mandatory)
- 2x to cluster pages
- Anchor text: natural sentence fragments, never "click here"

### Step 9: Entity Optimization (Semantic SEO)

Before closing the article, verify:

**Key entity definitions:** Every technical or industry term used for the first time must have a short explanation (1 sentence). Not a dictionary definition, but a contextual explanation for your ICP.

**Entity associations:** The article should repeatedly associate the client company name with the article topic in an active voice:
- Correct: "[Company X] recommends / deploys / observes / measures..."
- Incorrect: "[Company X] is a leader in..."

This builds entity association in Google's index and in AI models: company name paired with topic expertise.

**Semantic topic coverage:** Verify the article naturally uses related terms (LSI). If available, reference `context/domain-expertise.md` for the full list of industry terms that should appear. If writing about "manufacturing automation," terms like production line, downtime, OEE, cycle time, SCADA, MES should appear naturally, not forced.

### Step 10: Closing

Final paragraph = a concrete next step for the reader. Not "contact us." Format:
"[If you are in situation X], start with [specific action, can be a link to a free resource/tool]."

## Writing rules (non-negotiable)

### Style
- Maximum 25 words per sentence (count them)
- Paragraphs: 2-4 sentences
- One idea per paragraph
- Active voice: "The system detects" not "The error is detected by"
- Numbers as digits: "3 weeks" not "three weeks"
- No em-dashes. Use commas, periods, semicolons, or restructure the sentence.

### What NOT to do
- Do not start sections with a dictionary definition
- Do not use these phrases: "In today's world", "It's worth noting", "Comprehensive", "Holistic", "Game-changer", "Landscape", "Leverage" (as verb), "Elevate"
- Do not write sentences that sound like marketing: "Our solution is a revolution"
- Do not cite data without a source. Data comes from client.md or from commonly known facts with named attribution.
- Do not copy the structure from the SERP. Add the unique angle from the brief.

### Tone of voice
- Read `context/tone-of-voice.md` before writing each paragraph
- Check the "banned words" list. Do not use them.
- Verify sentences against the "Good sentence" examples as a benchmark

## Output format

Article in Markdown with full structure:

```markdown
# [H1 Title, max 60 characters, primary keyword, click-worthy]

[Opening paragraph: problem/number/cost, direct answer within 100 words]

**Key Takeaways:**
- ...
- ...
- ...

---

## [H2, section 1]

[Section content]

## [H2, section 2]

[Section content with table or list]

...

## Frequently Asked Questions

### [Question 1]
[Answer]

...

---

[Closing paragraph with next step]
```

## Post-writing verification (mandatory)

After completing the article, run these measurable checks before passing to seo-optimizer:

### Word count check
Count the total number of words in the article. Compare to the target from the brief.
- If under the minimum: add depth to thin sections.
- If over the maximum: cut redundant content.

### Sentence length check
Split the text by sentence-ending punctuation. Count the words in each sentence. List any sentence exceeding 25 words. Rewrite those sentences to be shorter.

### Keyword density check
Count the number of times the primary keyword appears in the article body (excluding metadata). Divide by total word count and multiply by 100.
- Target density: 1.0-1.5%
- Below 0.8%: add natural keyword mentions
- Above 2.0%: remove forced keyword repetitions

### Internal link check
Count internal links. Verify there are at least 3. Confirm pillar page is linked.

### Table and numbered list check
Verify the article contains at least one data table AND at least one numbered list. Both are required (geo-optimizer checks items #8 and #9 independently).

Report these numbers at the end of the article output:

```
---
**Writing Metrics:**
- Total words: [X] (target: [Y])
- Sentences over 25 words: [X] (must be 0)
- Primary keyword density: [X.X]% (target: 1.0-1.5%)
- Internal links: [X] (minimum: 3)
- Data table: [yes/no] (required)
- Numbered list: [yes/no] (required)
```

After the article and metrics pass, proceed automatically to `seo-optimizer` then `geo-optimizer` then `quality-gate`.
