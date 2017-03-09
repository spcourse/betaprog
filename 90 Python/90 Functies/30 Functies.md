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


## Voorbeeld 1: kwadraten berekenen

Als je van de getallen van 1 tot en met 20 de getallen zelf en hun kwadraten op het scherm wilt printen kan je gebruik maken van de standaardfunctie voor machtsverheffen uit de wiskundebibliotheek: `pow()`:

    import math

    for x in range(1,21):
        x_kwadraat = math.pow(x,2) 
        print " %d in het kwadraat = %d" % (x, x_kwadraat) 

Je kan zo'n functie ook zelf schrijven natuurlijk. We zullen die `MijnKwadraatFunctie()` noemen. De functie heeft één invoer-parameter (het getal zelf) en één uitvoer (het getal in het kwadraat).

    def MijnKwadraatFunctie(getal):
        antwoord = getal * getal
        return antwoord

    # hier begint het hoofdprogramma
    for x in range(1,21):
        x_kwadraat = MijnKwadraatFunctie(x) 
        print " %d in het kwadraat = %d" % (x, x_kwadraat) 

Eerst komt dus de definitie van de functie en zijn naam. Tussen de haakjes geef je aan welke variabelen er als invoer beschikbaar zijn: *parameters*. In dit geval de variabale `getal` waarna je het antwoord uitrekent. Dit antwoord, ook een getal, wordt vervolgens 'teruggegeven' aan de gebruiker die er vervolgens in de hoofdcode weer verder mee kan werken. In dit geval wordt het antwoord van de functie in de hoofdcode in een variabele (`x_kwadraat`) gestopt en vervolgens op het scherm geprint.

Belangrijk om hier op te merken is ook dat de naam van de variabelen in de functie zelf helemaal losstaat van de waarde en de naam van variabelen in de hoofdcode zelf. In de functie zelf weet het programma bijvoorbeeld niet wat `x` is. Het is een gesloten wereld en je kan in de functie alleen werken met de variabele `getal`. 

Bestudeer dit voorbeeld goed en probeer zelf de naam en functionaliteit te veranderen zodat het bijvoorbeeld de derdemacht van het getal uitrekent. In dit geval lijkt het een beetje overbodig om een aparte functie te maken voor een simpele opdracht, maar je zal al snel merken dat sommige stukken code die je in een functie onderbrengt al snel vrij groot kunnen worden.

## Voorbeeld 2: meerdere parameters

Je kan ook meerdere parameters meegeven. Dit is bijvoorbeeld een functie die het grootste getal bepaald aan de hand van 2 getallen die meegegeven worden aan de functie. Dus twee parameters en één return-waarde.

    def GrootsteGetal(a,b):
        grootste = 0
        if a > b:
           grootste = a
        else:
           grootste = b
        return grootste


    # hier begint het programma
    getal_1 = 126
    getal_2 = 14
    largest_number =  GrootsteGetal(getal_1, getal_2)
    print "het grootste getal = %d" % (largest_number)





## Voorbeeld 3: lijsten als invoer en uitvoer

Je kan meerdere variabelen meegeven als aparte waardes zoals hierboven, maar je kan ze ook in een lijst meegeven. Daarnaast is de uitkomst van een functie niet altijd 1 enkel getal, maar kan net zo goed een rij getallen zijn of een meer complex object.

In het onderstaande voorbeeld wordt in de hoofdcode een lijst met x-waardes geproduceerd waarna een functie gevraagd wordt alle bijbehorende y-waardes uit te rekenen (volgens de functie $$f(x)= 8x^2-5x+9$$) en in een lijst te stoppen zodat het op het scherm geplot kan worden.

    import matplotlib.pyplot as plt

    def MijnPolynoom(L_x):
        L_y = []
        for x in L_x:
            y = 8 * x * x - 5 * x + 9
            L_y.append(y)
        return L_y
 

    # hier begint het programma
    L_xwaardes = [1, 2, 3, 4, 5, 6]
    L_ywaardes = MijnPolynoom(L_xwaardes)

    plt.plot(L_xwaardes, L_ywaardes, 'g-')
    plt.show()
 

---

Het gebruik van functies bevordert de leesbaarheid van je code. Met goed
gekozen namen voor deze functies kun je snel een overzicht krijgen van wat het
geheel doet. Je leest dan bijvoorbeeld eerst alleen even snel de functienamen van een programma.

Mocht je nou jezelf betrappen op code kopiëren en plakken, probeer dan een
manier te verzinnen hoe je de code efficiënt kan hergebruiken! Gebruik dan ofwel een loop, ofwel een functie.
