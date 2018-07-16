# Afstand

Schrijf een programma met een daarin een functie die de gemiddelde afstand tussen twee punten in een vierkant met afmeting $$1\times 1$$ berekent.


## Achtergrond

Dit is een typisch voorbeeld van een duidelijk en ogenschijnlijk simpel probleem dat analytisch nogal lastig op te lossen is. Probeer het maar eens, dan zal je al snel zien dat je vastloopt. Maar maak in ieder geval een schatting, dan kun je zien of het antwoord van je programma realistisch is, voordat je het inlevert.

![](vierkant.png)


## Specificatie

- De naam van het programma is `afstand.py`.

- Definieer daarin een functie `vierkant($$N$$)` die als parameter het aantal keer ($$N$$) accepteert en de gemiddelde afstand tussen twee punten in zo'n vierkant `return`t.


## Probleemanalyse

- Genereer steeds twee random punten: dus twee random $$x$$-waardes en twee random $$y$$-waardes, en bereken de afstand tussen de punten

- Doe dit bovenstaande een groot aantal keer en hou in een aparte variabele de totale afstand bij.

- Bereken de gemiddelde afstand door de totale afstand te delen door $$N$$.


## Testen

	checkpy afstand.py
