# Matches tellen

Maak een functie die het *aantal* keer telt dat een `needle` in een `haystack` voorkomt.

    >>> result = count_exact_matches("atgacatgcacaagtatgcat", "atgc")
    >>> print result
    2

## Specificatie

- Maak een nieuw bestand aan met de naam `countmatches.py`.
- Definieer zelf een functie `count_exact_matches` met twee parameters:
	- `haystack`, dat is de string waarin we zoeken
	- `needle`, dat is de string die we zoeken
- De functie moet het aantal keer tellen dat de `needle` in de `haystack` voorkomt en dat als integer returnen.

## Hints

- Maak gebruik van de functie `find`.
- Hou in een variabele bij waar in de string je gebleven bent.

## Testen

Test je functie met `checkpy`!

    checkpy countmatches
