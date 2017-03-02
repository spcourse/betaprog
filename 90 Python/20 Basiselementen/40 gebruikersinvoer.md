# Invoer door een gebruiker

Behalve printen naar een gebruiker van jouw programma, kan je ook om invoer van een gebruiker vragen. Zo kun je interactieve programma's schrijven die op basis van zulke invoer berekeningen doen. In Python zijn er verschillende functies om om invoer te vragen. Eén daarvan is `input()`, en deze gebruik je zoals hieronder:

	sum_result = input("Wat is 1 + 2? ")
	print "1 + 2 =", sum_result

De string `"Wat is jouw naam?"` die aan de functie `input` wordt meegegeven, print `input` naar de gebruiker toe. Dan wacht `input` totdat de gebruiker iets invult, en geeft als resultaat terug wat de gebruiker heeft ingevuld. In het voorbeeld hierboven wordt de uitkomst van `input` aan de naam `sum_result` gekoppeld. Op de volgende regel wordt de waarde van `sum_result` uitgeprint. 

`input` is een nuttige functie om interactie met de gebruiker van jouw programma mogelijk te maken. Let wel, `input` probeert meteen het correcte type toe te kennen aan wat de gebruiker invult. Vult je gebruiker een geheel getal in, dan maakt `input` hier direct een geheel getal van binnen Python waar jij mee kan rekenen. Zou je in plaats van het getal `3`, de string `drie` intikken, dan kan `input` daar niks mee en je programma zal dan crashen.
