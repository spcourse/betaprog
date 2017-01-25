# Datavisualisatie: meerdere grafieken tegelijk
   
We kunnen maar een zeer kleine hoevelheid mogelijkheden laten zien die `pyplot` ons biedt om data te visualiseren. Als laatste zullen we nu kijken hoe we twee grafieken naast elkaar kunnen tekenen. We zullen we dit gebruiken op het moment dat er gevraagd wordt zowel de snelheid als de positie van een object te tekenen als functie van de tijd.

Om meerdere figuren tegelijk af te beelden gebruik je het commando `subplot`. Als voorbeeld gaan we zowel de cosinus als de sinus weergeven, en in een grafiek ernaast tekenen we voor hetzelfde gebied in $$x$$ de grafiek $$x^2$$.

![](DubbelGrafiekExample.png)

Dit is de code die daarbij hoort:

    import math
    import numpy as np
    import matplotlib
    matplotlib.use('Agg')
    import matplotlib.pyplot as plt

    L_x    = []
    L_x2   = []
    L_sinx = []
    L_cosx = []

    for x in np.arange(0.,2*math.pi,0.01):
        L_x.append(x)
        L_x2.append(x*x)
        L_sinx.append(math.sin(x))
        L_cosx.append(math.cos(x))

    # gemeenschappelijke figuur (bevat beide sub-figuren)
    plt.figure(1)

    plt.subplot(121)  # ga naar subplot 1
    plt.plot(L_x, L_sinx, 'b-', L_x, L_cosx, 'r--')

    plt.subplot(122)  # ga naar subplot 2
    plt.plot(L_x, L_x2, 'g-')

    # teken beide grafieken op het scherm
    plt.savefig("naam.png")
