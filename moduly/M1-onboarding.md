# M1 — Onboarding: tożsamość

**Efekt:** świeża sesja wie, z kim gada i jak ma się zachowywać.
**Tworzysz:** `<mózg>/<Imie>.md` · `<mózg>/SOUL.md` · `<mózg>/rules/wspolpraca.md` · `<mózg>/.NOW.md` · szkielet pamięci.

## Krok 1 — Wywiad tożsamościowy (10–15 min)

Prowadź rozmowę, nie ankietę: jedno pytanie naraz, dopytuj o konkrety, parafrazuj i potwierdzaj.

**Ścieżka wspomagana (sprawdzona w praktyce):** jeśli użytkownik ma inną sesję Claude, która zna jego historię pracy — może w niej wygenerować DRAFTY odpowiedzi na pytania wywiadu i wkleić je tutaj. Draft to propozycja, nie odpowiedź: przeczytaj każdą użytkownikowi, a on **zatwierdza albo poprawia per odpowiedź** — zwłaszcza „jak pracuję" i „czego nie znosisz", bo tam generatory najchętniej wstawiają okrągłą watę („ceni porządek i efektywność"). Fikcja zatwierdzona w M1 zostaje w mózgu na zawsze — nie przepuszczaj jej.

Zbierz:

**O człowieku (→ `<Imie>.md`):**
- Rola i praca: czym się zajmuje, dla kogo, co jest sednem jego roboty?
- Rytm i styl: jak wygląda dzień pracy, jakie narzędzia, co go wybija z rytmu?
- Czego oczekuje od Claude — a czego **nie znosi**? (to pytanie daje najlepsze odpowiedzi)
- Jak się do niego zwracać?

**O asystencie (→ `SOUL.md`):**
- Charakter: rzeczowy pomocnik / partner z własnym zdaniem / coś innego?
- Ton: formalny–luźny, zwięzły–objaśniający, humor tak/nie?
- Czy asystent ma imię? (opcjonalne — pomaga w adopcji)

**Zasady współpracy (→ `rules/wspolpraca.md`):**
- Co Claude może robić od ręki, a co zawsze wymaga potwierdzenia?
- Czerwone linie: czego nie robić nigdy?

## Krok 2 — Utwórz katalog i pliki

```bash
mkdir -p <mózg>/memory <mózg>/rules
```

Wypełnij szablony treścią z wywiadu (szablony w `szablony/`, opisy pól w środku):
- `szablony/USER.md.szablon` → `<mózg>/<Imie>.md`
- `szablony/SOUL.md.szablon` → `<mózg>/SOUL.md`
- `szablony/rules-wspolpraca.md.szablon` → `<mózg>/rules/wspolpraca.md`
- `szablony/NOW.md.szablon` → `<mózg>/.NOW.md` — zapytaj: „nad czym teraz siedzisz?" i wpisz 2–3 pozycje
- `szablony/MEMORY.md.szablon` → `<mózg>/MEMORY.md` (na start pusty indeks)
- `szablony/RECENT.md.szablon` → `<mózg>/.RECENT.md` (pierwszym wpisem będzie dzisiejsza instalacja)

Po zapisaniu **pokaż użytkownikowi `<Imie>.md` i `SOUL.md` w całości** — niech poprawi, co nie brzmi jak on. To jego pliki.

## Krok 3 — Podepnij mózg do Claude Code

Do `~/.claude/CLAUDE.md` (utwórz, jeśli nie istnieje; jeśli istnieje — **to robota M3**, na razie tylko dopisz importy na górze):

```markdown
# Kontekst ładowany na starcie sesji
@<mózg>/<Imie>.md
@<mózg>/SOUL.md
@<mózg>/rules/wspolpraca.md
@<mózg>/.NOW.md
@<mózg>/MEMORY.md
```

Ścieżki wpisz pełne (np. `@~/brain/Anna.md`). `CLAUDE.md` jest **lokalny per maszyna** — przy syncu mózgu na drugi komputer ten jeden plik konfiguruje się osobno.

## Test M1

Świeża sesja → „Kim jestem i jak lubię pracować?" → odpowiedź z plików, konkretna, w ustalonym tonie. Nie przechodzi → sprawdź ścieżki importów.
