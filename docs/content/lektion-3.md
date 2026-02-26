# Lektion 3 - EJ KLAR, arbete pågår så sakteliga

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

---

### Utskrift på en rad
Följande exempel skriver ut alla jämna positiva heltal mindre än 10, på en rad, skiljda av mellanslag. Detta genom att lägga till ett argument `end` i funktionen `print()`.

Exemplet använder också en förkortad version för att öka värdet på variabeln tal med 2. Användning av förkortad version är helt frivilligt.
```py
tal = 2
while tal < 10:
    print(tal, end=" ")
    tal += 2  # Förkortad version av tal = tal + 2
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

Det sistnämnda uppnås med hjälp av funktionen `range()`. 

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


---

TODO - tankar

Teori att ta upp (kanske): 

- f-strängar
- nästlade repetitionssatser? 
- ruta med tabell på fler utökade tilldelningsoperatorer dvs += osv 
- break och continu, 

Exempel jag vill ha med?

- summera tal, typ summan av alla tal melan x och y
- Skriv ut en basic gångertabell med print(i * 5) exempelvis
- skriv ut som tabell kanske? Jag vet att det var en main-stay i planeringsstadiet iofs
- Fakultet vore kul, men kanske som en del i uppgiften?
- Köra-igen funktionalitet, alltså bara tekniken att wrappa programmet i en while
- Validering av användarinput - fråga igen tills det blir rätt

---

## Inlämning 3

### Testkörning