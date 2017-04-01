# Initials

Schrijf een functie die van een gegeven naam de initialen bepaalt.

	>>> result = initials("Johann Friedrich Miescher")
	>>> print result
	JFM

## Specificatie

- Maak een nieuw bestand genaamd `initials.py`.

- Definieer in dit bestand een functie `initials()` die als parameter een naam accepteert en een string met initialen teruggeeft (met behulp van `return`).

- De functie moet werken voor een willekeurige hoeveelheid namen (minimaal één!).

## Hints ##

- Start je functie met een variabele `result`:

		result = ""

- Loop door alle letters van de naam en bedenk hoe je kunt signaleren dat je een initiaal gevonden hebt.

- Voeg alle initialen toe aan de variabele `result`, zodat ze hierin verzameld worden. Helaas kun je voor strings geen `append()` gebruiken!

- Eindig de functie met `return result` om de verzamelde initialen terug te geven zodat ze geprint kunnen worden.

## Testen ##

Om snel te kunnen testen is het handig om onderaan je bestand een aantal standaardtests op te nemen. Neem de volgende tests over in je programma:

	print initials("Johann Friedrich Miescher")
	print initials("Phoebus Levene")
	print initials("Martha Chase")

Als je de functie `initials` hebt geschreven, en je voert het programma uit, dan zal het de resultaten van deze tests uitprinten. Zo kun je direct zien of het allemaal goed werkt.

Als je eigen tests werken, gebruik dan `checkpy` om te controleren of je functie echt werkt voor alle denkbare gevallen!
