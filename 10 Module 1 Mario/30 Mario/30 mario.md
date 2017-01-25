# Mario

## tl;dr

Implementeer een programma dat een halve piramide uitprint van een door de gebruiker gegeven hoogte.

	Hoe hoog moet de pyramide zijn? 5
	    ##
	   ###
	  ####
	 #####
	######

	Hoe hoog moet de pyramide zijn? 3
	  ##
	 ###
	####

## Het idee

Aan het einde van wereld 1-1 in Super Mario Brothers moet Mario een halve pyramide van blokken beklimmen voordat hij mag springen naar een vlaggenpost. Dit ziet er zo uit:

![](mario.png)

## Specificatie

* Schrijf in een bestand genaamd `mario.py` een programma dat de halve pyramide van Mario nabouwt door middel van hekjes (`#`).

* Vraag eerst aan de gebruiker de hoogte van de halve piramide. Dit mag enkel een geheel positief getal zijn tussen 0 en 23. (Dat betekent: 0 en 23 wel, -1, 24 en 176 niet)

* Wanneer de gebruiker een hoogte invult die niet toegestaan is, dan vraag je de gebruiker opnieuw naar de hoogte. Net zo lang tot de gebruiker een goede hoogte invult.

* Je mag wél aannemen dat de gebruiker braaf gehele getallen (integers) invult. We houden dus geen rekening met bijvoorbeeld kommagetallen.

* Als de hoogte bekend is, genereer dan door middel van `print` en één of meer loops de halve pyramide.

* Let goed op dat er geen spatie tussen de rand van je scherm en de onderste laag van je pyramide staat!

## Hints

* Tel goed hoe veel spaties en hekjes er op elke regel moeten staan.

* Denk goed na over welke loopstructuur (`for` en `while`) je wilt gebruiken.

* In Python kun je strings vermenigvuldigen door gehele getallen (integers). Probeer maar eens `"Hello" * 3`.

* `print` in Python voegt autmatisch spaties toe als je gebruik maakt van `,`. Een alternatief is om strings aan elkaar te plakken (concatenaten) door middel van `+` zoals in `print "Geen spatie" + "hier"`.

* Deel het probleem op in delen. Zorg bijvoorbeeld eerst dat de gebruiker een getal kan invoeren. Daarna kun je kijken of je kan voorkomen dat de gebruikers foutieve input geeft, en dan de pyramide zelf.

## Testen

Loop weer eerst je eigen programma na. Wat gebeurt er als je 0 voor hoogte invult? Kan je programma alle foute input afhandelen? Test dan je programma door middel van checkpy met:

	checkpy mario
