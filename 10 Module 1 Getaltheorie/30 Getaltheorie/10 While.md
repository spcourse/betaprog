# Nog een loop: `while`

In de vorige hoofdstukken hebben we gewerkt met `for`-loops. Die zijn heel handig als je vóór de berekening weet waar deze moet eindigen. Als je bijvoorbeeld loopt over deze lijst:

	metingen_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]

dan weet je dat de loop vijf keer zal draaien, omdat de lijst vijf elementen heeft. En als we, zoals in het eerste hoofdstuk, de oneven getallen tussen 1 en 20 willen optellen, dan weet je dat je bij 20 moet stoppen.

Maar wat nou als we niet weten waar het verhaal eindigt? Hieronder zie je een voorbeeld waarbij we de loop af willen breken zodra de som van de getallen *tot 
dan toe* groter is dan 50. Probeer onderstaande code te runnen zodat je ziet wat er precies gebeurt.

    som = 0
	getal = 0
    while som <= 50:
	    getal = getal + 1
        som = som + getal
        print "%d  som = %d" % (getal, som)
    print "Ik stop omdat de som meer dan 50 is"

De opdracht met `while` kun je hier lezen als "zolang som kleiner is of gelijk aan 50". Elke keer dat we weer bovenaan de loop zijn aangekomen, wordt die voorwaarde gecontroleerd, en als daar niet meer aan wordt voldaan, dan stopt de loop.

Je kunt een `for`-loop meestal ook als een `while`-loop schrijven. Bijvoorbeeld:

	for i in range(10):
	    print "getal %d" % i

Dat kun je ook schrijven als:

	i = 0
	while i < 10:
		print "getal %d" % i
	    i = i + 1

Je ziet dat de `for`-loop wel iets korter op te schrijven is in dit geval. Maar de keerzijde is, dat je sommige problemen mooier opschrijft met een `while`-loop. Daar komen we zo.
