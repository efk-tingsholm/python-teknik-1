# Lektion 4 - Arbete pågår, ej klar!

TODO

Faktiska exempelsaker

- Loopa genom lista
- Loopa genom och göra nåt, typ om elementet är < 10 så öka det med 20
- Skriva in tal från användaren direkt på lista
- split() för text?
- kolla om element x finns i lista? "XXX" in min_lista?


## Listor

När man mäter något lite mer seriöst, temperatur, längd, ljudnivå eller annat, så får man oftast inte bara ett mätvärde, utan man tar många mätvärden över tid, man får en mätserie.

Oavsett om det handlar om mätserier eller namnlistor så behövs därmed ett sätt att spara mer än ett värde i samma variabel - en lista helt enkelt.

En lista är en samling av värden, dessa värden kallas element. Varje element har en position i listan, denna position kallas index. Det går att ändra, ta bort och lägga till element i listan.

### Skapa lista
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

### Index
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

### Loopa genom lista
För att skriva ut eller komma åt alla element i en lista ett i taget kan man använda en loop, med fördel en for-loop.

#### med range()
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

#### utan range()
Här används listans variabelnamn direkt i for-loopen. Sparar rader, men helt frivilligt.
```py
ord_lista = ["skruv", "mutter", "bult", "brickor"]

# Skriv in listans variabelnamn direkt i for-loopen
for ord in ord_lista:
    print(ord, end=" ") # print med mellanslag, en rad
```
> Ger utskriften: skruv mutter bult brickor

### Lägga till i lista
Både enkel append() och loopa och appenda

## Övrigt
Vill vi ens ta upp skillnad funktione/metod i python, kanske som inforuta?

Kanske inte ta exempel på alla nedanstående, men eller jo kanske, iaf ha med som resurser, dock inte kräva dem i inlämning kanske.

Hmm, dessa två punktlistor kanske borde vara sammanfattning, och introducera de flesta av dem via exempel istället?

### Funktioner

- len()
- sum()
- max()
- min()

### Metoder

- reverse()
- sort()
- clear()
- count(a)
- index(a)
- append(a)
- remove(a)



