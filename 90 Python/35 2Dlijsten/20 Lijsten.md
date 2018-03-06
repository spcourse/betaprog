# Lijsten in lijsten, 2D-lijsten

Behalve één dimensionale lijsten, waarin we elementen op een rij kunnen opslaan, kunnen we in Python ook twee dimensionale lijsten maken.
Zo kun je bijvoorbeeld een tabel nabouwen, en deze door middel van twee coordinaten indexeren. We gaan nu een tabel maken door een lijst met daarin lijsten te definiëren.
Stel je hebt de volgende lijst:

    >>> lijst = ['a', 'b', 'c', 'd']

Om het tweede element te pakken gebruik je de brackets `[` en `]`.

    >>> print(lijst[2])
    c

Laten we er een naam aan geven:

    >>> element = lijst[2]
    >>> print(element)
    c

Stel je nu voor dat de elementen die in je lijst zitten ook lijsten zijn. Dat kan gewoon!

    >>> lijst = [ ['a', 'b', 'c'], ['d', 'e', 'f'], ['g', 'h', 'i'] ]
    >>> print(lijst[2])
    ['g', 'h', 'i']

Alternatief:

    >>> element = lijst[2]
    >>> print(element)
    ['g', 'h', 'i']

Je hebt nu een element, en dat is een lijst. Klopt. Maar hoe pak je daar dan
weer een element uit? Gebruik gewoon weer de brackets `[` en `]`! Stel we
willen de `h` pakken. Dan moeten we eerst uit `lijst` het derde element pakken
(index 2) om de lijst met de `h` te krijgen. Vervolgens moeten we van die lijst
het tweede element pakken (index 1) om de `h` te krijgen. Je kan dat in één
keer doen:

    >>> print(lijst[2][1])
    h

Of met een tussenstap:

    >>> element = lijst[2]
    >>> print(element[1])
    h

Alternatief:

    >>> element = lijst[2]
    >>> letter = element[1]
    >>> print(letter)
    h

Je kan dit dan zien als een tweedimensionaal veld of tabel waar je x- en y-coördinaten
kunt gebruiken! Om een tweedimensionale lijst aan te maken kun je het volgende doen:

    >>> l = []
    >>> for y in range(number_of_columns):
    >>>     l.append([]) # add row
    >>>     for x in range(number_of_rows):
    >>>         l[y].append( 'your element here' )

Om zoiets netjes te printen kun je het volgende doen:

    >>> for row in l:
    >>>     for xy in row:
    >>>         print(xy, end="") # no new line
    >>>     print()  # print a newline for the next row
