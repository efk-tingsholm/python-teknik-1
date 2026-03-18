# progress.md — Teknik GY25 Python (Teknik 1) arbetsområde

## Status
- [x] Lektion 1: Setup + print/input + float/round + Exit Ticket 1
- [x] Lektion 2: if/elif/else + rimlighet + felmeddelanden + Exit Ticket 2
- [x] Lektion 3: Loopar + tabeller (tidssteg)
- [x] Lektion 4: Listor + enkel statistik
- [ ] Lektion 5: Funktioner (anti-copy-paste)
- [ ] Lektion 6: Simulering temperatur + matplotlib
- [ ] Lektion 7: pygame-skelett + styrda ändringar
- [ ] Lektion 8: capstone-workshop + inlämning

## Beslut (standarder)
- Verktyg: VS Code + Python + Python extension (Microsoft).
- Körning: Run-knappen som standard. Terminal som backup/felsökning.
- Inlämningar: 1 fil per inlämning (ingen zip).
- Filnamn:
  - Inlämning 1: `main.py`
  - Inlämning 2+ : `förnamn_efternamn_inl_X.py`
- Header i varje fil:
  - `# Namn: ...`
  - `# Klass: ...`
- Kodstil: beskrivande variabelnamn + `snake_case`.
- Bedömning: kravbaserat (komplettering ok, alla inlämningar ska göras).
- Admonitions: används för tips/felsökning/överkurstexter (MkDocs Material).
  - Bonus/överkurser läggs gärna i hopfällbara rutor (`???`).

## MkDocs-format
- En lektion = en sida (`lektion-1.md`, `lektion-2.md`, ...).
- CTA-stil: rubrik → kort text → kodexempel.
- Efter setup-fasen: minimalt med screenshots.

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

## Lektion 3 (detaljer)
### Innehåll
- Introduktion iteration: loopar för att upprepa kod.
- `while`-loop:
  - grundstruktur + indentering
  - varning för oändlig loop + hur man stoppar (Ctrl+C)
  - exempel: räkna 1–5
  - utskrift på en rad med `print(..., end=" ")`
  - hopfällbara rutor: `print(end=...)`, bonus `lower()`/`strip()`
- `for`-loop:
  - `range(stopp)`, `range(start, stopp)`, `range(start, stopp, steg)`
  - negativt steg (nedräkning)
- Tabellutskrift och formatering:
  - “tabell” som en rad per varv + rubrikrad
  - f-strängar (f-strängar / f-strings): variabler i text och kolumnbredd/justering (`<`, `>`, `^`)
  - exempel på att välja kolumnbredd (rubrik + maxvärde + luft)
  - bonus: tusentalsavskiljare via format (och enkel svensk-ish variant med replace)
- Exempel/recept:
  - gångertabell (först enkel, sedan snyggare tabell)
  - summan mellan två tal (inkl. input och variabler i `range()`)
  - bonus: produkt med steg i `range()`
  - “köra igen”-mönster (wrap i `while`)
- MkDocs/UX:
  - code copy-knapp aktiverad (Material: `content.code.copy`)
  - bonusruta: `time.sleep()` för “levande” simulering

### Inlämning 3 (E/F)
- Tema: robotbatteri över tid (tidssteg = timme).
- Input: startnivå batteri (heltal) 50–100, annars felmeddelande och avslut.
- Simulering i loop (rekommenderat `while`):
  - NORMAL: batteriet minskar 7 % per timme
  - SPARLÄGE: vid 25 % eller lägre minskar batteriet 3 % per timme + meddelande i tabellen
  - batterinivån får inte bli negativ (kläm till 0)
  - avsluta med rad som visar att roboten stänger av vid 0 %
- Output: tabell med kolumner (Timme/Varv, Energi, Meddelande) + testkörningsexempel.
- Stilkrav: beskrivande variabelnamn, header med namn/klass, 1 fil.

## Lektion 4 (detaljer)
### Innehåll
- Introduktion listor: varför listor (mätserie/logg = många värden).
- Skapa listor:
  - tom lista `[]`
  - lista med startvärden (exempel med heltal/ord)
  - varning/info: Python kan blanda datatyper i listor, men vi siktar på en typ (t.ex. bara tal).
- Index:
  - första elementet `lista[0]`, tredje `lista[2]`
  - negativa index: `lista[-1]`, `lista[-2]`
  - varning: `IndexError` om index är utanför listans range.
- Loopa genom listor:
  - med `range()` + `len()` (när man behöver index)
  - utan `range()` (loop direkt över elementen)
  - repetition: utskrift på en rad med `print(..., end=" ")`.
- Lägga till i lista:
  - `append()` som standard
  - bygga lista med inmatning i `while` styrd av bool (utan `break`).
- Bonus/admonitions:
  - ta bort element: `remove(x)` (första förekomsten) och `pop(index)` (RemoveAt-liknande).
- Loopa och förändra:
  - filtrera till ny lista (t.ex. ta bort negativa tal genom att bara spara giltiga)
  - ändra i befintlig lista med index (t.ex. öka alla tal < 10 med 5).
- Enkel statistik på listor:
  - `len`, `min`, `max`, `sum`, medelvärde `sum/len`, spann `max-min`
  - info/tips: kontrollera tom lista innan `min/max` och medelvärde.
- Medlemskap:
  - kontrollera om värde finns i lista med `in` (ord- och tal-exempel).

### Inlämning 4 (instruktion)
- Tema: dygnsmedeltemperaturer (Göteborg) med outliers/felvärden.
- Input: heltal en temperatur i taget tills användaren skriver `klar`.
- Rimlighetskontroll: giltigt intervall (t.ex. -25 till 35, inklusive).
  - ogiltiga värden ignoreras och räknas (räknare för outliers).
- Output:
  - antal giltiga, min, max, medelvärde, spann
  - samt antal ogiltiga/outliers
  - om listan är tom: felmeddelande och avslut.
- Stilkrav: beskrivande variabelnamn + minst en strukturkommentar.

## Att göra (nästa steg)
- [ ] Starta skelett för `lektion-5.md` (funktioner: anti-copy-paste).
- [ ] Bestäm Exit Ticket 5 (funktioner + återanvändning, ev. testdata med random som verktyg/bonus).
- [ ] Uppdatera `tools/ai-prompts.md` vid behov (t.ex. prompt för “gör 5 extra övningar på samma tema”).