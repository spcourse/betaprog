# Monopoly #

![](MonopolyBordInternationaal.jpg){:.inline}{: style="width:50%"}

Bij banken, verzekeraars en het centraal planbureau worden modellen opgesteld die 
onze economie beschrijven. Alle facetten die een rol spelen krijgen een plek en met 
behulp van een computer worden verschillende scenario's doorgerekend (gesimuleerd) 
om zo risico's in te schatten op bepaalde gebeurtenissen of om het effect van bepaalde
maatregelen te bekijken. 

Door de onderlinge afhankelijkheid van de parameters wordt het al snel ondoenlijk 
om het met de hand door te rekenen, zeker als het effect van bepaalde maatregelen een 
random component heeft. Met behulp van een computer gaat dat snel en kan je zelfs de 
settings vinden waarin je dingen kan optimaliseren: dat kan het maximaliseren van je 
winstkansen zijn, maar ook het minimaliseren van de kans dat je failliet gaat of een 
mix ertussenin.

We zullen in deze module een simpel voorbeeld doorrekenen: Monopoly met twee spelers.
Omdat we niet veel tijd hebben zullen we dit stap voor stap opbouwen. Voor degene die 
de smaak te pakken heeft en nu al droomt van een baan op de Risk analysis van JP Morgen 
hebben we nog wat suggesties voor extra opgaves gemaakt.

## Opdracht 1: Trump mode: 1 speler met oneindig veel geld

We gaan een groot aantal potjes Monopoly simuleren waarin we 1 speler rond laten lopen en hem 
straten laten kopen. We spelen in de zogenaamde Trump-Mode. De speler heeft oneindig veel geld, 
er is geen concurrentie.
		
Doel van deze opdracht is om te bepalen wat het gemiddeld aantal worpen is waarna alle straten 
zijn verkocht. Schrijf in een bestand `Monopoly.py` een functie waarin je  

{: .language-python}
	Monopoly simulator: 1 speler, Trump mode 
    We hebben XXX potjes gesimuleerd
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had
	
Om je te helpen deze opdracht te maken is het handig de volgende tussenstappen door te nemen.

### Tussenstap 1: dobbelsten in Python - random integers

Het enige nieuwe Python element dat we nodig hebben is een manier om een dobbelsteen te 
gooien. Een random geheel getal tussen de 1 en de 6 dus. Dat zouden we zelf kunnen 
'bouwen' met behulp van de random() functie die we eerder hebben leren kennen, maar er 
is een speciale functie voor in Python, namelijk 'randint()'.

{: .language-python}
	# from random import *
	dobbelsteen = randint(1,6) 
	
Met Monopoly gooi je met twee dobbelstenen. Begin je programma met een kleine oefening waarin
je duizend worpen simuleert en voor elke worp steeds twee dobbelstenen gooit. Zorgt dat 
op het scherm voor elke worp het aantal ogen geprint wordt en maak duidelijk aan de gebruiker 
als er een zogenaamde 'dubbel' gegooid wordt (het aantal ogen op beide dobbelstenen is gelijk).
Hou het aantal 'dubbelen' bij en print dat aan het eind van het programma op het scherm.


{: .language-python}
	worp 1: totaal van 2 dobbelstenen =  5
	worp 2: totaal van 2 dobbelstenen =  9
	worp 3: totaal van 2 dobbelstenen = 10
	        Yes, we hebben een dubbel: 5+5
	worp 4: ...
	worp 5: ...
	..
	worp 1000: totaal van 2 dobbelstenen = 3

    print "Het percentage dubbele worpen = xx,xx procent"	

### Tussenstap 2: Enkel potje: rondlopen op leeg bord

We gaan eerst rondlopen op het Monopolybord. Gooi steeds met twee dobbelstenen en hou de plek bij 
waar de speler staat op het bord. Print dat op het scherm. Hierbij is start positie 0, de gevangenis 
positie 10 en de Kalverstraat positie 39. Zorg dat je positie altijd tussen de 0 en de 39 zit, ook 
al heb je meerdere rondjes gemaakt.

{: .language-python}
	Na worp 1: positie 6
	Na worp 2: positie 9
	Na worp 3: positie 17
    Na worp 4: ...

