# M3 — Migracja: „rozpoznaj burdel"

**Efekt:** wszystko, co użytkownik zbudował do tej pory, jest bezpieczne i wpięte w nową strukturę. Zero strat.
**Wejście:** skan z M0. Jeśli M0 wykazał czysty stan — pomiń cały moduł.

> To najważniejszy moduł instalatora. Użytkownik ma działający dorobek: notatki, pamięci, CLAUDE.md-y, skrypty, hooki. Twoim zadaniem jest go **przenieść, nie zaorać** — a jego zaufanie zbudujesz tym, że niczego nie zgubisz.

## Krok 1 — Archiwum stanu zastanego (ZAWSZE pierwsze)

Zanim COKOLWIEK zmienisz:

```bash
mkdir -p <mózg>/archiwum/stan-zastany-$(date +%F)
```

Skopiuj (nie przenoś!) do archiwum wszystko, co będziesz ruszać: CLAUDE.md-y, pliki pamięci, konfiguracje. Dopisz `<mózg>/archiwum/stan-zastany-<data>/README.md`: co skąd skopiowane i dlaczego. Od tej chwili masz pełny punkt powrotu.

## Krok 2 — Mapa zastanego

Na bazie skanu z M0 zrób tabelę i **pokaż ją użytkownikowi**:

| Element | Gdzie jest | Co to | Propozycja |
|---------|-----------|-------|-----------|
| np. CLAUDE.md ×2 | `~/.claude/` + `~/praca/` | dublujące się instrukcje | scalić → jeden + importy |
| np. pamięć | `~/.claude/memory-shared/` | 40 plików faktów | przenieść do `<mózg>/memory/` + zbudować indeks |
| np. hook auto-zapisu | `settings.json` | zapis rozmów na FTP | **nie ruszać** — działa |

Kategorie propozycji: **integruj** (wchodzi do nowej struktury) · **zostaw** (działa, nie dotykaj) · **archiwum** (nieużywane/zdublowane — do archiwum z opisem dlaczego).

## Krok 3 — Zatwierdzenie per element

Przejdź mapę z użytkownikiem pozycja po pozycji. On decyduje, Ty wykonujesz. Sporne przypadki:

- **Dwie rozjechane pamięci / dwa CLAUDE.md** — nie wybieraj „lepszej". Porównaj treść, pokaż różnice, zaproponuj scalenie z zachowaniem obu wersji w archiwum.
- **Działające automatyzacje (hooki, skrypty, integracje)** — domyślnie **zostaw**. Migracja mózgu nie może zepsuć działającego warsztatu.
- **Istniejący vault/sejf z notatkami:**
  - **żywy** → mózg zamieszkał w nim już w M0 (jeden sejf, bez kopiowania); w M3 tylko wpinasz tożsamość/pamięć/stan w jego strukturę;
  - **martwy/półmartwy** → wartościowe treści **KOPIUJESZ do mózgu** (per element, z zatwierdzeniem), a stary sejf oznaczasz jako **zamrożone archiwum** (np. plik `ARCHIWUM-README.md` w środku: co to, kiedy zamrożone, co przeniesione). NIE kasujesz w dniu migracji — propozycję usunięcia składasz przy przeglądzie po 2 tygodniach, decyzja należy do użytkownika.
  - **Nigdy nie linkuj z mózgu do plików poza mózgiem** — po syncu na drugą maszynę takie linki są martwe (zasada 6 z INSTALL.md).
- **Porzucone narzędzia** (stary dashboard, nieużywana apka notatek) — do archiwum, ale zapytaj wprost: „tego nie używasz od X — archiwizujemy?"

## Krok 4 — Wykonanie

1. Przenieś zatwierdzone treści do struktury mózgu:
   - fakty/notatki o sobie → `<Imie>.md` lub `memory/` (jeden fakt = jeden plik, patrz M5)
   - wiedza robocza (klienci, projekty, dostępy-opisy) → `memory/` + linia w `MEMORY.md`
   - stan bieżący → `.NOW.md`
2. Scal CLAUDE.md-y: jeden `~/.claude/CLAUDE.md` z importami `@` (projekty mogą mieć swoje lokalne CLAUDE.md — ale bez dublowania treści globalnej).
3. Elementy „archiwum" → `<mózg>/archiwum/` z jedną linijką w README archiwum: co i dlaczego.

## Test M3

1. Użytkownik wskazuje 3 rzeczy, które „system wiedział przed migracją" → świeża sesja ma je wiedzieć nadal.
2. `archiwum/stan-zastany-<data>/` zawiera kopię wszystkiego, co ruszałeś.
3. Zapytaj wprost: „czy jest coś, czego się boisz, że zginęło?" — i sprawdźcie to razem.
