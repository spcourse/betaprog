# Het vermoeden van Goldbach

Het vermoeden van Goldbach is een van de oudste onopgeloste problemen in de wiskunde. Goldbach stelde:

*"Elk even getal groter dan 2 kan geschreven worden als de som van twee priemgetallen."*

Een priemgetal mag hierbij twee keer gebruikt worden. Hoewel dit inderdaad klopt voor alle getallen tot $$4\cdot10^{18}$$ is er nog altijd geen bewijs. We gaan ons steentje bijdragen. 

## Opgave

Laat met een programma **goldbach.py** zien dat alle even getallen tot 1000 inderdaad te schrijven zijn als de som van twee priemgetallen. Concreet: laat voor elk even getal ook expliciet zien dat het te schrijven is als de som van twee priemgetallen:

   	16 = ...
	18 = 5 + 13 
    20 = 3 + 17 
    22 = 5 + 17
    24 = ...

Maar nog belangrijker is natuurlijk als je een getal vindt dat *niet* aan het vermoeden (*conjecture*) van Goldbach voldoet. Zorg dat jouw programma zo'n ontdekking duidelijk op het scherm aangeeft. Bingo!

### Tips

Je mag in deze opgave de onderstaande Python constructie gebruiken die kijkt of een element wel of niet in een in een lijst voorkomt. De volgend constructie zal op het scherm printen dat 7 inderdaad een priemgetal is.

    priemen = [2,3,5,7,11]
    x = 7
	if x in priemen:
	   print "Ja, het getal %d komt voor in mijn priemlijst" % x

En als je voor elk van de getallen 1 tot en met 40 wilt bekijken of ze in de lijst staan gebruik je dus:

    priemen = [2,3,5,7,11]
    for x in range(1,41):
	    if x in priemen:
            print "Ja, het getal %d komt voor in mijn priemlijst" % x
