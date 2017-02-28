# Monopoly #

![](MonopolyBordInternationaal.jpg){:.inline}{: style="width:50%"}

Bij banken, verzekeraars en het centraal planbureau worden modellen opgesteld die 
onze economie beschrijven. Alle facetten die een rol spelen krijgen een plek en met 
behulp van een computer worden verschillende scenario's doorgerekend (gesimuleerd) 
om zo risico's in te schatten op bepaalde gebeurtenissen of om het effect van
maatregelen te bekijken. 

Door de onderlinge afhankelijkheid van de parameters wordt het al snel ondoenlijk 
om het met de hand door te rekenen, zeker als het effect van bepaalde maatregelen een 
random component heeft. Met behulp van een computer gaat dat snel en kan je zelfs de 
settings vinden waarin je dingen kan optimaliseren: dat kan het maximaliseren van je 
winstkansen zijn, maar ook het minimaliseren van de kans dat je failliet gaat of een 
mix ertussenin.

We zullen in deze module een simpel voorbeeld doorrekenen: Monopoly met twee spelers.
Omdat we niet veel tijd hebben zullen we dit stap voor stap opbouwen. Voor degene die 
de smaak te pakken heeft en nu al droomt van een baan op de Risk analysis van JP Morgan 
hebben we nog wat suggesties voor extra opgaves gemaakt.

Twee dingen om alvast te weten voor je aan deze opdracht begint:

   1. Om goed te zien of je code werkt zul je vaak dingen printen. Dit stelt je in staat 
      te kijken of in elke nieuwe stap die je implementeert de 'logica' van je programma 
	  inderdaad zo werkt zoals jij het voor ogen had. Zodra je er eenmaal van overtuigd 
	  bent dat een bepaalde stap werkt kan je het print-statement weghalen (uitcommentarieren). 
	  Als je dat niet doet wordt het erg onoverzichtelijk. 
   2. Deze module werkt toe naar een redelijk complexe simulatie van Monopoly. Om te zorgen 
      dat je zelf de code goed begrijpt is het belangrijk om eenvoudig te beginnen en steeds
	  een nieuwe component of laag van complexiteit toe te voegen aan het programma. Om te zorgen 
	  dat je bij elke stap een soort rustpunt hebt ('dit werkt') zullen we bij elke opdracht 
	  vragen de code in een apart bestand op te slaan. De nieuwe opdracht begint dan ook in 
	  een nieuw bestand en is vaak een uitbreiding van de bestaande code tot dan toe.
	     

## Opdracht 1: Trump mode: 1 speler met oneindig veel geld

We gaan een groot aantal potjes Monopoly simuleren waarin we 1 speler rond laten lopen en hem 
straten laten kopen. We spelen in de zogenaamde Trump-Mode. De speler heeft oneindig veel geld, 
er is geen concurrentie.
		
Doel van deze opdracht is om te bepalen wat het gemiddeld aantal worpen is waarna alle straten 
zijn verkocht. Schrijf in een bestand `Monopoly_opdracht1.py` een functie 
`simuleer_groot_aantal_potjes_Monopoly(Npotjes)`. De variabele Npotjes geeft aan hoeveel potjes er 
gesimuleerd moeten worden. In ons geval 10000. Wanneer de functie wordt aangeroepen met 10000 
potjes moet het volgende worden uitprint: 

{: .language-python}
	Monopoly simulator: 1 speler, Trump mode 
    We hebben 10000 potjes gesimuleerd
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had
	
Om je te helpen deze opdracht te maken is het handig de volgende tussenstappen te doorlopen. 

<br>

### Tussenstap 1: dobbelsteen in Python - random integers

Het enige nieuwe Python element dat we nodig hebben is een manier om een dobbelsteen te 
gooien. Een random geheel getal tussen de 1 en de 6 dus. Dat zouden we zelf kunnen 
'bouwen' met behulp van de random() functie die we eerder hebben leren kennen, maar er 
is een speciale functie voor in Python, namelijk 'randint()'.

{: .language-python}
	import random
	dobbelsteen = random.randint(1,6) 
	
Met Monopoly gooi je met twee dobbelstenen. 

Hoewel het niet essentieel is voor de opgave is het wel goed om even te oefenen met het 
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

We beginnen nu met onze functie `simuleer_potje_Monopoly()`. Deze functie zullen we langzaam 
uitbreiden tot we in tussenstap 4 een 'echt' potje Monopoly zullen simuleren. We beginnen 
simpel door eerst een rondje te lopen met 1 speler op een Monopolybord en steeds te kijken 
op welke positie de speler zich bevindt.

Gooi steeds met twee dobbelstenen en hou de plek bij waar de speler staat op het bord. Print 
dat op het scherm. Hierbij is start positie 0, de gevangenis positie 10 en de Kalverstraat 
positie 39. 

