# Het duizendste priemgetal #

## tl;dr

Implementeer een programma dat op verzoek het n-de priemgetal genereert.

	Naar welk priemgetal bent u op zoek? 1000
	9717

## Het idee

Zoals gezegd is een computer geweldig in het snel uitvoeren van een heleboel "domme" stappen. Een voorbeeld waar een computer zó veel effectiever is dan een enkele persoon, is het uitrekenen van priemgetallen. De definitie van een priemgetal is niet al te ingewikkeld. Maar bepalen hoeveel delers een willekeurig getal heeft kan ontzettend veel tijd kosten. Python to the rescue!

## Specificatie

- Schrijf in een bestand genaamd `priemgetal.py` een programma dat een priemgetal met de gewenste rangorde bepaalt.

- Vraag de gebruiker om de rangorde van het priemgetal in te voeren. Dit moet een geheel getal zijn, groter dan 2.

- Als de gebruiker een rangorde invult die niet toegestaan is, dan vraag je de gebruiker opnieuw naar de rangorde. Net zo lang tot de gebruiker een geldige rangorde invult.

- Zodra de rangorde bekend is, bereken het juiste priemgetal en rapporteer dit terug aan de gebruiker.

- Zorg dat het programma niets anders uitvoert dan dit getal!

## Hints

- Bovenstaande opdracht bestaat uit een aantal onderdelen die bij elkaar moeten komen. Volg de stappen hieronder om je programma op te bouwen.

- Als je wilt controleren of je programma goed werkt kun je je gevonden lijst priemgetallen hier controleren met een lijst bekende priemgetallen <http://primes.utm.edu/lists/small/1000.txt>

## Stap 1

Schrijf een programma in een bestand genaamd `priem.py` dat van een bepaald getal onderzoekt of het een priemgetal is of niet. Aan het eind van het programma moet duidelijk op het scherm geprint worden of het getal een priemgetal is of niet. Het begint met een variabele `number`, waarin we het getal zetten dat onderzocht moet worden:

    number = input("Voer een getal in: ")
    # TODO: hier komt jouw code

De functie input hierboven laat de gebruiker van jouw programma iets invullen. Als de gebruiker het getal 37 invult, moet aan het eind van het programma geprint worden:

    Het getal 37 is een priemgetal 

Bij een niet priemgetal, zoals 36, moet geprint worden:

	Het getal 36 is geen priemgetal

Begin zo simpel mogelijk. Gebruik een `for`-loop en `%` (modulo) om te bepalen hoeveel getallen een deler zijn van `x`. Als je dit bijhoudt in de loop (tellen!), kun je na aflopen van de loop bepalen of het getal een priemgetal is of niet. Print je conclusie uiteindelijk op het scherm, zoals in het voorbeeld hierboven.

## Stap 2

Hierboven keken we alleen of een getal een priemgetal was of niet. We kunnen dit stukje code nu hergebruiken en voor *elk* getal onder de 100 bepalen of het een priemgetal is of niet.

Maak een nieuw bestand **priem100.py**. Gebruik een `for`-loop om alle getallen onder de 100 te genereren en bepaal voor elk van deze getallen of het wel of niet een priemgetal is. Voor elk getal moet je dus weer het delers bepalen en je zal dus uiteindelijk twee `for`-loops gebruiken in elkaar (*nested loops* of *geneste loops*).

Schrijf bovenstaande procedure en maak deze goed werkend. Vervolgens willen we het uitbreiden door alle gevonden priemgetallen te bewaren in een lijst. We moeten dus bij de conclusie 'priem' het juiste getal opslaan. Aan het eind van het programma willen we deze lijst dan printen:

	priemgetallen = []
	...
	...
	...
    print priemgetallen
   
Geef dan ook nog na het printen van de lijst aan hoeveel priemgetallen je gevonden hebt. Hoe weet je hoeveel priemgetallen er in de lijst staan? Klopt je antwoord? Check het op internet!

## Stap 3

We gaan nu terug naar de opdracht. We geven een voorzetje voor de strategie van het programma:

- Verzin hoe je per kandidaat-priemgetal bijhoudt of het inderdaad een priemgetal is terwijl je over de mogelijke delers heenloopt.

- Bedenk van tevoren hoe je de lijst met (1000) gevonden priemgetallen gaat opslaan.

- Problemen? Print bij elke kandidaat-priem wat informatie, zodat je weet waar je bent in de berekening en je ziet of de computer ook echt jouw bedoelde strategie volgt.

- Begin klein. Zorg dat je programma eerst de priemgetallen tot 10 kan vinden. Dat is klein genoeg om te zien of het programma precies doet wat de bedoeling is, en kun al snel ontdekken wat er mis gaat.

> Misschien is het raar of vervelend om een programma in te tikken, waarna je ontdekt dat het niet goed werkt. Dat is het lot van de programmeur: het is gewoon heel moeilijk om een precies algoritme te formuleren en dan helemaal correct om te zetten naar programmacode. Soms ben je een uitzondering vergeten, maar net zo goed heb je ergens een tikfout gemaakt. Bedankt dan dat de beste programmeurs op deze manier werken!

## Wiskundetips

Hoewel het in deze opgave niet echt gaat om de snelheid van het programma is in deze specifieke opgave veel tijd te winnen door slim gebruik te maken van een aantal elementen uit de wiskunde. Maar let op! Doe dit pas als je zeker weet dat je programma hierboven *correct* is. Je kunt dan optimalisaties toepassen en snel vergelijken of je niet een *bug* in je code hebt geïntroduceerd. Dat zou jammer zijn voor een beetje tijdswinst!

- Behalve 2 zijn even getallen nooit een priemgetal.

- Als je een deler vindt hoef je niet verder te zoeken omdat je dan weet dat het geen priemgetal is.

- Als je wilt bepalen of 137 een priemgetal is, welke kandidaat-delers bekijk je dan voordat je zeker weet dat het een priemgetal is? Doe dit op pen en papier. Delen door 2 en alle oneven getallen tot het getal is een beetje teveel van het goede. Een wiskundige deelt bijvoorbeeld alleen door 2, 3, 5, 7, 11. Bedenk waarom.
