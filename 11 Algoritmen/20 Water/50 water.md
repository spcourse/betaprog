# Water

Implementeer een programma dat aan een gebruiker diens waterverbruik rapporteert, door het aantal minuten douchen om te rekenen naar flesjes drinkwater.

	Hoeveel minuten douche je? 1
	12

	Hoeveel minuten douche je? 10
	120

## Specificatie

* Schrijf in een nieuwe file genaamd `water.py` een programma dat de gebruiker vraagt voor de lengte van zijn of haar douche sessie in minuten. Print vervolgens het overeenkomstige aantal flesjes water uit. Ga er vanuit dat één minuut douchen overeenkomt met 12 flesjes water (van 0.5L).

* Om het simpel te houden, mag je aannemen dat de gebruiker altijd braaf een positief getal invoert. Je hoeft dus geen foutafhandeling te implementeren voor het geval de gebruiker dat niet doet.

* Het resultaat moet er precies uitzien als de voorbeelden hierboven.

## Hints

* Dit programma voldoet aan het cliché van een standaard computerprogramma: het heeft *invoer*, *berekeningen*, en *uitvoer*. Probeer die drie onderdelen ook terug te laten komen in je code!

* Maak gebruik van de `input`-functie en gebruik `int()` om de invoer van de gebruiker om te zetten van een string naar een integer, zodat je de berekening kunt uitvoeren.

* Achterhaal uit bovenstaande opdracht en uit de voorbeelden de formule die we nodig hebben om de berekening te doen. Dan is het belangrijkste deel van het werk gedaan.

## Testen

Loop eerst je eigen programma na, werkt deze voor alle normale invoer? Vul bijvoorbeeld eens als aantal douche-minuten de waarden 0, 10 en 137 in. Lijkt alles te werken, dan is het tijd om `checkpy` erbij te pakken. Testen gaat net zo als bij `hello`, alleen roep je nu de test voor `water` aan. Zo dus:

	checkpy water

Zie je unhappy smileys, en kom je er niet uit wat er fout gaat? Vraag om hulp!
