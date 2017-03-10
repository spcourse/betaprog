# Installeren

Python is zelf een programma, en moet je dus installeren op je eigen computer. Hieronder vind je de instructies. Mislukt de installatie? Gebruik dan een [online versie van Python](/python/ide).

## Om te beginnen

Je hebt twee programma's nodig op je computer:

1. **Anaconda**, een versie van Python die makkelijk te installeren is. Er zitten ook een boel *packages* bij, waarin extra functionaliteit zit voor grafieken, statistiek en nog allerlei andere dingen.

2. **Visual Studio Code**, een *editor* om code in te schrijven. Dit is in feite een soort tekstverwerker, maar dan speciaal bedoeld voor programmacode.

## Anaconda

Anaconda is een wetenschappelijke distributie die veel handige functionaliteit meelevert, zo zijn er modules voor het tekenen van grafieken en allerlei wiskundige berekeningen. Het nadeel hiervan is dat de installatie vrij groot is, grofweg 400MB. Het kan dus even duren voordat je deze hebt gedownload! De download link vind je [hier](https://www.continuum.io/downloads). Let erop dat je als je een Mac hebt je de versie voor de Mac download, en draait jouw computer op Windows dat je dan de Windows versie download. **Belangrijk**: Wij werken in deze cursus met Python 2.7, download dus de 2.7 versie van Anaconda!

Zodra de download klaar is, moet je het gedownloade bestand uitvoeren. Volg simpelweg de installatie instructies, als het goed is hoef je hier niks aan te veranderen. Maak je geen zorgen, je installeert geen leuke sidebars voor jouw browser. 


## Visual Studio Code

Behalve een installatie van Python, in de vorm van Anaconda, heb je ook een editor nodig om code in te schrijven. Code is op zich niks meer dan tekst. Daarom kan je in de meest basale teksteditor al programmeren. Toch is het handig om een editor te hebben die jou wat ondersteuning biedt, zoals belangrijke keywoorden uitlichten en spellingcorrectie. Daarom vragen we je Visual Studio Code te installeren. [Hier](https://code.visualstudio.com/) vind je de downloadlink. 

Ook hier geldt, zodra je het bestand hebt gedownload moet je deze nog uitvoeren en installeren. Als het goed is hoef je niks aan te passen aan de installatie.


## Proefrit

Nu je zowel Anaconda als Visual Studio Code hebt geïnstalleerd, kunnen we gaan kijken of alles werkt. Voordat we beginnen, maak ergens op jouw computer een map aan genaamd `socode`. Dan heb je een plek om in te werken. Maak vervolgens binnen `socode` een map aan genaamd `week1`.  

Open nu Visual Studio Code. Zodra je dit hebt gedaan zie je het volgende scherm:

![visualstudio](visualstudio.png)

Klik linksboven op het dropdown menu **file** en kies dan onder Windows voor **Open Folder...** en onder Mac voor **Open...**. Open vervolgens de `week1` map die je hebt aangemaakt. Dan zie je de volgende sidebar verschijnen:

![visualnewfile](visualnewfile.png)

Maak via deze sidebar een nieuw bestand aan genaamd `hello.py`. Zet hierin de volgende regel code: 

	print "Hello, World!"

 Sla het bestand `hello.py` op. En nu, voor het moment van de waarheid, druk je op de volgende toets combinatie **ctrl**+**\`**. Dat is dus tegelijkertijd de **ctrl** en **\`**. Dan zie je het volgende scherm verschijnen:

![visualterminal](visualterminal.png)

Dit is de terminal, een plek om commando's in uit te voeren. Wij zullen dit voornamelijk gebruiken om Python aan te roepen, en Python code uit te voeren. Laten we dat meteen doen, voer het volgende commando in:

	python hello.py

Daar heb je het, jouw eerste (werkende) programma.


## checkpy

Om jou te helpen controleren of wat je programmeert ook daadwerkelijk in overeenstemming is met de opdracht, hebben wij een programma geschreven genaamd **checkpy**. Dit programma kun je installeren door in de terminal het volgende commando uit te voeren:

	pip install checkpy

Dit kan even duren, en je zult wat tekst over je scherm zien gaan. Daarna is checkpy geïnstalleerd. Behalve checkpy hebben we ook tests nodig om de opdrachten die jij zometeen gaat maken te testen. Deze tests kun je downloaden door het volgende commando in de terminal te voeren:

	checkpy -d jelleas/progbeta2017tests

Om te testen of alles werkt, en of `hello.py` klopt, voer je het volgende commando in de terminal uit:

	checkpy hello

Kleurt alles groen en zie je enkel vrolijke smileys? Dan zit je goed, en heb je aan onze eisen voor de opdracht voldaan! Mocht er iets rood kleuren, geen paniek! Kijk goed na of je precies hebt gedaan wat er is gevraagd, en mail gerust als je klem zit.