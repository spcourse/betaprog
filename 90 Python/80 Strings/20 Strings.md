# Strings

In [module 1](/python/basiselementen) heb je al kennis gemaakt met het datatype **string**. We definieerden een string als een reeks letters. In Pythoncode worden ze geschreven met aanhalingstekens: `'enkele'` of `"dubbele"`.

## Indexeren

Je kunt een willekeurig teken (een **character**) uit een string pakken door de string
te indexeren:

	>>> woonplaats = "Amsterdam"
	>>> print woonplaats[0]
	A
	>>> print woonplaats[1]
	m

Dit werkt dus net als bij een list!

## Strings samenvoegen

Het is ook mogelijk strings samen te voegen:

	>>> land = "Nederland"
	>>> print land
	Nederland
	>>> locatie = woonplaats + ", " + land
	>>> print locatie
	Amsterdam, Nederland

Zo hebben we één string, `locatie`, samengesteld uit drie andere strings.

## Strings doorzoeken met de `find` functie

Python heeft aardig wat functies ingebouwd om je te helpen met strings. Deze zijn te vinden in de module `string`. Dooor de volgende regel bovenaan je Pythoncode te zetten, kun je deze functies gebruiken:

    import string

Een functie die in de komende opdrachten erg van pas komt is `find`. Je kunt de `help`-opdracht gebruiken om hierover meer informatie te vinden. Daarvoor moet je eerst `python` opstarten.

	# python
	Python 2.7.10 (default, Oct 12 2015, 13:57:30) 
	Type "help", "copyright", "credits" or "license" for more information.
	>>> help(string.find)
	find(s, *args)
	    find(s, sub [,start [,end]]) -> in
    
	    Return the lowest index in s where substring sub is found,
	    such that sub is contained within s[start,end].  Optional
	    arguments start and end are interpreted as in slice notation.
    
	    Return -1 on failure.

Lees het eerst even door! Dan gaan we er nu stap voor stap doorheen, laten we bovenaan beginnen met:

	string.find(s, sub [,start [,end]]) -> in

Dat betekent dat er twee *verplichte* argumenten zijn. `s` (waar je in zoekt),
en `sub` (waar je naar op zoek bent). Vanaf nu noemen we `s` de `haystack` en
`sub` de `needle`. We zoeken naar een naald in een hooiberg. We kunnen dit uitproberen:

    string.find("atgacatgcacaagtatgcat","atgc")

Het resultaat van deze opdracht is de index van het **eerste** voorkomen van de
string `atgc`. Probeer ook eens wat andere zoekopdrachten uit. Merk op, dat als
de needle onvindbaar is, je -1 als waarde terugkrijgt.

We gaan verder met het bestuderen van de Python-handleiding. Je kunt
nog aangeven *van waar* en *tot waar* in de string je wilt zoeken. Je kunt zien
dat deze argumenten optioneel zijn door het gebruik van de brackets `[` en `]`.

Als je goed naar het zojuist gegeven voorbeeld kijkt zie je dat `atgc` *twee*
keer voorkomt: één keer op index vijf en één keer op index 15. Om de tweede te vinden kunnen we de optionele argumenten gebruiken. Het eerste argument is `start`, wat aangeeft vanaf welke index `find()` zal zoeken. Door te starten met zoeken ná de index van de eerste match, kun je de tweede match vinden:

    string.find("atgacatgcacaagtatgcat", "atgc", 6)

(Waarom 6? Tel het even na!)

In de handleiding staat dat de waardes van `start` en `end` geïnterpreteerd
worden zoals dat gebeurt bij `slice notation`. Voor nu is het belangrijk dat je weet dat er wordt gezocht vanaf `start` **tot** `end`.
