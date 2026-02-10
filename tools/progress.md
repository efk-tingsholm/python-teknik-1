# progress.md — Teknik GY25 Python (Teknik 1) arbetsområde

## Status
- [x] Lektion 1: Setup + print/input + float/round + Exit Ticket 1
- [x] Lektion 2: if/elif/else + rimlighet + felmeddelanden + Exit Ticket 2
- [ ] Lektion 3: Loopar + tabeller (tidssteg)
- [ ] Lektion 4: Listor + enkel statistik
- [ ] Lektion 5: Funktioner (anti-copy-paste)
- [ ] Lektion 6: Simulering temperatur + matplotlib
- [ ] Lektion 7: pygame-skelett + styrda ändringar
- [ ] Lektion 8: capstone-workshop + inlämning

## Beslut (standarder)
- Verktyg: VS Code + Python + Python extension (Microsoft).
- Körning: Run-knappen som standard. Terminal som backup/felsökning.
- Inlämningar: 1 fil per exit ticket (ingen zip).
- Filnamn: `main.py` för exit tickets.
- Header i varje fil:
  - `# Namn: ...`
  - `# Klass: ...`
- Kodstil: beskrivande variabelnamn + `snake_case`.
- Exit tickets bedöms F/E (kravbaserat). Komplettering ok men alla ska göras.
- Admonitions: används för tips/felsökning/överkurstexter (MkDocs Material).

## MkDocs-format
- En lektion = en sida (`lektion-1.md`, `lektion-2.md`, ...).
- CTA-stil: rubrik → kort text → kodexempel.
- Efter setup-fasen: minimalt med screenshots.
- Exempelkörning: markera användarinput med `>`.

## Lektion 1 (detaljer)
### Innehåll
- Installera Python (Add to PATH) och VS Code (högerklick “Open with Code”).
- Skapa kursmapp + lektionsmapp, öppna mapp i VS Code.
- Installera Python-extension.
- Kontrollera interpreter via statusrad (Python 3.x).
- print(), variabler, kommentarer, input(), float(), round().
- Admonitions: python-alias (Windows), decimalpunkt, datatyper, felsökning.

### Exit Ticket 1 (E/F)
- Header med namn/klass.
- Program: fråga namn + hastighet km/h, räkna om till m/s, skriv mening med namn + m/s.
- Exempel: 50 km/h → 13.89 m/s.
- Input i exempelkörning markeras med `>`.

## Lektion 2 (detaljer)
### Innehåll
- Jämförelser: `==`, `!=`, `<`, `>`, `<=`, `>=`.
- `if/elif/else`.
- `and` / `or` + hopfällbar info-ruta för kedjad jämförelse och `not`.
- Indentering, kolon `:`, `==` vs `=`, vanliga fel.
- Nästlade if: rimlighet → klassificering (säkerhetskontroll först).

### Exit Ticket 2 (E/F)
- Koncept: bromssträcka med friktion (koppling till tidigare mekanik).
- Input: hastighet km/h.
- Rimlighet: hastighet < 0 eller > 300 → orimligt.
- Beräkningar:
  - omvandla km/h → m/s
  - anta konstanter: `mu = 0.8`, `g = 9.82`
  - bromssträcka: `s = v**2 / (2*mu*g)`
  - avrunda (uppgiftstext: 1 decimal)
- Output: bromssträcka + klassificering kort/medel/lång (10/30 m).
- Stilkrav: beskrivande variabelnamn + minst en kommentar (t.ex. `# Rimlighetskontroll`).

## Att göra (nästa steg)
- [ ] Starta skelett för `lektion-3.md` (loopar + tabell över tid).
- [ ] Bestäm Exit Ticket 3 (kopplat till loopar/tabell, gärna “över tid”-tänk).
- [ ] Uppdatera `tools/ai-prompts.md` (korrekturläsningsprompt finns; ev. fler prompts senare).
