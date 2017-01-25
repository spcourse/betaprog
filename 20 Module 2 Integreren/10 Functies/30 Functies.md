# Functies

Bij het programmeren zul je vaak merken je een stuk code kan (of moet) hergebruiken. Zo'n stuk code kan je in een apart stuk van je programma onderbrengen als aparte entiteit (dat noemen we een *functie*). De 'echte' code wordt zo een stuk overzichtelijker en je kan dat aparte stukje functionaliteit ook gebruiken in andere programma's die je gaat schrijven. Een aantal functies die we al zijn tegengekomen zijn bijvoorbeeld de functie die de sinus van een getal berekent: de `sin()`-functie die in de wiskunde bibliotheek is ondergebracht: `math.sin()`. Zulke functies kan je zelf ook schrijven en zullen we in de opdrachten vandaag gaan doen.

In je hoofdcode kun je een functie vervolgens vragen een opdracht uit te voeren. Een functie heeft altijd invoerwaarden (de variabelen waar hij iets mee moet doen) en een uitvoerwaarde (het resultaat van het werk). De manier waarop je een functie definieert en invoer en uitvoer manipuleert worden duidelijk in onderstaande voorbeeld.

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
 

## Opdracht: nulpunten vinden van een tweedegraads-polynoom en plotten

Schrijf in een bestand `functies.py` een programma dat een functie van de vorm $$f(x)=ax^2+bx+c$$ op het scherm plot en de nulpunten vindt. Het vinden van de nulpunten (de x-waardes waarvoor geldt $$f(x)=0$$) moet in een aparte functie `nulpunten(a,b,c)` gebeuren die als parameters de parameters van de polynoom meekrijgt en de twee nulpunten in een lijst teruggeeft. Bereken de nulpunten met behulp van de abc-formule.

Roep als test de functie aan met de waarden $$a = 1$$, $$b = 2$$ en $$c = -10$$. Die polynoom heeft namelijk twee nulpunten.

> Let op dat je dus één Python-bestand maakt (`functies.py`) met daarin alleen de code voor deze opdracht. Zoals gezegd moet daar één functie in staan (`nulpunten`) en daarnaast wat testcode. Bij uitvoeren (runnen) van dit programma moet de grafiek verschijnen en moeten de nulpunten van de gegeven functie naar het scherm geprint worden.

Breid je functie nu uit zodat je functie ook raad weet met polynomen die helemaal geen nulpunten hebben. In dat geval moet je nog steeds de functie op het scherm printen, maar moet er op het scherm netjes verschijnen dat deze polynoom geen nulpunten heeft.

Extra: als je nog tijd over hebt kan je misschien de figuur 'mooi' te maken. Probeer bijvoorbeeld de polynoom zelf en de nulpunten duidelijk weer te geven op het scherm zoals in de figuur hieronder.

![](PolynoomAnalyse.png)

## Sanity check

Let op dat je alleen de volgende Python-onderdelen hebt gebruikt in je oplossingen:

- alle onderdelen van module 1
- `math.pow()`
- `def`
- `return`
- `elif` (find out what you can do with that!)

Let op! Andere functies van `math` en `numpy` mag je (nog) niet gebruiken!
