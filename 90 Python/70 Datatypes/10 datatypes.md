# Datatypes

Python kent verschillende datatypes om mee te werken. `string`s en `int`s heb je al voorbij zien komen. Zo zijn `string`s rijtjes van "letters" (of andere tekens) en `int`s zijn gehele getalen. Afhankelijk van het datatype waar je mee werkt, kun je verschillende operaties doen. Kijk maar naar de operatie `*`:

- `3 * 5` geeft `15` (het resultaat is een integer)
- `"vijf" * 5` geeft `"vijfvijfvijfvijfvijf"` (het resultaat is een string)

En de operatie `-`:

- `9 - 4` geeft `5` (wederom een integer)
- `"negen" - 4` geeft een foutmelding!

Niet elke operatie kan dus met alle verschillende datatypes omgaan, en afhankelijk van het type komt er een ander soort resultaat uit. 

Naast integers zijn er ook floating-point-getallen (`float`s). Hiermee kunnen we dus kommagetallen gebruiken in Python. De meeste rekenkundige operaties kun je ook met floats doen: `3.0 / 2.0` geeft `1.5`.

Kijken we naar de interactie tussen `int`s en `float`s dan zien we iets eigenaardigs. Zo is `3 * 5` nog steeds `15`, maar is `3 * 5.0` ineens `15.0`. Ook is `1 / 2` gelijk aan `0` en `1 / 2.0` gelijk aan `0.5`. Python maakt namelijk van de uitkomst van een berekening waar zowel een `int` als een `float` in voorkomen automatisch een `float`. Vaak is dit ook wat je wilt, maar niet altijd.

Kommagetallen zijn namelijk lastig te representeren. Zou je bijvoorbeeld in ons decimaal stelsel het resultaat van `1/3` uitschrijven dan krijg je `0.3333...` tot in de oneindigheid. Hoe langer we doorgaan met het schrijven van 3-en, hoe preciezer de uitkomst van `1/3`, maar we kunnen het nooit precies opschrijven. In de binaire wereld van 0-en, en 1-en komt hetzelfde probleem voor, maar dan bij `1/10`. Dit betekent dat er ergens een compromis gesloten moet worden, en we noodgedwongen een klein afrondingsfoutje maken als we rekenen met `float`s. 

Probeer in de Python-shell maar eens de volgende regel uit: `print "%.100f" % (1.0 / 10)`. Deze regel laat Python 100 cijfers achter de komma printen. Om afrondingsfouten te voorkomen is het goed om berekeningen niet zomaar in `float`s uit te voeren! Waar mogelijk gebruik je een `int`. Je kan `float`s naar `int`s converteren door middel van de `int()` functie. Zo converteer je de `float` `4.9` naar de `int` `4` met `int(4.9)`.
