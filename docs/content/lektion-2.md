# Lektion 2

Program behöver kunna "välja" olika saker beroende på situation, selektion. Detta sker genom att man i källkoden använder jämförelseoperatorer som jämför olika variabler och värden med varandra.

## Jämförelser

Jämförelser ger värdet `True` eller `False`. Datatypen kallas **bool** (boolean).

### Lika med, ==
Utvärderar om två värden är likadana, notera att man har dubbla likhetstecken.

```py
ålder = 16
print(ålder == 18)
# False
```

Det går också att spara "svaret" från en jämförelse i en variabel. Och det går också bra att jämföra strängar med text istället för tal.
```py
namn = "Eva"

# Spara "svaret" från jämförelsen i en variabel 
ärEmil = namn == "Emil"

# Variabeln kan sen skrivas ut eller användas till annat
print(ärEmil)
# False
```

### Inte lika med, !=
Utvärderar om två värden är olika, och returnerar då sant.

```py
print(5 != 9)
# True

x = 12
print(12 != x)
# False
```

### Större/mindre än, < och >
Utvärderar om det första värdet är större/mindre än det andra.
```py
temp = -3
print(temp < 0)
# True

speed = 70
print(speed > 90)
# False

```

### Eller lika med, >= och <=
Utvärderar om det första värdet är större/mindre eller lika med det andra.
```py
poäng = 50
print(poäng >= 50)
# True

temp = 60
print(temp <= 60)
# True

```

!!! warning "Tilldelning och jämförelse"
    - `=` är tilldelning, `x = 5` betyder “spara 5 i x”.
    - `==` är jämförelse, `x == 5` betyder “är x lika med 5?”


## If-satser
### if
Köra kod baserat på utfallet av en jämförelse.

En if-sats ser strukturellt ut enligt följande:
```py
if villkor:
    kod som ska köras om sant

```
Notera att både kolon efter jämförelsen och att koden som kommer efteråt är indenterad, intabbad, är viktigt.


Nedan följer ett mer fungerande exempel där användaren får skriva in ett tal.

```py
# Låt användaren skriva in en temperatur, spara i variabel temp
temp = float(input("Temperatur: "))

# kolla OM värdet i temp är under noll, i så fall skriv ut att det är kallt
if temp < 0:
    print("Det är kallt!")

# Skriv alltid ut det här i slutet.
print("Klart.")

```

!!! warning "Kolon och indentering är obligatoriskt"
    I Python måste du ha `:` efter villkoret och indenterad kod på raden/raderna under, annars får du fel och programmet kan inte köras eller fungerar inte som det ska.



### else
Man kan kombinera en if med else, och då få ett alternativ för vad som ska hända om jämförelsen inte är sann. Notera att else måste ligga efter en if-sats, det går inte att använda else för sig själv.

Vi fortsätter med samma temperaturexempel som ovan, men nu med en else, här kan BARA ETT av alternativen hända. Antingen är det minusgrader, eller så är det noll/varmare.
```py
temp = float(input("Temperatur: "))
if temp < 0:
    print("Minusgrader")
else:
    print("Noll eller varmare")

```

### elif
Det går att kombinera flera villkor för att kunna nå fler än två olika utfall. Detta görs genom att kombinera if med elif, som står för "else if". Här är det viktigt att if-måste vara först, det går inte att använda elif utan if. Om man vill använda else måste else även här vara sist.

Temperaturexemplet fortsätter. Här finns det fyra olika alternativ som kan ske baserat på vad användaren skriver in, men bara ETT av alternativen kan hända. 


```py
temp = float(input("Temperatur: "))
if temp < 0:
    print("Kallt")
elif temp < 20:
    print("Svalt")
elif temp < 30:
    print("Lagom")
else:
    print("Varmt")

```
> Koden körs uppifrån och ned, så först undersöks första villkoret, sen andra, sen tredje och om inget av de stämmer så infaller else

## Fler villkor i samma if
Det kan ibland vara relevant att undersöka om ett angivet värde är inom ett tillåtet intervall, kanske att den inskrivna temperaturen inte får vara orimligt låg eller hög. Det går såklart att uppnå med hjälp av elif, men det går också att kombinera fler villkor i en if-sats.

### or
Här används or för att kombinera två villkor, om temp är mindre än -50 grader, ELLER högre än 60, skriv ut att det är orimligt.

```py
temp = float(input("Temperatur: "))
if temp < -50 or temp > 60:
    print("Orimligt mätvärde")
else:
    print("Mätvärdet verkar rimligt")
```

