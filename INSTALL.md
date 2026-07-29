# INSTALL — scenariusz instalacji (wykonuje Claude)

> **Czytasz to jako Claude Code?** To jest Twój scenariusz. Prowadzisz człowieka przez instalację przenośnego mózgu: zadajesz pytania, tworzysz pliki, testujesz. Człowiek może być nietechniczny — tłumacz co robisz jednym zdaniem, bez żargonu. Rozmawiaj w języku użytkownika (domyślnie polski).

## Zasady nadrzędne (obowiązują przez całą instalację)

1. **NIC nie ginie.** Zanim cokolwiek zmienisz w istniejących plikach użytkownika — pełna kopia do archiwum (M2). Kasowanie zabronione. Zawsze.
2. **Proponujesz → człowiek zatwierdza.** Każdą decyzję o przeniesieniu/archiwizacji istniejącego elementu przedstawiasz jako propozycję z uzasadnieniem. Nie działasz po cichu.
3. **Warstwami, nie hurtem.** Instalujesz rdzeń. Nie dokładaj własnych ulepszeń, dodatkowych plików ani rozszerzeń — nadmiar zabija adopcję.
4. **Po każdym module test.** Nie przechodź dalej, dopóki test modułu nie przejdzie.
5. **Wzorzec, nie treść.** Treść tożsamości i pamięci pochodzi od użytkownika — z wywiadu i migracji. Nie wymyślaj za niego.

## Przebieg

Wykonaj moduły po kolei. Szczegóły każdego w `moduly/`:

| Moduł | Plik | Efekt | Czas |
|-------|------|-------|------|
| **M0 — Rozpoznanie** | (poniżej) | wiesz, kto przed Tobą i co już ma | 5 min |
| **M1 — Onboarding** | `moduly/M1-onboarding.md` | tożsamość: `<Imie>.md`, `SOUL.md`, zasady | 15–20 min |
| **M2 — Migracja** | `moduly/M2-migracja.md` | istniejący setup zarchiwizowany i zintegrowany | 10–60 min |
| **M3 — Skille** | `moduly/M3-skille.md` | 4 skille rdzenia + dobrane wywiadem z katalogu | 10–15 min |
| **M4 — Samouczenie** | `moduly/M4-samouczenie.md` | reguły pamięci wpisane, mechanizmy aktywne | 5 min |
| **Test końcowy** | (poniżej) | świeża sesja zdaje 3 pytania kontrolne | 5 min |

## M0 — Rozpoznanie (zrób to teraz)

1. Przedstaw się jednym zdaniem: co za chwilę razem zrobicie i że nic z istniejących plików nie zginie.
2. Zapytaj o **imię** użytkownika i potwierdź **język** rozmowy.
3. Zapytaj o **lokalizację katalogu-mózgu**. Domyślna propozycja: `~/brain`. **Jeśli użytkownik ma już żywy vault/sejf z notatkami (np. Obsidian)** — zaproponuj, żeby mózg zamieszkał w nim (podkatalog lub pliki w korzeniu, jak woli): jedna lokalizacja, jeden przyszły sync; sejf półmartwy lub „nie chcę mieszać" → mózg osobno. (W zespołach przyjmijcie wspólną konwencję — jedna nazwa na wszystkich maszynach ułatwia sync później.)
4. **Zeskanuj istniejący setup** (tylko odczyt, niczego nie zmieniaj):
   - `~/.claude/CLAUDE.md` oraz `CLAUDE.md` w katalogach projektów, które wskaże użytkownik
   - `~/.claude/commands/` i `~/.claude/skills/` (istniejące skille)
   - katalogi pamięci (np. `~/.claude/memory*`, foldery notatek, vaulty Obsidian)
   - narzędzia własne (`~/bin`, skrypty, hooki w `~/.claude/settings.json`)
5. Zrelacjonuj co znalazłeś w 5–10 punktach i powiedz, co z tym będzie: **jeśli setup istnieje → M2 będzie migracją; jeśli pusto → M2 pomijasz.**

## Moduły M1–M4

Przeczytaj i wykonaj kolejno:
- `moduly/M1-onboarding.md`
- `moduly/M2-migracja.md` (pomiń tylko, gdy M0 wykazał czysty stan)
- `moduly/M3-skille.md`
- `moduly/M4-samouczenie.md`

## Test końcowy

1. Poproś użytkownika o **restart sesji** (wyjść z Claude i wejść ponownie — w dowolnym katalogu).
2. W świeżej sesji użytkownik zadaje 3 pytania kontrolne:
   - „Kim jestem i czym się zajmuję?"
   - „Jak lubię pracować i czego nie znosisz mi robić?"
   - „Nad czym teraz pracuję?"
3. Claude ma odpowiedzieć **z plików mózgu, bez sięgania do historii rozmów**. Wszystkie 3 poprawne → instalacja zakończona.
4. Na pożegnanie pokaż użytkownikowi rytm dnia: rano `/briefing`, wieczorem `/daily-summary`, raz na jakiś czas `/memory-dream`. To wszystko, co musi zapamiętać.

## Gdy coś pójdzie nie tak

- Test nie przechodzi → sprawdź importy `@` w `~/.claude/CLAUDE.md` (literówki w ścieżkach to 90% przypadków).
- Konflikt z istniejącym CLAUDE.md → wróć do zasady 2: pokaż różnice, zaproponuj scalenie, człowiek decyduje.
- Cokolwiek zepsute → archiwum z M2 ma stan sprzed instalacji. Nic nie zginęło.
