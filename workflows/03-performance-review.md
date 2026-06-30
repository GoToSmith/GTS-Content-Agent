# Workflow 03: Performance Review

**Cel:** Miesięczny audit wyników bloga — rankingi, content decay, AI citations, refresh plan.

**Czas:** ~20 min (Claude) + ~10 min review (użytkownik)

**Uruchomienie:**
```
Zrób miesięczny performance review bloga
```

---

## Warunki wstępne

- [ ] Blog istnieje i ma min. 5 opublikowanych artykułów
- [ ] Google Search Console połączone (opcjonalnie, przez MCP)
- [ ] `context/published/` zawiera archiwum artykułów

---

## Krok 1: Zbierz dane GSC (jeśli MCP dostępny)

Pobierz z Google Search Console per artykuł:
- Average Position (ranking)
- Clicks + Impressions + CTR (ostatnie 28 dni vs poprzednie 28 dni)
- Top queries per URL

Jeśli brak MCP → poproś użytkownika o export danych z GSC (Performance → Export).

---

## Krok 2: Content Decay Detection

Zidentyfikuj artykuły z **content decay** (degradacja rankingu):

Sygnały decay:
- Ranking dropped >5 pozycji vs poprzedni miesiąc
- CTR drop >20% przy stabilnych impressions
- Artykuł starszy niż 6 miesięcy bez update
- Daty w treści są nieaktualne (np. "w 2024 roku")

---

## Krok 3: AI Citation Audit (GEO)

Sprawdź ręcznie lub przez Perplexity API (jeśli dostępne):

Dla top 10 artykułów sprawdź czy pojawiają się w:
- Perplexity — zadaj primary keyword jako pytanie
- ChatGPT Search — sprawdź czy artykuł jest cytowany
- Google AI Overviews — wyszukaj keyword i sprawdź overview

Zapisz: cytowany / nie cytowany / partial citation.

Jeśli artykuł nie jest cytowany mimo dobrego rankingu → prawdopodobnie brak GEO signals (FAQ, structured claims, direct answer). Dodaj do refresh list.

---

## Krok 4: Content Gap Analysis

Na bazie GSC queries:

1. Które queries generują impressions ale mały CTR? → title/meta do optymalizacji
2. Które queries pojawiają się na pozycji 8-20? → artykuł do wzmocnienia (internal links, refresh)
3. Które queries nie mają pokrycia? → nowe artykuły do kolejki

---

## Krok 5: Refresh Priority List

Stwórz listę z priorytetami:

| Artykuł | Problem | Akcja | Priorytet |
|---------|---------|-------|-----------|
| [URL] | Content decay — ranking -8 pozycji | Refresh: nowe dane + GEO signals | Wysoki |
| [URL] | Brak AI citation | Dodaj FAQ + structured claims | Średni |
| [URL] | CTR 1.2% przy top 5 | Przepisz title + meta | Wysoki |

---

## ⏸ Review (użytkownik, ~10 min)

Przedstaw:
- Wyniki miesięczne (summary: co rośnie, co spada)
- Content decay list
- AI citation status
- Refresh priority list

Czekaj na zatwierdzenie refresh planu.

---

## Krok 6: Aktualizacja topic-clusters.md

Po zatwierdzeniu:
- Zaktualizuj statusy artykułów (published → needs-refresh)
- Dodaj nowe keywords z gap analysis do kolejki
- Usuń keywords które zostały opublikowane

---

## Summary

```
Performance Review — [Miesiąc YYYY]

Opublikowane: [X] artykułów
Średni ranking: [X] pozycja
CTR: [X]%
AI citations: [X]/[total] artykułów cytowanych

Do refreshu: [X] artykułów
Nowe keywords w kolejce: [X]

Następny review: [data za miesiąc]
```
