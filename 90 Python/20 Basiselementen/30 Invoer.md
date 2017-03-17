# Invoer door een gebruiker

Behalve printen naar een gebruiker van jouw programma, kun je ook om invoer van een gebruiker vragen. Zo kun je **interactieve programma's** schrijven die op basis van gebruikersinvoer berekeningen doen. In Python zijn er verschillende functies om om invoer te vragen. Eén daarvan is `raw_input()`, en deze gebruik je zoals hieronder:

	voornaam = raw_input("Geef je voornaam: ")
	print "Hallo,", voornaam

De string `"Geef je voornaam: "` die achter de functie `raw_input` staat, zorgt dat meteen een bericht op het scherm wordt geprint. Dan wacht `raw_input` totdat de gebruiker iets invult en op **enter** drukt. Wat de gebruiker heeft ingevuld krijgt nu een naam. In het voorbeeld hierboven wordt de invoer aan de naam `voornaam` gekoppeld. Op de volgende regel wordt de waarde van `voornaam` weer uitgeprint.

Nu komt uit `raw_input` altijd een string. Maar soms wil je natuurlijk dat de gebruiker een getal invoert om daar een berekening mee te doen. Dan kun je de conversie-functies van hierboven gebruiken. Bijvoorbeeld:

	aantal_stoelen = raw_input("Hoeveel stoelen moeten gereserveerd worden? ")
	aantal_stoelen = int(aantal_stoelen)
