# Reële getallen

We hebben geleerd dat je een geheel getal als volgt print:

    x = 100
    print "x heeft de waarde %d" % (x)

Zodra de computer de string naar het scherm print zet hij op de plek waar `%d` staat de waarde die in de variabele *x* opgeslagen staat. In ons geval 100. De vorm `%d` geeft aan dat het een *geheel* getal is.

Vaak is een variabele die je gebruikt helemaal geen geheel getal.

    breuk = 3./17.
    print "breuk = %d" % (breuk)

Als je dit print zal je zien dat, hoewel de variabele `breuk` de waarde 0.176471 heeft, dit programma toch de waarde 0 op het scherm print. Dat komt omdat je met `%d` hebt aangegeven dat je een geheel getal wil afdrukken. In Python worden dan de cijfers achter de komma simpelweg afgekapt.

Als je wilt dat de computer een reëel getal, een `float` in computertaal, print op het scherm, dan geef je dat aan met het `%f` karakter.

    breuk = 3./17.
    print "breuk = %f" % (breuk)

Nu zal wel de volledige waarde geprint worden op het scherm. In veel toepassingen wil je vaak maar een beperkt aantal decimalen weergeven. Als je 2 getallen achter de komma wilt aangeven dan gebruik je de volgende syntax:

    breuk = 3./17.
    print "breuk = %.2f" % (breuk)

Probeer een aantal opties. Net als bij het printen kan het ook misgaan als reële getallen en gehele getallen gemixt worden in je programma zelf. Lees zeker het onderstaande stukje over een van de bekende valkuilen en de manier waarop je die kan omzeilen.

> Het is handig om je probeersels op te slaan in een apart bestand, zodat je nog kunt terugkijken en stukjes code overnemen voor latere opdrachten. Dit testbestand hoef je niet in te leveren.

## Bekende valkuil: mix van gehele en reële getallen

Een veel voorkomende fout die gemaakt wordt in programma's is dat een computer denkt dat elke bewerking van gehele getallen zelf ook weer een geheel getal is. Het volgende programma zal aan de variabele z de waarde 1 toekennen, het eerste gehele getal onder de 1.3333. En dat is natuurlijk niet wat je bedoelde.

    x = 4
    y = 3
    z = x/y
    print z

Zodra een van de getallen in de wiskundige operatie een reëel getal is zal het resultaat ook een reëel getal zijn. De manier om de variabele z de waarde 1.3333 te geven is een van de variabelen (x of y of beide) een reëel getal te maken. De 2 meest gebruikte manieren om dat te doen:

Oplossing 1:

    x = 4.0
    y = 3
    z = x/y
    print z

Oplossing 2:

    x = float(4)
    y = 3
    z = x/y
    print z


## Een rij reële getallen met behulp van `numpy.arange()`

In Module 1 hebben we de for-loop gebruikt om een variabele steeds met 1 op te hogen. In de for-loop constructie gebruikten we daarvoor de `range()` functie. De getallen 1 tot (en niet tot en met) 10, printen op het scherm, ze in een lijst stoppen en die printen aan het eind van het programma deden we als volgt.

    L_x = []
    for x in range(1,10):
	   print "x heeft nu de waarde %d" % (x)
	   L_x.append(x)
	print L_x

In Module 1 hebben we tijdens het tekenen van grafieken gezien hoe we punten (een lijst met x-waardes en een lijst met y-waardes) op het scherm kunnen tekenen. Om een functie te tekenen met een hoge precisie, in ons geval sin(x) leerden we dat we als we de functie wilde tekenen tussen 0 en 2pi we kleine stapjes, stel 0.01 moeten nemen. In Python is er een standaard functie die dat voor je kan doen, de `arange()` functie. Het is een functie die opgenomen is in de numpy bibliotheek.

    import numpy as np               # numpy mdule: nodig voor arange-functie
    import math                      # math module: nodig voor sin()-functie
    L_x = []
    L_y = []
    
	# x loopt van 0 tot 2pi in stapjes van 0.01
    for x in np.arange(0,2*math.pi, 0.01):
        y = math.sin(x)
        L_x.append(x)
        L_y.append(y)		  

Als je bijvoorbeeld de getallen van 2 tot 3 op het scherm wilt printen in stapjes van 0.02 dan kan doe je dat als volgt:

    import numpy as np
	x_begin = 2
	x_eind = 3
    dx = 0.02
	for x in np.arange(x_begin, x_eind, dx):
	    print x

## Bekende valkuil: subtiel verschil tussen 'tot' en 'tot en met'

In het laatste voorbeeld zal het getal 2.0 wel, maar het getal 3.0 niet op het scherm geprint worden. In een van de opdrachten zal je wel degelijk het eindpunt moeten gebruiken. Let daarop. Probeer bovenstaande voorbeeld iets aan te passen zodat het eindpunt wel degelijk geprint wordt 		  
