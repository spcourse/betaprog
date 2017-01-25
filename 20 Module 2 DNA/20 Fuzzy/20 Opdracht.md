# Opdrachten

Het lijkt misschien lastig of veel werk om dit te programmeren. Een belangrijke
vaardigheid bij het programmeren is een groot en moeilijk probleem opdelen in
kleinere problemen die makkelijker op te lossen zijn. Dit noemen we
probleem*decompositie*. Voor dit algoritme zien we twee duidelijke delen: eerst
moet je alle mogelijke waarden voor `a` en `b` genereren, en vervolgens kun je
die gebruiken om de fuzzy matches te vinden.

Dit maal werk je in een bestand met de naam `fuzzyMatches.py`. Om de functies te
gebruiken die je in exactMatches.py hebt gebruikt moet je deze nog importeren.
Dit kan op dezelfde manier als waarop we alles van de strings module importeren:

    from exactMatches import *

Let er op dat je alle bestanden in dezelfde map hebt staan!

Je test met `checkpy fuzzyMatches.py`.

## Opdracht 3: `split_needle`

Maak een functie `split_needle()` die, gegeven een string, alle mogelijke
substrings genereert met één missend karakter.

Voorbeeld:

    >>> result = split_needle("abcd"):
    >>> print result
    [('', 'bcd'), ('a', 'cd'), ('ab', 'd'), ('abc', '')]
    >>> print split_needle("abcde")
    [('', 'bcde'), ('a', 'cde'), ('ab', 'de'), ('abc', 'e'), ('abcd', '')]

Het formaat dat je hier gebruikt is een lijst met tuples. Een *tuple* is een manier om bij elkaar horende waarden tot één te combineren. Bijvoorbeeld zo:

    >>> part_a = "left"
    >>> part_b = "right"
    >>> my_tuple = (part_a, part_b)
    >>> print my_tuple
    ('left', 'right')
    >>> print my_tuple[0]
    left

Daarnaast heb je waarschijnlijk een manier nodig om substrings te maken. In Python kun je daarvoor aan de slag met string *slicing*. Zie [Think Python](http://greenteapress.com/thinkpython/html/thinkpython009.html#toc89) voor uitleg hierover!

## Opdracht 4: `fuzzy_matches`

Maak dan een functie `fuzzy_matches` die, gegeven een haystack en een needle,
een lijst met indices van alle fuzzy matches oplevert.

Voorbeeld:

    >>> result = fuzzy_matches("atgacatgca", "atgc")
    >>> print result
    [0, 5]

Er zijn meerdere manieren om dit te doen. Hier een paar tips.

1. Het eerste wat je hier wil doen is alle mogelijke delen van de needle genereren door de functie die je net hebt gemaakt te gebruiken.

2. Dan kun je per paar gaan zoeken naar het eerste deel en het tweede deel. Voor de matches van een paar kun je vervolgens de formule toepassen om te checken of er een match op die index is of niet.

3. Uiteindelijk wil je wellicht gedupliceerde elementen uit de lijst verwijderen, omdat dit het antwoord beter controleerbaar maakt.

Merk op dat dit nog niet bijzonder efficiënt is. Zo worden er waarschijnlijk
meerdere malen dezelfde indices doorzocht op matches. Kun je een deel afsluiten
zodat er geen dubbel werk gedaan wordt? Kun je meer verbeteringen vinden?
