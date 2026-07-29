# ANEKS — sync mózgu między komputerami (Syncthing)

> **To NIE jest część instalacji.** Transport dokłada się, gdy mózg pożyje kilka dni na pierwszej maszynie. Wykonuje osoba techniczna zespołu.

**Efekt:** ten sam katalog-mózg na dwóch (lub więcej) komputerach; zmiana na jednym pojawia się na drugim w sekundy.

## Zasada №1 — co synchronizujesz, a czego NIE

- ✅ **Synchronizujesz:** katalog-mózg (np. `~/brain/`) — tożsamość, pamięć, stan.
- ❌ **NIE synchronizujesz:** `~/.claude/` — tam żyją aktywne sesje, locki i runtime; dwie maszyny się o nie pogryzą. `~/.claude/CLAUDE.md` zostaje lokalny per maszyna (różni się importem tożsamości).

## Instalacja (obie maszyny)

```bash
brew install syncthing
brew services start syncthing
```

Panel: `http://localhost:8384` na każdej maszynie osobno.

## Parowanie

1. Maszyna B: panel → *Actions → Show ID* → skopiuj Device ID.
2. Maszyna A (źródło mózgu): *Add Remote Device* → wklej ID → zaakceptuj.
3. Maszyna B: zaakceptuj przychodzące parowanie. W tej samej sieci łączą się w sekundy.

## Udostępnienie katalogu-mózgu

1. Maszyna A: *Add Folder* → Folder Path = katalog-mózg → *Sharing* → zaznacz maszynę B.
2. Maszyna B: przyjmij folder → ustaw tę samą ścieżkę (np. `~/brain`).

**Test:** dopisz linijkę w `.NOW.md` na A → pojawia się na B w kilka sekund.

## Druga maszyna — podpięcie Claude

Na maszynie B w `~/.claude/CLAUDE.md` te same importy `@` co na A (jeśli to ta sama osoba) albo import własnej tożsamości (jeśli to drugi członek zespołu — jego `<Imie>.md` może żyć w tym samym mózgu obok).

## Higiena zapisu równoległego

Gdy dwie maszyny piszą do **tych samych** plików (`MEMORY.md`, wspólny `.NOW.md`) w tym samym czasie — zapisuj atomowo (plik tymczasowy + `mv`), nie edycją „w miejscu":

```bash
tmp=$(mktemp) && cat MEMORY.md > "$tmp" && echo "- nowy wpis" >> "$tmp" && mv "$tmp" MEMORY.md
```

Pliki per-fakt w `memory/` konfliktów praktycznie nie łapią — to najlepszy format do syncu. Wielki płaski plik pamięci przez sync = merge-piekło; dlatego go nie mamy.

## Czego NIE robić

- ❌ Nie dokładaj od razu serwera/VPS jako trzeciego ciała — najpierw niech sync dwóch maszyn pożyje i się sprawdzi.
- ❌ Nie synchronizuj przez Dropbox/iCloud — konflikty plików `.md` rozwiązują gorzej niż Syncthing, a iCloud potrafi „odchudzać" pliki lokalnie.
