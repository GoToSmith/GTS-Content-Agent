---
name: geo-optimizer
description: Checklist 12 pozycji GEO (Generative Engine Optimization) — optymalizacja pod AI search (Perplexity, ChatGPT Search, Google AI Overviews). Wywołaj po seo-optimizer, przed quality-gate.
allowed-tools: [Read]
---

# Skill: geo-optimizer

## Kiedy używać

Automatycznie po `seo-optimizer`. Nie pytaj użytkownika — iteruj.

## Czym jest GEO i dlaczego ma znaczenie

AI search engines (Perplexity, ChatGPT Search, Google AI Overviews) cytują strony które:
1. Mają bezpośrednie, wyodrębnione odpowiedzi na pytanie
2. Używają structured claims (twierdzenie + mechanizm + implikacja)
3. Mają tabele, listy, FAQ — formaty które LLM może wyekstrahować
4. Cytują źródła z konkretnymi nazwami i datami
5. Definiują kluczowe pojęcia (entity optimization)

Artykuł dobry pod GEO = artykuł który LLM może zacytować bez czytania całości.

## Checklist — 12 pozycji

### Direct Answer
1. W pierwszych 100 słowach jest bezpośrednia odpowiedź na primary query?
   - Format: "[Primary topic] to/oznacza/polega na [odpowiedź]. [Kluczowy szczegół]."
   - Test: czy LLM może wyciąć te 2 zdania i odpowiedzieć nimi na pytanie?

2. TL;DR / Key Takeaways section istnieje z 3-5 punkatami?
   - Każdy punkt = jedna falsifiable claim
   - Test: czy ktoś kto przeczyta tylko TL;DR rozumie główną tezę artykułu?

### Structured Claims
3. Min. 3 structured claims w formacie "[Twierdzenie] ponieważ [mechanizm], co oznacza [implikacja]"?
   - Twierdzenie: konkretne i falsifiable (nie "to ważne")
   - Mechanizm: wyjaśnienie DLACZEGO (nie "dlatego że")
   - Implikacja: co to oznacza dla czytelnika
   - Przykład: "Artykuły z FAQ section są cytowane przez Perplexity 40% częściej ponieważ LLM-y indeksują pytania jako osobne fragmenty, co oznacza że wystarczy 5 dobrych pytań żeby być widocznym w AI search."

4. Każde statystyczne twierdzenie ma konkretną atrybucję?
   - Poprawnie: "Według raportu Semrush z 2024, 65% zapytań..."
   - Niepoprawnie: "Badania pokazują że..."

### FAQ Section
5. FAQ section istnieje z min. 5 pytaniami?

6. Pytania są sformułowane jak naturalne pytania z Google (z icp.md)?
   - Poprawnie: "Jak obliczyć ROI z automatyzacji produkcji?"
   - Niepoprawnie: "Czym jest ROI automatyzacji?"

7. Każda odpowiedź FAQ zaczyna się od direct answer (max 2 zdania)?

### Tabele i Listy Strukturalne
8. Artykuł zawiera min. jedną tabelę z danymi lub porównaniem?

9. Artykuł zawiera min. jedną numerowaną listę kroków (proces/instrukcja)?

### Entity Optimization
10. Kluczowe pojęcia są zdefiniowane przy pierwszym użyciu?
    - Test: czy LLM który nie zna tematu zrozumie o czym mówisz bez kontekstu z zewnątrz?

11. Nazwa firmy klienta jest użyta min. 3x w kontekście ekspertyzy (nie tylko w stopce)?
    - Format: "[Firma X] wdraża / obserwuje / rekomenduje / zauważa..."
    - To buduje entity association: nazwa firmy ↔ temat artykułu

### Freshness Signals
12. Artykuł zawiera datę lub "aktualne dane na [rok]"?
    - AI search preferuje świeże treści
    - Jeśli dane są z poprzedniego roku — zaznacz to wyraźnie

## Output format

```markdown
## GEO Optimizer Report

**Pass:** X/12 | **Fail:** X/12

### Critical Issues (wpływają na cytowalność)

| # | Kryterium | Problem | Poprawka |
|---|-----------|---------|----------|
| 1 | Direct Answer | [problem] | [dodaj zdanie: "..."] |
| 3 | Structured Claims | [problem] | [w sekcji X zamień na format: ...] |

### Naniesione poprawki

[Lista konkretnych zmian — cytuj fragmenty przed i po]

**Przed:** "[oryginalny fragment]"
**Po:** "[poprawiony fragment]"
```

Jeśli wszystkie 12 PASS — napisz "GEO check: 12/12 PASS" i przejdź do quality-gate.
Jeśli są FAIL — nanieś poprawki bezpośrednio w artykule, potem przejdź do quality-gate.
