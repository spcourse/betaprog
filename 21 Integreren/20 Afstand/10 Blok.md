# Afstand

Schrijf een functie die de gemiddelde afstand tussen 2 punten in een vierkant met afmeting 1 x 1 berekent. Gebruik de volgende strategie:

  - Genereer twee random punten: dus 2 keer een random x-waarde en 2x een random y-waarde en bereken de afstand tussen de punten

  - Doe dit bovenstaande een groot aantal (N) keer en bewaar de totale afstand (som afstanden)

  - Bereken de gemiddelde afstand door de totale afstand te delen door N.

![](vierkant.png)

Dit is een typisch voorbeeld van een duidelijk en simpel probleem dat analytisch nogal lastig op te lossen is. Probeer het maar eens. 

## Specificatie

- Maak een nieuw bestand genaamd `afstand.py`.

- Definieer in dit bestand een functie `vierkant()` die geen parameters accepteert en de gemiddelde afstand tussen 2 punten in een vierkant teruggeeft (met behulp van `return`).

## Tip: bedenk van tevoren welk antwoord je verwacht

Net zoals je bij een gewone natuurkunde- of wiskundeopdracht is het belangrijk om vooraf een schatting te maken van de uitkomst zodat je een duidelijk verkeerd antwoord gelijk herkent. Wat denk je dat het antwoord moet zijn ? Als je programma klaar is kan je ook heel makkelijk de gemiddelde afstand in een vierkant van 2x2 uitrekenen. Wat denk je ? Is dat 'gewoon' 2 keer zo groot als je antwoord bij het 1x1 vierkant .... of is het misschien $$x^2$$ keer zo groot ... of juist $$\sqrt{2}$$ ? 

## Testen

	checkpy afstand.py