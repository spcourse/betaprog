# Monte Carlo

Het is mogelijk een integraal te benaderen door gebruik te maken van random getallen.

![embed](https://player.vimeo.com/video/138378068)


1.  Definieer rechthoek dat het integratiegebied omsluit

    Definieer een gebied (vaak een rechthoek) dat het de integraalregio omsluit. Kies dus 
    een  $$x_{min}$$, $$x_{max}$$, $$y_{min}$$ en $$y_{max}$$ zodanig dat geldt 

      - $$x_{min} \leq a$$ en $$x_{max} \geq b$$

      - voor $$a \leq x \leq b$$ : $$y_{min} \leq f(x)  \leq y_{max}$$

    Kies de meest smalle rechthoek met $$x_{min} = a$$ en $$x_{max} = b$$.

2.  Gooi random punten in de rechthoek

    Gooi een groot aantal random punten $$(x_i, y_i)$$ in het rechthoek dat het integratiegebied om sluit en 
    bekijk voor elk punt of het binnen het integratiegebied valt ('goed') of erbuiten ('fout'). Hou bij welke 
    fractie van de punten in het integratiegebied valt: $$f_{goed}$$.

3.  Bepaal de integraal

    De integraal is de fractie punten die binnen de grafiek vallen keer de oppervlakte van de totale box. 
    In het geval van een rechthoek wordt dat gegeven door:

    $$
        \int_a^b f(x)~dx = f_{goed}~~\cdot~(x_{max}-x_{min})\cdot(y_{max}-y_{min})
    $$

## Voorbeeld

Van de functie $$sin(x)$$ weten we dat het op het domein $$0 < x < \pi$$ tussen de 0 en de 1 ingesloten ligt. We 
definieren dan ook een box om het integratiegebied heen en 2000 random punten gegooid. Daarvan bleek 63.15% 
(1263/2000) binnen het integratiegebied te vallen. De schatting die we maken van de integraal met behulp van 
deze 2000 punten is dan ook: 0.6315$$\pi \approx 1.984$$. Zodra dit werkt kunnen we natuurlijk ook 1 miljoen 
punten gooien in plaats van 2000. 

![](MonteCarloExample.png)
