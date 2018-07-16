# Goldbach

Schrijf een programma dat laat zien dat het vermoeden van Goldbach correct is voor de even getallen tot en met 1000.

	# python goldbach.py
	16 = ...
	18 = 5 + 13 
	20 = 3 + 17 
	22 = 5 + 17
	24 = ...

## Achtergrond

Het vermoeden van Goldbach is een van de oudste onopgeloste problemen in de wiskunde. Goldbach stelde:

*"Elk even getal groter dan 2 kan geschreven worden als de som van twee priemgetallen."*

Een priemgetal mag hierbij ook twee keer gebruikt worden (6=3+3). Hoewel dit vermoeden inderdaad blijkt te kloppen voor alle getallen tot $$4\cdot10^{18}$$ is er nog altijd geen analytisch bewijs voor de stelling. De computer is ongeschikt om het vermoeden te bewijzen (je kunt immers niet tot oneindig tellen), maar je kan het vermoeden wel ontkrachten door een even getal te identificeren dat niet te schrijven is als de som van twee priemgetallen. We gaan ons steentje bijdragen in deze zoektocht.

## Specificatie

Laat met een programma **goldbach.py** zien dat alle even getallen tot 1000 inderdaad te schrijven zijn als de som van twee priemgetallen. Concreet: laat voor elk even getal ook *expliciet* zien (op het scherm) dat het te schrijven is als de som van twee priemgetallen, zoals in het voorbeeld hierboven.

Nog belangrijker is natuurlijk als je een getal vindt dat *niet* aan het vermoeden van Goldbach voldoet. Zorg dat jouw programma zo'n ontdekking duidelijk op het scherm aangeeft. Bingo!

## Hints

- Bepaal altijd met pen en papier je strategie en ga dus niet gelijk tikken. De 5-10 minuten die je hieraan besteedt verdien je dik terug tijdens het omzetten naar programmacode.

- Gebruik weer een lijst priemgetallen als basis. Bedenk zelf tot waar de lijst moet lopen om de even getallen tot 1000 van delers te voorzien.

- Je mag in deze opgave de onderstaande Python constructie gebruiken die kijkt of een element wel of niet in een in een lijst voorkomt. De volgend constructie zal op het scherm printen dat 7 inderdaad een priemgetal is.

		priemlijst = [2,3,5,7,11]
		x = 7
		if x in priemlijst:
		    print ("Ja, het getal {} komt voor in mijn priemlijst".format(x))

  En als je voor elk van de getallen 1 tot en met 40 wilt bekijken of ze in de lijst staan gebruik je dus:

		priemlijst = [2,3,5,7,11]
		for x in range(1,41):
		    if x in priemlijst:
		        print ("Ja, het getal {} komt voor in mijn priemlijst".format(x))

  Deze hint geven we natuurlijk niet zomaar. Er is voor deze opdracht een 'elegante' oplossing te bedenken waarin deze 
  constructie gebruikt wordt. Je kan het ook op een minder elegante (brute-force) manier oplossen natuurlijk.

## Testen

Loop nu de specificatie bovenaan de opdracht goed door en zorg dat je programma precies zo werkt als daar beschreven is.

Nu ben je klaar om te testen:

	checkpy goldbach
