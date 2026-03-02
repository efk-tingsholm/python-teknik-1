# Lektion 3

Program behöver också ofta kunna upprepa rader med kod, iteration. Detta sker genom att man i källkoden använder så kallade "loopar", eller iterationssatser, främst while-loop och for-loop.

## While
En while-loop upprepar en eller flera rader kod så länge som loopens villkor är sant. Att likna vid när en if-sats är sann/falsk. While-loopar är bra när man inte vet från början riktigt hur många gånger koden behöver upprepas.

```
while villkor:
    Kod som ska upprepas!
    Kan vara flera rader.
    Men indenteringen behövs..
Denna rad upprepas INTE.
```
Notera, att om villkoret är sant från början, och inte kan ändras under loopens gång så kommer loopen aldrig sluta, en s.k. oändlig loop. 

??? warning "Oändlig loop"
    Om villkoret i en loop inte kan ändras så kommer loopen att antingen inte köras alls, eller fortsätta utföras om och om igen. I nedanstående exempel upprepas loopen utan att stanna.

    ```py
    tal = 5
    while tal > 2:          # Variabeln tal kommer alltid att ha värdet 5,
        print("Hejsan!")    # och därmed alltid vara större än 2 --> loopen kör för evigt.
    ```

    Vad gör man om man fastnat i en oändlig loop? Man kan ju packa ihop och gå hem. Men ett annat bra alternativ är att stoppa programmet, brukar fungera med `ctrl + c` i konsollen i VS Code.



### Heltal från 1 till 5
Följande exempel skriver ut positiva heltal från och med 1 till och med 5, följt av ett avslutande meddelande.
```py
tal = 1
# While-loopen ser ut som if-satsen, men det står while istället för if. 
while tal <= 5: 
    print(tal)      # De rader som ska upprepas om villkoret är sant 
    tal = tal + 1   # måste vara indenterade.

# Om/när villkoret är falskt kör programmet nästa rad efter while-loopen. 
print('Loopen har avslutats') 
```
Exemplet ovan ger följande utskrift:
```
1
2
3
4
5
Loopen har avslutats
```



### Utskrift på en rad
Följande exempel skriver ut alla jämna positiva heltal mindre än 10, på en rad, skiljda av mellanslag. 

För att få utskriften på en rad och med mellanslag mellan används argumentet `end` i funktionen `print()`.

Exemplet använder också en förkortad version för att öka värdet på variabeln tal med 2. Användning av förkortad version är helt frivilligt.

??? info "Utökade tilldelningsoperatorer"
    Det är vanligt att utföra matematiska operationer på en variabel, t.ex. att addera 2 som i exemplet ovan, det är så vanligt att det finns förkortade versioner för fler tilldelningar än bara addition. Notera, helt frivilligt.

    | Lång version | Kort version | Betyder |
    |---|---|---|
    | `x = x + 2` | `x += 2` | lägg till |
    | `x = x - 2` | `x -= 2` | dra ifrån |
    | `x = x * 2` | `x *= 2` | multiplicera |
    | `x = x / 2` | `x /= 2` | dividera |


    Exempel:

    ```py
    tal = 10
    tal += 3   # samma som tal = tal + 3
    tal *= 2   # samma som tal = tal * 2
    print(tal) # 26
    ```


```py
tal = 2
while tal < 10:
    print(tal, end=" ")
    tal += 2  # Förkortad version av: tal = tal + 2
```
Exemplet ovan ger följande utskrift:
```
2 4 6 8
```

??? info "print() med end"
    `end` är ett argument som lägger till en bit text i slutet av utskriften. 
    
    Därför fungerar det att skriva ett tomt mellanslag `" "`. Det kommer alltså att läggas till ett mellanslag efter varje siffra som skrivs ut.
    
    Testa att skriva något annat. Kanske en helt tom sträng `""`. Eller varför inte `"glassbåt"`.

---


## For
For-loopar upprepar sitt innehåll ett visst antal gånger, och är därmed bra att använda när man vill upprepa något ett specifikt antal gånger, "köra loopen ett visst antal varv". 

