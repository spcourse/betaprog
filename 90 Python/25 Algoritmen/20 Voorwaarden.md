# Voorwaardelijke instructies

In de voorgaande programma's schreven we scriptjes die regel voor regel van boven naar beneden werden uitgevoerd. Een soort stapsgewijze handleiding. Programma's worden interessanter als we *uitzonderingen* willen beschrijven.

Tot nu toe konden we bijvoorbeeld geen programma schrijven dat slechts geld van je bankrekening afschrijft als er ook iets opstaat (stufi-dag). Hiervoor hebben we een **conditional** nodig. In Python kun je gebruik maken van het `if`-statement. Dit ziet er in een voorbeeld als volgt uit:

    1  balance = 100
    2  expense = 30
    3  
    4  # pay expenses only if balance allows it
    5  if balance - expense > 0:
    6      balance = balance - expense
    7  
    8  print("Remaining balance:", balance)

Een `if`-statement in Python kent de volgende structuur:

    if conditie:
        code

Een **voorwaarde (condition)** kent uiteindelijk maar twee mogelijke opties. In Python zijn dit `True` en `False` (dit noemen we "boolean" waardes, naar [George Boole](https://en.wikipedia.org/wiki/Boolean_algebra#Values)). In de code hierboven is deze boolean het resultaat de expressie `balance - expense > 0`. Hier wordt gebruik gemaakt van de vergelijkingsoperator `>`. Deze operator vergelijkt twee waarden, in dit geval de uitkomst van `balance - expense` en `0`, en produceert een boolean. Afhankelijk van de uitkomst, dat kan dus zijn `True` of `False`, wordt de code die bij de `if`-statement hoort uitgevoerd.

De `:` op regel 5 hierboven laat zien dat bij de `if` een **codeblok** hoort. Dat is dus precies het deel van de code dat slechts wordt uitgevoerd als aan de voorwaarde is voldaan. Zo'n blok bestaat vaak uit meerdere regels code, en om duidelijk te maken welke regels dat zijn, gebruik je **indentatie**. Dat is een aantal spaties of tabs van de kantlijn af. In de code hierboven hebben we vier spaties gebruikt om aan te geven dat regel 6 bij het `if`-statement hoort. Omdat regel 8 weer meer naar links staat, is die regel niet meer afhankelijk van de uitkomst van de conditie op regel 5. Die regel wordt dus *onvoorwaardelijk* uitgevoerd.

## Uitzonderingen stapelen

Behalve `if`, kent Python ook de `if-else` constructie. Deze ziet er als volgt uit:

    balance = 100

    if balance >= 0:
        print("balance is positive")
    else:
        print("balance is negative")

Hiermee hebben we een manier om één stuk code uit te voeren als de conditie `True` blijkt, en een ander stuk bij `False`.

Niet elk probleem is binair. Dan is `elif` een uitkomst. `elif` is een samenvoegsel van `else` en `if`. Je kan `elif` als volgt gebruiken:

    balance = 100

    if balance >= 1000:
        print("I'm rich!")
    elif balance >= 0:
        print("At least I'm not broke.")
    else:
        print("Nope")

## Meer operatoren

Mocht je meer nodig hebben dan de vergelijkingsoperatoren hierboven:

- `==`  gelijk aan (let op: een enkele = is toekennen, een dubbele vergelijken!)
- `!=`  ongelijk aan
- `>` 	groter dan
- `>=`	groter of gelijk aan
- `<` 	kleiner dan
- `<=`	kleiner dan of gelijk aan

## Combinaties van voorwaarden

Je kunt verschillende voorwaarden combineren. Als je wilt weten of een getal zich in een bepaald bereik bevindt (bijvoorbeeld tussen de 3 en de 39) dan kun je dat doen met `and`:

    x = 15
    x_min = 3
    x_max = 39
    if x > x_min and x < x_max:
        print("het getal", x, "bevindt zich tussen", x_min, "en", x_max)

Hier zijn de drie operators om voorwaarden te combineren:

- `not` ontkenning
- `and` combinatie (allebei moeten `True` zijn)
- `or` combinatie (één van beide moet `True` zijn)
