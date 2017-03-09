# Hello

## tl;dr

Implementeer een programma dat een simpele begroeting uitprint als volgt:

	Hello, world!

Voor wat context, zie [wikipedia](https://nl.wikipedia.org/wiki/Hello_world_(programma)).

## Specificatie

Tijd om ons eerste programma te schrijven. Maak een nieuw bestand aan en sla dit op als `hello.py`. Plaats in het bestand het volgende stukje Python code:

	print "Hello, world!"

Zie hoe sommige delen van de tekst anders kleuren in de editor. Dit is "syntax highlighting", en wordt door de editor toegevoegd om de programmacode voor jou als programmeur te verduidelijken.

Sla nu je bestand op, en *run* dit door het volgende commando uit te voeren in de terminal:

	python2 hello.py

Als het goed is zie je nu in de terminal de tekst `Hello, world!` staan.

## Testen

Test altijd zelf je programma's. Staan er bijvoorbeeld geen extra hoofdletters of missende uitroeptekens in het resultaat? Is de uitvoer *precies* zoals in het voorbeeld uit de opgave?

Ben je tevreden? Test je programma dan met `checkpy`. Daarmee kun je in deze cursus controleren of je programma's volledig voldoen aan de specificaties uit de opgaven. Dit doe je door het volgende commando uit te voeren in de terminal:

	checkpy hello

Het is hierbij wel belangrijk dat wanneer je dit commando uitvoert je je in de map bevindt waar jouw opdracht `hello.py` zich bevindt. Als je nu alleen maar *happy* smileys ziet dan slagen de tests, en kun je verder met de volgende opdracht. Slagen ze niet, dan is het tijd om te *debuggen*.

Zie je de volgende error? **"No such file or directory:"** Check dan of je je wel in de juiste map (directory) bevindt. Was dit niet het probleem? Kijk dan nog eens goed naar je code, staat er bijvoorbeeld geen extra spatie ergens? Elke letter telt! Kom je er niet uit, stuur een mail!

Ben je straks klaar met alle opdrachten van de week? Dan kun je al je bestanden in één keer testen door het volgende commando uit te voeren:

    checkpy -m module1

Dit checkt voor jou in één keer al jouw opdrachten van de eerste module. 

Let wel, checkpy is erg streng. Het is de bedoeling dat je zorgt dat je programma de check door komt. Mocht je niet begrijpen waarom je antwoord wordt afgekeurd, spreek dan meteen een assistent aan tijdens het practicum. We kijken dan met je mee.