{: .language-python}
	Na worp 1: positie 6
	Na worp 2: positie 9
	Na worp 3: positie 17
    Na worp 4: ...

Let op: zorg dat je positie altijd tussen de 0 en de 39 zit, ook al heb je meerdere rondjes gemaakt. 
Je zou hiervoor bijvoorbeeld de modulo (`%`) operator kunnen gebruiken die je kent uit module 1.

### Tussenstap 3: Enkel potje: rondlopen op het 'echte' bord (zonder te kopen)

Niet elke positie op het bord correspondeert met een straat. Niet alleen de hoekpunten natuurlijk, maar 
ook de Kans en Algemeen fonds kaarten en de belastingen zijn niet te koop. Maak een lijst (lengte 40
waarbij je voor elke positie op het bord laat zien welke waarde aan de plek op het bord verbonden is. 
De eerste 11 posities zijn dan:

{: .language-python}
   bord_waardes = [0, 60, 0, 60, 0, 200, 100, 0, 100, 100, 0, ......]

Zoek op internet op hoe het Monopoly bord verder in elkaar zit zodat je niet alleen van de eerste 11, 
maar van alle 40 velden weet voor welk geldbedrag ze te koop zijn. Als de waarde kleiner is dan 1 euro 
(of gewoon gelijk aan nul) dan is dat een zogenaamd lege straat (niet te koop).

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

Het is dus belangrijk dat we bijhouden hoeveel straten (en welke) we al in ons bezit hebben. Dit kunnen we 
doen met behulp van een lijst (weer lengte 40) waarbij je voor elke plek op het bord bijhoudt of hij in het 
bezit is van de speler. Of niet. Die lijst begint als een lijst met 40 nullen. 

{: .language-python}
    bezittingen = [0,0,0,0,.....,0,0]

Elke keer als je op een nieuwe positie komt kan je nu nagaan:

  - is er op die positie iets te koop: straat, station, electriciteit?
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
	           speler 1 heeft 1 huis in zijn/haar bezit. Er staan nu nog XXX velden te koop.

Omdat je weet hoeveel straten er in totaal te koop zijn in het spel weet je nu ook wanneer je alle 
straten in je bezit hebt. Stop met gooien als dat gebeurt en print op het scherm hoeveel beurten je 
nodig had:

{: .language-python}
    Monopoly is afgelopen: na worp XXX had de speler alle straten in zijn bezit

### Tussenstap 5: Meerdere potjes: gemiddeld aantal worpen tot einde spel

We hebben met de functie `simuleer_potje_Monopoly()` die we in tussenstap 1-4 gemaakt hebben nu 
de mogelijkheid om een enkel potje Monopoly te simuleren. Als je dit een paar keer doet zul je 
zien dat het aantal worpen dat je nodig hebt sterk varieert omdat je aan het eind van het spel 
natuurlijk maar net op dat laatste overgebleven vakje terecht moet komen. Het doel van deze 
opdracht was om uit te zoeken hoeveel worpen de speler *gemiddeld* nodig zou hebben om alle 
velden in zijn bezit te krijgen. Om deze vraag te beantwoorden zullen we een groot aantal 
potjes moeten simuleren zodat we daarvan het gemiddeld aantal worpen kunnen bepalen.

Schrijf een functie `simuleer_groot_aantal_potjes_Monopoly()` die een groot aantal potjes 
kan simuleren door steeds de functie `simuleer_potje_Monopoly()` aan te roepen. Pas ook de 
functie `simuleer_potje_Monopoly()` zodanig aan dat hij als return value het aantal worpen 
van het potje teruggeeft. Begin met 1 potje en voer dat dan op naar 2, 10 en uiteindelijk 
naar 1000 (of 10000) als je er zeker van bent dat je programma goed werkt. 
Hou voor elk potje bij in een lijst hoeveel worpen er nodig waren om alle straten in bezit 
te krijgen en maak daarvan een grafiek (histogram). Bepaal uiteindelijk ook het gemiddeld 
aantal worpen dat nodig was om alle straten te verkopen en print het op het scherm in het 
format dat aan het begin van de opgave gespecificeerd was:

{: .language-python}
	Monopoly simulator: 1 speler, Trump mode 
    We hebben 10000 potjes gesimuleerd
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had

<br>

## Opdracht 2: Realisme toevoegen: effect van startgeld

![](GoldenDollar.png){:.inline}{: style="width:20%"}

In een gewoon potje Monopoly krijg je 1500 euro startgeld en verdient je 200 euro voor elke   
keer dat je START passeert. Zo'n eindige hoeveelheid startgeld heeft invloed op de snelheid 
waarmee je nieuwe straten kan kopen en in deze opgave gaan uitzoeken welk effect dit precies 
heeft. 

Let op: we gaan nu een aanpassing aan de bestaande code maken uit Opdracht 1. Om te zorgen dat 
de code uit opdracht 1 bewaard blijft gaan we deze opdracht maken in een nieuw bestand. Maak 
een nieuw Python bestand aan, `Monopoly_opdracht2.py`, kopieer de code die je tot nu toe hebt 
en ga verder in deze nieuwe file.

Pas in je nieuwe programma de functie `simuleer_potje_Monopoly()` zodanig aan dat je elk potje 
begint met een bepaalde hoeveelheid startgeld en dat je gedurende het spel bijhoudt hoeveel 
geld je op elk moment hebt. Evalueer nu elke keer dat je op een straat terechtkomt die nog te 
koop staat of je wel genoeg geld heeft om het te kopen. De verwachting is dat je in een 
potje nu gemiddeld iets meer worpen nodig hebt om alle straten te kopen dan in opdracht 1 
waarin geld geen rol speelde.

Test je code door de speler een enorme hoeveelheid startgeld mee te geven. Met een bedrag 
van een miljoen euro reproduceer je namelijk effectief de situatie van opdracht 1. Vervolgens 
gaan we werken met realistische waardes. Begin met 3000 euro startgeld en verlaag dat steeds 
met 500 euro: 2500, 2000, 1500, 1000, 500 tot 0 euro. Simuleer voor elke keuze van het startgeld 
25000 potjes om zo nauwkeurig mogelijk het gemiddeld aantal worpen te bepalen dat nodig is om 
alle straten te kopen en maak uiteindelijk een grafiek van het gemiddeld aantal worpen als 
functie van de hoeveelheid startgeld. 

In het officiele Monopolyspel krijgt elke speler 1500 euro. Print voor die specifieke 
hoeveelheid startgeld het aantal worpen dat je nodig hebt om alle straten te kopen en 
print dat als volgt op het scherm:

{: .language-python}
	Monopoly simulator: 1 speler, 1500 euro startgeld, 25000 potjes
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had
    
Gebruik de waardes uit de grafiek om een inschatting te maken hoeveel meer 'worpen' er gedaan 
moeten worden voor elke 100 euro meer of minder startgeld.

Tip: Je mag de hoeveelheid startgeld in deze opdracht automatisch aanpassen, maar je mag 
dit ook met de hand doen door steeds een nieuwe waarde te kiezen en het gemiddeld aantal 
worpen van een groot aantal simulaties te doen. 

## Opdracht 3: Realisme toevoegen: twee spelers

In het echt wordt het spel Monopoly gespeeld door twee spelers. Doel van deze opdracht is om eerst 
te evalueren wat het voordeel is van de speler die begint met gooien en vervolgens te bestuderen hoe
we in het spel dit nadeel voor speler 2 kunnen herstellen.
 
![](Balans.png){:.inline}{: style="width:35%"}
 
Voeg eerst een tweede speler toe in je simulaties, laat beide spelers beginnen met 1500 euro startgeld 
en bepaal het verschil in aantal straten tussen speler 1 en speler 2 op het moment dat alle 
straten verkocht zijn. Dit verschil zal elk potje verschillen. Simuleer 50.000 potjes om een goede 
schatting te krijgen van het gemiddelde verschil. Je zal zien dat speler 1 inderdaad een klein voordeel 
heeft op speler 2.

De vraag is nu of en zo ja hoe we deze 'oneerlijke' situatie kunnen repareren. Een van de 'knoppen' 
waar je aan kan draaien is dit spel is de hoeveelheid startgeld die de spelers krijgen. Als speler 
2 meer startgeld krijgt kan hij iets van zijn achterstand repareren. Bepaal de hoeveelheid extra 
startgeld die we aan speler 2 moeten geven aan het begin van het spel zodat hij gemiddeld net zoveel 
straten in zijn bezit heeft als speler 1 op het moment dat alle straten verdeeld zijn ? Geef speler 2 
steeds wat meer geld (kies een paar punten) en bereken steeds het verschil. Als je een paar puten hebt 
kan je een grafiek zoals hierboven waardoor je een goede afschatting kan maken van de hoeveelheid geld 
dat het evenwicht hersteld. 

Reproduceer de grafiek en geef zowel in de grafiek als geprint naar het scherm aan hoeveel extra geld 
speler 2 moet krijgen om het evenwicht te herstellen. Het antwoord moet op 50 euro nauwkeurig zijn.

## Samenvatting

De simulatie die we hier gedaan hebben is een versimpelde versie van de vaak zeer complexe 
modellen waarmee grote financiele partijen risico's inschatten en strategieen bepalen. 
Tegelijkertijd worden deze simulaties ook gebruikt door politieke partijen om de effecten 
van hun keuzes door te rekenen in verschillende scenario's.










	
	
	
