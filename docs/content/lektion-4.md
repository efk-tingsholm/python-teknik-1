# Lektion 4

När man mäter något lite mer seriöst, temperatur, längd, ljudnivå eller annat, så får man oftast inte bara ett mätvärde, utan man tar många mätvärden över tid, man får en mätserie.

Oavsett om det handlar om mätserier eller namnlistor så behövs därmed ett sätt att spara mer än ett värde i samma variabel - en lista helt enkelt.

En lista är en samling av värden, dessa värden kallas element. Varje element har en position i listan, denna position kallas index. Det går att ändra, ta bort och lägga till element i listan.

## Skapa lista
En lista kan skapas genom att listelementen skrivs innanför hakparenteser, åtskilda av kommatecken.

```py
# Lista med text-strängar
ord_lista = ["hej", "på", "dig"]

# Lista med tal, decimaltal
tal_lista = [12.5, 13.0, 12.8, 13.1]

# Utskrift
print(ord_lista) # ["hej", "på", "dig"]
```

??? warning "Datatyper i listor"
    I Python *kan* en lista innehålla olika datatyper, t.ex. `[1, 2.5, "hej"]`.

    Men det kan vara bra att alltid jobba med samma datatyp i listan, t.ex. inte ha text i en lista för tal. Annars kan vanliga beräkningar som `sum(values)`, `min(values)` och `max(values)` ge fel om listan innehåller både tal och text.

## Index
Varje element har en position i listan, som kan beskrivas med ett heltal, positionen kallas index. Det första elementet i listan har index 0, det andra elementet har index 1, och så vidare.


```py
values = [12.5, 13.0, 12.8, 13.1]
```

| Element | Index |
|--------:|------:|
| 12.5    | 0     |
| 13.0    | 1     |
| 12.8    | 2     |
| 13.1    | 3     |


Det går att komma åt ett enskilt element i listan via dess index, antingen för att spara i en variabel eller skriva ut.

```py
tal = [7, 12, 3, 25, 9, 18, 4]

# Vanliga index (0, 1, 2, 3, ...)
forsta_talet = tal[0]
tredje_talet = tal[2]

print("Första talet:", forsta_talet)  # 7
print("Tredje talet:", tredje_talet)  # 3

# Du kan också skriva ut direkt
print("Fjärde talet:", tal[3])        # 25
```

Det går också att använda negativa index, de räknar från slutet, där index -1 motsvarar sista elementet.

```py
tal = [7, 12, 3, 25, 9, 18, 4]

# Negativa index räknar från slutet
sista_talet = tal[-1]
nast_sista_talet = tal[-2]

print("Sista talet:", sista_talet)            # 4
print("Näst sista talet:", nast_sista_talet)  # 18

# Exempel: tredje från slutet
print("Tredje från slutet:", tal[-3])         # 9
```

!!! warning "Index utanför listan"
    Om du försöker använda ett index som inte finns i listan får du ett exekveringsfel (IndexError).

    Exempel: om listan har 7 element så är sista giltiga index `6`.
    Om du försöker läsa `tal[7]` så kraschar programmet.

## Loopa genom lista
För att skriva ut eller komma åt alla element i en lista ett i taget kan man använda en loop, med fördel en for-loop.

### med range()
Här behöver man också använda funktionen `len()` för att få ut hur många element det finns på listan.

```py
tal = [4, 12, 7, 19, 3]

# Använd len() för att få ut och spara att det finns fem element
antal = len(tal)

# Använd variabeln antal för att styra range()
for i in range(antal):
    print(tal[i])
```
Ger utskriften:
```
4
12
7
19
3
```

### utan range()
Här används listans variabelnamn direkt i for-loopen. Sparar rader, men helt frivilligt.
```py
ord_lista = ["skruv", "mutter", "bult", "brickor"]

# Skriv in listans variabelnamn direkt i for-loopen
for ord in ord_lista:
    print(ord, end=" ") # print med mellanslag, en rad
```
> Ger utskriften: skruv mutter bult brickor


