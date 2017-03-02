We gaan nu verder werken met de ideeën uit het vorige hoofdstuk, en voorbeelden uit de getaltheorie bestuderen. Dit zijn problemen die handig met de computer uit te voeren zijn, omdat ze hele grote hoeveelheden klein rekenwerk vereisen. Aan ons de taak om op een efficiënte manier te noteren hoe de computer dit gaat aanpakken: programmeren dus.

Eerst twee belangrijke strategische tips bij het oplossen van een probleem met behulp van een programma:

- Een computer is niet 'slim', maar voert droog commando's uit. Het is jouw taak als programmeur om de computer de juiste dingen te laten doen.

- Bepaal altijd met pen en papier je strategie en ga dus niet gelijk tikken. De 5-10 minuten die je hieraan besteedt verdien je dik terug tijdens het omzetten naar programmacode.
 
# Reeksen priemgetallen #



Een van de resultaten van je vorige programma is de *lijst* van priemgetallen. Je hebt die lijst opgeslagen en later weer uitgeprint. Zo'n lijst kan heel handig zijn als invoer voor verdere analyse. We gaan nu proberen extra informatie uit die reeks priemgetallen te halen.

## Opgave

Schrijf een programma **priem_reeks.py** dat de *langste aaneengesloten reeks niet-priemgetallen* bepaalt. Lees dat nog maar een keer. Om dit goed te begrijpen, schrijf je bijvoorbeeld de eerste tien priemgetallen op papier. Dan tel je hoeveel ruimte er tussen elk van de priemgetallen zit: tussen 2 en 3 zit natuurlijk géén ruimte.

Om het programma dan echt te schrijven, kun je starten met de code uit de opgave hierboven. Maar pas op: in deze opgave gebruiken we niet de lijst met de eerste 1000 priemgetallen, maar alle priemgetallen onder het getal 10000. Da's net even een verschil. Kun je het beste een `for`-loop of een `while`-loop gebruiken?

Zorg ten slotte dat je output er netjes uitziet en dat we als gebruiker iets aan de informatie hebben: print eerst de twee priemgetallen waartussen de reeks ingeklemd zit en dan op de volgende regel de lengte van de reeks!



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
