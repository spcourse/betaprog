# Voorwaardelijke instructies

Tot nu toe hebben we een lang tekstbestand gemaakt met drie soorten regels:

- instructies (die Python kent, zoals `print`)
- commentaar (waar Python niets mee doet, maar die wij kunnen lezen)
- lege regels (waar Python niets mee doet, en die helpen onderscheid te maken tussen stukken code)

Nu gaan we een nieuwe Python-instructie gebruiken: `if`. Bij deze instructie combineer je een *voorwaarde* met een aantal regels die alleen worden uitgevoerd als aan de voorwaarde voldaan is. Bijvoorbeeld als je wilt kijken of een getal positief is. Tik het maar over.
	
	x = 15
	if x > 0:
	    print "Het getal %d is positief." % x

Je ziet dat er een voorwaarde wordt gesteld: `x > 0`, ofwel `x` moet positief zijn. En er is vervolgens een regel die alléén wordt uitgevoerd als `x > 0`. Probeer het maar uit.

> De regel na de `if` begint met vier spaties. Dat noemen we *inspringen*. Met deze spaties laat je zien dat dit een regel is die onder controle van de `if` staat: wordt alleen gedaan als aan de voorwaarden is voldaan. Als de volgende regel weer zónder vier spaties is, dan valt deze niet meer 'onder' de `if`, zoals we dat noemen.

Om te printen of een getal een negatief is zou je een extra regel toe kunnen voegen, maar je kan de 'stroom' van het programma ook sturen als er juist niet aan de voorwaarde voldaan is. Als je bijvoorbeeld wilt testen of een getal positief of negatief is dan kan je naast de `if` ook de `else`-constructie gebruiken.

	x = 15
	if x > 0:
	    print "het getal %d is positief" % x
	else:
        print "het getal %d is negatief" % x

> Hierboven ziet je dat er twee regels beginnen met vier spaties: één na de `if` en één na de `else`. Dat betekent dus dat precies die regels onder controle van respectievelijk de `if` en de `else` staan.

Je kunt verschillende voorwaarden combineren. Als je wilt weten of een getal zich in een bepaald bereik bevindt (bijvoorbeeld tussen de 3 en de 39) dan kun je dat doen met `and`:

	x = 15
    x_min = 3
    x_max = 39	
	if x > x_min and x < x_max:
	    print "het getal %d bevindt zich tussen %d en %d" % (x, x_min, x_max)

**Let op:** de constructie: if 3 < x < 39 werkt niet. Je moet net als in het bovenstaande voorbeeld door logisch combineren van losse (enkelvoudige) voorwaardes de stroom van je programma vormgeven.

Hier een lijstje van voorwaarden die je in Python kunt gebruiken:

- `>` 	groter dan
- `>=`	groter of gelijk aan
- `<` 	kleiner dan
- `<=`	kleiner dan of gelijk aan
- `==`	is gelijk aan
- `!=`	is niet gelijk aan