## Lägga till i lista
För att lägga till ett nytt element i en lista använder man metoden append().
Det betyder att värdet läggs sist i listan.

### append()
Följande exempel lägger till talen 40 och sen 5 på en befintlig lista, dessa hamnar sist, i den ordning de läggs till.
```py
tal = [10, 20, 30]

tal.append(40)
tal.append(5)

print(tal)  # [10, 20, 30, 40, 5]

```

??? info "Bonus: ta bort element (remove och pop)"
    Det finns två vanliga sätt att ta bort element ur en lista:

    - `remove(x)` tar bort **första förekomsten** av värdet `x`.
    - `pop(index)` tar bort elementet på ett visst **index**.

    ```py
    tal = [10, 20, 30, 20, 40]

    tal.remove(20)   # tar bort första 20
    print(tal)       # [10, 30, 20, 40]

    tal.pop(1)       # tar bort elementet på index 1
    print(tal)       # [10, 20, 40]
    ```


### append() med loop
Ofta vill man fylla en lista genom att läsa in flera värden. Här skriver användaren in olika heltal tills denne skriver "klar".

```py
# En tom lista som kan fyllas på.
tal_lista = []

# En bool som ska styra loopen.
fortsatt = True

# Upprepa sålänge som variabeln fortsatt är sann.
while fortsatt:
    # Ta in en ny text från användaren, en gång varje varv
    text = input("Skriv in ett heltal (eller klar): ")

    # OM texten som skrivs in är "klar" så avbryts loopen,
    # annars lägger vi till talet på listan
    if text == "klar":
        fortsatt = False
    else:
        # int() används för att konvertera till heltal
        tal_lista.append(int(text)) 

# Efter loopen är färdig, skriv ut hela listan med ord
print("Du matade in:", tal_lista)

```
> Om du vill kontrollera hur många tal användaren matade in kan du använda len(tal_lista).





## Loopa och förändra värden

### Filtrera fram en ny lista 
Ibland behöver man bara vissa värden ur sin datamängd, av någon anledning. Exempelvis så kanske bara de positiva talen är relevanta, ett sätt att lösa det problemet är att göra en ny lista och lägga bara de positiva talen på den. Det görs här genom att loopa genom listan, och med en if-sats undersöka för varje tal om det är positivt, och i så fall lägga till det på den nya listan.

```py
tal = [5, -2, 12, -7, 0, 9, -1]
positiva_tal = []

for t in tal:
    # OM talet t just detta varvet i loopen är positivt, lägg till.
    if t > 0:
        positiva_tal.append(t)

print("Original:", tal)
print("Positiva tal:", positiva_tal)
```

### Ändra värden i listan
Om du vill ändra några av värdena i listan behöver man använda index i sin loop. I det här exemplet ökas alla tal som är mindre än 10 med 5.

```py
tal = [4, 12, 7, 19, 3, 25, 9]

antal = len(tal)
for i in range(antal):
    # Om talet i listan med index i är mindre än 10, addera 5.
    if tal[i] < 10:
        tal[i] = tal[i] + 5

print("Ändrad lista:", tal)
```


## Finns X i listan?
För att kolla om ett värde finns i en lista kan du använda ordet `in`.
Det ger True (sant) eller False (falskt).

```py
delar = ["skruv", "mutter", "bult", "bricka"]

print("bult" in delar)     # True
print("spik" in delar)     # False

sokord = input("Skriv ett ord att söka efter: ")
if sokord in delar:
    print("Ja, det finns i listan!")
else:
    print("Nej, det finns inte i listan.")

```


## Statistik med listor
När du har en lista med tal kan du snabbt räkna ut enkel statistik med inbyggda funktioner.

