---
name: seo-optimizer
description: Checklist 25 pozycji on-page SEO. Ocena pass/fail per pozycja + konkretne poprawki. Wywołaj po article-writer, przed geo-optimizer.
allowed-tools: [Read]
---

# Skill: seo-optimizer

## Kiedy używać

Automatycznie po `article-writer`. Nie pytaj użytkownika — iteruj.

## Checklist — 25 pozycji

Sprawdź każdą. Dla każdej: PASS / FAIL + poprawka jeśli FAIL.

### Title Tag (H1)
1. Max 60 znaków?
2. Primary keyword w pierwszych 3 słowach?
3. Click-worthy — daje powód do kliknięcia bez clickbait?
4. Unikalny — nie duplikuje innych artykułów na blogu?

### Meta Description
5. Max 155 znaków?
6. Zawiera primary keyword (naturalnie)?
7. Zawiera benefit dla czytelnika?
8. Ma soft CTA (np. "Sprawdź jak", "Dowiedz się")?

### Header Structure
9. Jeden i tylko jeden H1?
10. H2 pokrywają główne subtopics (min. 4)?
11. H2 zawierają keyword variations / LSI (nie verbatim primary keyword)?
12. Hierarchia H1 > H2 > H3 jest zachowana?

### Keyword Placement
13. Primary keyword w pierwszym akapicie (pierwsze 100 słów)?
14. Primary keyword w min. jednym H2?
15. Density primary keyword: 1–1.5% (nie over-optimization)?
16. Secondary keywords wplecione naturalnie min. 2x?

### Internal Links
17. Min. 3 internal links?
18. Pillar page jest zlinkowana?
19. Anchor text naturalny (nie "kliknij tutaj" ani "więcej")?
20. Brak broken links (linki do istniejących stron)?

### External Links / Citations
21. Min. 2 linki do wiarygodnych zewnętrznych źródeł (z nazwą w tekście)?
22. Źródła są konkretne — nie "według badań" ale "według raportu [nazwa] [rok]"?

### Technical On-Page
23. URL slug zawiera primary keyword, jest krótki i bez stop words?
24. Obrazy (jeśli są) mają alt text z keyword?
25. Schema JSON-LD jest zdefiniowana (Article + FAQ minimum)?

## Output format

```markdown
## SEO Optimizer Report

**Pass:** X/25 | **Fail:** X/25

### Issues (tylko FAIL)

| # | Kryterium | Problem | Poprawka |
|---|-----------|---------|----------|
| X | [nazwa] | [co jest nie tak] | [konkretna zmiana] |
| X | [...] | [...] | [...] |

### Poprawione elementy

[Lista konkretnych zmian do wprowadzenia w artykule — nie "popraw tytuł" ale "zmień tytuł z X na Y"]
```

Jeśli wszystkie kryteria PASS — napisz "SEO check: 25/25 PASS" i przejdź do geo-optimizer.
Jeśli są FAIL — nanieś poprawki bezpośrednio w artykule, potem przejdź do geo-optimizer.