### and
Det går också att vända på det, och skriva en if-sats som undersöker om värdet Är i rätt intervall, d.v.s. mellan -50 OCH 60. Detta uppnås med nyckelordet and.

```py
temp = float(input("Temperatur: "))

# Skillnad, utvärderar om mätvärdet är INOM intervallet istället 
# för utanför jfr med förra exemplet.
if temp >= -50 and temp <= 60:
    print("Mätvärdet verkar rimligt")
else:
    print("Orimligt mätvärde")

```

??? info "Kortare villkor (och `not`)"
    **1) Kedjade jämförelser (kortare än `and`)**  
    Om du vill kolla att ett värde ligger i ett intervall kan du skriva så här:
    ```py
    if -50 <= temp <= 60:
        print("Rimligt")
    else:
        print("Orimligt")
    ```

    **2) `not` (vänder på ett villkor)**  
    `not` betyder “inte”. Det gör ett sant villkor falskt, och tvärtom.
    ```py
    if not (-50 <= temp <= 60):
        print("Orimligt")
    else:
        print("Rimligt")
    ```

## Nästlade if-satser
Man kan ha if-satser inuti andra if-satser. Det kan vara vettigt exempelvis om man vill göra en rimlighetskontroll först, och först om den är ok gå vidare till den jämförelse man faktiskt vill göra.

Temperaturexemplet fortsätter. Nu kontrollerar vi först om det inskrivna värdet är rimligt, sen OM det är rimligt går vi vidare till att utvärdera om det är kallt eller lagom eller nåt. Om det inte är rimligt vill man ju inte lägga mer tid och energi på det.

```py
temp = float(input("Temperatur (°C): "))

# Undersök om det är rimligt med den "yttre" if-satsen
if temp < -50 or temp > 60:
    print("Orimligt mätvärde")
else:
    # Om det blir "else", så vet vi att temperaturen är rimlig.
    # Här inne skrivs vår andra if-sats.
    if temp < 0:
        print("Kallt")
    elif temp < 20:
        print("Svalt")
    elif temp < 30:
        print("Lagom")
    else:
        print("Varmt")
```
> Tänk på den yttre if-satsen som säkerhetskontroll och den inre if-satsen som själva jobbet som ska utföras.

## Inlämning 2
Du ska skriva ett program och lämna in via classroom. Du ska lämna in en fil som heter main.py. Överst i filen ska du skriva följande info:

```py
# Namn: XXXX YYYY
# Klass: NATE25
```

Ditt program ska:

- Fråga efter din hastighet i km/h.
- Utföra en rimlighetskontroll, hastigheten måste vara större än 0 och mindre än 300 km/h.
- Beräkna bromssträckan enligt formel: (Notera att formeln kräver m/s som enhet)

    $$
    s = \frac{v^2}{2 \mu g}
    $$

    $s$ – sträcka (m)<br>
    $v$ – hastighet (m/s)<br>
    $\mu$ – friktionskoefficient (–) *Denna kan antas till 0.8 i uppgiften* <br>
    $g$ – tyngdacceleration (m/s$^2$) 

<!-- Ett litet avstånd för att göra skilland på formel och resten av punktlistan -->
<div style="margin-top: 1rem;"></div>

- Skriva ut ett meddelande som innehåller:
    - Bromssträckan (avrundad till 1 decimal den här gången).
    - Ett utlåtande om sträckan är kort/medel/lång, under 10 m för kort, under 30 m för medel, resten lång.

Stilkrav:

- Använd beskrivande variabelnamn, t.ex. fart_kmh och fart_ms.
- Ha minst en beskrivande kommentar som delar upp/förtydligar vad som händer, exempelvis # Rimlighetskontroll
    ```
    # Rimlighetskontroll
    all din kod som gör rimlighetskontroll
    ```

### Testkörning
Såhär skulle det kunna se ut när man kör programmet:
```
Vad är din hastighet? Svara i km/h: 25
Din bromssträcka är 3.1 m (kort).
```

```
Vad är din hastighet? Svara i km/h: 50
Din bromssträcka är 12.3 m (medel).
```

```
Vad är din hastighet? Svara i km/h: 250
Din bromssträcka är 306.9 m (lång).
```

```
Vad är din hastighet? Svara i km/h: -20
Orimlig hastighet. Ange ett värde mellan 0 och 300 km/h.
```

```
Vad är din hastighet? Svara i km/h: 400
Orimlig hastighet. Ange ett värde mellan 0 och 300 km/h.
```


> Din text kan självklart vara annorlunda.