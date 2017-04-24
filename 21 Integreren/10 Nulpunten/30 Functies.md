# Nulpunten

Schrijf een programma dat de nulpunten berekent van de polynoom $$f(x)=x^2+2x-10$$ en de grafiek van de functie plot.

	# python nulpunten.py
	De nulpunten zijn -4.32 en 2.32


![](PolynoomAnalyse.png)

## Achtergrond


Schrijf in een bestand `nulpunten.py` een programma dat een functie van de vorm $$f(x)=ax^2+bx+c$$ op het scherm plot en de nulpunten vindt. Het vinden van de nulpunten (de x-waardes waarvoor geldt $$f(x)=0$$) moet in een aparte functie `nulpunten(a,b,c)` gebeuren die als parameters de parameters van de polynoom meekrijgt en de twee nulpunten in een lijst teruggeeft. Bereken de nulpunten met behulp van de abc-formule.

Roep als test de functie aan met de waarden $$a = 1$$, $$b = 2$$ en $$c = -10$$. Die polynoom heeft namelijk twee nulpunten.

## Specificatie

- Schrijf een functie `nulpunten(a, b, c)` die de nulpunten van de polynoom $$f(x)=ax^2+bx+c$$ berekent.

- De functie nulpunten kan teruggeven:

	- een lege lijst `[]` als er geen nulpunten zijn
	- een lijst met twee elementen `[n1, n2]` waarin `n1` en `n2` de nulpunten van de polynoom zijn

## Hoe te beginnen

1. Maak een bestand `nulpunten.py` aan.

2. Schrijf hierin een functie `nulpunten(a, b, c)`.

3. Voeg onder de functie-definitie een test-aanroep toe:

		nulpunten(1, 2, -10)



## Hints

Breid je functie nu uit zodat je functie ook raad weet met polynomen die helemaal geen nulpunten hebben. In dat geval moet je nog steeds de functie op het scherm printen, maar moet er op het scherm netjes verschijnen dat deze polynoom geen nulpunten heeft.

## Testen

	checkpy nulpunten.py

(Werkt het niet? Update dan nog eens met `checkpy -u`.)