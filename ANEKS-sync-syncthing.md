# ANEKS — sync mózgu między urządzeniami

> **To NIE jest część instalacji.** Transport dokłada się, gdy mózg pożyje kilka dni na pierwszej maszynie. Wykonuje osoba techniczna zespołu.

**Efekt:** ten sam mózg na wszystkich urządzeniach jednej osoby — komputery, iPhone/iPad, docelowo serwer. Zmiana na jednym pojawia się na pozostałych w sekundy.

## Zasada nadrzędna — rozłączne transporty

Każdy plik ma **dokładnie JEDEN transport**. Dwa transporty na tym samym pliku = fabryka konfliktów.

| Co | Transport | Kiedy |
|----|-----------|-------|
| **Widoczne pliki `.md` (mózg)** | **Obsidian Sync** (chmura) | komputery + iPhone/iPad od razu; serwer przez headless — etap VPS |
| **Ukryte / konfiguracyjne** (wybrane pliki `~/.claude` itp.) | **Syncthing** (bezpośrednio maszyna↔maszyna) | dopiero na etapie VPS |
| **Runtime sesji** (aktywne sesje, locki w `~/.claude`) | **żaden — zawsze lokalny** | nigdy |

Do tego separacja osób: **każda osoba = własny vault + własne konto Obsidian Sync (płatne per osoba) + docelowo własny serwer**. Między osobami nie współdzieli się niczego; nazwa i ścieżka vaulta to sprawa osobista — musi być tylko identyczna na urządzeniach tej samej osoby.

## Część A — Obsidian Sync (komputery + mobile)

1. **Mózg = vault Obsidiana.** Jeśli mózg powstał jako zwykły folder: w Obsidianie *Open folder as vault* i wskaż katalog-mózg. Nic się nie przenosi — vault to po prostu folder.
2. **Konto + subskrypcja**: konto Obsidian + plan Sync. W vaulcie: *Settings → Sync → utwórz remote vault → Connect*.
3. **Kolejne urządzenia** (drugi komputer, iPhone, iPad): zainstaluj Obsidian, zaloguj na to samo konto, *Connect* do remote vault. Na komputerach — ta sama ścieżka lokalna co na pierwszym.
4. **Ustawienia typów plików** (*Settings → Sync*): na WSZYSTKICH urządzeniach te same, najlepiej z włączonym „all other types". Te ustawienia są **per-urządzenie** — rozjazd między urządzeniami to źródło „folderów-zombie" (folder wraca po skasowaniu, bo inne urządzenie trzyma pliki, których chmura nie zna).

**Test:** dopisz linijkę w `.NOW.md` na komputerze → otwórz Obsidian na telefonie → zmiana widoczna po kilku sekundach.

### Pułapki (sprawdzone bliznami)

- **NIGDY nie podpinaj pustego vaulta do istniejącego remote vaulta w trybie wypychania** — pusty vault potrafi wyczyścić chmurę. Przy podłączaniu nowego urządzenia zawsze wybieraj pobranie Z chmury.
- **iOS dosynchronizowuje tylko przy otwartym Obsidianie** — przed pracą na telefonie otwórz apkę i daj jej chwilę.
- **Nie mieszaj transportów**: vault NIE może leżeć w iCloud Drive/Dropbox, skoro nosi go Obsidian Sync.

## Część B — Syncthing (ukryte pliki, etap VPS)

Wchodzi dopiero, gdy dochodzi serwer — do przenoszenia plików, których Obsidian Sync nie widzi (ukryte/konfiguracyjne). Na etapie „komputery + mobile" NIE jest potrzebny.

- ✅ **Synchronizujesz:** wybrane pliki ukryte/konfiguracyjne — przez whitelist (`.stignore` z negacjami + catch-all `*`), identyczną na obu węzłach.
- ❌ **NIE synchronizujesz:** runtime `~/.claude` — aktywne sesje, locki; dwie maszyny się o nie pogryzą. `~/.claude/CLAUDE.md` zostaje lokalny per maszyna (różni się importem tożsamości).

Instalacja (obie maszyny):

```bash
brew install syncthing
brew services start syncthing
```

Panel: `http://localhost:8384`. Parowanie: maszyna B *Actions → Show ID* → maszyna A *Add Remote Device* → B akceptuje. Udostępnienie: A *Add Folder* → ścieżka → *Sharing* → B; B przyjmuje pod tą samą ścieżką.

Konfiguracja obowiązkowa (oba węzły): versioning **trashcan** (retencja ~14 dni) · **maxConflicts NIGDY 0** · żadnego automatycznego „wygrywa nowszy".

## Higiena zapisu równoległego

Gdy dwa urządzenia piszą do **tych samych** plików (`MEMORY.md`, `.NOW.md`) w tym samym czasie — zapisuj atomowo (plik tymczasowy + `mv`), nie edycją „w miejscu":

```bash
tmp=$(mktemp) && cat MEMORY.md > "$tmp" && echo "- nowy wpis" >> "$tmp" && mv "$tmp" MEMORY.md
```

Pliki per-fakt w `memory/` konfliktów praktycznie nie łapią — to najlepszy format do syncu. Wielki płaski plik pamięci przez sync = merge-piekło; dlatego go nie mamy.

## Czego NIE robić

- ❌ Nie dokładaj serwera/VPS, zanim sync komputerów i mobile nie pożyje i się nie sprawdzi.
- ❌ Nie dubluj transportów na tym samym pliku (Obsidian Sync + iCloud/Dropbox/Syncthing na tych samych `.md`) — patrz zasada nadrzędna.
- ❌ Nie łącz vaultów/kont między osobami — wspólne zasoby zespołu (jeśli kiedyś powstaną) to osobny folder z własnym transportem, nie czyjś mózg.
