# Riemann

Schrijf een functie die met behulp van een Riemann-som de integraal berekent van een willekeurige wiskundige functie met gespecificeerde integratiegrenzen. De wiskundige functie moet ook op het scherm weergeven worden.

## Specificatie

- Maak een nieuw bestand genaamd `riemann.py`.

- Schrijf een functie `riemann()` die integralen kan berekenen met behulp van de Riemannsom. 

- De functie `riemann()` moet vier argumenten accepteren:

	- `func` een functie waarvan we de integraal gaan bepalen
	- `a` het begin van het gebied
	- `b` het einde van het gebied
	- `n` hoeveel rechthoeken we gebruiken om de integraal te bepalen.

- De functie `riemann()` moet de juiste waarde van de integraal teruggeven als resultaat.

- De functie `riemann()` moet de wiskundige functie op het scherm laten zien.


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

Zet deze functies in je eigen programma en zorg dat je onderaan een aantal keer je `riemann()`-functie aanroept, om deze voorbeelden te controleren. Zo kun je `functie1()` van hierboven meegeven aan `riemann()` door aan te roepen:

    rieman(functie1, 0, 1, 10000)

## Hints

- Let op: als je het interval in $$N$$ stukjes verdeeld zijn er $$N+1$$ hoekpunten.

- Maak een plaatje van je grafiek zodat je duidelijk ziet welk gebied je aan het integreren bent. Je kunt in je `riemann()`-functie een stukje code opnemen om de grafiek te plotten.

- Test je functie altijd eerst op een integraal waarvan je de uitkomst kent. Dit is het geval voor een aantal van de functies die hierboven staan weergegeven. Pas als jouw functie die integralen goed uitrekent kan je met vertrouwen de onbekende nieuwe integraal aanpakken.


## Debuggen

Lijkt het niet te werken? 

- Check "op het oog" met een grafiek of de integraal überhaupt in de buurt komt van wat je mag verwachten.

- Als dat wel goed zit, kan het zijn dat het aantal stappen te klein is om tot een precies genoeg antwoord te komen. Probeer het aantal te verhogen en bekijk ook hoe dit de uitkomsten beinvloedt.


## Testen

	checkpy riemann
