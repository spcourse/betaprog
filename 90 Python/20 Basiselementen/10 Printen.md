# Printen

Als je een programma hebt geschreven kun je het uitvoeren (*runnen*). De computer loopt dan stap voor stap door je programma en voert de instructies uit die op elke regel staan.

Maak tekstbestand **module1.py** en zet er de volgende regels in:

    print "Hallo, wereld!"
    print "Hee, hallo daar."
    print "Zo tikt het lekker door."
    print "Grappig"
    print 'Hee, print dit nog?'
    print "Ivo's computer doet het vandaag niet."
    print 'Hij zei: "Hallo."'

> Oefenen doe je in deze cursus door elk voorbeeld letterlijk over te tikken. Gebruik niet de *copy-paste* functie, want dan maak je geen fouten en dan leer je veel minder. Tik dus alle voorbeelden over en verbeter ze als je een foutmelding krijgt!

Start nu het programma. Wat komt er uit? Heb je nog tikfouten gemaakt? En heb je gezien dat de aanhalingstekens soms verschillen? Je moet de reeks letters achter `print` starten en eindigen met aanhalingstekens: het geheel dat we uitprinten noemen we een *string*.

Voeg vervolgens ook nog de volgende regels toe:

    print 1
    print 1
    print 1 + 1
    print 1 + 1 + 1
    print 3 + 2
    print 8
    print 5 + 8 + 8 - 8
    print "5 + 8 + 8 - 8"

Je kunt dus ook rekenen. Het resultaat wordt eerst uitgerekend, en dan pas wordt er geprint. Behalve die laatste dan: daar staat de formule (*expressie*) tussen aanhalingstekens, en dan wordt het precies zo naar het scherm geprint. Net als hierboven bij de tekstjes. Dat is dus een *string* en geen formule die berekend kan worden.

> Krijg je een *foutmelding* als je je programma uitvoert? Dan is de kans groot dat je een tikfout hebt gemaakt waardoor Python niet meer begrijpt wat de bedoeling is. Kijk goed waar je de fout hebt gemaakt en probeer deze op te lossen. Kom je er niet uit, vraag dan vooral om hulp. Foutmeldingen leren begrijpen is een belangrijk onderdeel van deze cursus. Dat is ook waarom we heel graag willen dat je tijdens het oefenen fouten maakt!

Nu gaan we berekeningen en tekst combineren:

    print "Het 1e getal van Fibonacci is %d" % 1
    print "Het 2e getal van Fibonacci is %d" % 1
    print "Het 3e getal van Fibonacci is %d" % (1 + 1)
    print "Het 4e getal van Fibonacci is %d" % (1 + 2)
    print "Het 5e getal van Fibonacci is %d" % (2 + 3)

Als je dit programma uitvoert, dan zie je dat precies waar `%d` stond, nu de uitkomst van de berekening is geplaatst.

We kunnen nu allerlei dingen printen en uitrekenen. We kunnen ook, zoals in de laatste voorbeelden, de resultaten van een berekening op een nette manier printen, zodat de *gebruiker* van het programma begrijpt waar we mee bezig zijn. Experimenteer er nog maar even mee. Mocht je iets tegenkomen dat je niet begrijpt, vraag dan gerust wat het betekent.
