# Lijsten

Lijsten in Python zijn handig om data te groeperen en vervolgens als geheel te verwerken. Zo kun je berekeningen niet alleen maar op bijvoorbeeld losse getallen toepassen (is dit specifieke getal een priemgetal?) maar ook op hele verzamelingen.

Een lijstje met namen van docenten kun je zo bewaren:

	docenten = ["Martijn", "Ivo", "Jelle", "Maarten", "Huub", "Marianne"]

Elk element in deze lijst is een *string*, maar zo'n lijst kan ook getallen of zelfs andere lijsten bevatten. Ook door elkaar heen. Elk element heeft een *positie*; daarmee kun je een element uit een lijst opvragen:

    print docenten[2]

Probeer dit uit, want het antwoord is misschien niet precies wat je verwacht. Probeer daarom ook even het getal `2` te veranderen in andere getallen.

## Elementen toevoegen en wijzigen

Als je een lijst hebt met 5 temperatuurmetingen van het Science Park, dan kun je die als volgt definiëren en uitprinten:

	metingen_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]
    print metingen_science_park

We printen hier de hele lijst in één keer uit, in plaats van een enkel element. Als je nu een zesde meting doet (20,5 graad) kun je die toevoegen met behulp van de `append`-instructie:

    metingen_science_park.append(20.5)
    print metingen_science_park

In plaats van de lijst printen kunnen we ook de individuele elementen van de lijst printen of het aantal elementen in de lijst berekenen. Dat laatste doen we met een ingebouwde Python functie `len`. Meer daarover later in deze cursus.

    print "Het eerste element van de lijst is", metingen_science_park[0]
    print "Het aantal elementen in de lijst is", len(metingen_science_park)

Elementen vervangen doe je net zoals met variabelen door middel van `=`. Zo wordt op de regel: `docenten[2] = "Marianne"` de string `"Jelle"` vervangen door `"Marianne"`.

## Loopen met een lijst

Eerder hebben we gekeken naar for-loops, waarbij we gebruik maakten van `range`. Bijvoorbeeld in het volgende stukje code:

	for i in range(8):
	    print i

Het blijkt dat `range` een *functie is die een lijst produceert*. Omdat we hier `8` meegeven als argument, produceert `range(8)` een lijst getallen van 0 tot 8. Dit betekent dat het bovenstaande stukje code equivalent is aan het volgende:

	for i in [0,1,2,3,4,5,6,7]:
	    print i

Dat betekent dat je de `for`-loop het beste zo kan lezen: voor elk element `i` in verzameling `[0,1,2,3,4,5,6,7]` doe `print i`. De naam `i` wordt elke **iteratie** gekoppeld aan de bijbehorende waarde uit de verzameling. De eerste iteratie zal `i` dus worden gekoppeld aan `0`, de tweede aan `1`, etc. Elke iteratie wordt de code die bij de `for`-loop hoort uitgevoerd, in dit geval `print i`. Kortom, het uitvoeren van bovenstaande code zal dus de getallen 0 tot en met 7 op je scherm produceren.

We kunnen dus ook zelf een lijst bedenken en gebruiken met een `for`-loop. Bijvoorbeeld met kommagetallen:

	metingen_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]
    metingen_science_park.append(20.5)
    for meting in metingen_science_park:
	    print "de meting was", meting, "graden"

Probeer de code zeker even uit, zodat je goed ziet wat de uitvoer is. Let op dat de `for`-loop nu geen gebruik meer maakt van `range`.

Naast het direct loopen over de elementen in een lijst kan het soms handig zijn om juist te loopen over de **posities** in de lijst en zo de elementen op te roepen.

	metingen_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]
    metingen_science_park.append(20.5)
    for positie in range(0, len(metingen_science_park)):
	    print positie, 
	    print "de meting was", metingen_science_park[positie], "graden"
