# Loops

Soms is het handig om van een hele reeks getallen te bepalen of ze aan een bepaalde eis voldoen. Omdat zulk "dom werk" precies is wat een computer zo goed kan, is dat een basiselement in bijna alle programmeertalen. We noemen dit een *loop*.

## Herhaling

Als we tien keer iets willen doen, dan ziet het er bijvoorbeeld zo uit:

	for x in range(1, 11):
		print "hallo"

We gebruiken hier het commando `range()` met een begingetal en eindgetal om aan te geven hoe vaak de loop uitgevoerd zal worden. Daarbij telt Python van het begin *tot* het einde---dus niet *tot en met*!

Verder zie je dat we net als bij `if` weer kunnen inspringen om duidelijk te maken welke instructies bij de loop horen: vier spaties vóór de `print`-instructie. Dat is dus precies de instructie die meerdere malen uitgevoerd gaat worden.

## Tellen

In het voorbeeld hierboven wordt een regel code tien keer herhaald. Dat werkt al heel efficiënt (het zijn maar twee regels code), maar vaak willen we tijdens het herhalen ook iets tellen, zodat we bijvoorbeeld weten hoe ver we zijn. Stel dat we bijvoorbeeld de getallen van 1 tot en met 10 op het scherm willen printen en dan aangeven dat we klaar zijn:

	for getal in range(1,11):
    	print getal
	print "Ik ben klaar" 

Deze loop werkt met een *variabele* genaamd `getal` om voor elke stap een nieuwe waarde vast te houden. Als de loop begint zal de variabele `getal` op 1 gesteld worden en daarna worden de handelingen uitgevoerd die in het programma beschreven staan. Als alle handelingen van de loop uitgevoerd zijn gaat het programma terug naar de beginregel bij `for`, en zet nu de variabele `getal` op 2. Vervolgens worden wederom alle handelingen uitgevoerd.

![embed](https://player.vimeo.com/video/179484836?byline=0&portrait=0)

## Rekenen

Zoals je hierboven zag, kun je in de loop naar de variabele `getal` verwijzen om iets uit te printen. Je kunt de variabele ook gebruiken als onderdeel van een herhalende berekening. Als je bijvoorbeld de som van alle getallen tot en met 20 wil uitrekenen en het resultaat vervolgens op het scherm wilt printen werkt dat als volgt:

    som = 0
	for getal in range(1,21):
    	som = som + getal
	print "De som van de getallen van 1 tot en met 20 is %d" % (som) 

Voordat we over de getallen *loopen* zetten we een variabele `som` op 0. Die gebruiken we om tijdens de loop het totaal bij te houden.

Dan gaan we `for`-loop in. We tellen bij elke stap de waarde van `getal` op bij de variabele `som`. Zoals gebruikelijk in een `for`-loop, verandert `getal` bij elke stap. Nadat we zo alle getallen hebben doorlopen, printen we de uiteindelijke waarde van de variabele `som`. Let op: die `print`-opdracht staat niet in de loop, anders wordt deze ook twintig keer uitgevoerd! Maar, probeer gerust uit of dit inderdaad zo werkt.

## Een loop met een voorwaarde

Je kunt tijdens een loop de getallen ook verschillend behandelen. Als we bijvoorbeeld de som van de <b>even</b> getallen tussen 1 en 20 willen printen kunnen we een `if`-statement gebruiken. 

    som = 0
	for getal in range(1,21):
        if getal % 2 == 0:
           som = som + getal
	print "De som van de even getallen van 1 tot en met 20 is %d" % (som)

We gebruiken in dit stukje code ook de `%` (*modulo-operator*) om te bepalen of een getal een veelvoud is van 
2. De modulo-operator is werkt als volgt: `y % x` geeft je de *rest* van de deling als je het getal `y` door `x` hebt gedeeld. De formule `7 % 2` levert dus 1 op; `35 % 8` geeft 3.. Zo'n bouwsteen als de modulo-operator kan je ook prima inzetten om te kijken of een getal een veelvoud is van een ander getal. Als `679875 % 37` precies gelijk is aan 0 betekent dat dat 679875 een veelvoud is van 37. 

In het voorbeeld hierboven testen we voor elk van de getallen of het een even getal is (rest 0 als je door 2 deelt). *Als dat zo is* tellen we het getal op bij de variabele `som`. Aan het eind van de loop printen we de waarde weer op het scherm. Alle oneven getallen worden dus helemaal genegeerd.

> Let op dit detail: we gebruiken `==` om te kijken of twee getallen aan elkaar gelijk zijn. Het antwoord daarop is 'waar' of 'niet waar'. Een veelvoorkomende fout is dat hier een enkele `=` gebruikt wordt. Bestudeer dus goed het verschil tussen die twee operatoren.

## Variabelen nuttig gebruiken

Dit stukje code rekent heel specifiek de som van de even getallen van 1 tot en met 20 uit. 

    som = 0
	for getal in range(1, 21):
        if getal % 2 == 0:
           print "Yes! %d is een even getal" % getal
           som = som + getal
	print "de som van de even getallen van 1 tot en met 20 is %d" % (som)

Stel dat we het programma nu gaan aanpassen om de even getallen van 1 tot en met 88 op te tellen, dan moeten we het programma op *twee* plekken aanpassen. Kopieer bovenstaande code maar eens en pas deze aan zodat deze tot 88 telt en zinvolle uitvoer geeft. Bij een klein stukje code gaat zo'n aanpassing nog wel, maar bij een groter probleem merk bepaalde informatie vaak in de code voorkomt en zorgvuldig aangepast moet worden. Grote kans op fouten!

Zorg daarom dat je, nadat je het specifieke probleem hebt opgelost, je code zo universeel mogelijk maakt. Het onderstaande stukje code rekent de som uit van de even getallen van 1 tot en met `max_getal`. Die variabele hoef je dus alleen in het begin van je code een waarde te geven (20, 138613 of in dit geval 88) en verder zie je dat getal nergens terug komen. De informatie wordt via de variabele `max_getal` doorgegeven naar alle plekken waar deze nodig is.

    som = 0
    max_getal = 88
	for getal in range(1, max_getal+1):
        if getal % 2 == 0:
           print "Yes! %d is een even getal" % getal
           som = som + getal
	print "de som van de even getallen van 1 tot en met %d is %d" % (max_getal, som)

## Stapgrootte van een loop

Je kunt met `range` ook de stapgrootte opgeven. `for` telt dan zoals voorheen van begin tot einde, en neemt niet stappen van 1, maar van de grootte die jij hebt ingesteld. Dit ziet er zo uit:

    for getal in range(1, 100, 10):
       ...

Elke stap in de `for`-loop zal dan steeds 10 verder zijn dan de vorige. Denk even na welke stappen gemaakt zouden worden bij de loop hierboven; of neem de code over en zet er een `print` in om het gedrag te bestuderen.

## Opdracht

Schrijf nu zelf een stukje code met `for`-loop die de som van de oneven getallen van 1 tot en met 20 uitrekent en vervolgens de som `print`. Sla dit programmaatje apart op, in een bestand genaamd **oneven.py**. Gebruik de stapgrootte van `range` om alleen de oneven getallen te genereren, zodat het programma efficiënt werkt. Vergeet niet om commentaar toe te voegen!
