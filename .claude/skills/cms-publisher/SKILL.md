---
name: cms-publisher
description: Formatuje zatwierdzony artykuł do CMS (Webflow lub WordPress), ustawia wszystkie metadane i schema, publikuje jako DRAFT. Zwraca URL podglądu. Człowiek klika publish.
allowed-tools: [Read, Write, WebFetch]
---

# Skill: cms-publisher

## Kiedy używać

Po zatwierdzeniu artykułu przez użytkownika (Review Gate #2). Zawsze ostatni krok w workflow 02.

## Input wymagany

- Zatwierdzony artykuł (Markdown)
- Output z quality-gate (dla metadanych)
- `context/client.md` (autor, kategoria, tagi)
- Brief (dla slug, meta description)

## Workflow

### Krok 1: Przygotuj metadane

```yaml
title: [H1 z artykułu — max 60 znaków]
slug: [keyword-angle bez stop words]
meta_description: [max 155 znaków — z briefa lub wygeneruj]
author: [z client.md]
category: [dopasuj do struktury bloga klienta]
tags: [primary keyword, 2-3 secondary keywords, branża]
published_date: [data dzisiejsza YYYY-MM-DD]
status: DRAFT
```

### Krok 2: Wygeneruj Schema JSON-LD

Zawsze: Article schema + FAQ schema (jeśli artykuł ma FAQ section).

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[H1]",
  "description": "[meta description]",
  "author": {
    "@type": "Organization",
    "name": "[nazwa firmy z client.md]",
    "url": "[domena z client.md]"
  },
  "publisher": {
    "@type": "Organization",
    "name": "[nazwa firmy]"
  },
  "datePublished": "[YYYY-MM-DD]",
  "dateModified": "[YYYY-MM-DD]",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "[domena]/blog/[slug]"
  }
}
```

FAQ Schema (jeśli artykuł ma FAQ):
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[Pytanie 1]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[Odpowiedź 1]"
      }
    }
  ]
}
```

### Krok 3: Publikacja (z MCP)

**Jeśli Webflow MCP dostępny:**
1. `create_blog_post(title, body_html, slug)`
2. `set_seo_fields(meta_title, meta_description, og_image_alt)`
3. `add_custom_code(schema_json_ld)` — dodaj schema w `<head>`
4. `set_categories_tags(category, tags)`
5. `set_status(DRAFT)`
6. `get_preview_url()` → zwróć użytkownikowi

**Jeśli WordPress MCP dostępny:**
1. `create_post(title, content, status=draft)`
2. `set_post_meta(meta_key, meta_value)` dla Yoast/RankMath fields
3. `add_post_tag(tags)`
4. `set_post_category(category)`

**Jeśli brak MCP (manual mode):**
Wygeneruj gotowy package dla ręcznego wklejenia:

```markdown
## Package do ręcznego wklejenia w CMS

**Title:** [...]
**Slug:** /blog/[...]
**Meta:** [...]
**Category:** [...]
**Tags:** [...], [...], [...]

**Schema (wklej w <head> lub custom code field):**
[JSON-LD]

**Treść artykułu:**
[Artykuł sformatowany pod CMS]
```

## Output

```
## CMS Publisher — Done

Status: DRAFT (nie opublikowano)
URL podglądu: [URL] lub "Manual mode — sprawdź package powyżej"

Metadane:
- Title: [...]
- Slug: /blog/[...]
- Meta: [...]
- Schema: Article + FAQ

NASTĘPNY KROK: Przejdź do [URL], sprawdź podgląd i kliknij Publish.
```
