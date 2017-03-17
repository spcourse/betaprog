## Opdracht 4: Een iets complexer model: f(x) = ax+b en fits in Python zelf 

Iemand in de onderzoeksgroep heeft geopperd dat er welleens een (lineair) verband zou kunnen zijn tussen 
de lengte van mensen en het inkomen van hun ouders. Dat zou verschillende oorzaken kunnen hebben, maar dat 
is voor later. De eerste stap in het onderzoek is om eerst te bekijken of er uberhaupt een verband is. We 
gaan proberen een verband te vinden in de data.

Een vlakke lijn fitten is alleen toepasselijk als er geen afhankelijkheid is tussen de variabelen. In de meeste 
gevallen is dat wel het geval: hoogte zeeniveau als functie van de tijd (sinus), aantal vervallen van een radioactief 
element (exponentieel) of de snelheid van planeten als functie van hun afstand tot de zon (omgekeerd evenredig met 
de wortel van de afstand tot de zon). Ook in die gevallen volgen we hetzelfde procede: varieer de parameters tot de 
$$\chi^2$$ minimaal is. Het fitten van een model aan metingen is een standaard procedure die je als onderzoeker vaak 
tegen zult komen als je verschillende hypotheses wilt testen of de onderliggende dynamica bloot wilt leggen. Het 
implementeren van een fit in een model met meerdere (gecorreleerde) parameters wordt al snel erg complex en kost 
enorm veel rekenkracht tenzij je het slim aanpakt. Net als in bijna elke programmeertaal zijn er bibliotheken vol 
functies in Python die je daarmee kunnen helpen. Hoewel we in deze cursus deze functionaliteit en alle bijbehorende 
details niet verder zullen gebruiken door gebrek aan tijd, willen we hier toch een voorbeeld geven waarin je ziet hoe 
dat in de praktijk gaat.

#### Fitten in Python: f(x) = C (1 vrijheidsgraad)

    # import the module that contains the fit-tool
    from scipy.optimize import curve_fit

    # define our model. In our case a constant function: f(x) = a 
    def MyFitFunction(x, a):
        return a

    # define data and errors
    data_x       = [1,2,3,4,5,6,7,8,9,10]
    data_y       = [171.2, 169.1, 170.8, 169.4, 173, 171, 174, 174, 173, 176]
    data_y_error = [4,4,2,2,2,2,2,2,4,4]
    
    popt, pcov = curve_fit(MyFitFunction, data_x, data_y, None, data_y_error)
    print "Best value: f(x) = %5.2f" % popt[0]

De laatste regel blijft nu nog magie, maar `popt` is een lijst met de 'optimale' 
parameters van de functie die je aan de data hebt gefit. In ons geval is dat maar 
1 parameter omdat we een constante functie aanhouden als model. Je kan zelf in de 
documentatie opzoeken hoe je zelf uit `pcov` (de covariantiematrix) de onzekerheid 
op de parameter kan bepalen. 

#### Fitten in Python: f(x) = ax+ b (2 vrijheidsgraden)

Als je nu in plaats van een constante functie een lineaire functie wilt fitten 
$$f(x) = ax+b$$ en je wilt de resultaten printen dan hoef je maar op 2 plekken een 
verandering aan te brengen. Op de plek waar je de functie die je fit definieert en 
op de plek waar je de resultaten print naar het scherm. Zoek ze maar op.

    # import the module that contains the fit-tool
    from scipy.optimize import curve_fit

    # define our model. In our case a constant function: f(x) = a * x + b 
    def MyFitFunction(x, a, b):
        return a * x + b

    # define data and errors
    data_x       = [1,2,3,4,5,6,7,8,9,10]
    data_y       = [171.2, 169.1, 170.8, 169.4, 173, 171, 174, 174, 173, 176]
    data_y_error = [4,4,2,2,2,2,2,2,4,4]
    
    popt, pcov = curve_fit(MyFitFunction, data_x, data_y, None, data_y_error)
    print "Best value: f(x) = %5.2f * x + %5.2f" % (popt[0], popt[1])

#### Opdracht 4: een fit aan de data met als model: f(x) = ax+b 

Schrijf een programma `statistiek_opdracht4.py()` waarin je zowel een rechte lijn als een lineair 
verband fit aan de data. Gebruik hiervoor de tools in Python zoals hierboven beschreven en reproduceer 
de grafiek die helemaal aan het begin van deze module werd getoond. Laat dus zowel de data als de 
beide 'beste' functies in de grafiek zien. Zorg hierbij ook dat de waardes van de parameters worden 
weergegeven. Print de waardes ook op het scherm als output:

{: .language-python}
    Een fit van f(x)=c     geeft als beste waarde:  c = x.xx
    Een fit van f(x)=ax+b  geeft als beste waardes: a = x.xx  en b = x.xx
    
    
    

    
	