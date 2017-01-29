# Tellers

Het is vaak informatief om neer te zetten over *welke* meting het gaat als we een waarde uitprinten. Om dat te doen, kunnen we zelf een teller bijhouden:

    teller = 0
    for meting in metingen_science_park:
        teller = teller + 1
        print "de %d e meting was %f graden" % (teller, meting)

Met behulp van al deze informatie kunnen we ook makkelijk het *gemiddelde* uitrekenen. Bedenk dan dat `teller` aan het einde van de loop precies de telling van het totaal aantal elementen van de lijst bevat!

    som = 0
    teller = 0
    for meting in metingen_science_park:
        teller = teller + 1
        som = som + meting
        print "De %d e meting was %d graden." % (teller, meting)
    gemiddelde_temp = som / teller
    print "De gemiddelde temperatuur was %f graden." % gemiddelde_temp

Of we kunnen met zo'n loopje bijhouden op hoeveel dagen de temperatuur boven de 20 graden uitkwam:

    hete_dagen = 0
    for meting in metingen_science_park:
        if meting > 20:
            hete_dagen = hete_dagen + 1
    print "Op %d dagen was de temperatuur boven de 20 graden" % hete_dagen

Van lijsten is het belangrijk dat je weet hoe je een lijst definiert, hoe je elementen toevoegt aan een lijst en hoe je de individuele elementen afzonderlijk lukt bekijken.

## Opdracht

Probeer nu eens een programma te schrijven dat een lijstje met temperaturen in graden Celcius omrekent naar een nieuw lijstje met overeenkomstige temperaturen in graden Fahrenheit. De formule om Celsius in Fahrenheit te converteren zoek je natuurlijk even op in een zoekmachine. Begin je programma met deze variabele:

	temps = [36, 37, 37.5, 38, 39]

> Let op! Zorg dat de uitkomsten van je algoritme goed controleert met voorbeelden. Als je met breuken van natuurlijke getallen gaat werken (bijvoorbeeld `3/4`) dan zal Python de tussenresultaten afkappen om te zorgen dat het antwoord ook een geheel getal is. Dat wil je niet. Zorg dus dat je een hint geeft dat je met reeële getallen wil werken: `3.0/4.0`.
In het voorbeeld van de gemiddelde temperatuur zou je in de problemen zijn gekomen als de individuele metingen gehele graden waren geweest. Om te forceren dat een getal (in ons geval de variabele som) door Python als een reëel getal gezien op het moment dat je de berekening uitvoert kan je de volgende syntax gebruiken: gemiddelde_temp = float(som) / teller.

Sla dit programma op in een bestand **temperaturen.py** en bewaar het voor het inleveren. Zorg dat je programma de resulterende lijst uitprint, en let op dat je een versie inlevert met de temperaturen zoals hierboven genoemd!
