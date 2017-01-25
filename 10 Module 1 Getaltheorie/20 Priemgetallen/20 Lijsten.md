# Lijsten

Lijsten in Python zijn handig om data te groeperen en vervolgens als geheel te verwerken. Zo kun je berekeningen niet alleen maar op bijvoorbeeld losse getallen toepassen (is dit specifieke getal een priemgetal?) maar ook op hele verzamelingen.

## Lijsten maken

Een lijstje met namen van docenten kun je zo bewaren:

	docenten = ["Martijn", "Ivo", "David", "Florian", "Olmo", "Dominique", "Maarten"]

Elk element in deze lijst is een *string*, maar zo'n lijst kan ook getallen of zelfs andere lijsten bevatten. Ook door elkaar heen. Elk element heeft een *positie*; daarmee kun je een element uit een lijst opvragen:

    print docenten[2]

Probeer dit uit, want het antwoord is misschien niet precies wat je verwacht. Probeer daarom ook even het getal `2` te veranderen in andere getallen.

## Elementen toevoegen

Als je een lijst hebt met 5 temperatuurmetingen van het Science Park, dan kun je die als volgt definiëren en uitprinten:

	metingen_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]
    print metingen_science_park

We printen hier de hele lijst in één keer uit, in plaats van een enkel element. Als je nu een zesde meting doet (20,5 graad) kun je die toevoegen met behulp van de `append`-instructie:

    metingen_science_park.append(20.5)
    print metingen_science_park

In plaats van de lijst printen kunnen we ook de individuele elementen van de lijst printen of het aantal elementen in de lijst berekenen. Dat laatste doen we met een ingebouwde Python functie `len`. Meer daarover later in deze cursus.

    print "Het eerste element van de lijst is %d" % metingen_science_park[0]
    print "Het aantal elementen in de lijst is %d" % len(metingen_science_park)

Nu kunnen we dus in ieder geval de hele lijst gebruiken, en invididuele elementen uitprinten.

## Loopen met een lijst

Om nu de gegevens in een lijst te verwerken, moeten we vaak ieder element van de lijst individueel bekijken. Daarvoor kunnen we de `for`-loop gebruiken:

	metingen_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]
    metingen_science_park.append(20.5)
    for meting in metingen_science_park:
	    print "de meting was %d graden" % meting

Probeer de code zeker even uit, zodat je goed ziet wat de uitvoer is. Let op dat de `for`-loop nu niet meer gebruik maakt van `range`.


> Zoals je ziet in bovenstaande voorbeeld zal het programma het gemiddelde afronden. `%d` zegt namelijk dat je een geheel getal op het scherm wilt printen. Als je een reëel getal wilt printen moet je `%f` gebruiken. Naar deze *formats* kijken we later in de cursus nog verder.

Naast het direct loopen over de elementen in een lijst kan het soms handig zijn om juist te loopen over de *posities* in de lijst en zo de elementen op te roepen.

	metingen_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]
    metingen_science_park.append(20.5)
    for positie in range(0,len(metingen_science_park)):
	    print "de meting was %f graden" % metingen_science_park[positie]
