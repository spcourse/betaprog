# Monopoly #

![](MonopolyBordInternationaal.jpg){:.inline}{: style="width:50%"}

Bij banken, verzekeraars en het centraal planbureau worden modellen opgesteld die 
onze economie beschrijven. Alle facetten die een rol spelen krijgen een plek en met 
behulp van een computer worden verschillende scenario's doorgerekend (gesimuleerd) 
om zo risico's in te schatten bij bepaalde gebeurtenissen of om het effect van
nieuwe maatregelen te onderzoeken. 

Door de onderlinge afhankelijkheid van de parameters in dat soort modellen wordt het 
al snel ondoenlijk om het met de hand door te rekenen. Zeker als het effect van 
maatregelen een random component heeft. Met behulp van een computer gaat dat snel en 
kan je zelfs de settings vinden waarin je dingen kan optimaliseren: dat kan het 
maximaliseren van je winstkansen zijn, maar ook het minimaliseren van de kans dat 
je failliet gaat. Of een mix van die scenario's.

In deze module gaan we een simpel voorbeeld doorrekenen: Monopoly met twee spelers, 
waarbij we stap voor stap meer complexiteit toevoegen. Voor degene die de smaak te 
pakken heeft en nu al droomt van een baan op de Risk-Analysis divisie van JP Morgan 
hebben we nog wat suggesties voor extra opgaves gemaakt.

Twee dingen om alvast te weten voor je aan deze opdracht begint:

   1. Om goed te zien of je code werkt zul je vaak dingen printen. Erg handig, want het 
      stelt je in staat te kijken of in elke nieuwe stap die je implementeert de 'logica' 
	  van je programma inderdaad zo werkt zoals jij het voor ogen had. Zodra je er eenmaal 
	  van overtuigd bent dat een bepaalde stap werkt kan je het print-statement weghalen 
	  (uitcommentarieren). Het printen kost veel tijd en is erg onoverzichtelijk voor 
	  uitgebreide simulaties.
   2. Deze module werkt toe naar een redelijk complexe simulatie van Monopoly. Om te zorgen 
      dat je zelf de code goed begrijpt is het belangrijk om eenvoudig te beginnen en steeds
	  een nieuwe component of laag van complexiteit toe te voegen aan het programma. Om 
	  de werkende code van elke opdracht te bewaren zullen we je bij elke nieuwe opdracht 
	  vragen het oude bestand te saven en in een nieuw bestand verder te gaan. De nieuwe 
	  opdracht, in een eigen bestand, is vaak een uitbreiding van de bestaande code tot dan toe.
	     

## Opdracht 1: Trump mode: 1 speler met oneindig veel geld

We gaan een groot aantal potjes Monopoly simuleren waarin we 1 speler rond laten lopen en hem 
straten laten kopen. We spelen in de zogenaamde Trump-Mode. De speler heeft oneindig veel geld, 
er is geen concurrentie.
		
Doel van deze opdracht is om te bepalen wat het gemiddeld aantal worpen is waarna alle straten 
zijn verkocht. Schrijf in een bestand `Monopoly_opdracht1.py` een functie 
`simuleer_groot_aantal_potjes_Monopoly(Npotjes)`. De variabele `Npotjes` geeft aan hoeveel potjes er 
gesimuleerd moeten worden. In ons geval 10000. Wanneer de functie wordt aangeroepen met 10000 
potjes moet het volgende worden uitprint: 

{: .language-python}
	Monopoly simulator: 1 speler, Trump mode 
    We hebben 10000 potjes gesimuleerd
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had
	
Om je te helpen deze opdracht te maken is het handig de volgende tussenstappen te doorlopen. 

### Tussenstap 1: dobbelsteen in Python - random integers

Het enige nieuwe Python element dat we nodig hebben is een manier om een dobbelsteen te 
gooien. Een random geheel getal tussen de 1 en de 6 dus. Dat zouden we zelf kunnen 
'bouwen' met behulp van de `random()` functie die we eerder hebben leren kennen, maar er 
is een speciale functie voor in Python, namelijk `randint()`.

{: .language-python}
	import random
	dobbelsteen = random.randint(1,6) 
	