For-loopen börjar med ordet `for`, följt av ett variabelnamn, ofta används `i`. Variabeln fungerar som en räknare, och kommer att få olika värde varje varv i loopen, ofta +1. Därefter kommer nyckelordet `in`, följt av information om vilka värden variabeln i ska ha under loopens varv.

Det sistnämnda kan uppnås med hjälp av funktionen `range()`. 

### range(stopp)
Funktionen `range()` kan anropas med ett argument, som då fungerar som övre gräns, eller "antal varv" i loopen.

```py
for i in range(6):
    print(i)
```
Exemplet ovan ger följande utskrift. Notera att loopen går 6 varv, skriver ut 6 tecken, men inte det faktiska talet 6. Samt att värdet på variabeln `i` ändras från 0 --> 1  --> 2  --> ... --> 5.
```
0
1
2
3
4
5
```
### range(start, stopp)
Funktionen range() kan också anropas med två argument, i exemplet nedan fungerar 3 som undre gräns och 10 som övre gräns. Notera att den undre gränsen är inkluderad, så 3:an skrivs ut, men inte 10.
```py
for i in range(3, 10):
    print(i, end=", ") # Både kommatecken och mellanslag mellan talen. 
```
> Utskrift: 3, 4, 5, 6, 7, 8, 9, 

### range(start, stopp, steg)
Funktionen range() kan också anropas med tre argument. Där det tredje argumentet fungerar som stegstorlek. Följande exempel börjar på 5, och ska räkna till 20, med stegstorlek på 2, alltså 5 --> 7 --> 9 osv.

```py
for i in range(5, 20, 2):
    print(i, end=" ") 
```
> Utskrift: 5 7 9 11 13 15 17 19

Notera att steget kan vara negativt, så att det blir en nedräkning istället för en uppräkning. 
```py
for i in range(15, 5, -3): # Räkna från och med 15, till 5, med steget -3.
    print(i, end=" ") 
```
> Utskrift: 15 12 9 6

## Gångertabellen
Loopar kan användas för att skriva ut tabeller av olika slag, exempelvis en gångertabell. Det går bra att använda antingen while eller for såklart. I exemplet nedan används en for-loop, och räknevariabeln `i` utnyttjas.

Nedanstående exempel skriver ut gångertabellen för talet 8. Det går självklart också bra att ta in ett tal från användaren med `input()`, men det gör vi inte här. 


```py
tal = 8
for i in range(tal): 
    print(i, "*", tal, "=", i * tal) 
```
Ger följande utskrift, notera att 0 * 8 = 0 är med, men inte 8 * 8 = 64.
```
0 * 8 = 0
1 * 8 = 8
2 * 8 = 16
3 * 8 = 24
4 * 8 = 32
5 * 8 = 40
6 * 8 = 48
7 * 8 = 56
```

Om man föredrar att ha med 64 och inte 0, så kan man ändra i funktionen `range()`.
```py
tal = 8
for i in range(1, tal + 1): # Blir alltså range(1, 9), och då får vi med 8.
    print(i, "*", tal, "=", i * tal) 
```
> Ger liknande utskrift som förra exemplet, men utan 0 och med 64 istället.



Det är också möjligt att skriva en rubrikrad till sin tabell, före loopen börjar, se nedanstående exempel:
```py
tal = 8
print("Variabel Tal Produkt")
print("--------------------")
for i in range(1, tal + 1): 
    print(i, "*", tal, "=", i * tal) 
```
Ger följande utskrift, nu har jag ju överdrivit, men det blev ju inte något vidare snyggt, kolumnerna och rubrikerna matchar ju inte alls!
```
Variabel Tal Produkt
--------------------
1 * 8 = 8
2 * 8 = 16
3 * 8 = 24
4 * 8 = 32
5 * 8 = 40
6 * 8 = 48
7 * 8 = 56
8 * 8 = 64
```

