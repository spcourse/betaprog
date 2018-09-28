# Online programmeren

Om online te kunnen programmeren maken wij gebruik van een online integrated development environment, de CS50 IDE. Om toegang te krijgen tot deze omgeving moet je wat stappen door. Daarna kun je gelijk aan de slag!

## Aanmaken van de CS50 IDE

Om toegang te krijgen tot de ontwikkelomgeving kun je het volgende doen:

1. Registreer bij edX op [https://courses.edx.org/register](https://courses.edx.org/register). Je hoeft je niet aan te melden voor een cursus.

2. Bevestig je account via de link in je e-mail.

3. Login met jouw net aangemaakte account op [https://cs50.io/](https://cs50.io/).

4. Er wordt je wellicht gevraagd een nieuwe workspace aan te maken. Vul hiervoor de volgende gegevens in:

    - Workspace name: ide50
    - Description: CS50 IDE
    - Template: Harvard's CS50 (*belangrijk*)

Na het aanmaken van de workspace, zie je dit scherm in jouw browser:

![cs50](cs50.png)

We noemen dit een geïntegreerde ontwikkelomgeving, omdat je hier alles vindt wat je nodig hebt om programma's te ontwikkelen: een overzicht van je bestanden, een tekst-editor om programma-code in te tikken, en een plek om je programma's uit te proberen.

Mocht je liever een wat donker scherm willen (zoals alle hackers ;-)), ga dan naar het dropdown menu **view** -> **night mode**. Voel je ook vrij om nog een beetje te speuren door de dropdown menu's. Het is okee als je nog niet begrijpt wat alles betekent.

## Proefrit

Links bovenin zie je een map-icoontje met daarachter de tekst **~/workspace**. Rechtsklik of ctrl+klik hierop en selecteer vervolgens **New Folder**. Noem deze map **week1**.

Onderin het scherm zie je de terminal, een omgeving waarin je commando's kan uitvoeren. Tik maar eens het volgende commando in achter de `$`:

    ls

Het commando `ls` is een afkorting van list. Dit commando geeft een lijst van alle bestanden en mappen in de "huidige" map. Standaard begint de terminal in de map `~/workspace`, en door het uitvoeren van het commando `ls` zie je alleen de map `week1` die je net hebt aangemaakt. Laten we nu de "huidige map" veranderen door middel van het volgende commando:

    cd week1

Het commando `cd` is hier een afkorting van compact disc... uh, nee... *change directory*. Het verandert dus de huidige map naar een andere map, in dit geval `week1`. Zou je nu `ls` nog een keer uitvoeren, dan zijn er geen resultaten (je krijgt dan ook letterlijk geen zichtbare resultaten). Laten we hier verandering in brengen door middel van het volgende commando:

    touch hello.py

Nu hebben we een bestand aangemaakt genaamd `hello.py` binnen de map `week1`. Om dit te controleren voer nog een `ls` uit. Het commando `touch` kijkt of een file (in dit geval `hello.py`) bestaat, en zo niet, dan maakt het deze aan.

Om de file `hello.py` te openen, ga je naar links bovenin je scherm waar je een map-icoontje ziet gevolgd door de tekst `~/workspace`. Druk op het driehoekje ernaast om de map `~/workspace` uit te klappen. Doe vervolgens hetzelfde bij de map `week1`, en dubbelklik dan op de file `hello.py`. Nu opent er een nieuwe tab genaamd `hello.py` en kunnen we meteen beginnen met programmeren!

Voer in het bestand `hello.py` de volgende regel code in:

    print("Hello, World!")

Sla `hello.py` vervolgens op. Dit is jouw eerste (Python-)programma, en deze kunnen we uitvoeren door het volgende commando in de terminal te voeren:

    python hello.py

Als het goed is zie je direct daaronder de woorden: `Hello, World!` staan.

## Extra tips

Handig om te weten is dat je via het commando `cd` ook een map omhoog kan via:

    cd ..

Hier staat `..` voor de map boven de huidige. Wil je verder omhoog? Dan kan dat via `../..`. Ook kan je `cd` de instructie geven om niet relatief van de huidige map te bewegen, maar absoluut ten opzichte van jouw login map. Bijvoorbeeld:

    cd ~/workspace/week1

Dat brengt je meteen naar de map `week1` binnen `workspace`.

## Installeren van Matplotlib en Checkpy

We gebruiken een programma om te checken of je opdrachten op de juiste manier werken. We vragen je om heel precies te zijn in het geven van de juiste uitvoer. Hiervoor hebben wij een programma geschreven dat `checkpy` heet en dit wordt niet standaard meegeleverd met de online ontwikkelomgeving. Daarnaast gaan we aan de slag met het plotten van grafieken, en hiervoor hebben we een Python module nodig genaamd `matplotlib`. Ook deze moeten we apart downloaden.

Om zowel `matplotlib` en `checkpy` te downloaden voer je in de terminal één voor één de volgende commando's uit:

    pip install matplotlib
    pip install checkpy
    checkpy -d Jelleas/progbgtests

Het kan best eventjes duren per commando, en er zal aardig wat tekst over je scherm ratelen. Mocht er weinig tekst staan, speur dan naar een eventuele foutmelding en vraag eventueel om hulp!

Om te testen of alles werkt, en of `hello.py` klopt, voer je het volgende commando in de terminal uit:

    checkpy hello

Kleurt alles groen en zie je enkel vrolijke smileys? Dan zit je goed, en heb je aan onze eisen voor de opdracht voldaan! Mocht er iets rood kleuren, geen paniek! Kijk goed na of je precies hebt gedaan wat er is gevraagd, en vraag gerust als je klem zit.