ter volledigheid: met Monopoly gooi je elke beurt met twee dobbelstenen.

Hoewel het niet essentieel is voor de opgave is het goed om even te oefenen met het 
gooien van de dobbelstenen. Schrijf een korte functie `oefenen_met_de_dobbelstenen()` die 
duizend worpen simuleert en voor elke worp steeds twee dobbelstenen gooit. Zorg dat op het 
scherm voor elke worp het aantal ogen geprint wordt en maak duidelijk aan de gebruiker als 
er een zogenaamde 'dubbel' gegooid wordt (het aantal ogen op beide dobbelstenen is gelijk).
Houd het aantal 'dubbelen' bij en print dat aan het eind van het programma op het scherm.

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

Let op: de functie `oefenen_met_de_dobbelstenen()` heb je in de rest van de opgave niet meer 
nodig. Je kan hem in je programma laten staan, uitcommentarieren of gewoon helemaal weghalen.

### Tussenstap 2: Enkel potje: rondlopen op leeg bord

We beginnen nu onze simulatie door een nieuwe functie te definieren: `simuleer_potje_Monopoly()`
Deze functie zullen we langzaam uitbreiden tot we in tussenstap 4 een 'echt' potje Monopoly zullen 
simuleren. We beginnen simpel door eerst een rondje te lopen met 1 speler op een Monopolybord en 
steeds te kijken op welke positie de speler zich bevindt.

Gooi steeds met twee dobbelstenen en hou bij op welk veld de speler staat. Print dat op het scherm. 
Hierbij is start positie 0, de gevangenis positie 10 en de Kalverstraat positie 39. 

{: .language-python}
	Na worp 1: positie 6
	Na worp 2: positie 9
	Na worp 3: positie 17
    Na worp 4: ...

Let op: zorg dat je positie altijd tussen de 0 en de 39 zit, ook al heb je meerdere rondjes gemaakt. 
Je zou hiervoor bijvoorbeeld de modulo (`%`) operator kunnen gebruiken die je kent uit module 1.

### Tussenstap 3: Enkel potje: rondlopen op het 'echte' bord (zonder te kopen)

