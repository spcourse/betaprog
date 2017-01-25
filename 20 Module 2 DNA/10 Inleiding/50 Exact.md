# Opdrachten
Maak een nieuw bestand aan met de naam `exactMatches.py`. De volgende twee
functies maak je in dit bestand. Je kan testen of deze functies correct gemaakt
zijn door checkpy te draaien:

    checkpy exactMatches.py

## Opdracht 1: `count_exact_matches`

Maak een functie `count_exact_matches` die in elk geval twee argumenten heeft:

- `haystack`, dat is de string waarin we zoeken
- `needle`, dat is de string die we zoeken

De functie moet het aantal keer tellen dat de needle in de haystack voorkomt en
dat als integer returnen.

Voorbeeld:

    >>> result = count_exact_matches("atgacatgcacaagtatgcat", "atgc")
    >>> print result
    2

Hints:

- Maak gebruik van de functie `find`.
- Hou een variabele bij waarin je bijhoudt vanaf welke index `find()` moet gaan zoeken.

## Opdracht 2: `exact_matches`

Maak een functie `exact_matches`, vergelijkbaar met de functie die je net
gemaakt hebt. Deze keer moet er een lijst ge`return`t worden met de *indices*
van de matches van de `needle` in `haystack`.

Voorbeeld:

    >>> result = exact_matches("atgacatgcacaagtatgcat", "atgc")
    >>> print result
    [5, 15]

Hint:

* Dit is bijna hetzelfde als de functie `count_exact_matches` alleen ga je nu
  niet tellen maar moet je de indices aan een lijst toevoegen met behulp van de
  functie `append()`.
