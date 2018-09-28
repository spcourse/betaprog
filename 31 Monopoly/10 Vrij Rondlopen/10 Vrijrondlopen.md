# Donald Trump edition

Schrijf een programma dat een vereenvoudigde versie van het spel Monopoly simuleert.

    Monopoly simulator: 1 speler, Trump mode
    We hebben 10000 potjes gesimuleerd
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had

## Achtergrond

We gaan een groot aantal potjes Monopoly simuleren waarin we 1 speler rond laten lopen en hem straten laten kopen. We spelen in de zogenaamde Trump-Mode. De speler heeft oneindig veel geld, er is geen concurrentie. Doel van deze opdracht is om te bepalen wat het gemiddeld aantal worpen is
waarna alle straten zijn verkocht.

Om je te helpen deze opdracht te maken is het handig de volgende tussenstappen te doorlopen.

## Dobbelstenen

Elke beurt in het spel begint met het gooien van twee dobbelstenen. Dat zijn dus twee random getallen tussen 1 en 6. Dat zouden we kunnen regelen met behulp van de `random()`-functie die we eerder hebben leren kennen, maar er wordt bij Python ook een speciale random-functie voor gehele getallen meegeleverd: `randint(start, end)`.

{: .language-python}
    import random
    dobbelsteen = random.randint(1,6)

**Schrijf** een functie `worp_met_twee_dobbelstenen()` zonder parameters die een worp met twee dobbelstenen teruggeeft. In je code zou je deze functie als volgt willen gebruiken:

      resultaat = worp_met_twee_dobbelstenen()
      print("Totaal aantal ogen van twee dobbelstenen: {}".format(resultaat))

**Schrijf** om te testen een functie `oefenen_met_de_dobbelstenen()` die duizend
worpen simuleert en voor elke worp steeds twee dobbelstenen gooit. Zorg dat op
het scherm voor elke worp het aantal ogen geprint wordt en maak duidelijk aan
de gebruiker als er een zogenaamde 'dubbel' gegooid wordt (het aantal ogen op
beide dobbelstenen is gelijk). Houd het aantal 'dubbelen' bij en print dat aan
het eind van het programma op het scherm.

{: .language-python}
    worp 1: totaal van 2 dobbelstenen =  5
    worp 2: totaal van 2 dobbelstenen =  9
    worp 3: totaal van 2 dobbelstenen = 10
            Yes, we hebben een dubbele: 5+5
    worp 4: ...
    worp 5: ...
    ..
    worp 1000: totaal van 2 dobbelstenen = 3

    print "Het percentage dubbele worpen = xx,xx procent"

Let op: de functie `oefenen_met_de_dobbelstenen()` heb je in de rest van de
opgave niet meer nodig. Je kunt hem in je programma laten staan of gewoon
helemaal weghalen.

## Rondlopen op een leeg bord

We beginnen nu onze simulatie door een nieuwe functie te definieren:
`simuleer_potje_Monopoly()` Deze functie zullen we langzaam uitbreiden tot we
een 'echt' potje Monopoly simuleren. We beginnen simpel door eerst een rondje
te lopen met één speler op een Monopolybord en steeds te kijken op welke
positie de speler zich bevindt.

Gooi steeds met twee dobbelstenen en hou bij op welk veld de speler staat.
Print dat op het scherm. Hierbij is "start" positie 0, de gevangenis positie 10
en de Kalverstraat positie 39.

    Na worp 1: positie 6
    Na worp 2: positie 9
    Na worp 3: positie 17
    Na worp 4: ...

Let op: zorg dat je positie altijd tussen de 0 en de 39 zit, ook al heb je
meerdere rondjes gemaakt. Je zou hiervoor bijvoorbeeld de modulo (`%`) operator
kunnen gebruiken die je kent uit module 1.

## Rondlopen op het 'echte' bord

Niet elke positie op het bord correspondeert met een bezitting (straat, station
of water/electriciteit). De hoekpunten van het bord zijn niet te koop en ook de
"Kans" en "Algemeen fonds" kaarten en de belastingen zijn niet te koop. Maak een
lijst van lengte 40, waarbij je voor elke positie op het bord laat zien welke
waarde aan de plek op het bord verbonden is. De eerste 11 posities zijn dan:

{: .language-python}
    bord_waardes = [0, 60, 0, 60, 0, 200, 100, 0, 100, 120, 0, ......]

Zoek op internet op hoe het Monopolybord verder in elkaar zit zodat je niet
alleen van de eerste 11, maar van alle 40 velden weet voor welk geldbedrag ze
te koop zijn. Als de waarde kleiner is dan 1 euro (of gewoon gelijk aan nul)
dan is dat een zogenaamd leeg veld (niet te koop).

Voor elke positie op het bord kan je dan het volgende uitprinten:

    Na worp 1: positie  6 (straat)
    Na worp 2: positie  9 (straat)
    Na worp 3: positie 17 (leeg)
    Na worp 4: ...

Implementeer dit in je programma.

## Rondlopen op het bord en kopen

