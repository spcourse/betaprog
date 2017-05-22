# Opdracht: vrije val van base jumpers

In de vorige opgave is de luchtwrijving verwaarloosd waardoor je ook met behulp van de natuurkunde van de middelbare school de antwoorden kon controleren. We gaan nu een stuk realisme toevoegen: luchtwrijving. 

De luchtweerstand die een vallend voorwerp ondervindt is evenredig met het kwadraat van de snelheid:

$$F = \xi v^2$$, met $$ \xi = 0.24$$

Hoewel de luchtweerstand ook afhankelijkheid is van de oppervlakte en massa van het object en de dichtheid van de lucht zullen we in deze opdracht alleen het effect van de snelheid bestuderen. De wrijving betekent dat er een snelheid is waarbij de zwaartekracht en de wrijving elkaar in evenwicht houden. Deze maximum snelheid die een parachutespringer kan bereiken, ongeveer 196 km/uur, wordt [terminal velocity](https://en.wikipedia.org/wiki/Terminal_velocity) genoemd.

![](Freefall.png)

Schrijf een functie `basejump()` in een bestand **basejump.py** waarin de val wordt doorgerekend van een base jumper die van de top van de Burj Khalifa in Dubai (828 m) naar beneden springt. Volg dezelfde strategie als in de eerste, maar neem nu ook de luchtweerstand mee zoals gegeven in bovenstaande formule. Neem hierbij aan dat de basejumper 72 kilo weegt.

## Uitvoer

Zorg dat je programma de volgende resultaten oplevert:

- Een grafiek van de snelheid als functie van de tijd.

    Test je programma door net te doen of de toren 2000 meter hoog is en te kijken of je inderdaad vindt dat de terminal velocity ongeveer 196 km/uur is.

- Een grafiek van de hoogte als functie van de tijd. 

    Teken twee lijnen in dezelfde figuur: in groen/blauw de situatie als we de luchtweerstand wel/niet verwaarlozen.

Print de antwoorden op de volgende vragen. Denk weer aan het precies zijn in je antwoord en alleen het printen van de gevraagde waarden! Print beide antwoorden op een eigen regel.

De base jumper is eerst in vrije val, maar op 100 meter van het oppervlak moet deze de parachute opengooien.

- Hoeveel tijd (seconden) heeft de jumper vanaf de afsprong tot dat moment, als we de luchtweerstand buiten beschouwing laten?

- Hoeveel langer (seconden) heeft de base-jumper om te genieten van de vrije val dankzij de luchtweerstand?

Zoals altijd heb je ook hier mensen die het [randje opzoeken](https://en.wikipedia.org/wiki/Speed_skydiving). Omdat hij zijn sprong maakte in een gebied waar de luchtdruk enorm laag was is het record met 1342 km/uur veilig in handen van Felix Baumgartner.

## Testen

	checkpy basejump