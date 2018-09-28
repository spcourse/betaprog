# Het duizendste priemgetal

Implementeer een programma dat op verzoek het $$n$$-de priemgetal genereert.

	Naar welk priemgetal bent u op zoek? 1000
	7919

## Achtergrond

Zoals gezegd is een computer geweldig in het snel uitvoeren van een heleboel "domme" stappen. Een voorbeeld waar een computer zó veel effectiever is dan een enkele persoon, is het uitrekenen van priemgetallen. De definitie van een priemgetal is niet al te ingewikkeld. Maar bepalen hoeveel delers een willekeurig getal heeft kan ontzettend veel tijd kosten. Python to the rescue!

## Specificatie

- Vraag de gebruiker om de rangorde van het priemgetal (het hoeveelste) in te voeren. Dit moet natuurlijk een geheel en positief getal zijn. Je programma hoeft niet te controleren of de input wel een geheel en positief getal is, maar moet werken voor alle gehele positieve getallen als input.

- Als de gebruiker een rangorde invult die niet toegestaan is, dan vraag je de gebruiker opnieuw naar de rangorde. Net zo lang tot de gebruiker een geldige rangorde invult. Omdat je niet weet hoe vaak dat zal zijn, moet het een `while`-loop worden!

- Zodra de rangorde bekend is, bereken het juiste priemgetal en rapporteer dit terug aan de gebruiker.

- Zorg dat het programma niets anders uitvoert dan dit getal, zoals in het voorbeeld bovenaan de opdracht!

## Probleemanalyse

Neem vóór je gaat programmeren eerst een paar minuten om met **pen en papier** te schetsen hoe je zelf het probleem aan zou pakken, hoe je het probleem kunt opdelen in overzichtelijke stappen. De specificatie hierboven geeft al wat hints daarvoor!

Bij deze opdracht nemen we je aan de hand door een aantal stappen te geven om te doorlopen tijdens het ontwikkelen van de juiste oplossing.

## Stap 1: priem-check

Een belangrijk deel van de omschrijving hierboven is dat het om priemgetallen gaat. Wat is een priemgetal? Dat moeten we in Python zien uit te drukken.

Schrijf dus eerst een programma dat van een bepaald getal onderzoekt of het een priemgetal is of niet. Aan het eind van het programma moet duidelijk op het scherm geprint worden of het getal een priemgetal is of niet. Het begint met een variabele `number`, waarin we het getal zetten dat onderzocht moet worden:

    number = input("Voer een getal in: ")
    number = int(number)
    # TODO: hier komt jouw code

Als de gebruiker het getal 37 invult, moet aan het eind van het programma geprint worden:

    Het getal 37 is een priemgetal

Bij een niet-priemgetal, zoals 36, moet geprint worden:

	Het getal 36 is geen priemgetal

Begin zo simpel mogelijk. Gebruik een `for`-loop en `%` (modulo) om te bepalen hoeveel getallen een deler zijn van `x`. Als je dit bijhoudt in de loop (tellen!), kun je na afloop van de loop bepalen of het getal een priemgetal is of niet. Print je conclusie uiteindelijk op het scherm, zoals in het voorbeeld hierboven.

## Stap 2: check een hele lijst

We gaan een stap verder. We kunnen bovenstaand stukje code nu hergebruiken en voor *elk* getal onder de 100 bepalen of het een priemgetal is of niet.

Maak een extra `for`-loop om alle getallen onder de 100 langs te loopen en bepaal voor elk van deze "kandidaat-priemgetallen" of het wel of niet een priemgetal is. Voor elk getal moet je dus weer de delers bepalen en je zal dus uiteindelijk twee `for`-loops gebruiken in elkaar (*nested loops* of *geneste loops*).

Schrijf dus bovenstaande procedure en maak deze goed werkend. Vervolgens willen we het uitbreiden door elk gevonden priemgetal te `print`en. We moeten dus bij de conclusie 'priem' een `print`-opdracht geven.

Klopt je antwoord? Check het op internet!

## Stap 3: het zoveelste priemgetal

We gaan nu terug naar de opdracht: op zoek naar het n-de priemgetal. We geven een voorzetje voor de strategie van het programma:

- Je kunt nu niet meer met een `for`-loop simpelweg tot `n` loopen. Want we willen het `n`-de priemgetal; we willen niet weten of `n` een priemgetal is (zie je het verschil met stap 2?). Je moet dus in je programma gaan bijhouden *hoeveel* priemgetallen je al gevonden hebt. Gebruik hiervoor een variabele.

- Begin klein. Zorg dat je programma eerst de priemgetallen tot 10 kan vinden. Dat is klein genoeg om te zien of het programma precies doet wat de bedoeling is, en kun al snel ontdekken wat er mis gaat.

- Problemen? Print bij elke kandidaat-priem wat informatie, zodat je weet waar je bent in de berekening en je ziet of de computer ook echt jouw bedoelde strategie volgt.

> Misschien is het raar of vervelend om een programma in te tikken, waarna je ontdekt dat het niet goed werkt. Dat is het lot van de programmeur: het is gewoon heel moeilijk om een precies algoritme te formuleren en dan helemaal correct om te zetten naar programmacode. Soms ben je een uitzondering vergeten, maar net zo goed heb je ergens een tikfout gemaakt. Bedenk dan dat de beste programmeurs op deze manier werken!

## Stap 4: werkt het echt?

Loop nu de specificatie bovenaan de opdracht goed door en zorg dat je programma precies zo werkt als daar beschreven is.

Dan ben je klaar om te testen:

	checkpy priemgetal

## Stap 5: kleine optimalisaties

We zijn hierboven zo simpel mogelijk begonnen, zodat we snel tot een *correct* programma zijn gekomen (gecontroleerd door `checkpy`). Maar met behulp van wat wiskundig inzicht kunnen we kleine optimalisaties doen, waardoor het programma sneller wordt. 

- Behalve 2 zijn *even* getallen nooit een priemgetal (dit vraagt slechts een hele kleine aanpassing van je code).

- Als je een deler vindt hoef je niet verder te zoeken omdat je dan gelijk weet dat het geen priemgetal is. 

- Als je wilt bepalen of 137 een priemgetal is, welke kandidaat-delers bekijk je dan voordat je zeker weet dat het een priemgetal is? Doe dit op pen en papier. Delen door 2 en alle oneven getallen tot het getal is een beetje teveel van het goede. Een wiskundige deelt bijvoorbeeld alleen door 2, 3, 5, 7, 11. Bedenk waarom (dit vraagt waarschijnlijk een flinke aanpassing van je code).

## Hints

- Je kunt dit programma schrijven met alleen de Python-onderdelen die je tot nu toe hebt geleerd!

## Testen

Test voor de zekerheid nog een keer of je programma werkt volgens `checkpy`:

	checkpy priemgetal