## Snygg tabell med f-sträng
I Python kan man formatera sina strängar med något som kallas f-sträng, eller formatsträngar (f-string på engelska). Med dem kan man bland annat uppnå snygga tabeller.

Utöver det blir det också lättare att skriva text med variabler i, för f-strängar låter oss skriva variabler mitt i texten utan kommatecken, så det blir lättare att läsa vad det ska stå.

Man gör en f-sträng genom att skriva bokstaven `f` framför textsträngen, alltså framför citattecknet. Sen kan man med hjälp av klammerparenteser `{...}` skriva in variabler var som helst inne i strängen.
```py
tal = 8
print(f"Min variabel tal har värdet {tal}, det är ett bra värde!")
```
> Ger utskriften: Min variabel tal har värdet 8, det är ett bra värde!

För att snygga till en tabell kan man ange hur stor bredd varje kolumn ska ta, eller ja, varje variabel som skrivs in med f-sträng, mer specifikt. Det gör man inne i klammrarna genom att skriva kolon `:` och sen vilket format man vill ha.

Exempelvis betyder `{tal:>10}` att variabeln tal ska högerjusteras i en "kolumn" som är 10 tecken bred. 

På motsvarande sätt finns `:<5` för vänsterjustering, i en kolumn med bredden 5 här i exemplet, man kan ändra siffra till önskad bredd.

Beväpnade med detta tar vi oss an åttans gångertabell igen:

```py
tal = 8
print("Tal   Variabel   Produkt")
print("------------------------")
for i in range(1, tal + 1):
    # Nu skriver vi ut varje rad i tabellen med en f-sträng.
    print(f"{tal:<3} * {i:^8} = {i * tal:>7}")
```
> En bra startpunkt för kolumnbredd är att räkna antalet bokstäver i rubrik-ordet.

Exemplet ger nedanstående utskrift, notera hur mittenkolumnen är centrerad!
```
Tal   Variabel   Produkt
------------------------
8   *    1     =       8
8   *    2     =      16
8   *    3     =      24
8   *    4     =      32
8   *    5     =      40
8   *    6     =      48
8   *    7     =      56
8   *    8     =      64
```
> Jag tänker inte argumentera att det här var det snyggaste som finns, men både vänster och högerjustering samt centrering demonstrerades!

## Summan av tal mellan a och b
Ett annat klassiskt behov är att summera tal. Exempelvis alla tal mellan 5 och 15.

Detta kan man göra med hjälp av en variabel utanför loopen, och sen addera till den variabeln för varje varv som loopen går.
```py
# Gör en variabel att spara summan i
summa = 0

# Loopa från och med 5, till 16, dvs det sista värdet i kommer vara är 15.
for i in range(5, 16):
    summa = summa + i   # För varje varv i loopen, addera i till variabeln

# Efter loopen skriv ut värdet på variabeln
print(f"Summan är {summa}!")
```
> Ger utskriften: Summan är 110!


Detta kan utvecklas till att användaren själv kan välja vilka två tal som ska använda som start och stopp
```py
# Ta in start och stopp från anv, gör om till heltal med int().
start = int(input("Ange start: "))
stopp = int(input("Ange stopp: "))

# Samma kod som ovanstående exempel, fast med variablerna start och stopp.
summa = 0
for i in range(start, stopp + 1):
    summa = summa + i

print(f"Summan är {summa}!")
```

Man är såklart inte begränsad till summa och varje tal, man skulle också kunna tänka sig att bestämma produkten av vart trejde tal mellan 5 och 20.
```py
produkt = 1
for i in range(5, 20,3):  # 5*8*11*14*17, börjar på 5, ökar med 3 varje varv.
    produkt = produkt * i

print(f"Produkten är {produkt}!")
```
> Ger utskriften: Produkten är 104720!

??? info "Snygg utskrift av stora tal"
    Stora tal kan bli svåra att läsa, som syns i exemplet ovan.
    
    Med f-strängar kan du lägga in tusentalsavskiljare som gör tal mer lättlästa.

    ```py
    n = 1234567890
    print(f"{n:,}")                  # 1,234,567,890
    print(f"{n:,}".replace(",", " ")) # 1 234 567 890
    ```

