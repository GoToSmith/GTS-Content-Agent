# Workflow 02: Article Production

**Cel:** Wyprodukowanie jednego artykułu SEO+GEO od wybranego keywordu do draftu w CMS.

**Czas pracy Claude:** ~45 minut (nieinteraktywny)  
**Czas pracy użytkownika:** ~15-20 minut (2 review gates + publish)

**Uruchomienie:**
```
Napisz artykuł o [keyword] / Uruchom workflow 02 dla [keyword]
```

---

## Warunki wstępne (zero conditions)

Przed uruchomieniem sprawdź że istnieją:
- [ ] `context/client.md` — uzupełniony
- [ ] `context/icp.md` — uzupełniony
- [ ] `context/tone-of-voice.md` — uzupełniony
- [ ] `context/topic-clusters.md` — keyword jest na liście `queued`

Jeśli któregoś brakuje → zatrzymaj i poproś użytkownika o uzupełnienie.

---

## Krok 1: article-brief

Wywołaj skill `article-brief` z wybranym keywordem.

**Output:** 2-stronicowy brief z outline, EEAT plan, GEO signals plan, internal links, meta description, differentiating angles.

---

## ⏸ REVIEW GATE #1 — zatwierdź brief (5 minut)

Przedstaw brief użytkownikowi. Czekaj na zatwierdzenie.

Komunikat do użytkownika:
```
Brief jest gotowy. Zanim napiszę artykuł, potrzebuję Twojej akceptacji.
Sprawdź:
1. Czy outline pokrywa to co chcesz powiedzieć?
2. Czy differentiating angles są zgodne z Twoją perspektywą?
3. Czy EEAT plan (przykłady z client.md) są poprawne?

Napisz "OK" żeby kontynuować, lub podaj zmiany.
```

**Jeśli użytkownik zgłasza zmiany:** Zaktualizuj brief i wróć do review gate.

---

## Krok 2: article-writer

Wywołaj skill `article-writer` z zatwierdzonym briefem.

Input: brief + `context/client.md` + `context/icp.md` + `context/tone-of-voice.md`

**Output:** Pełny artykuł w Markdown, 1500–4000 słów, z pełną strukturą (H1-H3, FAQ, TL;DR, internal links).

---

## Krok 3: seo-optimizer

Wywołaj skill `seo-optimizer` automatycznie.

**Jeśli FAIL items:** Nanieś poprawki bezpośrednio. Nie pytaj użytkownika.

---

## Krok 4: geo-optimizer

Wywołaj skill `geo-optimizer` automatycznie.

**Jeśli FAIL items:** Nanieś poprawki bezpośrednio. Nie pytaj użytkownika.

---

## Krok 5: quality-gate

Wywołaj skill `quality-gate` automatycznie.

**Jeśli score < 80:** Przekaż diagnozę do `article-writer` z listą konkretnych zmian. Iteruj — max 3 rundy. Jeśli po 3 rundach score < 80 → poinformuj użytkownika z diagnozą.

**Jeśli score ≥ 80:** Przejdź do Review Gate #2.

---

## ⏸ REVIEW GATE #2 — przeczytaj finalny draft (10 minut)

Przedstaw użytkownikowi:
- Quality Gate score (np. "92/100")
- Link do artykułu (Markdown lub preview)
- 3 mocne strony i ewentualne uwagi

Komunikat:
```
Artykuł jest gotowy. Quality Gate score: [X]/100.

[Artykuł w Markdown]

Przeczytaj draft i napisz:
- "Publish" — jeśli akceptujesz i chcesz żebym wrzucił do CMS jako draft
- Zmiany — jeśli coś wymaga korekty
- "Stop" — jeśli nie chcesz publikować
```

**Jeśli użytkownik zgłasza zmiany:** Wprowadź je, ponownie uruchom quality-gate. Jeśli score ≥ 80, wróć do Review Gate #2.

---

## Krok 6: cms-publisher

Po zatwierdzeniu przez użytkownika — wywołaj skill `cms-publisher`.

**Output:** Draft w CMS z pełnymi metadanymi. URL podglądu dla użytkownika.

---

## Krok 7: Aktualizacja topic-clusters.md

Zmień status wybranego keywordu w `context/topic-clusters.md`:
- `queued` → `published` (z datą i URL artykułu)

---

## Summary dla użytkownika

```
Artykuł "[tytuł]" jest gotowy jako DRAFT w [CMS].

Podgląd: [URL]
Quality Gate: [score]/100
Następny krok: Otwórz podgląd, sprawdź formatowanie i kliknij Publish.

Kolejny artykuł z kolejki: [keyword] (lub powiedz mi który wybrać)
```
