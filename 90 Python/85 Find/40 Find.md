# Strings doorzoeken met de `find` functie

Python heeft functionaliteit ingebouwd om je te helpen met strings. De
volgende regel importeert alle functies die gedefinieerd staan in de module
`string`. Dit zijn allemaal functies die strings kunnen bewerken. Je kan deze functies importeren door het volgende bovenaan je bestand te zetten:

    from string import *

Lees de regel hierboven als volgt: van de module string, importeer alles. De functie waar wij naar gaan kijken is `find`. Als je de Python regel `help(find)` uitvoert, dan geeft Python de documentatie voor de functie `find`. Voor het gemak staat deze ook hieronder:

    >>> help(find)
    find(s, *args)
        find(s, sub [,start [,end]]) -> in
        
        Return the lowest index in s where substring sub is found,
        such that sub is contained within s[start,end].  Optional
        arguments start and end are interpreted as in slice notation.
        
        Return -1 on failure.

Lees het eerst even door! Dan gaan we er nu stap voor stap doorheen, laten we bovenaan beginnen met:

	find(s, sub [,start [,end]]) -> in

Dat betekent dat er twee *verplichte* argumenten zijn. `s` (waar je in zoekt),
en `sub` (waar je naar op zoek bent). Vanaf nu noemen we `s` de `haystack` en
`sub` de `needle`. We zoeken naar een naald in een hooiberg. We kunnen dit uitproberen:

    find("atgacatgcacaagtatgcat","atgc")

Het resultaat van deze opdracht is de index van het eerste voorkomen van de
string `atgc`. Probeer ook eens wat andere zoekopdrachten uit. Merk op, dat als
de needle onvindbaar is, je -1 als waarde terugkrijgt.

We gaan verder met het bestuderen van de Python-handleiding. Je kunt
nog aangeven *van waar* en *tot waar* in de string je wilt zoeken. Je kunt zien
dat deze argumenten optioneel zijn door het gebruik van de brackets `[` en `]`.

Als je goed naar het zojuist gegeven voorbeeld kijkt zie je dat `atgc` *twee*
keer voorkomt: één keer op index vijf en één keer op index 15. Om de tweede te vinden kunnen we de optionele argumenten gebruiken. Het eerste argument is `start`, wat aangeeft vanaf welke index `find()` zal zoeken. Door te starten met zoeken ná de index van de eerste match, kun je de tweede match vinden:

    find("atgacatgcacaagtatgcat", "atgc", 6)

(Waarom 6? Tel het even na!)

In de handleiding staat dat de waardes van `start` en `end` geïnterpreteerd
worden zoals dat gebeurt bij `slice notation`. Slice notation heb je pas later
deze week nodig. Voor nu is het belangrijk dat je weet dat `start` inclusief is
en `end` exclusief. Dus er wordt gezocht vanaf start *tot* end.
