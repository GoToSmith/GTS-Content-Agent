---
name: article-brief
description: Generuje 2-stronicowy brief per keyword: outline H1–H3, plan EEAT signals, internal links, typ schema, word count, 3 differentiating angles. Output trafia na Review Gate #1 do użytkownika.
allowed-tools: [Read, WebSearch, WebFetch]
---

# Skill: article-brief

## Kiedy używać

Po wyborze keyword przez użytkownika (z `context/topic-clusters.md`). Zawsze przed article-writer.

## Input wymagany

- Target keyword (primary)
- `context/client.md`
- `context/icp.md`
- `context/topic-clusters.md` (dla internal link plan)
- `context/competitors.md` (dla differentiating angles)

## Workflow

### Krok 1: Analiza search intent

Zidentyfikuj:
- **Typ intent:** Informational / Commercial Investigation / Transactional / Navigational
- **Kto pyta:** Jaki profil z icp.md najlepiej pasuje
- **Co naprawdę chce osiągnąć:** Nie "wie więcej" — co konkretnie zrobi z tą wiedzą
- **Poziom wiedzy:** Co już wie, czego nie wie

### Krok 2: SERP analysis (jeśli dostępny WebSearch)

Sprawdź top 5 wyników dla primary keyword:
- Jaką strukturę mają najlepiej rankujące artykuły
- Co robią dobrze (nie kopiuj — zrozum dlaczego)
- Co pomijają lub robią słabo (tu jest szansa)
- Czy są featured snippets / AI Overviews (format do pobicia)

### Krok 3: Outline H1–H3

Zasady:
- H1: primary keyword + angle który różnicuje od konkurencji
- H2: główne subtopics (4-8 sekcji) — każda odpowiada na osobne pytanie z icp.md
- H3: konkretne podpunkty (nie obowiązkowe — tylko gdy sekcja wymaga)
- Każdy H2 musi mieć "delivery promise" (co czytelnik z niej wyniesie)

### Krok 4: EEAT Plan

Wskaż konkretnie dla każdej sekcji:
- Jaki dowód/przykład z client.md wpleść
- Jakie dane zewnętrzne zacytować (z nazwą źródła)
- Gdzie przyznać ograniczenie lub kontekst (Trust signal)

### Krok 5: GEO Signals Plan

- **Direct Answer location:** Pierwszy akapit — sformułuj ją już w briefie
- **Structured claims:** Które sekcje będą miały "[Twierdzenie] ponieważ [mechanizm]"
- **FAQ questions:** 5-7 pytań z icp.md do pokrycia
- **Table location:** Która sekcja potrzebuje tabeli + co porównuje
- **TL;DR placement:** Początek lub koniec

### Krok 6: Internal Links

Z `context/topic-clusters.md`:
- 1x pillar page (obowiązkowy) — URL + sugerowany anchor text
- 2x cluster pages — URL + sugerowany anchor text
- Jeśli pillar page nie istnieje → wskaż że musi być stworzona

### Krok 7: Schema + Meta plan

- **Schema type:** Article / FAQ / HowTo / listicle — dobierz do formatu
- **Meta description draft:** Max 155 znaków z primary keyword + benefit + soft CTA
- **Slug suggestion:** keyword-primary-angle (bez stop words)

### Krok 8: Word count + format

Dobierz word count do intent:
- Informational (jak/co/dlaczego): 2000–3500 słów
- Commercial Investigation (porównanie/wybór): 2500–4000 słów
- Quick answer / Definition: 800–1500 słów
- Process / Tutorial (kroki): 1800–3000 słów

Format: standard article / listicle / step-by-step guide / comparison — dobierz do intent.

### Krok 9: Differentiating angles

3 konkretne kąty odróżniające ten artykuł od konkurencji:
1. [np. "Perspektywa wdrożeniowa: co się dzieje w tygodniu 2-4, nie tylko co wybrać"]
2. [np. "Dane z polskich firm, nie tylko US benchmarki"]
3. [np. "Szczery koszt wdrożenia — czego nie podają vendor strony"]

## Output format

```markdown
# Brief: [Primary Keyword]

**Keyword:** [primary keyword]
**Related:** [secondary keyword 1], [secondary keyword 2], [secondary keyword 3]
**Intent:** [typ + opis jednozdaniowy]
**Target reader:** [profil z icp.md]
**Word count:** [liczba] słów
**Format:** [article / listicle / guide / comparison]
**Schema:** [Article + FAQ / HowTo / etc.]

---

## Direct Answer (pierwsze 100 słów)

[Sformułuj już teraz — article-writer przepiszę w swoim stylu]

---

## Outline

**H1:** [Tytuł — max 60 znaków, primary keyword, differentiating angle]

**H2: [Sekcja 1]** — Delivery: [co czytelnik wyniesie]
- H3: [podpunkt] (opcjonalnie)
- EEAT: [jaki dowód/przykład z client.md wpleść]
- GEO: [structured claim / tabela / lista]

**H2: [Sekcja 2]** — Delivery: [co czytelnik wyniesie]
- EEAT: [...]
- GEO: [...]

[...]

**H2: FAQ — Często zadawane pytania**
1. [Pytanie 1 z icp.md]
2. [Pytanie 2]
3. [Pytanie 3]
4. [Pytanie 4]
5. [Pytanie 5]

---

## Internal Links

- **Pillar:** [URL] — anchor: "[anchor text]"
- **Cluster 1:** [URL lub "do stworzenia"] — anchor: "[anchor text]"
- **Cluster 2:** [URL lub "do stworzenia"] — anchor: "[anchor text]"

---

## Meta Description

[Max 155 znaków — primary keyword + główny benefit + soft CTA]

**Slug:** [keyword-angle]

---

## TL;DR (do umieszczenia na początku artykułu)

- [Wniosek 1]
- [Wniosek 2]
- [Wniosek 3]

---

## Differentiating Angles

1. [Kąt 1 — co ten artykuł ma czego nie mają top 5 wyników]
2. [Kąt 2]
3. [Kąt 3]

---

**[CZEKA NA ZATWIERDZENIE PRZEZ UŻYTKOWNIKA]**
```

Po wygenerowaniu briefa: zatrzymaj się i poczekaj na zatwierdzenie użytkownika (Review Gate #1).
