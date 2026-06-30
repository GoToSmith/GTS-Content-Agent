---
name: article-writer
description: Pisze pełny artykuł SEO+GEO (1500–4000 słów) na bazie zatwierdzonego briefa. Wbudowane sygnały EEAT, GEO i tone of voice klienta. Najważniejszy skill w silniku.
allowed-tools: [Read, Write, WebSearch, WebFetch]
---

# Skill: article-writer

## Kiedy używać

Po zatwierdzeniu briefa przez użytkownika (Review Gate #1). Nigdy bez briefa — każde słowo musi mieć uzasadnienie w briefie.

## Input wymagany

Przed uruchomieniem przeczytaj w tej kolejności:
1. `context/client.md` — kto pisze i dla jakiej firmy
2. `context/icp.md` — dla kogo piszesz, co już wie, jakim językiem mówi
3. `context/tone-of-voice.md` — jak piszesz, czego unikasz
4. Brief (output z `article-brief` skill) — struktura, outline, EEAT plan, target keyword

## Workflow

### Krok 1: Zrozum zadanie

Przed pisaniem odpowiedz sobie (nie na głos — wewnętrznie):
- Co czytelnik wpisał w Google/AI? Jaki ma problem w tej chwili?
- Co chce osiągnąć po przeczytaniu artykułu?
- Co wie, a czego nie wie na ten temat?
- Co klient (firma) chce żeby czytelnik zrozumiał lub zrobił?

### Krok 2: Napisz opening (pierwsze 100-150 słów)

**To jest najważniejsza część artykułu.**

Reguła: pierwsze zdanie musi zawierać albo (a) konkretną liczbę, albo (b) konkretny problem, albo (c) zaskakujący fakt. Nigdy nie zaczynaj od definicji tematu.

**Direct Answer (GEO signal):** W pierwszych 100 słowach umieść bezpośrednią odpowiedź na primary query — zanim pojawi się jakikolwiek kontekst. Perplexity i AI Overviews wyciągają tę odpowiedź jako cytat.

Formularz direct answer: "[Primary keyword] to/oznacza/polega na [odpowiedź w 1-2 zdaniach]. [Kluczowy szczegół który odróżnia dobrą odpowiedź od generycznej]."

### Krok 3: TL;DR / Key Takeaways (GEO signal — obowiązkowy)

Zaraz po openingu. Format:

```
**Kluczowe wnioski:**
- [Wniosek 1 — konkretny, falsifiable, z liczbą jeśli możliwe]
- [Wniosek 2 — mechanizm lub "dlaczego"]
- [Wniosek 3 — implikacja praktyczna]
- [Wniosek 4 — opcjonalnie]
```

**Dlaczego TL;DR na górze, nie na dole:** Perplexity i ChatGPT Search wyciągają treść z początku dokumentu jako pierwsze. Artykuł z TL;DR na górze jest cytowany częściej niż identyczny artykuł z TL;DR na dole lub bez TL;DR.

Każdy punkt TL;DR musi być self-contained — czytelnik który przeczyta tylko TL;DR powinien rozumieć główną tezę artykułu.

### Krok 4: Pisz sekcje główne (H2)

Dla każdej sekcji H2 z briefa:

**Struktura sekcji (obowiązkowa):**
1. **Teza** (1 zdanie) — co ta sekcja udowodni lub wyjaśni
2. **Mechanizm** (2-4 zdania) — jak/dlaczego to działa
3. **Dowód** (1-3 zdania) — konkretny przykład, dane, case study z client.md
4. **Implikacja** (1-2 zdania) — co to oznacza dla czytelnika

**Structured claims (GEO signal):** W każdej sekcji umieść min. jedno twierdzenie w formacie:
"[Faktualne twierdzenie] ponieważ [mechanizm], co w praktyce oznacza [implikacja dla czytelnika]."

Ten format jest chętnie cytowany przez AI search.

### Krok 5: Tabela lub lista strukturalna (GEO + SEO signal)

Każdy artykuł musi zawierać min. jedną tabelę lub strukturalną listę kroków.

**Kiedy tabela:** porównania, zestawienia, funkcje produktu, pro/con.
**Kiedy lista kroków:** procesy, instrukcje, checklist.

Tabele są cytowane przez AI Overviews 3x częściej niż akapity ciągłego tekstu.

### Krok 6: EEAT signals

Wpleć naturalnie — nie w osobnej sekcji:

- **Experience:** "W naszych wdrożeniach obserwujemy..." lub "Klienci których wdrażamy..." (dane z client.md)
- **Expertise:** Używaj terminologii z domeny, ale wyjaśniaj gdy potrzeba
- **Authority:** Odniesienie do case study z liczbami (z client.md)
- **Trust:** Przyznaj ograniczenia lub kontekst — "To działa gdy..., nie działa gdy..."

Minimum: 2 konkretne przykłady z client.md (case studies) wplecione jako naturalne ilustracje.

### Krok 7: FAQ section (GEO signal — obowiązkowy)

Min. 5 pytań. Format:

```
## Często zadawane pytania

### [Pytanie z icp.md — jak czytelnik faktycznie pyta]
[Odpowiedź: 2-4 zdania. Konkretna, bez owijania w bawełnę. Direct answer w pierwszym zdaniu.]

### [Pytanie 2]
[Odpowiedź]
```

Pytania pobierz z `context/icp.md` (sekcja "Pytania które wpisuje w Google/AI"). Uzupełnij longtiail wariantami primary keyword.

### Krok 8: Internal links

Zgodnie z briefem — min. 3:
- 1x do pillar page (obowiązkowy)
- 2x do cluster pages
- Anchor text: naturalne zdania, nie "kliknij tutaj"

### Krok 9: Entity Optimization (Semantic SEO)

Przed zamknięciem artykułu sprawdź:

**Definicja kluczowych encji:** Każde pojęcie techniczne lub branżowe użyte po raz pierwszy musi mieć krótkie wyjaśnienie (1 zdanie) — nie słownikową definicję, tylko kontekstowe wyjaśnienie dla Twojego ICP.

**Entity associations:** Artykuł powinien wielokrotnie łączyć nazwę firmy klienta z tematem artykułu w formie aktywnej:
- Poprawnie: "[Firma X] rekomenduje / wdraża / obserwuje / mierzy..."
- Niepoprawnie: "Firma X to lider w..."

To buduje entity association w indeksie Google i w modelach AI: nazwa firmy ↔ ekspertyza w temacie.

**Semantyczne pokrycie tematu:** Sprawdź czy artykuł używa naturalnie powiązanych terminów (LSI). Jeśli piszesz o "automatyzacji produkcji" — powinny pojawić się: linia produkcyjna, przestoje, OEE, czas cyklu, SCADA, MES — naturalnie, nie wymuszenie.

### Krok 10: Closing

Ostatni akapit = konkretny next step dla czytelnika. Nie "skontaktuj się z nami". Formularz:
"[Jeśli jesteś w sytuacji X] — zacznij od [konkretna akcja, może być link do darmowego zasobu/narzędzia]."

## Reguły pisania (bezwzględne)

### Styl
- Maksymalnie 25 słów per zdanie (liczyć!)
- Akapity: 2-4 zdania
- Jedna idea per akapit
- Aktywna strona: "System wykrywa" nie "Błąd jest wykrywany"
- Liczby cyframi: "3 tygodnie" nie "trzy tygodnie"

### Czego NIE robić
- Nie zaczynaj sekcji od definicji ze słownika
- Nie używaj fraz: "W dzisiejszych czasach", "Warto zaznaczyć", "Kompleksowy", "Holistyczny"
- Nie pisz zdań które brzmią jak marketing: "Nasze rozwiązanie to rewolucja"
- Nie cytuj danych bez źródła — dane albo z client.md, albo z powszechnie znanych faktów
- Nie kopiuj struktury z SERPu — dodaj unikalny kąt wynikający z briefu

### Tone of voice
- Czytaj `context/tone-of-voice.md` przed pisaniem każdego akapitu
- Sprawdź listę "słów zakazanych" — nie używaj ich
- Weryfikuj zdania przykładami z sekcji "Dobre zdanie" jako benchmarkiem

## Output format

Artykuł w Markdown z pełną strukturą:

```markdown
# [Tytuł H1 — max 60 znaków, primary keyword, click-worthy]

[Opening akapit — problem/liczba/fakt, direct answer w 100 słowach]

**Kluczowe wnioski:**
- ...
- ...
- ...

---

## [H2 — sekcja 1]

[Treść sekcji]

## [H2 — sekcja 2]

[Treść sekcji z tabelą lub listą]

...

## Często zadawane pytania

### [Pytanie 1]
[Odpowiedź]

...

---

[Closing akapit z next step]
```

Po napisaniu artykułu wywołaj automatycznie `seo-optimizer` → `geo-optimizer` → `quality-gate`.
