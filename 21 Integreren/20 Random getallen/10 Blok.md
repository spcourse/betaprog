# Random getallen

Een zeer handige bouwsteen in computer is het *random* getal. In de bibliotheek `random` zit een functie `random()` die een random getal produceert tussen 0 en 1. In Python gebruik je de functie als volgt:

    import random 
    x = random.random()
    print x

Elke keer dat je de functie aanroept zal het een nieuw getal opleveren. Tien random getallen achter elkaar doe je dus als volgt:

    import random 
    for i in range(0,10):
       x = random.random()
       print x

## Bouwen met bouwstenen

Zodra je een bouwsteen hebt kan je met behulp van logica en wiskundige manipulaties hier zelf andere objecten van bouwen. Als de computer bijvoorbeeld een random getal tussen 0 en 1 kan produceren dan kunnen we die zo omschrijven dat het transformeert in een random getal tussen een getal a en b.

Voorbeeld: tien random getallen tussen 0 en 2

    import random 
    for i in range(0,10):
       x = random.random()
       y = 2*x
       print y

## Opdracht: Een rij van 10 random getallen tussen a en b

Schrijf een functie `MijnRandomGetal()` die een getal genereert tussen *a* en *b* waarbij je de waardes van a en b zelf kan kiezen. Het moet zo werken als hieronder.

    import random 

    def MijnRandomGetal(a,b):
         getal = <hier jouw code>           
         return getal
     
    # hier begint het programma
    minimum = 2
	maximum = 5
    for i in range(1, 11):
       x = MijnRandomGetal(minimum, maximum)
       print x

Bekijk goed het voorbeeld hierboven waarbij we een random getal tussen 0 en 2 maakten en probeer eerst uit te vinden hoe je een random getal tussen de -1 en +1 zou kunnen maken. Daarna kan je dat abstract programmeren naar een algemene *a* en *b* als begin en eindwaardes van het interval waarbinnen je random getallen wilt gebruiken.


## Opdracht: De gemiddelde afstand tussen 2 punten in een vierkant

Schrijf een functie `Vierkant()` die de gemiddelde afstand tussen 2 punten in een vierkant met afmeting 1 x 1 berekent. Gebruik de volgende strategie:

  - Genereer twee random punten: dus 2 keer een random x-waarde en 2x een random y-waarde en bereken de afstand tussen de punten

  - Doe dit bovenstaande een groot aantal (N) keer en bewaar de totale afstand (som afstanden)

  - Bereken de gemiddelde afstand door de totale afstand te delen door N.

![](vierkant.png)

Dit is een typisch voorbeeld van een duidelijk en simpel probleem dat analytisch nogal lastig op te lossen is. Probeer het maar eens. 


## Tip: bedenk van tevoren welk antwoord je verwacht

Net zoals je bij een gewone natuurkunde- of wiskundeopdracht is het belangrijk om vooraf een schatting te maken van de uitkomst zodat je een duidelijk verkeerd antwoord gelijk herkent. Wat denk je dat het antwoord moet zijn ? Als je programma klaar is kan je ook heel makkelijk de gemiddelde afstand in een vierkant van 2x2 uitrekenen. Wat denk je ? Is dat 'gewoon' 2 keer zo groot als je antwoord bij het 1x1 vierkant .... of is het misschien $$x^2$$ keer zo groot ... of juist $$\sqrt{2}$$ ? 
