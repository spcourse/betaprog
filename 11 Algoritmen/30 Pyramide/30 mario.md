# Piramide

Implementeer een programma dat een halve piramide uitprint van een door de gebruiker gegeven hoogte.

	Hoe hoog moet de piramide zijn? 5
	        # #
	      # # #
	    # # # #
	  # # # # #
	# # # # # #

	Hoe hoog moet de piramide zijn? 3
	    # #
	  # # #
	# # # #

## Het idee

Aan het einde van wereld 1-1 in Super Mario Brothers moet Mario een halve piramide van blokken beklimmen voordat hij mag springen naar een vlaggenpost. Dit ziet er zo uit:

![](mario.png)

## Specificatie

* Schrijf in een bestand genaamd `piramide.py` een programma dat de halve piramide van Mario nabouwt door middel van hekjes (`#`) en spaties.

* Vraag, om het wat interessanter te maken, eerst aan de gebruiker de gewenste **hoogte** van de halve piramide. Dit moet een positief getal zijn, niet groter dan 23.

* Als de gebruiker een hoogte invult die niet toegestaan is, dan vraag je de gebruiker opnieuw naar de hoogte. Net zo lang tot de gebruiker een goede hoogte invult.

* Je mag wél aannemen dat de gebruiker braaf gehele getallen (integers) invult. We houden dus geen rekening met bijvoorbeeld kommagetallen.

* Als de hoogte bekend is, genereer dan met behulp van `print` en één of meer loops de halve piramide.

* Let goed op dat er geen spatie staat tussen de linker onderhoek van je piramide en de linkerrand van je scherm!

## Tips

* Tel goed hoe veel spaties en hekjes er op elke regel moeten staan.

* Denk goed na over welke loopstructuur (`for` en `while`) je wilt gebruiken.

## Stappen

Is bovenstaande een beetje teveel om in één keer te maken? Doe het dan in stappen, zoals programmeurs meestal doen:

1. Pak eerst de invoer aan. Zorg dat een gebruiker een getal kan invoeren en print deze dan weer uit.

2. Pas dan het programma aan zodat het geen foutieve invoer meer accepteert, zoals in de specificatie staat.

3. Zorg dat je op dit moment een variabele `hoogte` hebt met daarin de door de gebruiker aangegeven hoogte.

4. Zorg dan dat het programma een aantal (`hoogte`) hekjes kan printen op één regel.

5. Zorg dan dat je een vierkant kunt printen: meerdere (`hoogte`) hekjes op een regel, en meerdere (`hoogte`) van zulke regels.

7. Maak nu een halve piramide door op elke regel het juiste aantal hekjes te printen.

6. Nu is het tijd om de uitvoer tot in de puntjes gelijk te maken aan de voorbeelden!

## Testen

Loop weer eerst je eigen programma na. Wat gebeurt er als je 0 voor hoogte invult? Kan je programma alle foute input afhandelen? Test dan je programma door middel van checkpy met:

	checkpy piramide
