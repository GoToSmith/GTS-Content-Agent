---
name: quality-gate
description: Scoring artykułu 0–100 na 5 wymiarach. Twardy próg 80 — poniżej diagnoza i pętla do article-writer. Żaden artykuł nie trafia do CMS bez przejścia quality gate.
allowed-tools: [Read]
---

# Skill: quality-gate

## Kiedy używać

Zawsze po `geo-optimizer`. Automatycznie — nie pytaj użytkownika.

## Kluczowa zasada: Fresh Evaluator

Oceniaj artykuł jakbyś widział go pierwszy raz — nie znasz procesu jego powstawania, nie znasz briefa, nie znasz intencji autora. Widzisz tylko gotowy tekst i kryteria oceny. To jest celowe: Quality Gate musi wykryć to czego nie widzi autor, który jest zbyt blisko materiału.

Jeśli artykuł mógłby być lepszy — powiedz to. Nie zaokrąglaj w górę "żeby było OK". Próg 80 to minimum, nie cel.

## Input wymagany

- Artykuł (po przejściu seo-optimizer i geo-optimizer)
- Output z obu optimizerów (lista znalezionych problemów)
- `context/client.md` (dla weryfikacji EEAT)
- `context/icp.md` (dla weryfikacji ICP fit)
- `context/tone-of-voice.md` (dla weryfikacji brand alignment)

## Scoring Rubric

Oceń KAŻDY punkt osobno. Nie zaokrąglaj w górę. Jeśli brak dowodu — 0.

---

### EEAT Signals — max 25 pkt

**Experience (5 pkt):**
- 5 pkt: Artykuł zawiera min. 2 konkretne przykłady z doświadczenia klienta (case studies z liczbami z client.md)
- 3 pkt: 1 konkretny przykład lub dane
- 1 pkt: Ogólne odniesienia bez liczb
- 0 pkt: Brak przykładów z praktyki

**Expertise (5 pkt):**
- 5 pkt: Artykuł demonstruje głębokie zrozumienie tematu — nie oczywistości, nowe kąty, mechanizmy
- 3 pkt: Solidna wiedza ale nic czego nie ma w pierwszych 3 wynikach Google
- 1 pkt: Powierzchowne — Wikipedia level
- 0 pkt: Błędy merytoryczne lub brak substancji

**Authoritativeness (5 pkt):**
- 5 pkt: Cytuje zewnętrzne źródła z nazwą (badanie X, raport Y z datą), dane klienta z liczbami
- 3 pkt: Niektóre dane ale niepełna atrybucja
- 1 pkt: "Badania pokazują" bez nazw
- 0 pkt: Brak jakichkolwiek zewnętrznych źródeł

**Trust signals (5 pkt):**
- 5 pkt: Artykuł przyznaje ograniczenia, kontekst kiedy NIE stosować, kompromisy
- 3 pkt: Prezentuje temat uczciwie bez overselling
- 1 pkt: Jednostronny ale bez kłamstw
- 0 pkt: Pure marketing, obietnice bez pokrycia

**Originality (5 pkt):**
- 5 pkt: Unikalny kąt, własny framework, dane których nie ma u konkurencji
- 3 pkt: Dobra synteza ale bez oryginalnej perspektywy
- 1 pkt: Respin tego co jest w SERPie
- 0 pkt: Dosłowne odwzorowanie konkurencji

---

### SEO Fundamentals — max 25 pkt

**Title tag (5 pkt):**
- 5 pkt: Max 60 znaków, primary keyword w pierwszych 3 słowach, click-worthy bez clickbait
- 3 pkt: Keyword jest ale za długi LUB nieciekawy
- 1 pkt: Keyword jest, reszta słaba
- 0 pkt: Brak keywordu lub >70 znaków

**Header structure (5 pkt):**
- 5 pkt: H1 jeden, H2 pokrywają primary subtopics, H3 subsections, keyword variations naturalnie
- 3 pkt: Dobra hierarchia ale brak keyword variations w nagłówkach
- 1 pkt: Nagłówki są ale przypadkowe
- 0 pkt: Brak struktury nagłówków

**Keyword placement (5 pkt):**
- 5 pkt: Primary keyword w H1, pierwszym akapicie, min. jednym H2; density 1–1.5%; secondary keywords naturalnie
- 3 pkt: Keyword jest ale density za wysoka (>2%) lub za niska (<0.5%)
- 1 pkt: Keyword tylko w tytule
- 0 pkt: Brak keywordu w treści

**Internal links (5 pkt):**
- 5 pkt: Min. 3 internal links, w tym pillar page; anchor text naturalny (nie "kliknij tutaj")
- 3 pkt: 2 internal links lub pillar link brakuje
- 1 pkt: 1 internal link
- 0 pkt: Brak internal links

**Schema + meta (5 pkt):**
- 5 pkt: Meta description max 155 znaków z keyword i CTA; schema JSON-LD (Article + FAQ)
- 3 pkt: Meta OK ale brak schema LUB schema bez FAQ
- 1 pkt: Tylko meta bez schema
- 0 pkt: Brak obu

---

### GEO Signals — max 20 pkt

