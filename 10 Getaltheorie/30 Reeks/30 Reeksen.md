# Reeks

Schrijf een programma dat de *langste aaneengesloten reeks niet-priemgetallen* bepaalt onder de 10000 en een korte samenvatting daarvan geeft.

	# python reeks.py
	De langste reeks niet-priemgetallen onder de 10.000 begint op ... en eindigt bij ...
	De reeks is ... lang.
	
Lees goed wat er gevraagd wordt. Onder het getal 100 moet het antwoord zijn:

	De langste reeks niet-priemgetallen onder de 100 begint op 90 en eindigt bij 96
	De reeks is 7 lang.

De opdracht luidt om de langste reeks te vinden onder het getal 10.0000.
	

## Achtergrond

We gaan nu verder werken met eerdere ideeën, en voorbeelden uit de getaltheorie bestuderen. Dit zijn problemen die handig met de computer uit te voeren zijn, omdat ze hele grote hoeveelheden klein rekenwerk vereisen. Aan ons de taak om op een efficiënte manier te noteren hoe de computer dit gaat aanpakken: programmeren dus.

Om het idee van de reeks niet-priemgetallen goed te begrijpen, schrijf je bijvoorbeeld de eerste tien priemgetallen op papier en bekijk steeds de onderlinge afstand: tussen 2 en 3 is het verschil maar één, terwijl het verschil tussen 13 en 17 vier is (wat dus betekent dat er 3 opeenvolgende getallen tussen zitten die niet-priem zijn, namelijk 14, 15 en 16).

## Specificatie

- Bepaal altijd met pen en papier je strategie en ga dus niet gelijk tikken. De 5-10 minuten die je hieraan besteedt verdien je dik terug tijdens het omzetten naar programmacode.

- Maak een programma genaamd `reeks.py` en zorg dat het volgens bovenstaand voorbeeld de juiste informatie uitprint. Gebruik je bestaande priem-zoek programma als basis  en pas het zodanig aan dat het programma eerst een *lijst* priemgetallen genereert die kleiner zijn dan het getal 10.000. Omdat je in dit geval het eindgetal kent kan je nu beter een `for-loop` gebruiken dan een `while-loop`

- Stap (loop) vervolgens door de lijst priemgetallen heen en bepaal telkens hoe lang de reeks niet-priemgetallen is tussen het huidige en het vorige priemgetal. Houd bij wat de langste reeks is.

- Zorg dat je output er netjes uitziet en dat we als gebruiker iets aan de informatie hebben: print eerst de twee niet-priemgetallen die het begin en eind van de reeks vormen en dan op de volgende regel de lengte van de reeks!

## Testen

Loop nu de specificatie bovenaan de opdracht goed door en zorg dat je programma precies zo werkt als daar beschreven is.

Nu ben je klaar om te testen:

	checkpy reeks
