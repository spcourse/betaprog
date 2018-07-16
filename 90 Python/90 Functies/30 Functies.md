# Functies

Een *functie* is een stukje code waar je een naam aan geeft, zodat het hergebruikt kan worden. Een functie die je eerder al gebruikt hebt is `len()`, om de lengte van een lijst op te vragen. En denk aan de functies `arange()`, `plot()`, enzovoort.

Je kunt ook zelf functies definiëren. Als je bijvoorbeeld een stuk code hebt geschreven om data mooi te plotten, wil je niet telkens opnieuw de hele
code kopiëren als je nieuwe data hebt.

![embed](https://player.vimeo.com/video/241704136)

(In het filmpje gebruiken we `print` zonder haakjes `()`. Omdat de cursus in Python 3 werkt, moet je nu wél haakjes toevoegen als je iets wil printen.)


## Functies die iets printen

Functies zijn dus een belangrijk aspect van leren programmeren. Het begin van
een functie wordt aangegeven met `def`, daarna komt de functienaam (die je zelf
mag kiezen), en vervolgens komen de haakjes met daartussen mogelijke parameters:

    def print_groet():
        print("Hallo")

Dit is een functie die de string `Hallo` naar je terminal print. Als je
bovenstaande *definitie* in een Python-bestand zet weet de computer dat er nu
een functie is met de naam `print_groet()`. Maar de functie is nog niet
*uitgevoerd*! Dit moet je zelf nog doen door de functie expliciet *aan te
roepen*. Dit doe je zo:

    print_groet()

(In feite gebruik je dus nu de naam van de functie, maar zet je er niet de bijbehorende code bij. Die is al vastgelegd bij de definitie.)


## Functies die iets uitrekenen

Nu weet je hoe je een functie kan maken die iets *doet*. Wat een functie ook nog kan, is iets uitrekenen en dat vervolgens *doorgeven* zodat je er verder mee kan werken in de rest van je programma. Dit doe je met het commando `return`.

Bekijk de volgende functie:

    def plus5(a):
        return 5 + a

Je ziet dat de functie `plus5(a)` een parameter `a` nodig heeft om het antwoord te kunnen berekenen. Bij `return` zie je dat er een waarde wordt teruggegeven, een waarde die uitgedrukt is in een formule `5 + a`.

Let op dat de formule pas wordt geëvalueerd op het moment dat de functie is aangeroepen met een (geldige) parameter! Het antwoord van de functie staat dus niet van te voren vast, maar hangt af van de situatie.

Om het antwoord van de functie te kunnen gebruiken in de rest van het programma, moeten we de functie *aanroepen* en het resultaat in een variabele opslaan:

    interessant_getal = plus5(13)
    print interessant_getal

Bestudeer dit voorbeeld goed en probeer zelf de naam en functionaliteit te veranderen zodat het bijvoorbeeld de derdemacht van een getal uitrekent.


## Meerdere parameters

Bekijk de volgende functie die twee argumenten nodig heeft. Deze functie bepaalt het grootste van twee getallen. We hebben twee parameters en één return-waarde.

    def grootste(a,b):
        result = 0
        if a > b:
           result = a
        else:
           result = b
        return result

    # hier begint het hoofdprogramma
    num1 = 126
    num2 = 14
    interessant = grootste(num1, num2)
    print("Het grootste getal is {}".format(interessant))


## Lijsten als invoer of uitvoer

Je kunt meerdere variabelen meegeven als aparte waardes zoals hierboven, maar je kunt ze ook in een lijst meegeven. Daarnaast is de uitkomst van een functie niet altijd een enkel getal, maar kan ook complexer zijn.

In het onderstaande voorbeeld wordt in het hoofdprogramma een lijst met x-waardes geproduceerd waarna een functie gevraagd wordt alle bijbehorende y-waardes uit te rekenen (volgens de functie $$f(x)= 8x^2-5x+9$$) en in een lijst te stoppen zodat het op het scherm geplot kan worden.

    import matplotlib
    matplotlib.use('Agg')
    import matplotlib.pyplot as plt

    def polynoom(x_en):
        y_en = []
        for x in x_en:
            y = 8 * x * x - 5 * x + 9
            y_en.append(y)
        return y_en

    # hier begint het hoofdprogramma
    x_waardes = [1, 2, 3, 4, 5, 6]
    y_waardes = polynoom(x_waardes)

    plt.plot(x_waardes, y_waardes, 'g-')
    plt.savefig("polynoom.png")


## Stijl en ontwerp

Het gebruik van functies bevordert de leesbaarheid van je code. Met goed
gekozen namen voor deze functies kun je snel een overzicht krijgen van wat het
geheel doet. Je leest dan bijvoorbeeld eerst alleen even snel de functienamen in een programma.

Functies kunnen ook een oplossing zijn als je vaak ongeveer het zelfde stukje code schrijft. Mocht je nou jezelf betrappen op code kopiëren en plakken, probeer dan een manier te verzinnen hoe je de code efficiënt kan hergebruiken! Gebruik dan een loop of een functie.
