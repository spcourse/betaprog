# Pyplot

## Functies importeren

Je hebt in de vorige opgaven al kennis gemaakt met enkele ingebouwde functies van Python zoals `input`. Er zijn nog heel veel andere *functies*, maar die zijn niet standaard beschikbaar.

Voor het uitrekenen van de sinus van een getal is de functie `sin` beschikbaar. Maar als je in Python `sin(1.0)` opvraagt, dan verschijnt er een foutmelding:


    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    NameError: name 'sin' is not defined


Het gaat om de laatste regel van die foutmelding. Deze is in zo normaal mogelijk Engels geformuleerd en redelijk te begrijpen: Python kent de naam `sin` niet en kan er dus niks mee!

Om gebruik te maken van de `sin`-functie moet je zorgen dat de `math`-module en alle functies daarin beschikbaar worden in jouw programma:


    import math
    x = 0.5
    print math.sin(x)


Als je de functie `sin()` wilt gebruiken moet je nou eenmaal de module waarin de functie staat importeren. De functies die beschikbaar zijn in de math module kan je vinden in de [documentatie](https://docs.python.org/2/library/math.html). Zo zijn er [nog meer modules](https://docs.python.org/2/library/) die standaard worden meegeleverd met Python.

## Numpy

Een voorbeeld van een uitgebreidere wiskunde module is de `numpy` module. Documentatie en voorbeelden kan je vinden op <http://www.numpy.org>. We noemen meteen een handige functie die we in deze cursus een paar keer zullen gebruiken: `arange`.

Van de `for`-loops ken je nog de functie `range`. Dit is een functie die reeksen opeenvolgende nummers genereert. Zo zijn deze twee stukken code equivalent:


    # versie 1
    for i in range(1,10):
        print i

    # versie 2
    for i in [1,2,3,4,5,6,7,8,9]:
        print i


Nu werkt deze `range` functie alleen met gehele getallen. In wiskundige toepassingen willen we vaak veel kleinere stapjes nemen. Met behulp van `numpy.arange()` kan dat net zo makkelijk als met gehele getallen:


    import numpy

    for x in numpy.arange(2.0, 9.0, 0.1):
        print x


## Plotten

Het is vaak handig om je resultaten te visualiseren in een grafiek of door middel van een animatie. Dit is belangrijk om je resultaten inzichtelijk te maken, maar ook tijdens het ontwikkelen van (lees 'vechten met') je code. Tijdens het programmeren loop je vaak tegen problemen waarbij de computer niet lijkt te doen wat jij wilt. Dit zogenaamde debuggen, het uitzoeken waar je programa een andere lijn volgt dan de logica die jij erin denkt te hebben gestopt, gebeurt vaak door op bepaalde plekken iets te printen. Een alternatief is het visualiseren van de data uit je programma, omdat je dan in één oogopslag ziet waar het probleem zit.

Om je boodschap en conclusies goed over te brengen is het belangrijk dat je aandacht besteedt aan de presentatie zodat het voor je publiek duidelijk is. Neem dus de tijd om de bijbehorende grafiek netjes en duidelijk te maken.

Er is een module om resultaten te visualiseren in Python: `matplotlib`. Het is een zeer omvangrijke module waarvan we maar een fractie nodig zullen hebben. Een goede tutorial kan je [hier](http://matplotlib.org/users/pyplot_tutorial.html) vinden.

> Er bestaat een enorme variatie in de manier waarop data en resultaten gevisualiseerd worden. Denk altijd na hoe *jij* denkt dat je het best de informatie weer kan geven zodat de *gebruiker* de juiste conclusie trekt. Zoek vervolgens in de `matplotlib`-documentatie hoe je dat voor elkaar kunt krijgen.

Hieronder drie voorbeelden waarmee je de basis van `matplotlib` leert kennen. In de opgave hieronder ga je dit gebruiken. Vergeet niet de voorbeelden uit te proberen!

## Een lijst met punten

We beginnen met het plotten van wat punten waarvan we de x-waardes (0,1,2,3,4,5) en de y-waardes (0,1,4,9,16,25) hebben. In dit geval is het precies de functie x-kwadraat, maar dat hoeft natuurlijk niet. Om daar een grafiek van te maken doen we het volgende:

    import matplotlib
    matplotlib.use('Agg')
    import matplotlib.pyplot

    # de coordinaten per punt
    x_coords = [0,1,2,3,4,5]
    y_coords = [0,1,4,9,16,25]

    # plot punten (y tegen x) met groene rondjes
    matplotlib.pyplot.plot(x_coords, y_coords, "go")
    matplotlib.pyplot.savefig("myplot.png")


Hierbij is ervoor gekozen om de 'marker' (figuur waarmee elk punt weergegeven wordt) weer te geven als een groen rondje door middel van het meegeven van `"go"`. De grafiek wordt zodra je deze code runt opgeslagen in een bestand genaamd `myplot.png`. Je mag dit bestand natuurlijk ook anders noemen.

![](plotje1.png)

## Afkorten

Om lange regels te voorkomen kun je een lange modulenaam ook een kortere naam geven bij het importeren.


    import matplotlib
    matplotlib.use('Agg')
    # gebruik de afkorting 'plt'
    import matplotlib.pyplot as plt

    # de coordinaten per punt
    x_coords = [0,1,2,3,4,5]
    y_coords = [0,1,4,9,16,25]

    plt.plot(x_coords, y_coords, "go")
    plt.savefig("myplot.png")


## Meerdere grafieken en bijschriften

En natuurlijk horen er labels bij de assen, kan je 2 verschillende grafieken in 1 plot zetten en kan je zelf tekst weergeven. Om ook de grafiek x^3 in de grafiek te zetten (met rode lijnen) doe je het volgende:

    import matplotlib
    matplotlib.use('Agg')
    import matplotlib.pyplot as plt

    x_values  = [0,1,2,3,4,5]
    x_squared = [0,1,4,9,16,25]
    x_cubed   = [0,1,8,27,64,125]

    # let op: grafiek met twee datasets!
    plt.plot(x_values, x_squared, "go", x_values, x_cubed, "r-")

    plt.xlabel("de x-ax is klein")
    plt.ylabel("de y-as ix groot", fontsize = 25)

    plt.text(1.00,100., "mijn eerste plotje", color = "blue", fontsize = 20)
    plt.text(4.00,100., "$x^3$", color = "red", fontsize = 20)

    plt.savefig("myplot.png")


![](plotje2.png)

> Tip: de formule $$x^3$$ kunnen we mooi afdrukken bij de grafiek omdat we in pyplot *LaTeX* mogen gebruiken. Helaas kan dat alleen in plotjes!

## Hoge resolutie grafieken

In stap 2 hebben we een klein aantal punten gekozen waarbij je de waardes zelf in moet vullen. De grafiek ziet er dan ook niet bepaald mooi uit. Je kan natuurlijk met de computer ook zelf x-waardes en bijbehorende y-waardes berekenen. Bijvoorbeeld om de functie sin(x) te plotten in stapjes van 0.01 tussen 0 en 2*pi knopen we de verschillende dingen die we dit blok geleerd hebben aan elkaar en doen we het volgende:


    import matplotlib
    matplotlib.use('Agg')
    import matplotlib.pyplot as plt
    import numpy as np
    import math

    x_values = []   # lijst met x-waardes
    y_values = []   # lijst met y-waardes

    # x loopt van 0 tot 2pi in stapjes van 0.01
    for x in np.arange(0, 2*math.pi, 0.01):
        # bereken bijbehorende y-waarde voor elke x
        y = math.sin(x)
        
        # voeg data toe aan de lijsten
        x_values.append(x)
        y_values.append(y)

    # teken de grafiek
    plt.plot(x_values, y_values, "b-")
    plt.xlabel("x", fontsize = 20)
    plt.ylabel("sin(x)", fontsize = 20)
    plt.text(4.00, 0.50, "f(x) = sin(x)", color = "black", fontsize = 20)
    plt.savefig("myplot.png")


![](plotje3.png)