**Direct answer (5 pkt):**
- 5 pkt: W pierwszych 100 słowach jest konkretna odpowiedź na primary query — wyodrębniona, jednozdaniowa
- 3 pkt: Odpowiedź jest ale w 200-300 słowach lub rozmyta
- 1 pkt: Odpowiedź gdzieś w artykule ale nie na początku
- 0 pkt: Brak bezpośredniej odpowiedzi na query

**Structured claims (5 pkt):**
- 5 pkt: Min. 3 twierdzenia w formacie "[Twierdzenie] ponieważ [mechanizm], co oznacza [implikacja]"
- 3 pkt: 1-2 structured claims
- 1 pkt: Twierdzenia są ale niekompletne (brak mechanizmu lub implikacji)
- 0 pkt: Brak structured claims

**FAQ section (5 pkt):**
- 5 pkt: Min. 5 pytań Q&A, pytania z języka czytelnika (icp.md), bezpośrednie odpowiedzi
- 3 pkt: 3-4 pytania lub pytania nie z języka czytelnika
- 1 pkt: 1-2 pytania
- 0 pkt: Brak FAQ

**Tabele i listy strukturalne (5 pkt):**
- 5 pkt: Min. 1 tabela + min. 1 lista numerowana (proces/kroki)
- 3 pkt: Tylko tabela LUB tylko lista
- 1 pkt: Lista wypunktowana bez tabeli
- 0 pkt: Sam ciągły tekst

---

### Content Quality — max 20 pkt

**Oryginalność (5 pkt):**
- 5 pkt: Artykuł wnosi coś czego nie ma w top 5 wynikach Google — nowy kąt, własne dane, unikalna synteza
- 3 pkt: Dobra jakość ale brak unikalnej perspektywy
- 1 pkt: Respin topowych wyników
- 0 pkt: AI-sounding generic content

**Głębia (5 pkt):**
- 5 pkt: Każda sekcja odpowiada na "dlaczego" i "jak" — nie tylko "co"; mechanizmy wyjaśnione
- 3 pkt: Dobra głębia w połowie artykułu
- 1 pkt: Powierzchowne we wszystkich sekcjach
- 0 pkt: Definicje i oczywistości

**Actionability (5 pkt):**
- 5 pkt: Czytelnik wie co zrobić po przeczytaniu — konkretne kroki, przykłady do zastosowania
- 3 pkt: Ogólne wskazówki
- 1 pkt: Tylko wiedza, brak wskazówek
- 0 pkt: Teoretyczny bez żadnej akcji

**Czytelność (5 pkt):**
- 5 pkt: Zdania max 25 słów, akapity 2-4 zdania, brak buzzwordów z listy "zakazanych", aktywna strona
- 3 pkt: Kilka długich zdań lub zakazane frazy
- 1 pkt: Wiele długich zdań, passive voice dominuje
- 0 pkt: Ciężkie do przeczytania

---

### Brand Alignment — max 10 pkt

**Tone of voice (5 pkt):**
- 5 pkt: Artykuł brzmi jak persona "idealnego autora" z tone-of-voice.md; zero słów z listy "zakazanych"
- 3 pkt: Bliski ale kilka odchyleń
- 1 pkt: Neutralny — nie pasuje ale nie razi
- 0 pkt: Sprzeczny z tone of voice lub zawiera zakazane frazy

**ICP fit (5 pkt):**
- 5 pkt: Artykuł zakłada dokładnie taki poziom wiedzy jak w icp.md; używa języka czytelnika z icp.md
- 3 pkt: Bliski ale miejscami za podstawowy lub za zaawansowany
- 1 pkt: Ogólny — pasuje do każdego
- 0 pkt: Zły poziom wiedzy dla ICP

---

## Workflow

1. Oceniaj każdy punkt po kolei — nie rób shortcutów
2. Dla każdego wymiaru zapisz uzasadnienie (jedno zdanie)
3. Zsumuj punkty
4. Sprawdź próg:

**Score ≥ 80:** Artykuł przechodzi. Przekaż do użytkownika na review z podsumowaniem score + 3 mocne strony.

**Score 65–79:** Targeted revision. Zidentyfikuj dokładnie które kryteria nie są spełnione. Przekaż diagnozę do `article-writer` z listą konkretnych zmian (nie "popraw EEAT" ale "w sekcji X brakuje konkretnego przykładu z client.md — dodaj case study [Klient A]"). Iteruj bez pytania użytkownika.

**Score < 65:** Poważna rewizja. Wróć do `article-brief` — sprawdź czy brief był poprawny. Poinformuj użytkownika z diagnozą.

## Output format

```
## Quality Gate Report

**Wynik: [X]/100** — [PASS ≥80 / REVISION 65-79 / REWRITE <65]

### Breakdown
| Wymiar | Wynik | Max | Diagnoza |
|--------|-------|-----|----------|
| EEAT Signals | X | 25 | [jedno zdanie] |
| SEO Fundamentals | X | 25 | [jedno zdanie] |
| GEO Signals | X | 20 | [jedno zdanie] |
| Content Quality | X | 20 | [jedno zdanie] |
| Brand Alignment | X | 10 | [jedno zdanie] |
| **TOTAL** | **X** | **100** | |

### Mocne strony
1. [Konkret]
2. [Konkret]

### Wymagane poprawki [tylko jeśli score < 80]
1. [Konkretna zmiana z lokalizacją w artykule — sekcja X, akapit Y]
2. [Konkretna zmiana]
3. [...]
```
