# Opdracht: een appel valt van de Dom

Schrijf een functie `appel()` in een bestand **appel.py** die de beweging van de appel beschrijft als die op een hoogte van 100 meter wordt losgelaten.

![](GravityOverzicht.png)

Zorg dat je programma kleine stapjes in de tijd maakt ($$\Delta t=0.01$$
seconden) en hou steeds bij op welke hoogte de appel zich bevindt ($$x$$) en met
welke snelheid deze beweegt ($$v$$).

Bereken voor elke nieuw stapje in de tijd en in deze volgorde:

1. de kracht die op de appel werkt (F)
2. de versnelling die de appel daardoor krijgt (a)
3. de nieuwe snelheid die de appel daardoor krijgt (v)
    gebruik: $$v_{\rm nieuw} = v + a \Delta t$$
4. de nieuwe positie van de appel (x). 
    gebruik: $$x_{\rm nieuw} = x + v \Delta t$$

(Stap 1 en 2 kun je combineren, waardoor je in deze simulatie niet hoeft te weten wat de massa van de appel is!)

Je hebt dan alle informatie berekend over een bepaald punt in de tijd. Vervolgens kun je een stapje verder in de tijd maken en deze cyclus herhalen.

## Uitvoer

Zorg dat de volgende resultaten geprint worden door je programma:

1. Na hoeveel seconden raakt de appel de grond?

2. Met welke snelheid (km/uur) raakt de appel de grond?

3. Na hoeveel seconden heeft de appel een snelheid van 100 km/uur bereikt? Is
    een vallende appel daarmee sneller dan Bugatti Veyron (2.46 seconden) of niet?

De uitvoer moet heel precies zijn en alleen de gevraagde waarden bevatten elk op een aparte regel in dezelfde volgorde als hierboven. Bijvoorbeeld zo:

	000 s tot de appel de grond raakt
	000.0 km/uur is de snelheid waarmee de appel de grond raakt
	0.00 s duurt het tot de appel 100 km/uur gaat

## Tips

- Gebruik bovenstaande formule en start de appel dus op x = $${\rm R_{earth}}$$ + 100 meter. Als je wilt weten hoe hoog de appel is, gebruik dan h = x - $${\rm R_{earth}}$$.
- Let goed op het teken van de krachten en snelheden. je begint bij positieve $$x$$ en beweegt dan naar $$x=0$$ toe.
- In dit voorbeeld kan je de antwoorden ook zelf uitrekenen met behulp van pen en papier.
- Bereken alles eerst in m/s en reken dan voor punt 2 de snelheid om naar km/uur.


## Testen

	checkpy appel