# Printen

Als je een programma hebt geschreven kun je het uitvoeren (*runnen*). De computer loopt dan stap voor stap door je programma en voert de instructies uit die op elke regel staan.

Maak tekstbestand **oefening.py** (weet je nog hoe?) en zet er de volgende regels in:

    print("Hallo, wereld!")
    print("Hee, hallo daar.")
    print("Zo tikt het lekker door.")
    print("Grappig")
    print('Hee, print dit nog?')
    print("Ivo's computer doet het vandaag niet.")
    print('Hij zei: "Hallo."')

> Oefenen doe je in deze cursus door de voorbeelden letterlijk over te tikken. Gebruik niet de *copy-paste* functie, want dan maak je geen fouten en dan leer je veel minder. Tik dus alle voorbeelden over en verbeter ze als je een foutmelding krijgt!

Start nu het programma door in de Terminal in te geven:

    python oefening.py

Wat komt er uit? Heb je nog tikfouten gemaakt? En heb je gezien dat de aanhalingstekens soms verschillen? Je moet de reeks letters achter `print` starten en eindigen met aanhalingstekens (enkele of dubbele). Zo'n reeks noemen we een **string**.

We kunnen ook meerdere waarden op één regel printen. Standaard voegt het `print`-commando een **ENTER** toe aan de tekst, zodat de volgende `print` op een nieuwe regel doorgaat. Je kunt ook zorgen dat deze **ENTER** weggelaten wordt:

    print("De temperatuur is", end="")
    print(8, end="")
    print("graden")

Daarmee wordt de hele boodschap keurig op één regel geprint. Probeer vooral uit!

Je kan dit ook bereiken door meerdere waarden in één printstatement te stoppen:

    print("De temperatuur is", 8, "graden")

## Berekeningen

Voeg vervolgens ook nog de volgende regels toe:

    print(1)
    print(1 + 1)
    print(1 + 1 + 1)
    print(3 + 2)
    print(8)
    print(5 + 8 + 8 - 8)
    print("5 + 8 + 8 - 8")

Je kunt dus ook rekenen. Het *resultaat* van de berekening wordt naar het scherm geprint. Behalve die laatste dan: daar staat de formule (*expressie*) tussen aanhalingstekens. Net als hierboven bij de tekstjes. Dat is dus een string en geen formule die berekend kan worden.

> Krijg je een foutmelding als je je programma uitvoert? Dan is de kans groot dat je een tikfout hebt gemaakt waardoor Python niet meer begrijpt wat de bedoeling is. Kijk goed waar je de fout hebt gemaakt en probeer deze op te lossen. Kom je er niet uit, vraag dan vooral om hulp. Foutmeldingen leren begrijpen is een belangrijk onderdeel van deze cursus. Dat is ook waarom we heel graag willen dat je tijdens het oefenen fouten maakt!

## Operators

Hieronder vind je een lijstje van operators die je kunt gebruiken om formules samen te stellen.

| operator | uitleg                    |  
| -------- | ------------------------- |  
| `1 + 2`  | optellen                  |  
| `2 - 1`  | aftrekken                 |  
| `1 * 2`  | vermenigvuldigen          |  
| `2 / 1`  | delen                     |  
| `2 % 1`  | modulus (rest bij deling) |  
| `2 ** 1` | machtsverheffen           |  

Let op: als je twee gehele getallen deelt met de `/`-operator, zal er altijd een geheel getal uitkomen. Dan is `3/2` dus niet `1.5`, maar `1`. Dat is waarom de `%`-operator er mooi bijpast; die geeft de "rest", ofwel wat overblijft.
