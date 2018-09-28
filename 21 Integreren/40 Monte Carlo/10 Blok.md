# Monte Carlo

Schrijf een functie die middels de Monte Carlo-methode de integraal berekent van een willekeurige wiskundige functie  met gespecificeerde integratiegrenzen. Zorgt dat zowel de functie zelf als de gegooide punten (zowel de 'goede' als de 'foute') op het scherm weergegeven worden.

## Specificatie

- Maak een nieuw bestand genaamd `montecarlo.py`.

- Schrijf een functie `montecarlo()` die integralen kan berekenen met behulp van een Monte Carlo simulatie. 

- De functie `montecarlo()` moet vijf argumenten accepteren:

	- `func` een functie waarvan we de integraal gaan bepalen
	- `x1` de eerste x waarde
	- `y1` de eerste y waarde
	- `x2` de tweede x waarde
	- `y2` de tweede y waarde

- De functie `montecarlo()` moet de oppervlakte onder de grafiek teruggeven als resultaat.

- De functie `montecarlo()` moet de functie plotten en de punten *in* het integratiegebied (de 'goede' punten) in groen en de 'foute' punten in rood tekenen.


## Tests

Test je procedure met de volgende functie, die je makkelijk analytisch kunt controleren:

	def functie1(x):
		return x**2

Test ook met de volgende functies. Sommige daarvan zijn "integreerbaar", andere kun je alleen numeriek benaderen.

$$\int_{0}^{1}x^2 dx$$

$$\int_{0}^{1}x^{x+\frac{1}{2}} ~dx$$

$$\int_{0}^{\pi}sin(x) dx$$

$$\int_{0.2}^{2.2} \tan(\cos(\sin(x))) ~dx$$

$$\int_{0}^{\pi} \sin(x^2) ~dx$$

Zet deze functies in je eigen programma en zorg dat je onderaan een aantal keer je `montecarlo()`-functie aanroept, om deze voorbeelden te controleren.

## Hints

- Maak een plaatje van je grafiek zodat je duidelijk ziet welk gebied je aan het integreren bent.

- Maak ook een grafiek met rode en groene punten zoals in bovenstaand voorbeeld. Mocht je een fout gemaakt hebben in je logica dan zie je dat in een plaatje in 1 keer terwijl je daar anders uren naar moet zoeken in de code zelf.

- Bij 'negatieve' integratieregio's kun je de gebieden splitsen.

- In onderzoekstoepassingen wordt voor maximalisatie van de efficientie de rechthoek zo gekozen dat hij de integraal zo nauw mogelijk omsluit.

- Test je functie altijd eerst op een integraal waarvan je de uitkomst kent. Dit is het geval voor een aantal van de functies die hierboven staan weergegeven. Pas als jouw functie die integralen goed uitrekent kan je met vertrouwen de onbekende nieuwe integraal aanpakken.

- Denk goed na over hoe je omgaat met het deel van het integratiegebied dat onder de y-as valt.

## Testen

	checkpy montecarlo
