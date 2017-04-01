# Fuzzy matches

Maak in `fuzzymatches.py` een functie `fuzzy_matches` die, gegeven een haystack en een needle,
een lijst met indices van alle fuzzy matches oplevert.

    >>> result = fuzzy_matches("atgacatgca", "atgc")
    >>> print result
    [0, 5]

## Specificatie

Schrijf zelf een functie `fuzzy_matches` die twee argumenten accepteert:

- `haystack`, dat is de string waarin we zoeken
- `needle`, dat is de string die we zoeken

De functie moet alle indices van de fuzzy matches `return`en in een lijst.


## Hints

1. Het eerste wat je hier wil doen is alle mogelijke delen van de needle genereren door de functie `split_needle` die je net hebt gemaakt te gebruiken.

2. Dan kun je per paar gaan zoeken naar het eerste deel en het tweede deel. Voor de matches van een paar kun je vervolgens de formule toepassen om te checken of er een match op die index is of niet.

3. Uiteindelijk wil je wellicht gedupliceerde elementen uit de lijst verwijderen, omdat dit het antwoord beter controleerbaar maakt.

Merk op dat dit niet bijzonder efficiënt is. Zo wordt er waarschijnlijk
meerdere malen dezelfde indices doorzocht op matches. Kun je een deel afsluiten
zodat er geen dubbel werk gedaan wordt? Kun je meer verbeteringen vinden?

## Testen

    checkpy fuzzymatches
