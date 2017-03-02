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

* Vraag, om het wat interessanter te maken, eerst aan de gebruiker de gewenste hoogte van de halve piramide. Dit moet een positief getal zijn, niet groter dan 23.

* Als de gebruiker een hoogte invult die niet toegestaan is, dan vraag je de gebruiker opnieuw naar de hoogte. Net zo lang tot de gebruiker een goede hoogte invult.

* Je mag wél aannemen dat de gebruiker braaf gehele getallen (integers) invult. We houden dus geen rekening met bijvoorbeeld kommagetallen.

* Als de hoogte bekend is, genereer dan met behulp van `sys.stdout.write` en één of meer loops de halve pyramide.

* Let goed op dat er geen spatie staat tussen de linker onderhoek van je pyramide en de linkerrand van je scherm staat!

## Hints

* Tel goed hoe veel spaties en hekjes er op elke regel moeten staan.

* Denk goed na over welke loopstructuur (`for` en `while`) je wilt gebruiken.

* Deel het probleem op in delen. Zorg bijvoorbeeld eerst dat de gebruiker een getal kan invoeren. Daarna kun je kijken of je kan voorkomen dat de gebruikers foutieve input geeft, en dan de pyramide zelf.

## Testen

Loop weer eerst je eigen programma na. Wat gebeurt er als je 0 voor hoogte invult? Kan je programma alle foute input afhandelen? Test dan je programma door middel van checkpy met:

	checkpy mario
