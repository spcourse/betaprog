# Reeks

Schrijf een programma dat de *langste aaneengesloten reeks niet-priemgetallen* bepaalt onder de 10.000 en daar een korte samenvatting van geeft.

	# python reeks.py
	De langste reeks niet-priemgetallen onder de 10.000 begint op ... en eindigt bij ...
	De reeks is ... lang.
	
Lees goed wat er gevraagd wordt. Onder het getal 100 moet het antwoord zijn:

	De langste reeks niet-priemgetallen onder de 100 begint op 90 en eindigt bij 96
	De reeks is 7 lang.

De opdracht luidt om de langste reeks te vinden onder het getal 10.000.

## Achtergrond

Bepaal altijd met pen en papier je strategie en ga dus niet gelijk tikken. De 5--10 minuten die je hieraan besteedt verdien je dik terug tijdens het omzetten naar programmacode.

Om het idee van de reeks niet-priemgetallen goed te begrijpen, schrijf je bijvoorbeeld de eerste tien priemgetallen op papier en bekijk steeds de onderlinge afstand: tussen 2 en 3 is het verschil maar één, terwijl het verschil tussen 13 en 17 vier is (wat dus betekent dat er 3 opeenvolgende getallen tussen zitten die niet-priem zijn, namelijk 14, 15 en 16).

## Specificatie

- Maak een programma genaamd `reeks.py` en zorg dat het volgens bovenstaand voorbeeld de juiste informatie uitprint. Gebruik je bestaande priem-zoek programma als basis, en pas het zodanig aan dat het programma eerst een *lijst* priemgetallen genereert die kleiner zijn dan het getal 10.000. Omdat je in dat geval weet waar het eindigt, kun je nu beter een `for-loop` gebruiken dan een `while-loop`.

- Stap (loop) vervolgens door de lijst priemgetallen heen en bepaal telkens hoe lang de reeks niet-priemgetallen is tussen het huidige en het vorige priemgetal. Houd bij wat de langste reeks is in een aparte variabele.

- Zorg dat je output er netjes uitziet en dat we als gebruiker iets aan de informatie hebben: print eerst de twee niet-priemgetallen die het begin en eind van de reeks vormen en dan op de volgende regel de lengte van de reeks! Zie weer het voorbeeld bovenaan de opdracht.

## Testen

Loop nu de specificatie bovenaan de opdracht goed door en zorg dat je programma precies zo werkt als daar beschreven is. Test zelf met 100 en met 10.000.

Nu ben je klaar om te testen:

	checkpy reeks
