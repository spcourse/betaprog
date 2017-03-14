# Reeks

Implementeer een programma dat de *langste aaneengesloten reeks niet-priemgetallen* bepaalt en daarover nuttige informatie aan de gebruiker geeft.

	# python reeks.py
	De langste reeks niet-priemgetallen begint op ... en eindigt bij ...
	De reeks is ... lang.

## Achtergrond

We gaan nu verder werken met eerdere ideeën, en voorbeelden uit de getaltheorie bestuderen. Dit zijn problemen die handig met de computer uit te voeren zijn, omdat ze hele grote hoeveelheden klein rekenwerk vereisen. Aan ons de taak om op een efficiënte manier te noteren hoe de computer dit gaat aanpakken: programmeren dus.

Om het idee van de reeks niet-priemgetallen goed te begrijpen, schrijf je bijvoorbeeld de eerste tien priemgetallen op papier. Dan tel je hoeveel ruimte er tussen elk van de priemgetallen zit: tussen 2 en 3 zit natuurlijk géén ruimte. Wat is de langste reeks?

## Specificatie

- Bepaal altijd met pen en papier je strategie en ga dus niet gelijk tikken. De 5-10 minuten die je hieraan besteedt verdien je dik terug tijdens het omzetten naar programmacode.

- Maak een programma genaamd `reeks.py` en zorg dat het volgens bovenstaand voorbeeld de juiste informatie uitprint.

- We moeten bij dit probleem een grens stellen, anders kunnen we steeds maar blijven zoeken. Laten we zeggen dat we tot het getal 10.000 gaan en niet verder. Genereer nu eerst een *lijst* priemgetallen die kleiner zijn dan 10.000. Kun je het beste een `for`-loop of een `while`-loop gebruiken om dit te doen?

- Loop door de lijst heen en bepaal telkens hoe lang de reeks niet-priemgetallen is tussen het huidige en het vorige priemgetal. Houd bij wat de langste is.

- Zorg dat je output er netjes uitziet en dat we als gebruiker iets aan de informatie hebben: print eerst de twee priemgetallen waartussen de reeks ingeklemd zit en dan op de volgende regel de lengte van de reeks!

## Testen

Loop nu de specificatie bovenaan de opdracht goed door en zorg dat je programma precies zo werkt als daar beschreven is.

Nu ben je klaar om te testen:

	checkpy reeks
