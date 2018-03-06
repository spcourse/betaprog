# Strings

In [module 1](/python/basiselementen) heb je al kennis gemaakt met het datatype **string**. We definieerden een string als een reeks letters. In Pythoncode worden ze geschreven met aanhalingstekens: `'enkele'` of `"dubbele"`.

## Indexeren

Je kunt een willekeurig teken (een **character**) uit een string pakken door de string
te indexeren:

    >>> woonplaats = "Amsterdam"
    >>> print(woonplaats[0])
    A
    >>> print(woonplaats[1])
    m

Dit werkt dus net als bij een list!

## Strings samenvoegen

Het is ook mogelijk strings samen te voegen:

    >>> land = "Nederland"
    >>> print(land)
    Nederland
    >>> locatie = woonplaats + ", " + land
    >>> print(locatie)
    Amsterdam, Nederland

Zo hebben we één string, `locatie`, samengesteld uit drie andere strings.

## Strings doorzoeken met de `find` functie

Python heeft aardig wat functies ingebouwd om je te helpen met strings. Een functie die in de komende opdrachten erg van pas komt is `find`. Je kunt de `help`-opdracht gebruiken om hierover meer informatie te vinden. Daarvoor moet je eerst `python` opstarten.

    # python
    Python 3.6.0 (default, Aug 10 2017, 07:53:09)
    [GCC 4.8.4] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> help(str.find)
    find(...)
      S.find(sub[, start[, end]]) -> int

      Return the lowest index in S where substring sub is found,
      such that sub is contained within S[start:end].  Optional
      arguments start and end are interpreted as in slice notation.

      Return -1 on failure.

Lees het eerst even door! Dan gaan we er nu stap voor stap doorheen, laten we bovenaan beginnen met:

    S.find(sub[, start[, end]]) -> int

Dat betekent dat er twee *verplichte* argumenten zijn: `S` (waar je in zoekt),
en `sub` (waar je naar op zoek bent). We kunnen dit uitproberen:

    "atgacatgcacaagtatgcat".find("atgc")

Het resultaat van deze opdracht is de index van het **eerste** voorkomen van de
string `atgc`. Probeer ook eens wat andere zoekopdrachten uit. Merk op, dat als
de needle onvindbaar is, je -1 als waarde terugkrijgt.

We gaan verder met het bestuderen van de Python-handleiding. Je kunt
nog aangeven *van waar* en *tot waar* in de string je wilt zoeken. Je kunt zien
dat deze argumenten optioneel zijn door het gebruik van de brackets `[` en `]`.

Als je goed naar het zojuist gegeven voorbeeld kijkt zie je dat `atgc` *twee*
keer voorkomt: één keer op index vijf en één keer op index 15. Om de tweede te vinden kunnen we de optionele argumenten gebruiken. Het eerste argument is `start`, wat aangeeft vanaf welke index `find()` zal zoeken. Door te starten met zoeken ná de index van de eerste match, kun je de tweede match vinden:

    "atgacatgcacaagtatgcat".find("atgc", 6)

(Waarom 6? Tel het even na!)

In de handleiding staat dat de waardes van `start` en `end` geïnterpreteerd
worden zoals dat gebeurt bij `slice notation`. Voor nu is het belangrijk dat je weet dat er wordt gezocht vanaf `start` **tot** `end`.
