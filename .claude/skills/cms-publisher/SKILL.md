---
name: cms-publisher
description: Publishes an approved article to CMS (Webflow or WordPress) with full metadata and schema, or generates a Markdown package for manual upload. Returns a preview URL. Human clicks publish.
allowed-tools: [Read, Write, WebFetch]
---

# Skill: cms-publisher

## When to use

After the user approves the article (Review Gate #2). Always the last step in workflow `01-article-production`.

## Required input

- Approved article (Markdown)
- Output from quality-gate (for metadata)
- `context/client.md` (author, category, tags)
- Brief (for slug, meta description)
- `context/topic-clusters.md` (to update keyword status after publishing)

## Workflow

### Step 1: Prepare metadata

```yaml
title: [H1 from article, max 60 characters]
slug: [keyword-angle, no stop words]
meta_description: [max 155 characters, from brief or generate]
author: [from client.md]
category: [match to client blog structure]
tags: [primary keyword, 2-3 secondary keywords, industry]
published_date: [today's date YYYY-MM-DD]
status: DRAFT
canonical_url: [domain from client.md]/blog/[slug]
```

### Step 2: Generate Schema JSON-LD

Always generate: Article schema + FAQ schema (if article has an FAQ section).

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[H1]",
  "description": "[meta description]",
  "author": {
    "@type": "Organization",
    "name": "[company name from client.md]",
    "url": "[domain from client.md]"
  },
  "publisher": {
    "@type": "Organization",
    "name": "[company name]"
  },
  "datePublished": "[YYYY-MM-DD]",
  "dateModified": "[YYYY-MM-DD]",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "[domain]/blog/[slug]"
  }
}
```

FAQ Schema (if the article has an FAQ section):
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[Question 1]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[Answer 1]"
      }
    }
  ]
}
```

### Step 3: Publish

**PRIMARY path: CMS MCP connector**

**If Webflow MCP available:**
1. `create_blog_post(title, body_html, slug)`
2. `set_seo_fields(meta_title, meta_description, og_image_alt)`
3. `add_custom_code(schema_json_ld)` in `<head>`
4. `set_categories_tags(category, tags)`
5. `set_status(DRAFT)`
6. `get_preview_url()` and return to user

**If WordPress MCP available:**
1. `create_post(title, content, status=draft)`
2. `set_post_meta(meta_key, meta_value)` for Yoast/RankMath fields (title tag, meta description, canonical URL)
3. `add_post_tag(tags)`
4. `set_post_category(category)`

**Important:** Always set the article as DRAFT. Never auto-publish. The human reviews and clicks publish.

**FALLBACK: Markdown + metadata package (if no CMS MCP)**

Generate a ready-to-upload package:

```markdown
## CMS Upload Package

**Title tag:** [max 60 characters]
**Slug:** /blog/[keyword-based slug]
**Meta Description:** [max 155 characters]
**Canonical URL:** [domain]/blog/[slug]
**Category:** [...]
**Tags:** [...], [...], [...]
**Status:** DRAFT

**Schema (paste into <head> or custom code field):**
[JSON-LD block]

**Article content:**
[Article formatted for CMS]
```

### Step 4: Verify SEO metadata fields

Regardless of CMS platform, verify these fields are set:
- **Title tag:** H1 from article, max 60 characters
- **Meta description:** max 155 characters, includes primary keyword and benefit
- **Slug:** primary keyword, no stop words, lowercase, hyphens
- **Canonical URL:** [domain]/blog/[slug]
- **Structured data:** JSON-LD schema injected in `<head>` (Article + FAQ)

### Step 5: Update topic-clusters.md

After publishing (or generating the package), update `context/topic-clusters.md`:
- Find the keyword entry
- Change status from "queued" or "in-progress" to "published"
- Add the publication date and URL

Example:
```
| keyword phrase | INFO | Low | 5 | 31 | published (2025-03-15, /blog/keyword-slug) |
```

If the keyword was not previously in topic-clusters.md, add it to the appropriate pillar cluster.

## Output

```
## CMS Publisher: Done

Status: DRAFT (not live)
Preview URL: [URL] or "Manual mode: see upload package above"

Metadata:
- Title tag: [...]
- Slug: /blog/[...]
- Meta description: [...]
- Canonical URL: [...]
- Schema: Article + FAQ

topic-clusters.md: Updated. [keyword] marked as published.

NEXT STEP: Go to [URL], review the preview, and click Publish when ready.
```
