# Naalden splitsen

Schrijf een functie die, gegeven een string, alle mogelijke substrings met één missend karakter  genereert.

    >>> result = split_needle("abcd"):
    >>> print result
    [('', 'bcd'), ('a', 'cd'), ('ab', 'd'), ('abc', '')]
    >>> print split_needle("abcde")
    [('', 'bcde'), ('a', 'cde'), ('ab', 'de'), ('abc', 'e'), ('abcd', '')]

## Specificatie

Maak een bestand aan genaamd `fuzzymatches.py`.

Schrijf zelf een functie `split_needle` die één argument accepteert:

- `needle`, dat is de string die we gaan opsplitsen

De functie moet de naald op alle mogelijke manieren opslitsen, en daarbij telkens één letter weglaten. 

`split_needle` moet een lijst met tuples `return`-en. Een *tuple* is een manier om bij elkaar horende waarden bij één te houden. Bijvoorbeeld zo:

    >>> part_a = "left"
    >>> part_b = "right"
    >>> my_tuple = (part_a, part_b)
    >>> print my_tuple
    ('left', 'right')
    >>> print my_tuple[0]
    left

## Hints

* Je hebt een manier nodig om substrings te maken. In Python kun je daarvoor aan de slag met string *slicing*. Zie [Think Python](http://greenteapress.com/thinkpython/html/thinkpython009.html#toc89) voor uitleg hierover!
* Maak gebruik van de `append()` methode van een lijst.

## Testen

Let op dat deze test ook test voor de volgende opdracht: fuzzy matches. Het is dus prima als de tests voor fuzzy matches nog rood kleuren met sad smileys!

    checkpy fuzzymatches