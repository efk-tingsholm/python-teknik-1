# Lektion 3

Nu ska vi jobba med **iteration**, alltså att köra samma kod flera gånger. I Python gör man det med **loopar**.

En vanlig ingenjörsgrej är att göra en **tabell**:
- en rad per steg
- ofta över tid (tidssteg), eller över olika x-värden (värdetabell)

I den här lektionen går vi igenom:
- `for` (bestämt antal varv)
- `while` (kör så länge ett villkor är sant)
- tabeller + ett exempel där vi använder `if` inne i en loop


## for-loop (kör ett bestämt antal varv)

En `for`-loop används när du vet *hur många gånger* du vill loopa.

Exempel: skriv ut talen 1 till 5:

```py
for i in range(1, 6):
    print(i)
```

**Viktigt:** `range(1, 6)` betyder 1,2,3,4,5 (slutet 6 är **inte med**).


## range(): start, stopp, steg

`range()` kan skrivas på tre vanliga sätt:

1) `range(stopp)`
```py
for x in range(5):
    print(x)
# Skriver: 0,1,2,3,4
```

2) `range(start, stopp)`
```py
for x in range(3, 8):
    print(x)
# Skriver: 3,4,5,6,7
```

3) `range(start, stopp, steg)`
```py
for x in range(0, 11, 2):
    print(x)
# Skriver: 0,2,4,6,8,10
```


## Värdetabell (matte): y = x^2

En värdetabell är perfekt att göra med en loop.

Vi skriver en rubrikrad först, och sedan en rad per x:

```py
print("x  y")
print("-----")

for x in range(0, 11):
    y = x**2
    print(x, y)
```

Det blir inte “perfekt tabellformat”, men det blir en tydlig tabellidé: **en rad per x**.


## Tidssteg-tabell (teknik/fysik-spinn): sträcka vid konstant hastighet

Om en bil kör med konstant hastighet så gäller:
- sträcka = hastighet * tid

Vi kan skriva ut en tabell över tid, t.ex. varje sekund.

```py
hastighet_ms = 10  # m/s
total_tid = 10     # s

print("t (s)  sträcka (m)")
print("--------------------")

for t in range(0, total_tid + 1):
    sträcka = hastighet_ms * t
    print(t, "    ", sträcka)
```

Notera `total_tid + 1` så att även sista sekunden kommer med.


## if inne i en loop (markera en viktig händelse)

Ofta vill man göra något speciellt när ett värde passerar en gräns.

Exempel: skriv ut “PASSERAT 50 m!” när sträckan blir minst 50.

```py
hastighet_ms = 10
total_tid = 10

print("t (s)  sträcka (m)  kommentar")
print("--------------------------------")

for t in range(0, total_tid + 1):
    sträcka = hastighet_ms * t

    kommentar = ""
    if sträcka >= 50:
        kommentar = "PASSERAT 50 m!"

    print(t, "    ", sträcka, "       ", kommentar)
```

Här ser man en tydlig idé:
- loopen gör “standardjobbet” varje varv
- `if` gör “specialjobbet” ibland


## while-loop (kör så länge ett villkor är sant)

En `while`-loop används när du inte vet hur många varv det blir från början.

Exempel: räkna ner från 5 till 1:

```py
n = 5
while n > 0:
    print(n)
    n = n - 1

print("Start!")
```

**Viktigt:** i en `while` måste du nästan alltid uppdatera någon variabel (här `n`),
annars kan det bli en oändlig loop.


## Vanliga fel (felsökning)

### 1) Oändlig loop (while)
Om du glömmer att ändra variabeln i loopen kan programmet fastna.

```py
n = 5
while n > 0:
    print(n)
    # glömde: n = n - 1
```

### 2) Off-by-one (range)
`range(0, 10)` går till 9, inte 10.

Om du vill ha med 10: `range(0, 11)`.


## Inlämning 3

Du ska skriva ett program och lämna in via classroom. Du ska lämna in en fil som heter `main.py`.
Överst i filen ska du skriva följande info:

```py
# Namn: XXXX YYYY
# Klass: NATE25
```

### Uppgift: Tidssteg-tabell för rörelse (loop + tabell + if)

Programmet ska:

1) Fråga efter en hastighet i **km/h**
2) Fråga efter en total tid i **sekunder**
3) Göra rimlighetskontroll:
   - hastighet ska vara mellan 0 och 300 km/h
   - tid ska vara mellan 1 och 3600 s
4) Om värdena är rimliga:
   - räkna om hastigheten till m/s
   - skriva ut en tabell med en rad per sekund:
     - `t` (s)
     - `sträcka` (m), avrundad till 1 decimal
     - en kommentar-kolumn som skriver `"PASSERAT 100 m!"` från och med att sträckan är minst 100 m

**Tips:** använd en variabel `kommentar = ""` och sätt den med en `if`.

Stilkrav:
- Använd beskrivande variabelnamn (`hastighet_kmh`, `hastighet_ms`, `total_tid`, `sträcka`, …)
- Ha minst en kommentar som delar upp programmet, t.ex. `# Rimlighetskontroll`


### Testkörning (exempel)

```text
Ange hastighet i km/h: > 36
Ange total tid i sekunder: > 12

t (s)  sträcka (m)  kommentar
--------------------------------
0      0.0
1      10.0
2      20.0
3      30.0
4      40.0
5      50.0
6      60.0
7      70.0
8      80.0
9      90.0
10     100.0       PASSERAT 100 m!
11     110.0       PASSERAT 100 m!
12     120.0       PASSERAT 100 m!
```

Orimliga värden:

```text
Ange hastighet i km/h: > 400
Ange total tid i sekunder: > 10
Orimlig hastighet. Ange ett värde mellan 0 och 300 km/h.
```

```text
Ange hastighet i km/h: > 50
Ange total tid i sekunder: > 0
Orimlig tid. Ange ett värde mellan 1 och 3600 sekunder.
```
