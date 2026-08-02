# M2 — Szkielet: struktura pracy (PARA + GTD)

**Efekt:** mózg ma gdzie trzymać **robotę**, nie tylko wiedzę o użytkowniku.
**Tworzysz:** strukturę katalogów w mózgu · `<mózg>/rules/struktura.md` · `<mózg>/Dashboard.md`.

> **Dlaczego ten moduł istnieje i dlaczego stoi TUTAJ.** M1 dał tożsamość — Claude wie, z kim gada. Ale nie wie jeszcze, **gdzie ląduje robota**: notatka ze spotkania, pomysł, projekt, faktura. Bez tego M3 (migracja) nie ma dokąd przenosić dorobku, a skille z M4 (`/inbox-review`, `/new-project`) operują na katalogach, których nie ma. Szkielet musi stanąć **przed** migracją.

> **Zasada modułu: recepta, nie dyktat.** Poniższy układ to sprawdzony wzorzec (PARA + GTD), nie jedyna słuszna droga. Każdy element przedstawiasz **z powodem, dla którego tak wygląda**. Użytkownik może przemianować, scalić albo wyrzucić — ale **świadomie, po usłyszeniu powodu**, a nie dlatego, że nie wiedział, że ma wybór. Większość ludzi nie ma pomysłu na strukturę albo ma zły; po to tu jesteś.

## Krok 1 — Ustaw ramę (2 min)

Powiedz użytkownikowi wprost, zanim zaczniecie:

> „Zbudujemy teraz szkielet, w którym będzie mieszkać Twoja robota. Jedna rzecz na wstępie, bo większość ludzi się na niej potyka: **to nie jest system do pracy — to system do życia.** Jeśli wpiszemy tu tylko firmę, to za miesiąc założysz drugi system na resztę i wrócisz do punktu wyjścia, tylko z dwoma bałaganami zamiast jednego."

To zdanie jest ważniejsze, niż wygląda: użytkownik przychodzi z myślą „narzędzie do pracy" i sam sobie obcina połowę wartości.

## Krok 2 — Wywiad o obszary (5 min)

Nie pytaj „jakie masz obszary" — to pytanie dla kogoś, kto już zna odpowiedź. **Przejdź kategorie na głos i przy każdej zapytaj, czy to u niego osobna sprawa:**

- praca główna / firma, w której siedzi najwięcej
- drugi biznes, działalność poboczna, projekt, który zarabia albo ma zarabiać
- prywatne: dom, rodzina, sprawy urzędowe
- zdrowie i forma
- finanse (jeśli traktuje je osobno od prywatnych)
- nauka, pasja, coś, co konsekwentnie zżera czas

**Rekomendacja: 3–6 obszarów.** Mniej niż 3 → prawie zawsze znaczy, że ktoś myśli tylko o pracy; wróć do zdania z kroku 1. Więcej niż 6 → rozdrobnienie, zaproponuj scalenie (osobny obszar ma sens, gdy ma własnych ludzi, własne projekty i własną wiedzę).

Nazwy obszarów **daje użytkownik** — mają brzmieć jego językiem, nie Twoim.

## Krok 3 — Pokaż szkielet z uzasadnieniem (5 min)

Przedstaw układ i **powód przy każdym elemencie**. Bez powodów to tylko cudze foldery, które za tydzień zarosną.

```
<mózg>/
├── 1-Inbox/                      ← wszystko, co wpada, zanim zdecydujesz co z tym
├── 2-{Obszar}/
│   ├── About/                    ← trwała wiedza o obszarze
│   ├── Projekty/{Nazwa}/_PRD.md  ← aktywne, z celem i końcem
│   ├── Admin/{Nazwa}/            ← powtarzalne procesy, instrukcje
│   └── Archiwum/{Nazwa}/         ← zamknięte, bez powrotu
├── 3-{Obszar}/  …
├── Dziennik/RRRR-MM/             ← notatki dzienne
├── Backlog/                      ← pomysły jeszcze niezaczęte
└── Dashboard.md                  ← jeden punkt startu
```

