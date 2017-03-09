# Nulpunten

## tl;dr

Schrijf een programma dat de nulpunten berekent van de polynoom $$f(x)=ax^2+bx+c$$ en de grafiek van de functie plot.

	# python nulpunten.py
	De nulpunten zijn -4.32 en 2.32


![](PolynoomAnalyse.png)

## Achtergrond


Schrijf in een bestand `functies.py` een programma dat een functie van de vorm $$f(x)=ax^2+bx+c$$ op het scherm plot en de nulpunten vindt. Het vinden van de nulpunten (de x-waardes waarvoor geldt $$f(x)=0$$) moet in een aparte functie `nulpunten(a,b,c)` gebeuren die als parameters de parameters van de polynoom meekrijgt en de twee nulpunten in een lijst teruggeeft. Bereken de nulpunten met behulp van de abc-formule.

Roep als test de functie aan met de waarden $$a = 1$$, $$b = 2$$ en $$c = -10$$. Die polynoom heeft namelijk twee nulpunten.

> Let op dat je dus één Python-bestand maakt (`functies.py`) met daarin alleen de code voor deze opdracht. Zoals gezegd moet daar één functie in staan (`nulpunten`) en daarnaast wat testcode. Bij uitvoeren (runnen) van dit programma moet de grafiek verschijnen en moeten de nulpunten van de gegeven functie naar het scherm geprint worden.

Breid je functie nu uit zodat je functie ook raad weet met polynomen die helemaal geen nulpunten hebben. In dat geval moet je nog steeds de functie op het scherm printen, maar moet er op het scherm netjes verschijnen dat deze polynoom geen nulpunten heeft.

Extra: als je nog tijd over hebt kan je misschien de figuur 'mooi' te maken. Probeer bijvoorbeeld de polynoom zelf en de nulpunten duidelijk weer te geven op het scherm zoals in de figuur hieronder.
