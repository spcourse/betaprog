# Matches vinden

Maak een nieuw bestand aan met de naam `findmatches.py`.

Maak een functie `exact_matches` die de *indices* van de matches van de `needle` in `haystack` geeft.

    >>> result = exact_matches("atgacatgcacaagtatgcat", "atgc")
    >>> print result
    [5, 15]

## Specificatie

Schrijf zelf een functie `exact_matches` die twee argumenten aanneemt:

- `haystack`, dat is de string waarin we zoeken
- `needle`, dat is de string die we zoeken

De functie moet alle indices van waar de needle zich bevindt (matched) in de haystack `return`en in een lijst.

## Hints

* Deze opdracht lijkt op `count_exact_matches` alleen ga je nu
  niet tellen maar moet je de indices aan een lijst toevoegen.
* Maak gebruik van de `append()` methode van een lijst.

## Testen

Je kan testen of deze functie correct gemaakt is door checkpy te draaien:

    checkpy findmatches