| Element | Co trzyma | Dlaczego akurat tak |
|---------|-----------|---------------------|
| `1-Inbox/` | wszystko nowe, przed decyzją | **Jedno wejście. Dwa wejścia to zero wejść** — przy dwóch zawsze zapomnisz o jednym. Inbox ma być regularnie opróżniany, nie archiwizowany. |
| `About/` | kim/czym jest obszar: ludzie, infrastruktura, strategia | To **nie projekt** — nie ma końca. Wrzucanie wiedzy trwałej między projekty zabija jedno i drugie: projekty przestają pokazywać, co żyje, a wiedza ginie w zamkniętych folderach. |
| `Projekty/{X}/_PRD.md` | rzeczy z celem, zakresem i końcem | **Każdy projekt MUSI mieć `_PRD.md`.** Za miesiąc nie pamiętasz, po co to było — a Claude tym bardziej. PRD to jedno miejsce na cel, decyzje i to, co dalej. |
| `Admin/{X}/` | procesy powtarzalne, referencje techniczne | Test: „czy kiedyś sięgnę po to jak po podręcznik, żeby coś wykonać?" → tak = Admin. Tu ląduje projekt, który się skończył, ale zostawił po sobie proces. |
| `Archiwum/{X}/` | zamknięte, bez powrotu | Żeby `Projekty/` mówiły prawdę o tym, co naprawdę żyje. Katalog projektów z trupami przestaje być czytany. |
| `Dziennik/RRRR-MM/` | notatka dnia | Ciągłość: czym się zajmowałeś i na czym skończyłeś. Karmi podsumowania i pamięć. |
| `Backlog/` | pomysły niezaczęte | Żeby nie zaśmiecały `Projekty/` i żeby nie ginęły w głowie. |
| `Dashboard.md` | jeden hub: co aktywne, co pilne | Punkt startu dnia. Bez niego użytkownik nie wie, od czego zacząć. |

**Prefiksy cyfrowe** (`1-Inbox`, `2-Firma`…) — żeby katalogi sortowały się wg ważności, nie alfabetycznie. Inbox zawsze pierwszy, bo najczęściej dotykany.

**Cykl życia rzeczy** — powiedz to jednym zdaniem, bo to spina całość:

```
Backlog → Projekty/{X}/_PRD.md → Admin/{X}/  (został powtarzalny proces)
                               → Archiwum/{X}/ (skończone, martwe)
```

**Gdy użytkownik odrzuca element** — w porządku, ale **zapisz jego decyzję w `rules/struktura.md`** („Backlog świadomie pominięty — pomysły lądują w Inbox"). Inaczej będziesz mu to proponować co tydzień, a on będzie się zastanawiał, czy czegoś nie zepsuł.

## Krok 4 — Utwórz strukturę

Zbuduj katalogi dla zatwierdzonych obszarów. Przykład dla trzech:

```bash
mkdir -p <mózg>/1-Inbox <mózg>/Dziennik <mózg>/Backlog
for obszar in 2-Firma 3-Poboczne 4-Prywatne; do
  mkdir -p "<mózg>/$obszar"/{About,Projekty,Admin,Archiwum}
done
```

**Czego NIE robić:**
- nie twórz obszarów „na zapas" — puste katalogi zniechęcają i sugerują, że system jest większy niż życie użytkownika;
- nie kop podkatalogów głębiej, niż trzeba dziś — struktura ma rosnąć z użycia;
- nie wypełniaj `About/` treścią z głowy. To robi M3 (migracja) z realnego dorobku.

Załóż `Dashboard.md` z jedną sekcją na obszar i linkiem do aktywnych projektów (na razie pusty — wypełni się w M3 i przy pierwszym `/briefing`).

## Krok 5 — Zapisz regułę i podepnij ją

Bez reguły foldery zarosną w miesiąc — Claude musi wiedzieć, **gdzie co ląduje**, i sam tego pilnować.

Z szablonu `szablony/rules-struktura.md.szablon` utwórz `<mózg>/rules/struktura.md`: lista obszarów użytkownika, tabela „co gdzie ląduje", zasady nazewnictwa, cykl życia projektu i **jawnie zapisane odstępstwa** z kroku 3.

Dopisz import do `~/.claude/CLAUDE.md` (obok tych z M1):

```markdown
@<mózg>/rules/struktura.md
```

## Test M2

1. **Test czterech rzeczy** — zapytaj użytkownika, gdzie wylądują, i pozwól odpowiedzieć jemu:
   - faktura od podwykonawcy
   - pomysł na nowy produkt, którego jeszcze nie zaczyna
   - notatka ze spotkania sprzed godziny
   - instrukcja, jak co miesiąc robić backup

   **4/4 bez wahania = struktura jest jasna.** Wahanie przy którejkolwiek → nie użytkownik jest winny, tylko szkielet: dopytaj i popraw.
2. `rules/struktura.md` istnieje, jest zaimportowany, a świeża sesja potrafi z niego odpowiedzieć „gdzie zapisać notatkę ze spotkania?".
3. Zapytaj wprost: **„czy jest coś ważnego w Twoim życiu, co nie ma tu swojego miejsca?"** — jeśli tak, brakuje obszaru. Dodaj teraz, nie za miesiąc.
