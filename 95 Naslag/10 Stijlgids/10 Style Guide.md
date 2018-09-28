# Stijlgids

Programmacode is bij voorkeur goed leesbaar, niet alleen voor jezelf, maar ook voor een ander met wie je samenwerkt. Bij deze cursus is het belangrijk om niet alleen te kijken naar de functionaliteit van de code ("hoe maak ik dit") maar ook naar de kwaliteit ("hoe goed is dit leesbaar"). Eerder hebben we al kort een aantal richtlijnen genoemd voor het gebruiken van commentaar bij stukjes code. Maar er zijn meer aspecten, die je hieronder kunt vinden.

## Terminologie

Om te beginnen een paar dingen over terminologie:

- We hebben het vaak over "programma's". Een *programma* is een op zichzelf staan geheel, een stuk software dat een taak kan uitvoeren. Denk aan een rekenmachine op je telefoon. Of Microsoft Word. Python zelf is ook een programma. En jij schrijft in deze cursus dus een heleboel verschillende programma's.

- We hebben het ook vaak over "code". Een stuk *code* is een fragment, vaak onderdeel van een programma. Het woord code is niet telbaar, dat wil zeggen dat je niet kunt spreken van "een code" of "twee codes". Je kunt wel zeggen "mijn code werkt niet", dan gaat het kennelijk over het stuk code dat je zojuist geschreven hebt.

- Een programma bestaat uit "regels" code.

## Taalkeuze

Hieronder zul je zien dat de voorbeeldcode en het commentaar doorgaans in het Engels gesteld zijn. In de cursus werken we vaak in het Nederlands. Het is hoe dan ook belangrijk om de taalkeuze goed af te stemmen: variabelenamen en commentaar beide in het Nederlands óf beide in het Engels.

## Commentaar

Het is net zo makkelijk om te veel commentaar in je code te schrijven als te weinig. Om te bepalen waar commentaar nou echt nodig is, moeten we ons een beetje verplaatsen in de lezer van de code. Dat kan iemand anders zijn, iemand die jouw code gebruikt om een gaaf programma te schrijven. Maar je kunt het ook zelf zijn, een paar maanden later, wanhopig proberend om nog een beetje kaas te maken van hoe het ook alweer in elkaar zat. Die lezer, wat heeft die nodig?

- Samenvattingen van stukjes code. Meestal heb je je programma's of functies opgedeeld in functionele blokjes. Misschien zijn het maar een paar regels code. Het is vaak niet zo moeilijk om van zo'n blokje code samen te vatten wat de bedoeling is.

- Waarschuwingen voor potentiële problemen. Misschien heb je voor een bepaald stuk code een tijdelijke oplossing bedacht, waarvan je weet dat die niet in alle gevallen gaat werken (maar voor nu is het wel goed zo). Dan is het handig dat te documenteren door middel van een comment.

- Uitleg van erg complexe algoritmen. Soms is het gewoonweg niet anders dan dat je een behoorlijk complex systeem aan het schrijven bent. In dat geval kun je uitleg geven, of zelfs maar een link naar meer informatie.

- Bronvermelding. Om niet van plagiaat beschuldigd te worden is het natuurlijk belangrijk altijd een bron te vermelden als je een stuk code geheel of gedeeltelijk overneemt van iemand anders. Zelfs als je het nog flink verbouwt hoort dat erbij.

### Voorbeeld 1

Wanneer hoeft het nou bijvoorbeeld niet? Als je variabelenamen erg duidelijk zijn, dan hoef je misschien geen commentaar te schrijven. Maar soms kun je toch nog wat toevoegen:

    # bereken gemiddelde cijfer voor deze student
    average = sum / assignment_count + 1

(Nu weten we dat het niet zomaar om een gemiddelde gaat, maar om een cijfer. Afhankelijk van de rest van het programma heeft dit commentaar toegevoegde waarde.)

#### Schrijfwijze

Let ook op de schrijfwijze: geen hoofdletter, geen punt, en een spatie na het hekje `#`. Het commentaar staat *boven* de regel waar het over gaat.

### Voorbeeld 2

Het is gebruikelijk om bovenaan programma's wat algemene informatie op te nemen. Meestal gaat het om de namen van de auteurs, en een samenvatting van het doel van het programma.

    # Name: Jane Lee
    # Collaborators: John Doe
    #
    # This program calculates the average values of a series
    # of numbers input by the user.

#### Schrijfwijze

Let ook hier even op de schrijfwijze. De samenvatting in het commentaar hierboven is toch wat te lang om op één enkele regel op te nemen. In dat geval moeten we het expliciet over meerdere regels verdelen. Gewoon een regel toevoegen met een `#` ervoor.

We hebben ervoor gekozen om het nu na ongeveer 60 tekens af te kappen. De bedoeling is dat regels een redelijke lengte hebben: lezen gaat het prettigst als regels zo'n 45--90 tekens lang zijn, net als in boeken.

