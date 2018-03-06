# Big Data

Een veel voorkomende toepassing van computerprogramma’s is het inlezen, verwerken en analyseren van grote databestanden. Big data! We zullen in deze module leren hoe we data inlezen, en we gebruiken onze kennis van Python om de data te rubriceren en grafieken te maken van onze resultaten.

# Inlezen files en verwerken van de data

![](VanBastenKlein.jpg){:.inline}

Net zoals je getallen in het decimale, hexadecimale of binaire formaat weer kan geven wordt ook data in verschillende formaten bewaard in data-bases. Hier zullen we data bekijken die is opgeslagen in het zogenaamde CSV formaat (comma separate values): 'platte tekst', waarbij op elke regel verschillende variabelen gescheiden zijn door een komma. Dit is trouwens ook het formaat dat je krijgt als je je banktransacties download of een Excel file wegschrijft.

We gaan het inlezen en verwerken van data doen aan de hand van een voorbeeld:  de statistieken van voetballer Marco van Basten. Iemand heeft in een [tekstbestand](http://www.nikhef.nl/~ivov/Python/Voetbal/VanBasten.txt) bijgehouden hoeveel wedstrijden hij gespeeld heeft en hoeveel doelpunten hij gemaakt heeft. Dit is de tekst van het bestand:

    198182, Ajax, 1, 1
    198283, Ajax, 20, 9
    198384, Ajax, 26, 28
    198485, Ajax, 33, 22
    198586, Ajax, 26, 37
    198687, Ajax, 27, 31
    198788, AC Milan, 11, 3
    198889, AC Milan, 33, 19
    198990, AC Milan, 26, 19
    199091, AC Milan, 31, 11
    199192, AC Milan, 31, 25
    199293, AC Milan, 15, 13
    199394, AC Milan, 0, 0
    199495, AC Milan, 0, 0

> Let op: als je het bestand met Windows Kladblok/Notepad opent, dan staat alle data achter elkaar. Dat maakt niet uit voor de goede werking van je programma's.

Hieronder gaan we aan de slag met het beantwoorden van enkele vragen met behulp van dit databestand:

- wat zijn de voetbalseizoenen waarin Van Basten meer dan 20 keer gescoord heeft?
- wat is het totaal aantal doelpunten dat Van Basten heeft gescoord voor al zijn clubs?

## Stap 1: openen van de file, inlezen van de regels

Omdat het doorlopen van files in een computertaal een standaard procedure is, zijn er een aantal gemakkelijke commando's beschikbaar. Het `open` commando bijvoorbeeld dat vervolgens gebruikt kan worden om dingen uit die file te lezen of juist in weg te schrijven. Het volgende codefragment opent de file en gebruikt een `for`-loop om steeds de volgende regel in te lezen. De informatie in een regel van de file wordt opgeslagen in de variable `line`. Dit korte programma voert verder geen analyse uit maar print simpelweg `line` naar het scherm.

    input_file = open('VanBasten.txt', 'r')
    for line in input_file:
        print(line)
    input_file.close()

> Tip: klik in Canopy met de rechtermuisknop op de *opdrachtregel* van Python, en kies "Keep directory synced to editor". Dan kan Python het bestand `VanBasten.txt` altijd vinden.

De `'r'` bij de functie `open()` betekent 'read', lezen dus. Als je dit programma uitvoert zal je zien dat bijvoorbeeld de regel van 1988 zo op het scherm verschijnt:

    198889, AC Milan, 33, 19

## Stap 2: splitsen van de regel en in een lijst opslaan

Elke regel bestaat uit verschillende elementen die Toegang tot de verschillende parameters in de regel krijg je door de regel in stukken te ’knippen’. Dit doe je met het Python commando `split()`. Als parameter kan je aan split meegeven waar hij moet knippen. Wij willen dat hij bij elke komma (`,`) knipt, dus we voeren het volgende commando uit: `line.split(',')`. Dit commando produceert een lijst met elementen die de losse stukken bevatten. Hierop kun je afzonderlijke bewerkingen uitvoeren.

    input_file = open('VanBasten.txt', 'r')
    for line in input_file:
        print(line)
        data_opgeknipt = line.split(',')
        print(data_opgeknipt)
    input_file.close()

De regel met 1988 is nu in stukken geknipt en in een lijst gezet:

    ['198889', ' AC Milan', ' 33', ' 19\t\n']

De karakters `"\t"` (tab) en `"\n"` (return aan eind van de regel) zijn ook zichtbaar, hoewel we daar niet zoveel aan hebben.

## Stap 3: opslaan van de informatie in variabelen

In deze opgave zijn we alleen geinteresseerd in het seizoen en het aantal doelpunten. Zoals je ziet is die informatie opgeslagen in respectievelijk element 0 en 2 van de lijst.

Die informatie kunnen we nu dus opslaan in een variabele:

    seizoen = data_opgeknipt[0]
    doelpunten = data_opgeknipt[2]

### Probleem 1: uitpakken van variabelen

Zoals je ziet hebben de makers van de file het seizoen 1988-1889 in 1 getal
weergegeven: 198889. Slim van ze, maar wij zijn alleen geinteresseerd in het
jaar dat het seizoen is gestart.

Het handige voor ons is dat alle data nog als `string` in de lijst staat. Hoewel `198889` gezien kan worden als getal, behandelen we het nu als stuk tekst. Het eerste jaartal (1988) is verpakt in de eerste 4 karakters van die string. Om alleen die op te vragen kan je dus van element 0 in de lijst alleen de eerste 4 karakters selecteren.

    seizoen = data_opgeknipt[0][0:4]
    doelpunten = data_opgeknipt[2]

### Probleem 2: getallen versus tekst

Vanaf nu is het handig om de gegevens juist als getal te zien, zodat we ermee kunnen rekenen. Om te zorgen dat het jaartal en het aantal doelpunten een getal worden moet je ze expliciet omzetten.

    seizoen = int(data_opgeknipt[0][0:4])
    doelpunten = int(data_opgeknipt[2])

Je hebt nu dus de informatie tot je beschikking in een variabele. Vervolgens kun je met alle Python die je eerder hebt geleerd, de analyse uitvoeren.

## Stap 4: het analyseren van de data

We wilden het aantal totaal aantal doelpunten uitreken dat Van Basten voor zijn clubs heeft gescoord en ook aangeven in welke seizoenen hij meer dan 20 doelpunten maakte.

    input_file = open('VanBasten.txt', 'r')
    totaal_doelpunten = 0

    for line in input_file:
        data_opgeknipt = line.split(',')

        seizoen = int(data_opgeknipt[0][0:4])
        doelpunten = int(data_opgeknipt[2])

        totaal_doelpunten = totaal_doelpunten + doelpunten   

        if(doelpunten > 20):
            print("In {} scoorde Van Basten > 20 doelpunten, nl {}".format(seizoen, doelpunten))

    print("TOTAAL: In totaal scoorde Van Basten {} clubdoelpunten".format(totaal_doelpunten))
    input_file.close()

Gebruik altijd `close()` om het bestand netjes te sluiten na gebruik.

## Oefening

Download de file met de doelpunten statistiek van Van Basten en probeer de bovenstaande resultaten te reproduceren.