```py
tal = [4, 12, 7, 19, 3, 25, 9]

antal = len(tal)
minsta = min(tal)
storsta = max(tal)
summa = sum(tal)
medel = summa / antal
spann = storsta - minsta

print("Tal:", tal)
print("Antal:", antal)
print("Min:", minsta)
print("Max:", storsta)
print("Summa:", summa)
print("Medelvärde:", medel)
print("Spann (max-min):", spann)
```

!!! info "Tips: tom lista"
    Om listan är tom (inga tal) kan `min()`, `max()` och medelvärde ge fel.
    Därför är det bra att först kontrollera om `len(tal) == 0`.

## Övrigt
Bra att veta att dessa finns, ej supernödvändigt just nu.

- count(x) = räknar hur många gånger x finns i listan
- index(x) = ger index för första förekomsten av x
- clear()  = tömmer listan helt

```py
tal = [10, 20, 30, 20, 40]

print(tal.count(20))   # 2
print(tal.index(30))   # 2

tal.clear()
print(tal)             # []
```

## Inlämning 4

Du ska skriva ett program och lämna in via classroom. Du ska lämna in en fil som heter `förnamn_efternamn_inl_4.py`. Överst i filen ska du skriva följande info:

Överst i filen ska du skriva följande info:
```py
# Namn: XXXX YYYY
# Klass: NATE25
```

Programmet handlar om statistik för temperaturmätningar. Du har gjort flera temperaturmätningar på dygnsmedeltemperaturen i Göteborg. I en mätserie kan det ibland finnas outliers, t.ex. mätfel eller orimliga avläsningar. I det här scenariot antas giltiga temperaturer ligga i intervallet -25 °C till 35 °C.


Ditt program ska: 

- Låta användaren skriva in temperaturer som heltal, en temperatur i taget, ända tills användaren skriver "klar".

- Om en inmatad temperatur är inom det giltiga intervallet -25 till 35 (inklusive) ska den läggas till i en lista. 

- Om en inmatad temperatur är ogiltig, t.ex. -30, så ska den inte läggas på listan, men programmet ska räkna antalet ogiltiga temperaturer som matats in.

- När inmatningen är färdig så ska programmet skriva ut lite statistik om listan:
    - Antal temperaturer
    - Högsta temperatur
    - Lägsta temperatur
    - Medelvärdet av temperaturerna på listan
    - Temperaturspann (skillnaden högsta - lägsta)
    - ÄVEN: Antal ogiltiga temperaturer (som man räknat i punkt 3 ovan)

- Om listan är tom ska det skrivas ut ett felmeddelande, t.ex. "Inga giltiga temperaturer i datan."



Stilkrav:

- Använd beskrivande variabelnamn, t.ex. `temperaturer`, `antal_ogiltiga`, `minsta`, `storsta`.
- Ha minst en beskrivande kommentar som delar upp/förtydligar vad som händer, exempelvis # Rimlighetskontroll


### Testkörning
Såhär skulle det kunna se ut när man kör programmet, dina formuleringar kan självklart vara annorlunda.

```
Ange temperatur (heltal). Avsluta med klar: -50
Ange temperatur (heltal). Avsluta med klar: -5
Ange temperatur (heltal). Avsluta med klar: 3
Ange temperatur (heltal). Avsluta med klar: 4
Ange temperatur (heltal). Avsluta med klar: 8
Ange temperatur (heltal). Avsluta med klar: 13
Ange temperatur (heltal). Avsluta med klar: 27
Ange temperatur (heltal). Avsluta med klar: 40
Ange temperatur (heltal). Avsluta med klar: klar

==================================
Statistik för giltiga temperaturer
==================================
Antal temperaturer: 6
Högsta temperatur: 27
Lägsta temperatur: -5
Medelvärde: 8.33
Temperaturspann: 32
Antal ogiltiga temperaturer: 2
```

```
Ange temperatur (heltal). Avsluta med klar: 99
Ange temperatur (heltal). Avsluta med klar: 99
Ange temperatur (heltal). Avsluta med klar: 99
Ange temperatur (heltal). Avsluta med klar: klar

Inga giltiga temperaturer i datan.
```