## Indentatie

Indentatie gaat over het toevoegen van witruimte aan het begin van een regel. In Python is het in veel gevallen noodzakelijk om een regel te beginnen met spaties, bijvoorbeeld als je een functie definieert:

    def sum(x, y):
        result = x + y
        return result

Let wel op! Je kunt de extra witruimte invullen met tabs of met spaties. In heel veel gevallen is een tab zichtbaar als 8 spaties, maar soms ook als 4 of 2. Hoe dan ook, het wordt een probleem als je tabs en spaties door elkaar gaat gebruiken, want dan is onduidelijk wat de bedoeling is.

    def sum(x, y):
        result = x + y     # vier spaties
            return result  # 1 tab is hier 8 spaties geworden

De `return` staat een stukje extra naar rechts, maar in feite is het één tab. Het resultaat is dat het een stuk moeilijker leesbaar is. Bovendien begrijpt Python er ook niet zoveel meer van. Je krijgt al snel een foutmelding als je zoiets doet. Gebruik dus alleen maar spaties, of alleen maar tabs om te indenteren.

Oh, en misschien goed om nog even te herhalen. Als een regel eindigt op een dubbele punt (`:`), dan moeten alle regels eronder geïndenteerd worden. Tenminste, de regels die er inderdaad bij horen.

    def sum(arrayOfNumbers):
        result = 0
        for number in arrayOfNumbers:
            result = result + number
        return result

Hier zie je dat de regel `result = result + number` bij de `for`-loop hoort. De `return` staat echter weer een stukje naar links, waardoor je weet dat deze niet bij de `for`-loop hoort.

## Naamgeving

Veel elementen in je code hebben een *naam*. Het gaat dan vooral om functies en variabelen. We geven wat richtlijnen.

### Functies

De namen van functies mogen zo lang zijn als je wilt, mits redelijk. In dit geval is het belangrijk dat het doel van de functie zo duidelijk en precies mogelijk omschreven wordt.

    def user_average_this_year():
        ...

Je ziet dat in de naam meerdere woorden staan, die gescheiden zijn met een underscore (`_`). Dit is gebruikelijk in Python, alle functienamen met meerdere woorden zijn geschreven met kleine letters en met underscores ertussen.

### Variabelen

Namen van variabelen hou je het liefst net wat korter dan functienamen, omdat ze meestal vaker voorkomen. Denk dan aan één of twee woorden. Een paar voorbeelden:

    wall_height = 2.34
    earth_circumference = 40007.86
    total_rainfall = 823.3

Woorden afkorten is meestal niet de bedoeling. Hiervan wordt je code een stuk lastiger te lezen (een erg luie programmeur zou bovenstaande variabelen wellicht `wh`, `ecirc` en `t_rain` hebben genoemd, maar hoe moet je nog achterhalen wat daar bedoeld wordt?).

Er zijn uitzonderingen. Je programma gaat namelijk weleens over een bepaald onderwerp waar afkortingen gebruikelijk zijn. Wiskunde en natuurkunde hebben dit natuurlijk wel vaker. 

    v_rabbit = 0.002            # v is for "velocity"
    x_rabbit = 23.11            # x is for "displacement"

Toch zie je dat we de uitleg er wel bij moeten zetten, dus het is een goed idee om de afkortingen zoveel mogelijk te vermijden tenzij het evident is wat bedoeld wordt.

## Witregels en extra spaties

Net als in andere media waarin tekst een belangrijke rol speelt, kan in programma's witruimte worden ingezet om de leesbaarheid te vergroten.

### Witregels

Zoals hierboven beschreven bij "commentaar" kun je je programma vaak opdelen in blokjes code. Hiermee kun je bijvoorbeeld de verschillende stappen beschrijven in een algoritme. Zie hier een programma dat in drieën gesplitst is:

    number = input("Please enter a number: ")
    while number < 0:
        number = input("Please enter a *positive* number: ")

    # calculations: uses a complex loop to handle special cases
    while(number > 0):
        number -= 1
    if number == 0:
        number += 1

    # output: might not print zero (e.g., if user put in a float)
    print(user_input)

De drie onderdelen zijn respectievelijk: de gebruikersinvoer, de berekening, en de uitvoer. Die onderdelen kom je wel vaker tegen natuurlijk. Let ook op de aanwijzingen die we in het commentaar hebben toegevoegd: eerst uitleg van complex algoritme, daarna een waarschuwing dat het misschien niet altijd werkt (en vooral: wanneer!).

### Spaties rondom operatoren

Operatoren zoals `+`, `==`, `%` en `**` zijn veelgebruikt in formules en vergelijkingen. Het is de bedoeling om hier heel bewust spaties rondom de operatoren te plaatsen, zodat we formules goed leesbaar blijven:

    i = i + 1
    submitted += 1
    x = x * 2 - 1
    hypotenuse_squared = x * x + y * y
    c = (a + b) * (a - b)
