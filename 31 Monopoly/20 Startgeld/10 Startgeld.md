## Opdracht 2: Realisme toevoegen: effect van startgeld

![](GoldenDollar.png){:.inline}{: style="width:20%"}

In een officieel potje Monopoly krijg je 1500 euro startgeld en verdient je 200 euro elke   
keer dat je START passeert. Zo'n eindige hoeveelheid startgeld heeft invloed op de snelheid 
waarmee je nieuwe straten kan kopen. In deze opdracht zoeken we uit welk effect dit precies 
heeft. 

Let op: we gaan nu een aanpassing aan de bestaande code maken uit opdracht 1. Om te zorgen dat 
de code uit opdracht 1 bewaard blijft gaan we deze opdracht maken in een nieuw bestand. Maak 
dus een nieuw Python bestand aan, `Monopoly_opdracht2.py`, kopieer de code die je tot nu toe 
hebt gemaakt en ga verder in deze nieuwe file.

Pas in je nieuwe programma de functie `simuleer_potje_Monopoly()` zo aan dat je elk potje 
begint met een bepaalde hoeveelheid startgeld en dat je gedurende het spel bijhoudt hoeveel 
geld je op elk moment hebt. Evalueer nu ook elke keer dat je op een veld terechtkomt die nog 
te koop staat of je wel genoeg geld heeft om het te kopen. De verwachting is dat je in een 
potje nu gemiddeld iets meer worpen nodig hebt om alle straten te kopen dan in opdracht 1 
waarin geld geen rol speelde.

Begin met 3000 euro startgeld en verlaag dat steeds met 500 euro: 2500, 2000, 1500, 1000, 500 
tot 0 euro. Simuleer voor elke keuze van het startgeld 25000 potjes om zo nauwkeurig mogelijk 
het gemiddeld aantal worpen te bepalen dat nodig is om alle straten te kopen en maak uiteindelijk 
een grafiek van het gemiddeld aantal worpen als functie van de hoeveelheid startgeld. 

In het officiele Monopolyspel krijgt elke speler 1500 euro. Print voor die specifieke 
hoeveelheid startgeld het aantal worpen dat je nodig hebt om alle straten te kopen en 
print dat als volgt op het scherm:

{: .language-python}
	Monopoly simulator: 1 speler, 1500 euro startgeld, 10000 potjes
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had
    
Gebruik het verschil tussen het gemiddeld aantal worpen met 1000 euro of 2000 euro startgeld 
om een idee te krijgen wat het effect is (aantal worpen dat het spel er korter/langer over 
doet) voor elke 100 euro meer of minder stargeld.

Een paar tipos bij deze opdracht:

   1. Je mag de hoeveelheid startgeld in deze opdracht steeds met de hand aanpassen.

   2. Je kan je code testen door de speler een enorme hoeveelheid startgeld mee te geven. Met 1
      miljoen euro creeer je namelijk effectief eenzelfde situatie als in opdracht 1 waarin 
	  geld geen rol speelde.


<br>
	