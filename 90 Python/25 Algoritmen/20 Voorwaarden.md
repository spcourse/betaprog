# Voorwaardelijke instructies

In de voorgaande programma's schreven we scriptjes die regel voor regel van boven naar beneden werden uitgevoerd. Een soort stapsgewijze handleiding. Programma's worden interessanter als we *uitzonderingen* willen beschrijven.

Tot nu toe konden we bijvoorbeeld geen programma schrijven dat slechts geld van je bankrekening afschrijft als er ook iets opstaat (stufi-dag). Hiervoor hebben we een *conditional* nodig. In Python kun je gebruik maken van een `if`-statement. Dit ziet er in een voorbeeld als volgt uit:

	balance = 100
	expense = 30

	# pay only if balance allows it 
	if balance - expense > 0:
	    balance -= expense

	print "Remaining balance:", balance

Een `if`-statement in Python kent de volgende structuur:

	if conditie:
	    code
	
Een *conditie* kent uiteindelijk maar twee mogelijke opties. In Python zijn dit `True` en `False` (dit noemen we [boolean waardes](https://en.wikipedia.org/wiki/Boolean_algebra#Values), naar de bedenker [George Boole](https://en.wikipedia.org/wiki/Boolean_algebra#Values)). In de code hierboven is deze boolean het resultaat de expressie `balance - expense > 0`. Hier wordt gebruik gemaakt van de vergelijkingsoperator `>`. Deze operator vergelijkt twee waarden, in dit geval de uitkomst van `balance - expense` en `0`, en produceert een boolean. Probeer maar eens in de shell: `print 1 > 2` en `print 3 > 2`. Afhankelijk van de uitkomst, dat kan dus zijn `True` of `False`, wordt de code die bij de `if`-statement hoort uitgevoerd.

De `:` in de code hierboven laat zien dat bij de `if` een codeblok hoort. Dat is dus precies het deel van de code dat slechts wordt uitgevoerd als aan de voorwaarde is voldaan. Zo'n blok bestaat vaak uit meerdere regels code, en om duidelijk te maken welke regels dat zijn, gebruik je *indentatie*. Dat is een aantal spaties of tabs van de kantlijn af. In de code hierboven hebben we vier spaties gebruikt om aan te geven dat de regel `balance -= expense` bij de `if`-statement hoort. Omdat de regel eropvolgend, `print "Remaining balance:", balance`, minder indentatie kent, is de `if`-statement op die plek afgesloten.


## `if`-`elif`-`else`

Behalve `if`, kent Python ook de `if-else` constructie. Deze ziet er als volgt uit:


	balance = 100

	if balance >= 0:
	    print "balance is positive"
	else:
	    print "balance is negative"


Hiermee hebben we een manier om één stuk code uit te voeren mocht de conditie `True` blijken, en een ander mocht het `False` zijn.

Niet elk probleem is binair, en dan wil je wel eens meer opties. Dan is `elif` een uitkomst. `elif` is een samenvoegsel van `else` en `if`. Je kan `elif` als volgt gebruiken:

	balance = 100

	if balance >= 1000:
	    print "I'm rich!"
	elif balance >= 0:
	    print "At least I'm not broke."
	else:
	    print "Nope"


## Vergelijkingsmateriaal

Mocht je meer nodig hebben dan de vergelijkingsoperator `>`, dan is het internet een uitkomst. Voor de handigheid hier wat tips:

* `not` (True -> False, False -> True)
* `==`  (equal, Let op: een enkele = is toekennen, een dubbele vergelijken!)
* `!=`  (not equal)





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

