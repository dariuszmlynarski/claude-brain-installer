# M3 — Bazowe skille

**Efekt:** cztery skille działają od dnia 1: otwarcie dnia, zamknięcie dnia, higiena pamięci, radar automatyzacji.

## Krok 1 — Pobierz skille

Każdy skill żyje w osobnym publicznym repo. Zainstaluj do `~/.claude/commands/`:

```bash
mkdir -p ~/.claude/commands
for s in briefing daily-summary memory-dream skill-scout; do
  curl -fsSL "https://raw.githubusercontent.com/dariuszmlynarski/claude-skill-$s/main/$s.md" \
    -o ~/.claude/commands/$s.md
done
```

Jeśli któryś plik się nie pobrał (sieć, zmiana nazwy) — sklonuj repo `git clone` i skopiuj plik ręcznie.

| Skill | Rola | Kiedy |
|-------|------|-------|
| `/briefing` | otwarcie dnia: kalendarz, poczta, zadania | rano |
| `/daily-summary` | zamknięcie dnia: notatka dzienna, aktualizacja `.NOW`/`.RECENT` | wieczorem |
| `/memory-dream` | konsolidacja pamięci: duplikaty, martwe linki, sieroty | raz na tydzień–dwa |
| `/skill-scout` | wykrywa powtarzalne procesy warte automatyzacji | raz na tydzień–dwa |

## Krok 2 — Dostosuj placeholdery

Skille z rep mają placeholdery (`{VAULT}`, `{TWOJ_GMAIL}` itp.). Przejdź każdy plik i podmień na realia użytkownika:

- ścieżka mózgu/vaultu → jego `<mózg>`
- konta pocztowe/kalendarz → te, których używa (jeśli w ogóle — sekcje nieużywane **wytnij**, nie zostawiaj martwych)
- integracje, których nie ma (Todoist, dashboard) → wytnij lub oznacz „pomiń"

Zasada: **skill po dostosowaniu ma nie mieć ani jednego placeholdera i ani jednej sekcji, która u tego użytkownika nie zadziała.**

## Krok 3 — Test

1. `/briefing` w świeżej sesji → przechodzi bez błędów o brakujących plikach/kontach.
2. `/daily-summary` → tworzy notatkę dzienną i aktualizuje `.NOW.md` + `.RECENT.md`.

## Aktualizacje

Skille aktualizują się przez ponowne pobranie z repo (ten sam `curl`) + ponowne naniesienie dostosowań. Rzadko — tylko gdy autor ogłosi zmianę.
