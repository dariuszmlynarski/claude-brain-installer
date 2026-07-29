# ANEKS — integracje (MCP): poczta, kalendarz, zadania

> Skille takie jak `/briefing` sięgają do Twoich usług — kalendarza, poczty, menedżera zadań. Claude Code łączy się z nimi przez **MCP** (Model Context Protocol): mały „wtyk" per usługa. Bez wtyczki skill nie ma skąd wziąć danych.
>
> **To najbardziej techniczny moment całej instalacji.** Jeśli jesteś nietechniczny — zrób ten etap z osobą techniczną zespołu albo pozwól, żeby Claude Cię przeprowadził krok po kroku (umie).

## Jak to sprawdzić i dodać (mechanika)

```bash
claude mcp list                # co jest już podpięte
claude mcp add --scope user <nazwa> -- <komenda serwera>          # serwer lokalny (stdio)
claude mcp add --scope user --transport http <nazwa> <adres-url>  # serwer zdalny (http)
```

`--scope user` = integracja dostępna w każdym katalogu, nie tylko bieżącym. Po dodaniu: restart sesji i test (np. „pokaż moje jutrzejsze spotkania").

## Co podpiąć (wg tego, czego używasz)

| Usługa | Po co | Jak |
|--------|-------|-----|
| **Kalendarz** (Google Calendar / Outlook) | `/briefing` — plan dnia | serwer MCP dla Twojego dostawcy; Google wymaga OAuth (patrz niżej) |
| **Poczta** (Gmail / Outlook / IMAP) | `/briefing` — triage maili | jw. |
| **Menedżer zadań** (np. Todoist) | `/briefing`, `/inbox-review` — zadania | serwery MCP Todoist istnieją jako paczki `npx` z kluczem API |
| **Dysk** (Google Drive / OneDrive) | opcjonalnie — dostęp do dokumentów | jw. |

Konkretny serwer per usługa zmienia się w czasie (ekosystem MCP żyje), dlatego nie wklejamy tu komend, które za pół roku będą martwe. **Praktyczny sposób:** powiedz Claude'owi w sesji instalacyjnej np. *„znajdź aktualny, zaufany serwer MCP dla Google Calendar i przeprowadź mnie przez konfigurację"* — Claude sprawdzi, poda komendę `claude mcp add` i poprowadzi przez klucze/logowanie.

## Zasady bezpieczeństwa (nie do pominięcia)

1. **Klucze API i tokeny NIGDY w katalogu-mózgu** — mózg jest (docelowo) synchronizowany między maszynami i może trafić do backupu. Sekrety żyją w konfiguracji MCP (`claude mcp add` zapisuje je lokalnie) albo w menedżerze haseł.
2. **Serwery MCP tylko z zaufanych źródeł** — oficjalne repo dostawcy usługi albo znane, żywe projekty (gwiazdki, świeże commity). Serwer MCP widzi Twoje dane — traktuj wybór jak wybór aplikacji bankowej, nie jak wtyczkę do przeglądarki.
3. **Minimum uprawnień** — jeśli serwer pyta o zakres dostępu (np. Gmail read-only vs pełny), bierz najwęższy, który wystarcza skillom.
4. **OAuth Google** bywa najbardziej upierdliwy (projekt w Google Cloud, ekran zgody). To jednorazowa robota — zrób ją z osobą techniczną i zapisz do pamięci mózgu notatkę „jak to było zrobione".

## Gdy integracji (jeszcze) nie ma

Skille mają działać bez wywalania się: sekcje wymagające niepodpiętej usługi **oznacz w pliku skilla jako „pomiń — do czasu podpięcia MCP"** (M3 krok 3) albo wytnij, jeśli usługa nie będzie używana wcale. `/briefing` z samym kalendarzem to nadal dobry briefing.
