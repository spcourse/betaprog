# Grafieken

Het is handig om je resultaten te visualiseren in een grafiek of zelfs een filmpje. Dit is belangrijk om aan het eind van het project je resultaten inzichtelijk te maken, maar ook tijdens het ontwikkelen van je code. Er is een standaardpakket om resultaten te visualiseren in Python: `matplotlib`. Het is een zeer omvangrijk pakket waarvan we maar een fractie nodig zullen hebben.

> Om je boodschap en conclusies goed over te brengen is het belangrijk dat je aandacht besteedt aan de presentatie zodat het voor je publiek duidelijk is. Er bestaat een enorme variatie in de manier waarop data en resultaten gevisualiseerd worden. Denk altijd na hoe je denkt dat je het best de informatie weer kan geven zodat de "gebruiker" van je grafieken de juiste conclusie trekt. Zoek vervolgens in de `matplotlib`-documentatie hoe je dat voor elkaar kunt krijgen.

## Een lijst met punten

We beginnen met het plotten van wat punten waarvan we de x-waardes $$(0,1,2,3,4,5)$$ en de y-waardes $$(0,1,4,9,16,25)$$ hebben. In dit geval is het precies de functie $$x^2$$, maar dat hoeft natuurlijk niet. Om daar een grafiek van te maken doen we het volgende:

    import matplotlib.pyplot

    # de coordinaten per punt
    x_coords = [0,1,2,3,4,5]
    y_coords = [0,1,4,9,16,25]

    # plot punten (y tegen x) met groene rondjes
    matplotlib.pyplot.plot(x_coords, y_coords, 'go')
    matplotlib.pyplot.show()

Gebruik je de online-omgeving (cs50.io)? Gebruik dan het volgende alternatieve programma:

    import matplotlib
    matplotlib.use('agg')
    import matplotlib.pyplot

    # de coordinaten per punt
    x_coords = [0,1,2,3,4,5]
    y_coords = [0,1,4,9,16,25]

    # plot punten (y tegen x) met groene rondjes
    matplotlib.pyplot.plot(x_coords, y_coords, 'go')
    matplotlib.pyplot.savefig("test.png")

(In dat geval wordt de grafiek niet direct op het scherm getoond, maar opgeslagen in een plaatje genaamd `test.png`. Als je dit plaatje dubbelklikt wordt de grafiek alsnog getoond. Gebruik je de online-omgeving? Vervang dan steeds het commando `plot()` door het commando `savefig(naam)`!)

Wat betreft de opmaak van de grafiek kiezen we voor groene rondjes als 'markers', waarmee elk punt in de grafiek wordt weergegeven: dat is wat `'go'` betekent.

![](plotje1.png)

## Afkorten

Je kunt een lange modulenaam ook een kortere naam geven bij het importeren. In het geval van `matplotlib.pyplot` kun je dan de plot-opdrachten een stuk korter opschrijven:

    # gebruik de afkorting 'plt'
    import matplotlib.pyplot as plt

    # de coordinaten per punt
    x_coords = [0,1,2,3,4,5]
    y_coords = [0,1,4,9,16,25]

    plt.plot(x_coords, y_coords, 'go')
    plt.show()

## Meerdere grafieken en bijschriften

We breiden de plot wat uit: er komt een functie $$x^3$$ bij, we gebruiken een lijngrafiek en we voegen aslabels toe en een los tekstje:

    import matplotlib.pyplot as plt

    x_values  = [0,1,2,3,4,5]
    x_squared = [0,1,4,9,16,25]
    x_cubed   = [0,1,8,27,64,125]

    # let op: grafiek met twee datasets: x_squared en x_cubed
    plt.plot(x_values, x_squared, 'go', x_values, x_cubed, 'r-')

    # voeg labels toe aan de assen
    plt.xlabel('de x-as is klein')
    plt.ylabel('de y-as ix groot', fontsize = 25)

    # voeg losse tekst toe in de grafiek
    plt.text(1.00,100., "mijn eerste plotje", color = 'blue', fontsize = 20)

    # voeg losse tekst toe met LaTeX
    plt.text(4.00,100., "$x^3$", color = 'red', fontsize = 20)

    plt.show()

![](plotje2.png)

> Tip: de formule $$x^3$$ kunnen we mooi afdrukken bij de grafiek. De formule `x^3` in de code hierboven is geschreven in de taal $$\LaTeX$$.

## Hogere resolutie

Hierboven hebben we een klein aantal punten gekozen waarbij je de waardes
zelf in moet vullen. De grafiek ziet er dan ook wat hoekig uit. Om een scherpere grafiek te krijgen kun je de computer gewoon een heleboel y-waardes laten berekenen. Als we bijvoorbeeld de functie $$sin(x)$$ willen plotten in stapjes van $$0.01$$ tussen $$0$$ en $$2\pi$$ dan knopen we de verschillende dingen die we de dingen hiervoor aan elkaar en doen we het volgende:

    import numpy as np
    import math
    import matplotlib.pyplot as plt

    x_values = []
    y_values = []

    # x loopt van 0 tot 2pi in stapjes van 0.01
    for x in np.arange(0, 2*math.pi, 0.01):
        # bereken bijbehorende y-waarde voor elke x
        y = math.sin(x)

        # voeg data toe aan de lijsten
        x_values.append(x)
        y_values.append(y)

    # teken de hele grafiek
    plt.plot(x_values, y_values, 'b-')
    plt.xlabel('x', fontsize = 20)
    plt.ylabel('sin(x)', fontsize = 20)
    plt.text(4.00, 0.50, "f(x) = sin(x)", color = 'black', fontsize = 20)
    plt.show()

![](plotje3.png)

## Grafieken naast elkaar

Als laatste zullen we nu kijken hoe we twee grafieken naast elkaar kunnen tekenen. Je kunt dit bijvoorbeeld gebruiken op het moment dat er gevraagd wordt zowel de snelheid als de positie van een object te tekenen als functie van de tijd. Die hebben erg verschillende schalen, dus dan is het netter om ze niet in één grafiek te zetten maar naast elkaar.

Als voorbeeld gaan we zowel de cosinus als de sinus weergeven, en in een grafiek ernaast tekenen we voor hetzelfde gebied in $$x$$ de grafiek $$x^2$$.

![](plotje4.png)

Dit is de code die daarbij hoort:

    import math
    import numpy as np
    import matplotlib.pyplot as plt

    l_x    = []
    l_x2   = []
    l_sinx = []
    l_cosx = []

    for x in np.arange(0.,2*math.pi,0.01):
        l_x.append(x)
        l_x2.append(x*x)
        l_sinx.append(math.sin(x))
        l_cosx.append(math.cos(x))

    # gemeenschappelijke figuur (bevat beide sub-figuren)
    plt.figure(1)

    plt.subplot(121)  # ga naar subplot 1
    plt.plot(l_x, l_sinx, 'b-', l_x, l_cosx, 'r--')

    plt.subplot(122)  # ga naar subplot 2
    plt.plot(l_x, l_x2, 'g-')

    # teken beide grafieken op het scherm
    plt.show()
