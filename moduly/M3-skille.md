# M3 — Skille: rdzeń + dobór pod użytkownika

**Efekt:** cztery skille rdzenia działają od dnia 1 + użytkownik dostał skille dobrane do SWOJEJ pracy — nie hurtowy zestaw.

## Krok 1 — Zainstaluj rdzeń (zawsze, bez pytania)

Rdzeń to rytm dnia i higiena systemu — potrzebuje go każdy:

```bash
mkdir -p ~/.claude/commands
for s in briefing daily-summary memory-dream skill-scout; do
  curl -fsSL "https://raw.githubusercontent.com/dariuszmlynarski/claude-skill-$s/main/$s.md" \
    -o ~/.claude/commands/$s.md
done
```

| Skill | Rola | Kiedy |
|-------|------|-------|
| `/briefing` | otwarcie dnia: kalendarz, poczta, zadania | rano |
| `/daily-summary` | zamknięcie dnia: notatka dzienna, aktualizacja `.NOW`/`.RECENT` | wieczorem |
| `/memory-dream` | konsolidacja pamięci: duplikaty, martwe linki, sieroty | raz na tydzień–dwa |
| `/skill-scout` | wykrywa powtarzalne procesy warte automatyzacji | raz na tydzień–dwa |

Jeśli któryś plik się nie pobrał (sieć, zmiana nazwy) — sklonuj repo `git clone` i skopiuj plik ręcznie.

## Krok 2 — Wywiad: „jakie skille by Ci się przydały?"

Zapytaj użytkownika o jego powtarzalną robotę — 2–3 pytania w stylu:
- „Co robisz co tydzień, co Cię nudzi albo zjada czas?"
- „Gromadzisz gdzieś luźne notatki/pomysły? Co się z nimi dzieje?"
- „Prowadzisz projekty (klienci, kampanie, wdrożenia) — jak trzymasz ustalenia?"

Na bazie odpowiedzi **zaproponuj pasujące pozycje z katalogu** (niżej) — z jednym zdaniem uzasadnienia per skill. Instalujesz TYLKO zaakceptowane. Nic „na zapas" — nieużywany skill to szum; wszystko z katalogu można doinstalować później jednym poleceniem (użytkownik mówi Claude'owi „doinstaluj X z katalogu instalatora").

### Katalog opcjonalny

| Skill | Dla kogo | Instalacja |
|-------|----------|-----------|
| `/grill-me` — przemaglowanie planu przed robotą | każdy, kto planuje coś większego (kampania, oferta, wdrożenie) | `curl -fsSL https://raw.githubusercontent.com/dariuszmlynarski/claude-skill-grill-me/main/grill-me.md -o ~/.claude/commands/grill-me.md` |
| `/inbox-review` — wrzutnia notatek → GTD do zera | kto łapie luźne myśli/pomysły i chce, by nie ginęły | `curl -fsSL https://raw.githubusercontent.com/dariuszmlynarski/claude-skill-inbox-review/main/inbox-review.md -o ~/.claude/commands/inbox-review.md` |
| `/new-project` — projekt przez wywiad → folder + `_PRD.md` z roadmapą | kto prowadzi projekty i gubi ustalenia po rozmowach | `curl -fsSL https://raw.githubusercontent.com/dariuszmlynarski/claude-skill-new-project/main/new-project.md -o ~/.claude/commands/new-project.md` |
| `/dev-compound` — autorefleksja po sesji deweloperskiej | tylko kto pisze kod / buduje automatyzacje | `curl -fsSL https://raw.githubusercontent.com/dariuszmlynarski/claude-skill-dev-compound/main/dev-compound.md -o ~/.claude/commands/dev-compound.md` |

Jeśli wywiad ujawni potrzebę, której katalog nie pokrywa (np. cotygodniowy raport dla klienta) — **nie buduj skilla teraz**. Zanotuj ją jako pierwszego kandydata do `skill-candidates.md` — od tego jest `/skill-scout`, a skill zbudowany po 3 realnych wystąpieniach jest lepszy niż zgadywany na dzień 1.

## Krok 3 — Dostosuj placeholdery

Skille z rep mają placeholdery (`{VAULT}`, `{INBOX}`, `{TWOJ_GMAIL}` itp.). Przejdź każdy zainstalowany plik i podmień na realia użytkownika:

- ścieżka mózgu/vaultu → jego `<mózg>`
- konta pocztowe/kalendarz → te, których używa (jeśli w ogóle — sekcje nieużywane **wytnij**, nie zostawiaj martwych)
- integracje, których nie ma (Todoist, dashboard) → wytnij lub oznacz „pomiń"

Zasada: **skill po dostosowaniu ma nie mieć ani jednego placeholdera i ani jednej sekcji, która u tego użytkownika nie zadziała.**

## Krok 4 — Test

1. `/briefing` w świeżej sesji → przechodzi bez błędów o brakujących plikach/kontach.
2. `/daily-summary` → tworzy notatkę dzienną i aktualizuje `.NOW.md` + `.RECENT.md`.
3. Po jednym teście każdego zaakceptowanego skilla z katalogu.

## Aktualizacje

Skille aktualizują się przez ponowne pobranie z repo (ten sam `curl`) + ponowne naniesienie dostosowań. Rzadko — tylko gdy autor ogłosi zmianę.
