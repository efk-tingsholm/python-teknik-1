# project-brief.md — Python (Teknik) GY25

## Syfte
Bygga ett arbetsområde i **grundläggande programmering i Python** för **Teknikprogrammet åk 1**.
Materialet publiceras som **MkDocs Material**-sidor (en lektion per artikel).

## Målgrupp och förutsättningar
- Elever: TE1, inga förkunskaper, ofta låg datorvana.
- Upplägg: ca **8 veckor**, **1 lektion/vecka**, **90 min**.
- Verktyg: **VS Code** + Python installerat + **Python extension (Microsoft)**.
- Inlämning: Google Classroom.
- Standard: **EN FIL** per uppgift (ingen zip).
  - Exit tickets: `main.py`
  - Capstone senare: `game.py` (+ video + ev. txt/README)

## Struktur (grovplan 8 lektioner)
1. Setup + print/input + enheter
2. if/elif/else + rimlighet + felmeddelanden (inkl. and/or, indentering)
3. Loopar + tabeller (tidssteg-tänk)
4. Listor + enkel statistik
5. Funktioner (anti-copy-paste + teknikfunktioner)
6. Simulering: temperatur mot jämvikt + matplotlib-plot
7. Pygame-skelett + var ligger modellen? + styrda ändringar
8. Capstone-workshop + inlämning (kod + README + skärminspelning)

## Bedömning (övergripande)
- Exit tickets: **F/E** (målet är att alla gör alla; komplettering ok).
- Teoriprov: **F–A** (begrepp, kodläsning, felsökning, resonemang).
- Capstone: **F–A** (pygame + skärminspelning som muntlig kodgenomgång).

## Stil- och inlämningsregler (återkommande)
- Filnamn: alltid `main.py` (eller `game.py` för capstone).
- Header i varje fil:
  - `# Namn: ...`
  - `# Klass: ...`
- Variabelnamn: **beskrivande** + **snake_case**.
- Exit tickets kan kräva **minst en kommentar** som delar upp programmet (t.ex. `# Rimlighetskontroll`).


## Pedagogisk stil för elevsidor (MkDocs)
- CTA-stil: rubrik -> kort text -> kodexempel -> repeat.
- Få screenshots efter lektion 1 (setup), sedan mest kod.
- Exempelkörningar markerar input med `>`:
  - `Skriv namn: > Emil`


## Önskat arbetssätt i chatten
- Jobba **lektion för lektion**.
- Börja med rubrikstruktur/checklista, fyll sedan på rubrik för rubrik.
- När användaren klistrar in aktuell `.md`-text: ge konkreta förslag på förbättringar och var “admonitions” kan läggas.
- Ge färdiga textstycken och kod som kan klistras in i MkDocs.
- Ställ frågor en i taget när val behövs.
