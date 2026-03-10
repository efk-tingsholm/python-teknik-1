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

