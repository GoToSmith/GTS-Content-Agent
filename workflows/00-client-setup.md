# Workflow 00: Client Setup

**Cel:** Jednorazowe skonfigurowanie silnika dla nowego klienta. Uruchamia się raz.

**Czas pracy użytkownika:** ~2 godziny (wypełnienie kontekstu + review)  
**Czas pracy Claude:** ~30 minut (generowanie topic-clusters, competitors)

---

## Krok 1: Klon repo i setup

```bash
git clone https://github.com/gotosmith/seo-content-engine.git [nazwa-klienta]
cd [nazwa-klienta]
```

---

## Krok 2: Wypełnij pliki kontekstu (użytkownik)

Użytkownik wypełnia 3 pliki z szablonów:

1. `context/client.md` — na bazie `context/client.md.template`
   - Czas: ~45 min
   - Kluczowe: case studies z liczbami, UVP w jednym zdaniu

2. `context/icp.md` — na bazie `context/icp.md.template`
   - Czas: ~30 min
   - Kluczowe: pytania w języku czytelnika (min. 10), triggery zakupowe

3. `context/tone-of-voice.md` — na bazie `context/tone-of-voice.md.template`
   - Czas: ~30 min
   - Kluczowe: 5 dobrych zdań, 5 złych zdań, lista słów zakazanych

---

## Krok 3: Weryfikacja kontekstu (Claude Code)

Po uzupełnieniu plików przez użytkownika, Claude Code sprawdza:

- Czy `client.md` ma min. 3 case studies z liczbami?
- Czy `icp.md` ma min. 10 pytań czytelnika?
- Czy `tone-of-voice.md` ma przykłady dobrych/złych zdań?

Jeśli brakuje → poproś użytkownika o uzupełnienie konkretnych sekcji.

---

## Krok 4: Keyword Research (Claude Code)

Zapytaj użytkownika:
```
Podaj 3-5 seed keywords lub obszarów tematycznych które są najważniejsze dla biznesu klienta.
```

Wywołaj skill `keyword-research` per każdy seed.

Output: `context/topic-clusters.md` z 60-100+ frazami pogrupowanymi w pillar + cluster.

---

## Krok 5: Review topic-clusters (użytkownik)

Przedstaw użytkownikowi:
- Pillar topics (3-5)
- Top 15 fraz z uzasadnieniem priorytetu
- Recommended production order

Czekaj na zatwierdzenie. Wprowadź korekty jeśli potrzebne.

---

## Krok 6: Competitor Analysis (Claude Code)

Na bazie zatwierdzonych pillarów, zidentyfikuj per pillar:
- Top 5 domen rankujących na pillar keyword
- Ich mocne strony contentowe (czego nie pobijemy łatwo)
- Ich słabe strony (content gaps, brak EEAT, stare daty)

Zapisz do `context/competitors.md`.

---

## Krok 7: MCP Configuration (użytkownik)

Edytuj `.claude/mcp.json` — podłącz dostępne narzędzia:

```json
{
  "mcpServers": {
    "ahrefs": {
      "command": "npx",
      "args": ["ahrefs-mcp"],
      "env": { "AHREFS_API_KEY": "..." }
    },
    "webflow": {
      "command": "npx",
      "args": ["webflow-mcp"],
      "env": { "WEBFLOW_TOKEN": "...", "COLLECTION_ID": "..." }
    }
  }
}
```

Bez MCP silnik działa w trybie manual — jakość contentu identyczna, brak live keyword data.

---

## Krok 8: Test run

Uruchom workflow `02-article-production` dla najłatwiejszej frazy z kolejki (low difficulty, high fit).

Cel: weryfikacja że kontekst działa poprawnie i tone of voice jest właściwy przed produkcją seryjną.

---

## Setup complete

```
Setup klienta [nazwa] jest kompletny.

Podsumowanie:
- Pillar topics: [liczba]
- Keywords w kolejce: [liczba]
- MCP: [connected / manual mode]

Pierwszy artykuł rekomendowany: [keyword]
Uruchom: "Napisz artykuł o [keyword]"
```
