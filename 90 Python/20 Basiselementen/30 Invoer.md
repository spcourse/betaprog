# Invoer door een gebruiker

Behalve printen naar een gebruiker van jouw programma, kun je ook om invoer van een gebruiker vragen. Zo kun je **interactieve programma's** schrijven die op basis van zulke invoer berekeningen doen. In Python zijn er verschillende functies om om invoer te vragen. Eén daarvan is `raw_input()`, en deze gebruik je zoals hieronder:

	voornaam = raw_input("Geef je voornaam: ")
	print "Hallo,", voornaam

De string `"Geef je voornaam: "` die achter de functie `raw_input` staat, zorgt dat meteen een bericht op het scherm wordt geprint. Dan wacht `input` totdat de gebruiker iets invult en op **enter** drukt. Wat de gebruiker heeft ingevuld krijgt nu een naam. In het voorbeeld hierboven wordt de invoer aan de naam `voornaam` gekoppeld. Op de volgende regel wordt de waarde van `voornaam` weer uitgeprint.

## Types

Een **waarde** is een van de basale onderdelen in een programma. In de voorbeelden hierboven heb je bijvoorbeeld al reeksen letters en ook cijfers gezien. Zulke waarden hebben een bepaald **type**:

| voorbeeld             | type  |                                                    |  
| --------------------- | ----- | -------------------------------------------------- |  
| `'Hello, World!'` | str   | een reeks letters: een string                      |  
| `17`                | int   | een geheel getal: een integer                      |  
| `3.2`               | float | een kommagetal: een floating point number          |  
| `'3.2'`             | str   | wederom een string, want er staan aanhalingstekens |  

Je kunt waarden ook **converteren**. Gebruik `int()` om een waarde naar een integer om te zetten. Tenminste, als het kan, want anders wordt er geklaagd:

| conversie        | resultaat                                      |  
| ---------------- | ---------------------------------------------- |  
| `e = int('32')`        | `32`                                           |  
| `f = int('Hello')`     | `ValueError: invalid literal for int(): Hello` |  
| `g = int(3.99999)`     | `3` (let op! er gaat informatie verloren)      |  
| `h = int(-2.3)`        | `-2`                                           |  
| `i = float(32)`        | `32.0`                                         |  
| `j = float('3.14159')` | `3.14159`                                      |  
| `k = str(32)`          | `'32'`                                         |  
| `l = str(3.14159)`     | `'3.14159'`                                    |  
