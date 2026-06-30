# SEO Standards — Quality Rubric

Plik wspólny (nie klient-specific). Definiuje standardy jakości które silnik egzekwuje automatycznie.

## Word Count per Intent

| Intent | Min | Optimal | Max |
|--------|-----|---------|-----|
| Informational (jak/co/dlaczego) | 1500 | 2500 | 3500 |
| Commercial Investigation (porównanie) | 2000 | 3000 | 4000 |
| Quick Answer / Definition | 600 | 1000 | 1500 |
| Process / Tutorial | 1500 | 2500 | 3500 |
| Pillar Page | 3000 | 4000 | 6000 |

## Title Tag Formula

**Format:** [Primary Keyword] — [Benefit lub Angle] [(opcjonalnie: rok)]

**Reguły:**
- Max 60 znaków (liczyć ze spacjami)
- Primary keyword w pierwszych 3 słowach
- Brak clickbait (obietnice które artykuł spełnia)
- Unikalne per artykuł (sprawdź duplikaty)

**Przykłady dobrych tytułów:**
- "Automatyzacja produkcji: 5 wdrożeń które skróciły czas o 40%"
- "CRM dla małej firmy — co sprawdza się w Polsce [2025]"
- "Jak obliczyć ROI z wdrożenia systemu MES"

**Przykłady złych tytułów:**
- "Kompleksowy przewodnik po automatyzacji produkcji w Polsce" (za ogólny, "kompleksowy")
- "Wszystko co musisz wiedzieć o CRM" (clickbait bez substancji)

## Meta Description Formula

**Format:** [Primary Keyword] [benefit/outcome]. [Konkret — liczba, przykład, unikalna perspektywa]. [Soft CTA].

**Reguły:**
- Max 155 znaków
- Primary keyword naturalnie w pierwszym zdaniu
- Konkret — nie "dowiedz się więcej"
- CTA: "Sprawdź jak", "Zobacz przykłady", "Poznaj framework" — nie "Kliknij tutaj"

## Schema Types per Format

| Format artykułu | Schema obowiązkowy | Schema opcjonalny |
|-----------------|-------------------|-------------------|
| Standard article | Article + FAQ | BreadcrumbList |
| Step-by-step guide | Article + HowTo | FAQ |
| Comparison / Ranking | Article + FAQ | ItemList |
| Definition/Explanation | Article + FAQ | DefinedTerm |
| Case study | Article | Review |

## Internal Linking Minimum

- Min. 3 internal links per artykuł
- 1x pillar page (obowiązkowy)
- 2x cluster pages (powiązane tematycznie)
- Max 8 internal links (nie linkuj do wszystkiego)
- Anchor text: naturalny fragment zdania, nie "kliknij tutaj"

## On-Page Checklist (25 pozycji)

Patrz: skill `seo-optimizer/SKILL.md`

## GEO Signals Checklist (12 pozycji)

Patrz: skill `geo-optimizer/SKILL.md`

## Quality Gate Scoring

Patrz: skill `quality-gate/SKILL.md`

Twardy próg: 80/100 = minimum do publication.

## Zakazane praktyki SEO (nigdy)

- Keyword stuffing — naturalność > density
- Hidden text lub links
- Duplicate content między artykułami
- Thin content (<600 słów dla jakiegokolwiek artykułu)
- Kupowanie linków
- Clickbait tytuły które nie matchują treści
- Auto-generated content bez human review (ten silnik ma obowiązkowe review gates)

## Lokalne SEO (B2B Polish market)

Jeśli klient operuje w Polsce:
- Używaj polskich przykładów i danych (nie tylko anglojęzyczne case studies)
- Dodaj location-specific keywords naturalnie (np. "wdrożenie CRM Polska", "automatyzacja dla polskich firm")
- Cytuj polskie źródła i badania gdzie dostępne
- Uwzględniaj polskie regulacje jeśli temat tego wymaga (RODO, prawo pracy itp.)
- Daty i liczby w formacie polskim (DD.MM.YYYY, spacje jako separatory tysięcy)
