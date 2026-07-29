# M4 — Samouczenie i samooptymalizacja

**Efekt:** system rośnie sam — zapisuje lekcje, konsoliduje pamięć, nie puchnie.

To nie osobne narzędzie, tylko **reguły wpisane do mózgu** + skille z M3, które je egzekwują.

## Krok 1 — Dopisz reguły pamięci do `~/.claude/CLAUDE.md`

Dopisz sekcję (dostosuj ścieżkę mózgu):

```markdown
# Pamięć — jak zapisujesz wiedzę

- Jeden fakt = jeden plik w `<mózg>/memory/<slug>.md` (wzór: szablon w instalatorze).
- Po zapisaniu pliku dopisz JEDNĄ linię do `<mózg>/MEMORY.md`: `- [tytuł](memory/slug.md) — hook`.
- Zanim zapiszesz — sprawdź, czy fakt już istnieje: aktualizuj zamiast dublować. Błędne wpisy kasuj.
- Feedback/lekcje zapisuj z `**Why:**` (dlaczego tak) i `**How to apply:**` (jak stosować).
- MEMORY.md to indeks — nigdy nie wklejaj tam treści faktów.

# Audyt sesji

Gdy kończy się dłuższa sesja robocza (albo user mówi „kończymy"), zapytaj:
„Czy coś z tej sesji zapisać do pamięci?" — zaproponuj 1–3 konkrety. Zapisujesz dopiero po akceptacji, nie po cichu.
```

## Krok 2 — Objaśnij mechanizm użytkownikowi (2 minuty)

Cztery zdania, które musi usłyszeć:

1. **System pyta, nie zapisuje po cichu** — na koniec sesji proponuje, co zapamiętać; Ty decydujesz.
2. **Lekcje mają format** — nie „zapamiętaj że X", tylko X + dlaczego + jak stosować. Dzięki temu działają w przyszłych sesjach.
3. **`/memory-dream` to sprzątacz** — raz na tydzień–dwa scala duplikaty, usuwa martwe linki. Pamięć nie gnije.
4. **`/skill-scout` to radar** — gdy trzeci raz robisz to samo ręcznie, zaproponuje z tego skill.

## Krok 3 — Pierwszy fakt na żywo

Zamknij instalację zapisem pierwszego prawdziwego faktu: zapytaj użytkownika o jedną rzecz, którą Claude powinien wiedzieć na zawsze (ulubiony klient, konwencja nazewnictwa, cokolwiek realnego) → zapisz plik w `memory/` + linię w `MEMORY.md` na jego oczach. Niech zobaczy pełny cykl: fakt → plik → indeks → świeża sesja to wie.

## Miara życia systemu (sprawdź po 2 tygodniach)

System żyje, jeśli: świeża sesja nadal zdaje 3 pytania kontrolne · w `memory/` przybyły fakty · `.NOW.md` ma aktualną datę · `/briefing` lub `/daily-summary` używane regularnie. Jeśli nie — system dołączył do cmentarza porzuconych narzędzi; wróć do rozmowy, która warstwa uwiera.
