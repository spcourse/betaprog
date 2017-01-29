# Functies

Een *functie* is een stukje code waar je een naam aan geeft, zodat het hergebruikt kan worden. Een functie die je eerder al gebruikt hebt is `len()`, om de lengte van een lijst op te vragen. En denk aan de functies `arange()`, `plot()`, enzovoort.

Je kunt ook zelf functies definiëren. Als je bijvoorbeeld een stuk code hebt geschreven om data mooi te plotten, wil je niet telkens opnieuw de hele
code kopiëren als je nieuwe data hebt.

Functies zijn dus een belangrijk aspect van leren programmeren. Het begin van
een functie wordt aangegeven met `def`, daarna komt de functienaam (die je zelf
mag kiezen), en vervolgens komen de haakjes met daartussen mogelijke parameters:

    def print_test():
        print "abcdef"

Dit is een functie die de string `abcdef` naar je terminal print. Als je
bovenstaande *definitie* in een Python-bestand zet weet de computer dat er nu
een functie is met de naam `print_test()`. Maar de functie is nog niet
*uitgevoerd*! Dit moet je zelf nog doen door de functie expliciet *aan te
roepen*. Dit doe je zo:

    print_test()

(In feite gebruik je dus nu de naam van de functie, maar zet je er niet de bijbehorende code bij.)

---

Nu gaan we de functie uitbreiden! In plaats van dat het altijd `abcdef` print
willen we *bij de aanroep* bepalen wat geprint wordt. Daarvoor introduceren we een *parameter*:

    def print_test_2(parameter_1):
        print parameter_1

We kunnen de functie op verschillende manieren aanroepen:

    print_test_2("hijkl")

of (dit heeft hetzelfde resultaat):

    variabele_1 = "hijkl"
    print_test_2(variabele_1)

(Al die verschillende namen! Het is nogal verwarrend. Probeer te begrijpen dat de naam `parameter1` strikt in de functiedefinitie gebruikt wordt, en dat deze pas bij het daadwerkelijk *aanroepen* en uitvoeren van de functie een concrete waarde aanneemt.)

Nu weet je hoe je een functie kan maken die afhankelijk van de parameter iets *doet*. Wat een functie ook nog kan, is iets uitrekenen en dat vervolgens
*teruggeven* zodat je er verder mee kan werken in de rest van je programma. Dit
doe je met het woord `return`.

Bekijk de volgende functie die twee argumenten nodig heeft. De functie telt
deze waardes op en `return`t vervolgens het resultaat.

    def add(a, b):
        c = a + b
        return c

Hier moeten dus twee waardes in (logisch bij een functie die optelt)! En er
wordt iets *teruggegeven* waar we mee door kunnen rekenen. Om dit gebruiken
moeten we de functie aanroepen en het resultaat in een variabele opslaan.

    sum = add(13, 37)

Of zo:

    a = 10
    c = 23
    result = add(a, c)

Let op! De `c` in de bovenstaande code is een andere `c` dan die in de functie!
Ze hebben niks te maken met elkaar, ze heten alleen toevallig hetzelfde. Als je
een variabele aanmaakt in een functie bestaat die alleen in de functie zelf.

---

Het gebruik van functies bevordert de leesbaarheid van je code. Met goed
gekozen namen voor deze functies kun je snel een overzicht krijgen van wat het
geheel doet. Je leest dan bijvoorbeeld eerst alleen even snel de functienamen van een programma.

Mocht je nou jezelf betrappen op code kopiëren en plakken, probeer dan een
manier te verzinnen hoe je de code efficiënt kan hergebruiken! Gebruik dan ofwel een loop, ofwel een functie.
