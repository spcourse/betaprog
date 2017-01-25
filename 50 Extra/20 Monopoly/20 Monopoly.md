# Monopoly #

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

blabla2


## Random integers

Het enige nieuwe Python element dat we nodig hebben is een manier om een dobbelsteen te 
gooien. Een random geheel getal tussen de 1 en de 6 dus. Dat zouden we zelf kunnen 
'bouwen' met behulp van de random() functie die we eerder hebben leren kennen, maar er 
is een speciale functie voor in Python, namelijk 'randint()'.

{: .language-python}
	# from random import *
	dobbelsteen = randint(1,6) 
	
### Testopgave: rare worpen met twee dobbelstenen

Met Monopoly gooi je met twee dobbelstenen. Schrijf een Python programma `Opdracht1` waarbij 
je duizend worpen simuleert waarbij je voor elke worp steeds twee dobbelstenen gooit. Zorgt dat 
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

## Opdracht 1: rondlopen op het bord (1 speler, Trump mode)

We gaan een groot aantal potjes Monopoly simuleren waarin we 1 speler rond laten lopen en hem 
straten laten kopen. We spelen in de zogenaamde Trump-Mode. De speler heeft oneindig veel geld, 
er is geen concurrentie.

Doel van deze opdracht is om te bepalen wat het gemiddeld aantal worpen is waarna alle straten 
zijn verkocht. Schrijf in een bestand `Monopoly.py` een functie waarin je  

{: .language-python}
	Monopoly simulator: 1 speler, Trump mode 
    We hebben XXX potjes gesimuleerd
    Gemiddeld duurde het XXX worpen voor alle straten waren bezocht / verkocht
	
Om je te helpen deze opdracht te maken is het handig de volgende tussenstappen door te nemen.

### tussenstap 1: Enkel potje: rondlopen op leeg bord

We gaan eerst rondlopen op het Monopolybord. Gooi steeds met twee dobbelstenen en hou de plek bij 
waar de speler staat op het bord. Print dat op het scherm. Hierbij is start positie 0, de gevangenis 
positie 10 en de Kalverstraat positie 39. Zorg dat je positie altijd tussen de 0 en de 39 zit, ook 
al heb je meerdere rondjes gemaakt.

{: .language-python}
	Na worp 1: positie 6
	Na worp 2: positie 9
	Na worp 3: positie 17
    Na worp 4: ...


### tussenstap 2: Enkel potje: rondlopen op het 'echte' bord

Niet elke positie op het correspondeert met een straat. Niet alleen de hoekpunten natuurlijk, maar ook 
de Kans en Algemeen fonds kaarten en de belastingen. Maak een array (lengte 40) waarbij je voor elke 
positie op het bord laat zien welke waarde aan de plek op het bord verbonden is. De eerste 11 posities 
zijn dan:

{: .language-python}
   L_waardes = [0, 60, 0, 60, 0, 200, 100, 0, 100, 100, 0, ......]

Voor elke positie op het bord kan je dan gelijk checken of je op een  

{: .language-python}
	Na worp 1: positie  6 (straat)
	Na worp 2: positie  9 (straat)
	Na worp 3: positie 17 (leeg)
	Na worp 4: ...
	
### tussenstap 3: Enkel potje: rondlopen op het 'echte' bord - bijhouden wat al verkocht is

We stappen over het bord als Donald Trump, dus kunnen alles kopen wat we willen en hebben geen haast. 
We wandelen net zo lang door tot we alles in ons bezit hebben. De vraag is hoe lang dit duurt.

We moeten dus bijhouden wat in ons bezit is. Ook dat kan je doen met behulp van een lijst waarbij je 
voor elke plek op het bord bijhoudt of hij in je bezit is of niet. Die lijst (lengte 40) begint als 
een lijst waarin 40 nullen staan. 

{: .language-python}
    L_bezit = [0,0,0,0,.....,0,0]

Elke keer als je op een nieuwe positie komt kan je nu nagaan:
   a) is er op die positie een straat of iets anders om te kopen
   b) zo ja, heb ik dat al in mijn bezit of is het nog 'op de markt'
   
Als je bijvoorbeeld na worp 1 op plek 3 komt dan ziet L_bezit er als volgt uit.

{: .language-python}
    L_bezit = [0,0,1,0,.....,0,0]

Als er op de positie niks te kopen is of als je de straat al in je bezit hebt dan gooi je opnieuw en 
wandelen we verder. Door elke keer dat je een nieuwe straat in je bezit krijgt te kijken hoeveel straten 
je hebt kan je uitzoeken of je 'alles' in je bezit hebt. Je weet namelijk hoeveel velden er te koop zijn 
in het spel.

Print op het scherm zodra je alles in je bezit hebt.
{: .language-python}
    Monopoly is afgelopen: na worp XXX had de speler alle straten in zijn bezit

### tussenstap 4: Meerdere potjes: gemiddeld aantal worpen tot einde spel

De enige stap die je nu nog rest is om een groot aantal potjes te simuleren en steeds bij te  
houden na hoeveel worpen het potje afgelopen is. Dit zal varieren omdat je aan het eid van het 
spel maar net op het laatst overgebleven veld terecht moet komen.

Simuleer 1000 (of 10000) potjes en maak een grafiek (histogram) van het aantal worpen dat nodig 
was om alle straten in het bezit te krijgen. Bepaal vervolgens ook het gemiddeld aantal worpen 
dat nodig was.

 Print op het scherm zodra je alles in je bezit hebt.
{: .language-python}
    We hebben XXX potjes Monopoly gesimuleerd
    Gemiddeld heeft de speler na XXX worpen alle straten in zijn bezit
  






Verzin en manier om bij te houden of een 


![](MonopolyBordInternationaal.png)











	
	
	
