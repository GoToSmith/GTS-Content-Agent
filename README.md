# SEO Content Engine — Claude Code Context Layer

Klonujesz ten repo → wypełniasz 3 pliki kontekstu → piszesz `Napisz artykuł o [temat]` → dostajesz artykuł top 0.1% jakości SEO+GEO.

Zbudowany na [Claude Code](https://claude.ai/code). Bezpłatny, open-source, lokalny — żadnych SaaS.

---

## Czym jest ten engine

Context layer dla Claude Code który zamienia asystenta AI w wyspecjalizowany silnik contentowy:

- Pisze artykuły SEO zoptymalizowane pod **Google** i **AI search** (Perplexity, ChatGPT Search, AI Overviews)
- Stosuje 25-punktowy checklist SEO automatycznie
- Stosuje 12-punktowy checklist GEO (Generative Engine Optimization) automatycznie  
- Ocenia każdy artykuł w skali 0–100. Artykuł poniżej 80 pkt wraca do poprawki automatycznie — bez pytania
- Żaden artykuł nie trafia do CMS bez Twojej akceptacji (dwa review gates)

**Nie jest to:** narzędzie SaaS, plugin do WordPressa, ani generator spamu. To system pracy z Claude Code.

---

## Wymagania

- [Claude Code](https://claude.ai/code) (CLI lub web) z dostępem do API Anthropic
- Konto Anthropic z aktywnym API key
- Git (do klonowania i zarządzania repo)

Opcjonalnie (dla pełnej automatyzacji):
- MCP connector do Ahrefs lub SEMrush — dane o keyword difficulty
- MCP connector do Webflow lub WordPress — automatyczne publikowanie
- MCP connector do Google Search Console — miesięczny performance review

---

## Jak zacząć

### Krok 1: Sklonuj i otwórz w Claude Code

```bash
git clone https://github.com/GoToSmith/content-engine.git my-blog
cd my-blog
claude  # lub otwórz w Claude Code web
```

### Krok 2: Wypełnij 3 pliki kontekstu (~2 godz. raz na zawsze)

```bash
cp context/client.md.template context/client.md
cp context/icp.md.template context/icp.md  
cp context/tone-of-voice.md.template context/tone-of-voice.md
```

Otwórz każdy plik i wypełnij według instrukcji w szablonie:

| Plik | Co zawiera | Czas |
|------|-----------|------|
| `context/client.md` | Twoja firma, produkt, case studies z liczbami, UVP | ~60 min |
| `context/icp.md` | Kim jest czytelnik bloga, co wpisuje w Google, jakim językiem mówi | ~45 min |
| `context/tone-of-voice.md` | Jak piszesz, czego unikasz, przykłady dobrych i złych zdań | ~15 min |

> **Jakość artykułów = jakość tych 3 plików.** Im więcej konkretnych danych (liczby, case studies, cytaty klientów) — tym lepszy artykuł.

### Krok 3: Odkryj keywords (opcjonalnie)

```
Zrób keyword discovery dla [wpisz temat, np. "automatyzacja procesów"]
```

Engine rozbuduje temat do mapy keyword clusters i zapisze do `context/topic-clusters.md`.

### Krok 4: Napisz artykuł

```
Napisz artykuł o [keyword lub temat]
```

Engine:
1. Generuje brief → **czekasz na Twoją akceptację** (~5 min)
2. Pisze artykuł (1500–4000 słów w zależności od intencji)
3. Automatycznie optymalizuje SEO (25 checklist)
4. Automatycznie optymalizuje GEO (12 checklist)
5. Automatycznie ocenia 0–100 pkt; jeśli <80 — iteruje sam
6. Pokazuje finalny draft → **czekasz na Twoją akceptację** (~10 min)
7. Publikuje do CMS (jeśli skonfigurowany MCP)

---

## Struktura repo

```
content-engine/
├── CLAUDE.md                    # Główna instrukcja engine (nie edytuj)
│
├── context/
│   ├── client.md.template       # → skopiuj do client.md i wypełnij
│   ├── icp.md.template          # → skopiuj do icp.md i wypełnij
│   ├── tone-of-voice.md.template # → skopiuj do tone-of-voice.md i wypełnij
│   ├── topic-clusters.md        # Auto-generowany przez keyword-research
│   └── seo-standards.md         # Standardy jakości (nie edytuj)
│
├── .claude/skills/
│   ├── keyword-research/        # Ekspansja seed topics → keyword mapa
│   ├── article-brief/           # Generator briefa z analizą SERP
│   ├── article-writer/          # Pisanie artykułu (najważniejszy skill)
│   ├── seo-optimizer/           # 25-punktowy checklist on-page
│   ├── geo-optimizer/           # 12-punktowy checklist GEO
│   ├── quality-gate/            # Ocena 0-100, decyzja publish/iteruj
│   └── cms-publisher/           # Publikacja do Webflow/WordPress
│
└── workflows/
    ├── 00-client-setup.md       # Jednorazowy setup klienta
    ├── 01-keyword-discovery.md  # Miesięczne odkrywanie keywords
    ├── 02-article-production.md # Produkcja artykułu (główny workflow)
    └── 03-performance-review.md # Miesięczny audit wyników
```

---

## System jakości

Każdy artykuł jest oceniany automatycznie w skali 0–100:

| Kategoria | Pkt | Co sprawdza |
|-----------|-----|-------------|
| EEAT | 25 | Doświadczenie, ekspertyza, autorytet, wiarygodność, oryginalność |
| SEO on-page | 25 | Title tag, nagłówki, keyword placement, internal links, schemat |
| GEO | 20 | Direct answer, structured claims, FAQ, tabele, entity definitions |
| Jakość treści | 20 | Oryginalność, głębokość, actionability, czytelność |
| Brand | 10 | Tone of voice, dopasowanie do ICP |

**Próg publikacji: 80/100.** Artykuł poniżej progu wraca automatycznie do `article-writer` z diagnozą. Max 3 rundy iteracji — jeśli nadal <80, engine eskaluje do Ciebie z wyjaśnieniem.

---

## GEO — co to jest i dlaczego ważne

GEO (Generative Engine Optimization) to optymalizacja pod AI search: Perplexity, ChatGPT Search, Google AI Overviews.

Artykuły w tym engine mają wbudowane sygnały GEO:

- **Direct answer w pierwszych 100 słowach** — AI wyciąga odpowiedź z początku dokumentu
- **TL;DR na górze** (nie na dole) — Perplexity cytuje treść z początku strony
- **Structured claims** w formacie: "[Twierdzenie] ponieważ [mechanizm], co oznacza [implikacja]"
- **FAQ section min. 5 pytań** — cytowana przez AI 40% częściej niż ciągły tekst
- **Min. 1 tabela** — cytowana przez AI Overviews 3x częściej niż akapity
- **Named attribution** dla każdej statystyki ("badanie X, rok Y")

---

## Komendy

```
# Jednorazowy setup
Skonfiguruj engine dla [nazwa firmy]

# Keyword discovery (miesięcznie)
Zrób keyword discovery dla [seed topic]

# Produkcja artykułu (główna komenda)
Napisz artykuł o [keyword]

# Performance review (miesięcznie)  
Zrób miesięczny performance review bloga
```

---

## FAQ

**Czy potrzebuję płatnego planu Claude?**  
Tak — engine używa Claude Code z API Anthropic. Koszt jednego artykułu to ~0.50–2 USD w zależności od długości i liczby iteracji.

**Czy mogę używać dla wielu klientów/blogów?**  
Tak — sklonuj repo oddzielnie dla każdego klienta i wypełnij osobne pliki kontekstu.

**Czy engine działa po polsku i po angielsku?**  
Engine jest zaprojektowany pod polski rynek B2B, ale działa w obu językach. Ustaw język w `context/client.md` i `context/tone-of-voice.md`.

**Czy muszę mieć Ahrefs / SEMrush?**  
Nie. Bez tych connektorów engine ocenia keyword difficulty na podstawie analizy SERP i własnego osądu. Wyniki są mniej precyzyjne, ale engine działa.

**Czy mogę publikować bez MCP do WordPressa/Webflow?**  
Tak — `cms-publisher` ma tryb manualny: generuje gotowy Markdown + metadane, który kopiujesz do CMS ręcznie.

---

## Licencja

MIT — możesz używać, modyfikować i dystrybuować bez ograniczeń.

---

*Zbudowane przez [GoToSmith](https://gotosmith.eu) — GTM dla technologicznych founderów B2B.*
