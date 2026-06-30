# Workflow 01: Keyword Discovery

**Cel:** Ekspansja seed topics do pełnej mapy keyword clusters. Uruchamiaj miesięcznie lub gdy `topic-clusters.md` jest pusta.

**Czas:** ~30 min (Claude) + ~15 min review (użytkownik)

**Uruchomienie:**
```
Zrób keyword discovery dla [seed topic lub "odśwież topic clusters"]
```

---

## Warunki wstępne

- [ ] `context/client.md` uzupełniony
- [ ] `context/icp.md` uzupełniony (sekcja "Pytania które wpisuje w Google")

---

## Krok 1: Zbierz seed topics

Zapytaj użytkownika jeśli nie podał:
```
Podaj 3-5 obszarów tematycznych które są strategicznie ważne dla biznesu klienta.
Przykład: "automatyzacja produkcji", "dobór CRM dla SMB", "RODO w SaaS"
```

Jeśli `topic-clusters.md` już istnieje — odczytaj istniejące pillary i zapytaj czy rozszerzyć czy dodać nowe.

---

## Krok 2: Wywołaj keyword-research per seed topic

Dla każdego seed topic wywołaj skill `keyword-research`.

Uruchamiaj sekwencyjnie (nie równolegle) — każdy seed informuje kontekst następnego.

---

## Krok 3: Deduplikacja i klasteryzacja

Po zebraniu all keywords:
1. Usuń duplikaty (taka sama fraza lub bardzo podobna)
2. Zidentyfikuj nakładające się tematy (keyword cannibalization risk)
3. Potwierdź że każdy cluster ma min. 4 keyword (pillar + 3 cluster articles)

---

## Krok 4: Priority scoring

Dla każdego keyword oblicz Priority Score (1-10):

```
Priority = (Business Fit × 3) + (Inverse Difficulty × 2) + (Search Intent Weight × 2)
```

- Business Fit: 1-5 (z client.md)
- Inverse Difficulty: Low=3, Medium=2, High=1
- Intent Weight: COMM=3, INFO=2, TRANS=2, NAV=1

Top 15 keywords = recommended production order.

---

## ⏸ Review (użytkownik, ~15 min)

Przedstaw:
- Pillar topics (3-5) z uzasadnieniem
- Top 15 keywords z Priority Score
- Estimated coverage time

Czekaj na zatwierdzenie. Możliwe korekty:
- Zmiana priorytetu
- Usunięcie tematów zbyt dalekich od biznesu
- Dodanie tematów które Claude pominął

---

## Krok 5: Zapisz do topic-clusters.md

Po zatwierdzeniu — zaktualizuj lub utwórz `context/topic-clusters.md` z pełną mapą i statusami `queued`.

---

## Summary

```
Keyword discovery kompletny.

Pillary: [liczba] | Keywords w kolejce: [liczba]
Szacowany czas produkcji @ 3 art/tydzień: [X] tygodni

Rekomendowany pierwszy artykuł: [keyword]
Uruchom: "Napisz artykuł o [keyword]"
```