Niet elke positie op het bord correspondeert met een bezitting (straat, station of water/electriciteit). De 
hoekpunten van het bord zijn niet te koop en ook de Kans en Algemeen fonds kaarten en de belastingen 
zijn niet te koop. Maak een lijst (lengte 40 waarbij je voor elke positie op het bord laat zien welke 
waarde aan de plek op het bord verbonden is. De eerste 11 posities zijn dan:

{: .language-python}
    bord_waardes = [0, 60, 0, 60, 0, 200, 100, 0, 100, 100, 0, ......]

Zoek op internet op hoe het Monopoly bord verder in elkaar zit zodat je niet alleen van de eerste 11, 
maar van alle 40 velden weet voor welk geldbedrag ze te koop zijn. Als de waarde kleiner is dan 1 euro 
(of gewoon gelijk aan nul) dan is dat een zogenaamd leeg veld (niet te koop).

Voor elke positie op het bord kan je dan het volgende uitprinten:

{: .language-python}
	Na worp 1: positie  6 (straat)
	Na worp 2: positie  9 (straat)
	Na worp 3: positie 17 (leeg)
	Na worp 4: ...
	
Implementeer dit in je programma.
	
### Tussenstap 4: Enkel potje: rondlopen op het 'echte' bord (met kopen)

We gaan nu de functie `simuleer_potje_Monopoly()` uitbreiden zodat we ook straten kunnen kopen en daarbij 
bijhouden welke straten er wel/niet zijn verkocht. We beginnen daarmee door in de zogenaamde Donald Trump 
mode over het bord te stappen: we kunnen alles kopen, zijn de enige speler in het spel en we wandelen net 
zo lang door tot we alles in ons bezit hebben. De vraag die we in deze opdracht willen beantwoorden is de 
volgende: "hoe lang (hoeveel worpen) duurt het voor we alle straten in ons bezit hebben?".

Het is hierbij cruciaal dat we bijhouden hoeveel straten (en welke) we al in ons bezit hebben. Dit kunnen we 
doen met behulp van een lijst (weer lengte 40) waarbij je voor elke plek op het bord bijhoudt of hij in het 
bezit is van de speler. Of niet. Die lijst begint als een lijst met 40 nullen. 

{: .language-python}
    bezittingen = [0,0,0,0,.....,0,0]

Elke keer als je op een nieuwe positie komt kan je nu nagaan:

  - is er op die positie iets te koop: straat, station, water/electriciteit ?
  - zo ja, is het nog 'op de markt'?
   
Als je bijvoorbeeld na worp 1 op plek 3 komt en whitechapel road (of Brink in de Nederlandse versie) koopt 
kan je je lijst met bezittingen updaten. Gelijk erna ziet hij er dan zo uit:

{: .language-python}
    bezittingen = [0,0,1,0,.....,0,0]

Als er op de positie niks te koop is of als je de straat al in je bezit hebt dan gooien we gewoon 
opnieuw en wandelen we verder. Zorg dat je na elke worp waarbij je op een veld komt dat nog te koop 
is het op het scherm geprint wordt en ook gelijk hoeveel velden je in totaal in je bezit hebt na die 
aankoop.

{: .language-python}
	Na worp 1: positie  3 (straat).
	           speler 1 heeft 1 huis in zijn/haar bezit. Er staan nu nog 27 velden te koop.

Omdat je weet hoeveel straten er in totaal te koop zijn in het spel weet je nu ook wanneer je alle 
straten in je bezit hebt. Stop met gooien als dat gebeurt en print op het scherm hoeveel beurten je 
nodig had:

{: .language-python}
    Monopoly is afgelopen: na worp XXX had de speler alle straten in zijn bezit

### Tussenstap 5: Meerdere potjes: gemiddeld aantal worpen tot einde spel

We hebben met de functie `simuleer_potje_Monopoly()` die we in tussenstap 1-4 gemaakt hebben nu 
de mogelijkheid om een enkel potje Monopoly te simuleren. Als je dit een paar keer doet zul je 
zien dat het aantal worpen dat je nodig hebt om alle straten in je bezit te krijgen sterk varieert 
omdat je aan het eind van het spel natuurlijk maar net op dat laatste overgebleven vakje terecht 
moet komen. Het doel van deze opdracht was om uit te zoeken hoeveel worpen de speler *gemiddeld* 
nodig zou hebben om alle velden in zijn bezit te krijgen. Om deze vraag te beantwoorden zullen we 
een groot aantal potjes moeten simuleren zodat we daarvan het gemiddeld aantal worpen kunnen bepalen.

Schrijf een functie `simuleer_groot_aantal_potjes_Monopoly()` die, de naam zegt het al, een groot aantal potjes 
kan simuleren door steeds de functie `simuleer_potje_Monopoly()` aan te roepen. Pas ook de functie 
`simuleer_potje_Monopoly()` zo aan dat hij als return value het aantal worpen van het potje teruggeeft. Begin 
met 1 potje en voer dat dan op naar 2, 10 en uiteindelijk naar 10000 als je er zeker van bent dat je programma 
goed werkt. Hou voor elk potje bij (in een lijst) hoeveel worpen er nodig waren om alle straten in bezit te 
krijgen en maak daarvan een grafiek (histogram) als alle potjes gesimuleerd zijn. Bepaal op dat moment ook het 
gemiddeld aantal worpen dat nodig was om alle straten in je bezit te krijgen en print het op het scherm in het 
format dat aan het begin van de opgave gespecificeerd was:

{: .language-python}
	Monopoly simulator: 1 speler, Trump mode 
    We hebben 10000 potjes gesimuleerd
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had

Tip: als je een groot aantal potjes simuleert is het handig als het programma laat zien waar 
hij mee bezig is. Als er niks te zien is op het scherm vraagt de gebruiker zich anders af: 
"moet ik nog 1 minuut wachten of nog 1001 uur ? Een manier om dat op te lossen is bijvoorbeeld 
door elke 500 potjes even naar het scherm te printen dat je nu Monopoly-potje X van in totaal 
Y potjes aan het simuleren bent.
 
<br>
