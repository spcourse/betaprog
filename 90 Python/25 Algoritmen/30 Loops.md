# Loops

Soms is het handig om van een hele reeks getallen te bepalen of ze aan een bepaalde eis voldoen. Omdat zulk "dom werk" precies is wat een computer zo goed kan, is dat een basiselement in bijna alle programmeertalen. We noemen dit een **loop**.

## Herhaling

Als we tien keer iets willen doen, dan ziet het er bijvoorbeeld zo uit:

    for x in range(1, 11):
        print("hallo")

We gebruiken hier het commando `range()` met een begingetal en eindgetal om aan te geven hoe vaak de loop uitgevoerd zal worden. Daarbij telt Python van het begin *tot* het einde---dus niet *tot en met*!

Verder zie je dat we net als bij `if` weer kunnen inspringen om duidelijk te maken welke regel herhaald moet worden. Er staan hier vier spaties vóór `print`: dat is dus precies de instructie die meerdere malen uitgevoerd gaat worden.

## Voorbeelden van loops

![embed](https://vimeo.com/album/5380755/embed)

## Stapgrootte van een loop

Je kunt met `range` ook de stapgrootte opgeven. `for` telt dan zoals voorheen van begin tot einde, en neemt niet stappen van 1, maar van de grootte die jij hebt ingesteld. Dit ziet er zo uit:

    for getal in range(1, 100, 10):
        ...

Elke stap in de `for`-loop zal dan steeds 10 verder zijn dan de vorige. Denk even na welke stappen gemaakt zouden worden bij de loop hierboven; of neem de code over en zet er een `print` in om het gedrag te bestuderen.

## Soorten loops

Afhankelijk van de toepassing kies je een soort loop, zoals je in de filmpjes hierboven hebt gezien. In feite zijn `for` en `while` ook uitwisselbaar. Deze `for`-loop:

    for i in range(100):
        print("hi")

is gelijk aan de volgende `while`-loop:

    i = 0
    while i < 100:
        print("hi")
        i = i + 1

De `for`-loop is duidelijk wat compacter en zo sneller leesbaar. Dat is dus ook de loop die het vaakst gebruikt wordt. Maar toepassingen zoals gebruikersinvoer kun je eigenlijk alleen maar met een `while`-loop schrijven, dus deze heeft ook z'n nut.
