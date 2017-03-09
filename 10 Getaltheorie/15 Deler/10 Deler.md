# Deler

## tl;dr

Implementeer een programma dat aan een gebruiker twee getallen vraagt, en terug rapporteert of het eerste getal deelbaar is door de ander.

	Wat is het eerste getal? 16
	Wat is het tweede getal? 4
	deelbaar!

	Wat is het eerste getal? 27
	Wat is het tweede getal? 5
	niet deelbaar!

## Specificatie

* Schrijf in een nieuwe file genaamd `deler.py` een programma dat de gebruiker vraagt om twee gehele getallen. Print vervolgens als het eerste getal deelbaar is door het tweede het bericht `deelbaar!`, en zo niet dan print je `niet deelbaar!`. 

* Om het simpel te houden, mag je aannemen dat de gebruiker altijd braaf een positief getal invoert. Je hoeft dus geen foutafhandeling te implementeren voor het geval de gebruiker dat niet doet.

## Hints

* Dit programma voldoet aan het cliché van een standaard computerprogramma: het heeft *invoer*, *berekeningen*, en *uitvoer*. Probeer die drie onderdelen ook terug te laten komen in je code!

* Maak gebruik van de `input`-functie. Deze functie wacht input tot de gebruiker van jouw programma iets invult en geeft het resultaat daarvan terug.

* Achterhaal uit bovenstaande opdracht en uit de voorbeelden de formule die we nodig hebben om de berekening te doen. Dan is het belangrijkste deel van het werk gedaan.

## Testen

Loop eerst je eigen programma na, werkt deze voor alle normale invoer? Vul bijvoorbeeld eens het voorbeeld van de tl;dr in. Lijkt alles te werken, dan is het tijd om `checkpy` erbij te pakken. Testen gaat net zo als bij `hello`, alleen roep je nu de test voor `deler` aan. Zo dus:

	checkpy deler

Zie je unhappy smileys, en kom je er niet uit wat er fout gaat? Stuur een mail of kom langs!