### Tussenstap 3: Enkel potje: rondlopen op het 'echte' bord (kijken)

Niet elke positie op het correspondeert met een straat. Niet alleen de hoekpunten natuurlijk, maar ook 
de Kans en Algemeen fonds kaarten en de belastingen. Maak een array (lengte 40) waarbij je voor elke 
positie op het bord laat zien welke waarde aan de plek op het bord verbonden is. De eerste 11 posities 
zijn dan:

{: .language-python}
   L_waardes = [0, 60, 0, 60, 0, 200, 100, 0, 100, 100, 0, ......]

Voor elke positie op het bord kan je dan gelijk

{: .language-python}
	Na worp 1: positie  6 (straat)
	Na worp 2: positie  9 (straat)
	Na worp 3: positie 17 (leeg)
	Na worp 4: ...
	
### tussenstap 4: Enkel potje: rondlopen op het 'echte' bord (kopen)

We stappen over het bord als Donald Trump, dus kunnen alles kopen wat we willen en hebben geen haast. 
We wandelen net zo lang door tot we alles in ons bezit hebben. De vraag is hoe lang dit duurt. Het is dus 
belangrijk dat we bijhouden hoeveel straten (en welke) we al in ons bezit hebben. Dit kunnen we doen met 
behulp van een lijst (weer lengte 40) waarbij je voor elke plek op het bord bijhoudt of hij in je bezit 
is van de speler. Of niet. Die lijst begint als een lijst met 40 nullen. 

{: .language-python}
    L_bezit = [0,0,0,0,.....,0,0]

en elke keer als je op een nieuwe positie komt kan je nu nagaan:

    a) is er op die positie een straat of iets anders om te kopen ?
    b) zo ja, heb ik dat al in mijn bezit of is het nog 'op de markt' ?
   
Als je bijvoorbeeld na worp 1 op plek 3 komt dan ziet je ijst met bezittingen er als volgt uit.

{: .language-python}
    L_bezit = [0,0,1,0,.....,0,0]

Als er op de positie niks te kopen is of als je de straat al in je bezit hebt dan gooi je opnieuw en 
wandelen we verder. Zorg dat je na elke worp waarbij je op een veld komt dat nog te koop is het op 
het scherm geprint wordt en ook gelijk hoeveel velden je in totaal in je bezit hebt na die aankoop.

Omdat je weet hoeveel straten er in totaal te koop zijn in het spel weet je nu ook wanneer je alle 
straten in je bezit hebt. Stop mhet spel als dat gebeurt en print op het scherm hoeveel beurten je 
nodig had:

{: .language-python}
    Monopoly is afgelopen: na worp XXX had de speler alle straten in zijn bezit

### tussenstap 5: Meerdere potjes: gemiddeld aantal worpen tot einde spel

De enige stap die je nu nog rest is om een groot aantal potjes te simuleren en steeds bij te  
houden na hoeveel worpen het potje afgelopen is. Dit zal varieren omdat je aan het eid van het 
spel maar net op het laatst overgebleven veld terecht moet komen.

Simuleer 1000 (of 10000) potjes en maak een grafiek (histogram) van het aantal worpen dat nodig 
was om alle straten in het bezit te krijgen. Bepaal vervolgens ook het gemiddeld aantal worpen 
dat nodig was om alle straten te verkopen en print het op het scherm in het format dat bovenaan 
de opgave gespecificeerd is.


## Opdracht 2: Realisme toevoegen: 1500 euro startgeld

In een gewoon potje Monopoly heeft elke speler 1500 euro startgeld. Elke keer dat de speler start 
voorbij gaat krijgt hij er 200 euro bij. Neem dit stuk realisme mee en bekijk dus elke keer dat je 
op een straat terechtkomt die te koop staat of je wel genoeg geld hebt om het te kopen.

Bepaal het gemiddelde aantal worpen dat je nu nodig hebt om als speler alle straten te kopen. 

Je kan testen of jet programma werkt door met een kleine hoeveelheid geld te beginnen (500 euro bijvoorbeeld) 
waardoor je zeker in de problemen komt. Probeer een inschatting te maken van de hoeveelheid geld dat 
correspondeert met gemiddeld 1 worp minder.


## Opdracht 3: Realisme toevoegen: twee spelers










	
	
	
