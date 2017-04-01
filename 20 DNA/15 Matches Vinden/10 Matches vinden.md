# Matches vinden

Maak een functie die de *indices* van alle matches van een `needle` in een `haystack` oplevert.

    >>> result = exact_matches("atgacatgcacaagtatgcat", "atgc")
    >>> print result
    [5, 15]

## Specificatie

- Maak een nieuw bestand aan met de naam `findmatches.py`.
- Definieer zelf een functie `exact_matches` die twee argumenten aanneemt:
	- `haystack`, dat is de string waarin we zoeken
	- `needle`, dat is de string die we zoeken
- De functie moet alle relevante indices verzamelen in een lijst en deze `return`en.

## Hints

* Deze opdracht lijkt op `count_exact_matches`. Je gaat alleen niet tellen maar de indices opsommen.
* Maak gebruik van de `append()` methode van een lijst (weet je nog?).

## Testen

Test je functie met `checkpy`!

    checkpy findmatches