We gaan nu de functie `simuleer_potje_Monopoly()` uitbreiden zodat we ook
straten kunnen kopen en daarbij bijhouden welke straten er wel/niet zijn
verkocht. We beginnen daarmee door in de zogenaamde Donald Trump-mode over het
bord te stappen: we kunnen alles kopen, zijn de enige speler in het spel en we
wandelen net zo lang door tot we alles in ons bezit hebben. De vraag die we in
deze opdracht willen beantwoorden is de volgende: "hoe lang (hoeveel worpen)
duurt het voor we alle straten in ons bezit hebben?".

Het is hierbij cruciaal dat we bijhouden hoeveel straten (en welke) we al in
ons bezit hebben. Dit kunnen we doen met behulp van een lijst (weer lengte 40)
waarbij je voor elke plek op het bord bijhoudt of deze in het bezit is van de
speler. Die lijst begint als een lijst met 40 nullen.

{: .language-python}
    bezittingen = [0, 0, 0, 0, ....., 0, 0]

Elke keer als je op een nieuwe positie komt dan kun je nagaan:

- is er op die positie iets te koop: straat, station, water/electriciteit ?
- zo ja, is het nog 'op de markt'?

Als je bijvoorbeeld na één worp op plek 3 komt en Whitechapel Road koopt (of
Brink, in de Nederlandse versie) dan kun je je lijst met bezittingen updaten.
Meteen daarna ziet de lijst er zo uit:

{: .language-python}
    bezittingen = [0, 0, 1, 0, ....., 0, 0]

Als er op de positie niks te koop is of als je de straat al in je bezit hebt
dan gooien we gewoon opnieuw en wandelen we verder. Zorg dat je na elke worp
waarbij je op een veld komt dat nog te koop is het op het scherm geprint wordt
en ook gelijk hoeveel velden je in totaal in je bezit hebt na die aankoop.

    Na worp 1: positie  3 (straat).
               speler 1 heeft 1 huis in zijn/haar bezit. Er staan nu nog 27 velden te koop.

Omdat je weet hoeveel straten er in totaal te koop zijn in het spel weet je nu ook wanneer je alle straten in je bezit hebt. Stop met gooien als dat gebeurt en print op het scherm hoeveel beurten je nodig had:

## Rapporteer het resultaat

Zorg nu dat de functie `simuleer_potje_Monopoly()` na afloop het **aantal
worpen** teruggeeft waarbij het potje afgelopen was. Je zou het ook direct
kunnen `print`en in de functie, maar dat is niet de bedoeling! Verderop in de
opgave gaan we namelijk een groot aantal potjes Monopoly simuleren en dan
willen we niet dat bij elke simulatie een printje verschijnt. Gebruik `return`
dus.

In je code moet het dus als volgt werken:

{: .language-python}

    aantal_worpen = simuleer_potje_Monopoly()
    print("Klaar! Na worp {} had de speler alle straten in zijn bezit".format(aantal_worpen))

## Meerdere potjes en gemiddeld aantal worpen

We hebben met de functie `simuleer_potje_Monopoly()` nu de mogelijkheid om een enkel potje Monopoly te simuleren. Als je dit een paar keer doet zul je zien dat het aantal worpen dat je nodig hebt om alle straten in je bezit te krijgen sterk varieert omdat je aan het eind van het spel natuurlijk maar net op dat laatste overgebleven vakje terecht moet komen. Het doel van deze opdracht is om uit te zoeken hoeveel worpen de speler *gemiddeld* nodig zou hebben om alle velden in zijn bezit te krijgen. Om deze vraag te beantwoorden zullen we een groot aantal potjes moeten simuleren.

Schrijf een functie `simuleer_groot_aantal_potjes_Monopoly(aantal_potjes)` die een groot aantal potjes kan simuleren door steeds de functie `simuleer_potje_Monopoly()` aan te roepen:

    for potje in range(0, aantal_potjes):
        aantal_worpen = simuleer_potje_Monopoly()

1.  Begin met 1 potje en voer dat dan op naar 2, 10 en uiteindelijk naar 10000 als je er zeker van bent dat je programma goed werkt.

2.  Hou voor elk potje bij (in een lijst) hoeveel worpen er nodig waren om alle straten in bezit te krijgen.

3.  Maak een grafiek (histogram) van die lijst als alle potjes gesimuleerd zijn.

4.  Bepaal dan ook het gemiddeld aantal worpen dat nodig was om alle straten in bezit te krijgen en print het resultaat op het scherm, in het format dat aan het begin van de opgave gespecificeerd was:

        Monopoly simulator: 1 speler, Trump mode
        We hebben 10000 potjes gesimuleerd
        Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had

Tip: als je een groot aantal potjes simuleert is het handig als het programma laat zien waar het mee bezig is. Aan de andere kant moet er niet teveel informatie over het scherm scrollen. Een manier om dat op te lossen is bijvoorbeeld door elke 500 potjes even naar het scherm te printen dat je nu Monopoly-potje X van in totaal Y potjes aan het simuleren bent.

## En dan: de uitkomst teruggeven

Zorg tot slot dat de functie `simuleer_groot_aantal_potjes_Monopoly()` nu het gemiddeld aantal worpen teruggeeft dat nodig was om alle straten in je bezit te krijgen (via `return`).

## Testen

    checkpy monopoly_opdracht1
