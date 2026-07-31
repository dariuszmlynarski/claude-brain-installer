# Claude Brain Installer — przenośny „mózg" dla Claude Code

Instalator osobistego systemu kontekstu dla [Claude Code](https://claude.com/claude-code): po instalacji każda świeża sesja Claude wie, **kim jesteś, jak pracujesz i na czym skończyłeś** — bez wklejania kontekstu i bez przeklikiwania starych rozmów.

Nie musisz być techniczny. Instalację prowadzi sam Claude — Ty odpowiadasz na pytania.

## Czym to jest — w trzech zdaniach

„Mózg" to katalog zwykłych plików `.md`: **tożsamość** (kim jesteś, jak pracuje Twój asystent), **pamięć** (jeden fakt = jeden plik + indeks) i **stan bieżący** (na czym skończyłeś). Instalator to scenariusz, który Claude wykonuje na Twoim komputerze: przeprowadza wywiad, rozpoznaje i przenosi Twój dotychczasowy setup (nic nie ginie), instaluje bazowe skille i włącza mechanizmy samouczenia. Efekt sprawdzasz testem końcowym: świeża sesja odpowiada na 3 pytania kontrolne o Tobie — z plików, nie z historii rozmów.

## Moduły — co się dzieje po kolei

| Moduł | Co robi | Efekt | Czas |
|-------|---------|-------|------|
| **M0 — Rozpoznanie** | Claude pyta o imię, język i lokalizację mózgu, po czym skanuje istniejący setup (CLAUDE.md, skille, pamięci, narzędzia) — tylko odczyt | mapa tego, co już masz; decyzja, czy M2 będzie potrzebne | 5 min |
| **M1 — Onboarding** | wywiad o Tobie i o tym, jak ma pracować asystent | tożsamość: `<Imie>.md`, `SOUL.md`, zasady współpracy | 15–20 min |
| **M2 — Migracja** | istniejący setup: najpierw pełne archiwum, potem integracja do nowej struktury — **Claude proponuje, Ty zatwierdzasz per element** | dotychczasowy dorobek w nowej strukturze, zero strat | 10–60 min |
| **M3 — Skille** | instalacja 4 skilli rdzenia (`/briefing`, `/daily-summary`, `/memory-dream`, `/skill-scout`) + wywiad „co by Ci się przydało?" i dobór z katalogu opcjonalnego | rytm dnia i higiena pamięci działają od dnia 1 | 10–15 min |
| **M4 — Samouczenie** | wpisanie reguł pamięci: audyt sesji, zapis lekcji, konsolidacja, higiena kontekstu | system sam proponuje, co zapamiętać, i sam sprząta | 5 min |
| **Test końcowy** | restart sesji + 3 pytania kontrolne (kim jestem? jak pracuję? nad czym pracuję?) | odpowiedzi z plików mózgu = instalacja zaliczona | 5 min |

## Co dostajesz

- **Katalog-mózg** — zwykłe pliki `.md` w jednym folderze: tożsamość, pamięć, stan bieżący.
- **Migrację bez strat** — jeśli już masz jakiś setup (CLAUDE.md, notatki, pamięci), instalator go rozpozna i przeniesie. **Żelazna zasada: nic nie ginie.**
- **Bazowe skille** — otwarcie dnia (`/briefing`), zamknięcie dnia (`/daily-summary`), porządkowanie pamięci (`/memory-dream`), radar automatyzacji (`/skill-scout`) + **katalog opcjonalny dobierany wywiadem** („jakie skille by Ci się przydały?"): `/grill-me`, `/inbox-review`, `/new-project`, `/dev-compound`.
- **Samouczenie** — system sam proponuje, co zapamiętać, i sam sprząta swoją pamięć.

## Wymagania

- macOS z zainstalowanym Claude Code (`claude --version` coś zwraca)
- `git` (jest w macOS po instalacji Command Line Tools)
- opcjonalnie, pod skille dnia: dostęp do Twojego kalendarza/poczty/zadań — podpinany w trakcie instalacji przez MCP (`ANEKS-mcp-integracje.md`); bez tego skille działają w wersji okrojonej

## Instalacja — 3 kroki

1. Sklonuj to repo:
   ```bash
   git clone https://github.com/dariuszmlynarski/claude-brain-installer.git ~/claude-brain-installer
   ```
2. Odpal Claude Code w tym folderze:
   ```bash
   cd ~/claude-brain-installer && claude
   ```
3. Napisz do Claude:
   > Przeczytaj INSTALL.md i przeprowadź mnie przez instalację.

Resztę robi Claude — pyta, tworzy pliki, testuje. Instalacja trwa 30–60 minut (dłużej, jeśli masz duży istniejący setup do migracji).

## Struktura repo

| Plik | Dla kogo | Co robi |
|------|----------|---------|
| `INSTALL.md` | Claude | Główny scenariusz instalacji (moduły M1→M4) |
| `moduly/` | Claude | Szczegółowe instrukcje modułów |
| `szablony/` | Claude | Szablony plików mózgu |
| `ANEKS-mcp-integracje.md` | użytkownik + Claude (lub admin) | Podpięcie usług pod skille: kalendarz, poczta, zadania (MCP) |
| `ANEKS-sync-syncthing.md` | admin techniczny | Sync mózgu między urządzeniami: Obsidian Sync (komputery + iPhone/iPad) + Syncthing (ukryte pliki, etap VPS). Osobny etap, nie część instalacji |

## Filozofia (3 zasady)

1. **Wzorzec, nie treść** — instalator daje strukturę; treść (kim jesteś, co wiesz) jest Twoja.
2. **Warstwami, nie hurtem** — rdzeń dziś, kolejne warstwy gdy poczujesz potrzebę.
3. **Nic nie ginie** — migracja to integracja + jawne archiwum; kasowanie zabronione.

---

Autor wzorca: [Dariusz Młynarski](https://github.com/dariuszmlynarski) · Wzorzec sprawdzony w codziennej pracy od 2026. Skille dystrybuowane z osobnych rep: [briefing](https://github.com/dariuszmlynarski/claude-skill-briefing) · [daily-summary](https://github.com/dariuszmlynarski/claude-skill-daily-summary) · [memory-dream](https://github.com/dariuszmlynarski/claude-skill-memory-dream) · [skill-scout](https://github.com/dariuszmlynarski/claude-skill-skill-scout)
