---
name: keyword-research
description: Ekspanduje seed keyword do 60–100 fraz z intent classification, trudnością i klasteryzacją w pillar/cluster. Wyjście: aktualizacja topic-clusters.md.
allowed-tools: [Read, Write, WebSearch, WebFetch]
---

# Skill: keyword-research

## Kiedy używać

W workflow `01-keyword-discovery` (miesięcznie/kwartalnie) lub gdy topic-clusters.md jest pusta/niekompletna.

## Input wymagany

- Seed keyword lub obszar tematyczny (od użytkownika)
- `context/client.md` (dla kontekstu biznesowego)
- `context/icp.md` (dla rozumienia języka czytelnika)

Opcjonalnie (jeśli MCP dostępne):
- Ahrefs / SEMrush (dla real keyword data)

## Workflow

### Krok 1: Ekspansja seed keyword

Wygeneruj warianty seed keyword w 5 kategoriach:

1. **Exact + near-exact** — [seed keyword], [keyword synonim], [keyword z doprecyzowaniem]
2. **Question keywords** — "jak [seed]", "dlaczego [seed]", "kiedy [seed]", "co to jest [seed]"
3. **Comparison keywords** — "[seed] vs [alternatywa]", "najlepsz[y/a] [seed]", "[seed] ranking"
4. **Problem keywords** — "[problem który seed rozwiązuje]", "jak rozwiązać [problem]"
5. **Longtail specifics** — "[seed] dla [branża/rola]", "[seed] krok po kroku", "[seed] przykłady"

### Krok 2: Intent classification

Dla każdej frazy:
- **Informational (INFO):** chce zrozumieć, nauczyć się, dowiedzieć się
- **Commercial Investigation (COMM):** rozważa zakup, porównuje opcje
- **Transactional (TRANS):** gotowy do zakupu/działania
- **Navigational (NAV):** szuka konkretnej strony

### Krok 3: Difficulty estimation

Bez narzędzi MCP — oceń na podstawie SERP logic:
- **Low:** longtail (4+ słowa), niszowy temat, mała liczba wyników
- **Medium:** 2-3 słowa, temat branżowy, mieszane SERP
- **High:** head term (1-2 słowa), dominują big brands, featured snippets

Z narzędziami MCP — użyj Keyword Difficulty score:
- Low: KD < 30
- Medium: KD 30–60
- High: KD > 60

### Krok 4: Business fit scoring

Oceń każdą frazę pod kątem dopasowania do klienta (1-5):
5 = Idealny fit — artykuł naturalnie prowadzi do produktu/usługi klienta
3 = Dobry fit — temat powiązany, może generować awareness
1 = Słaby fit — temat zbyt ogólny lub niezwiązany z ofertą

### Krok 5: Klasteryzacja w pillar + cluster

Pogrupuj w 3-5 pillar topics:
- Pillar = broad topic, 1500+ słów, dużo search intent coverage
- Cluster = specific subtopic, 800-2500 słów, wspiera pillar

Każdy cluster powinien linkować do swojego pillara.

## Output format

Zaktualizuj `context/topic-clusters.md`:

```markdown
# Topic Clusters — [Klient]

Ostatnia aktualizacja: [data]

---

## Pillar 1: [Nazwa pillara]

**Pillar page:** [keyword] | Intent: INFO | Difficulty: [L/M/H] | Business fit: [1-5] | Status: [queued/in-progress/published]

### Cluster keywords:

| Keyword | Intent | Difficulty | Fit | Potencjał | Status |
|---------|--------|------------|-----|-----------|--------|
| [fraza 1] | INFO | Low | 5 | Wysoki | queued |
| [fraza 2] | COMM | Medium | 4 | Wysoki | queued |
| [fraza 3] | INFO | Low | 3 | Średni | queued |

---

## Pillar 2: [Nazwa pillara]

[...]

---

## Kolejka produkcji (recommended order)

1. [Keyword 1] — pillar, niska trudność, wysoki fit
2. [Keyword 2] — cluster Pillar 1, longtail, szybka wygrana
3. [...]
```

Po wygenerowaniu — przedstaw użytkownikowi summary (top 10 fraz z uzasadnieniem) i poczekaj na zatwierdzenie kolejki.
