# Claude Brain Installer — przenośny „mózg" dla Claude Code

Instalator osobistego systemu kontekstu dla [Claude Code](https://claude.com/claude-code): po instalacji każda świeża sesja Claude wie, **kim jesteś, jak pracujesz i na czym skończyłeś** — bez wklejania kontekstu i bez przeklikiwania starych rozmów.

Nie musisz być techniczny. Instalację prowadzi sam Claude — Ty odpowiadasz na pytania.

## Co dostajesz

- **Katalog-mózg** — zwykłe pliki `.md` w jednym folderze: tożsamość, pamięć, stan bieżący.
- **Migrację bez strat** — jeśli już masz jakiś setup (CLAUDE.md, notatki, pamięci), instalator go rozpozna i przeniesie. **Żelazna zasada: nic nie ginie.**
- **Bazowe skille** — otwarcie dnia (`/briefing`), zamknięcie dnia (`/daily-summary`), porządkowanie pamięci (`/memory-dream`), radar automatyzacji (`/skill-scout`).
- **Samouczenie** — system sam proponuje, co zapamiętać, i sam sprząta swoją pamięć.

## Wymagania

- macOS z zainstalowanym Claude Code (`claude --version` coś zwraca)
- `git` (jest w macOS po instalacji Command Line Tools)

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
| `ANEKS-sync-syncthing.md` | admin techniczny | Synchronizacja mózgu między komputerami (osobny etap, nie część instalacji) |

## Filozofia (3 zasady)

1. **Wzorzec, nie treść** — instalator daje strukturę; treść (kim jesteś, co wiesz) jest Twoja.
2. **Warstwami, nie hurtem** — rdzeń dziś, kolejne warstwy gdy poczujesz potrzebę.
3. **Nic nie ginie** — migracja to integracja + jawne archiwum; kasowanie zabronione.

---

Autor wzorca: [Dariusz Młynarski](https://github.com/dariuszmlynarski) · Wzorzec sprawdzony w codziennej pracy od 2026. Skille dystrybuowane z osobnych rep: [briefing](https://github.com/dariuszmlynarski/claude-skill-briefing) · [daily-summary](https://github.com/dariuszmlynarski/claude-skill-daily-summary) · [memory-dream](https://github.com/dariuszmlynarski/claude-skill-memory-dream) · [skill-scout](https://github.com/dariuszmlynarski/claude-skill-skill-scout)