## Köra igen?
Ibland kan man ha behov av att kunna köra ett program flera gånger på rad, och helt enkelt fråga användaren om denne vill köra igen. Detta kan uppnås genom att man lägger hela programmet inne i en loop.

Det går att uppnå på lite olika sätt, men det här är ett sätt.
```py
# Gör en variabel allra först, ge den ett värde
köra_igen = "j"

# Använd variabeln köra_igen för att styra när loopen körs
while köra_igen == "j":

    # Kör all din kod du har i programmet
    print("Hej! Nu kör vi programmet...")

    # När ditt program är klart, fråga om användaren vill köra igen.
    # Om användaren skriver "j" så kommer loopen köras igen.
    köra_igen = input("Vill du köra igen? (j/n): ")

# Annars avslutas programmet.
print("Programmet avslutas.")

```

??? info "Göra input mer förlåtande (lower och strip)"
    När man frågar användaren om ett svar kan det bli lite olika, stor bokstav, liten bokstav och extra mellanslag.
    
    Dessa extra användarpåhitt kan städas bort med hjälp av funktionerna `lower()` och `strip()`.

    - `.lower()` gör om texten till små bokstäver
    - `.strip()` tar bort mellanslag i början och slutet

    ```py
    köra_igen = input("Vill du köra igen? (j/n): ").lower().strip()
    ```
    Så även om användaren nu skriver "J", så kommer versalen att göras om till gemenen (liten bokstav) "j" och allt är frid och fröjd.

---



## Inlämning 3

Du ska skriva ett program och lämna in via classroom. Du ska lämna in en fil som heter `förnamn_efternamn_inl_3.py`. Överst i filen ska du skriva följande info:

```py
# Namn: XXXX YYYY
# Klass: NATE25
```

Programmet handlar om att simulera en robot och robotens batteri över tid.

Ditt program ska:

- Ta in ett startvärde från användaren, den nivå batteriet ska ha från början, mellan 50 och 100 %. Om värdet är otillåtet kan programmet stänga ner bara, det behöver INTE fråga igen.
- Programmet ska sedan simulera att robotens batteri sjunker med 7 %-enheter per timme, och skriva ut batterinivån för varje timme, som en tabell. (Tänk: en loop där varje varv motsvarar en timme.)
- När batterinivån är 25 % eller lägre går roboten in i batterisparläge, och drar mindre energi, 3 %-enheter per timme. Så länge som roboten är i sparläge ska ett meddelande skrivas ut i tabellen, se testkörning.
- När robotens batteri når noll ska tabellen avslutas med ett meddelande om att roboten stängs av. Notera att robotens batterinivå inte ska bli negativ, utan stanna på noll.

### Testkörning
Såhär skulle det kunna se ut när man kör programmet, dina formuleringar kan självklart vara annorlunda.

```
Ange startnivå på batteriet (50-100): -200
Orimligt värde. Ange ett heltal mellan 50 och 100.
```
```
Ange startnivå på batteriet (50-100): 89

Tid(h)  Energi(%)  Meddelande
-----------------------------
0       89
1       82
2       75
3       68
4       61
5       54
6       47
7       40
8       33
9       26
10      19         SPARLÄGE (3 %/h)
11      16         SPARLÄGE (3 %/h)
12      13         SPARLÄGE (3 %/h)
13      10         SPARLÄGE (3 %/h)
14      7          SPARLÄGE (3 %/h)
15      4          SPARLÄGE (3 %/h)
16      1          SPARLÄGE (3 %/h)
17      0          Batteriet är slut. Robot stänger av...
```




??? info "Bonus: time.sleep()"
    Ibland kan det vara kul att låta en simulering gå lite långsammare, så man hinner följa vad som händer.
    I Python kan man pausa programmet med funktionen `sleep()` i modulen `time`.

    ```py
    import time

    for varv in range(5):
        print("Varv:", varv)
        time.sleep(0.5)  # paus i 0.5 sekunder
    ```

