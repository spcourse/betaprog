# Matches tellen

Maak een nieuw bestand aan met de naam `countmatches.py`.

Maak een functie `count_exact_matches` die het aantal keer telt dat de needle in de haystack voorkomt.

    >>> result = count_exact_matches("atgacatgcacaagtatgcat", "atgc")
    >>> print result
    2

## Specificatie

Schrijf zelf een functie `count_exact_matches` die twee argumenten aanneemt:

- `haystack`, dat is de string waarin we zoeken
- `needle`, dat is de string die we zoeken

De functie moet het aantal keer tellen dat de `needle` in de `haystack` voorkomt en
dat als integer returnen.

## Hints

- Maak gebruik van de functie `find`.
- Houd een variabele bij waarin je bijhoudt vanaf welke index `find()` moet gaan zoeken.

## Testen

Je kan testen of deze functie correct gemaakt is door checkpy te draaien:

    checkpy countmatches