# Variabelen

Een **waarde** is een van de basale onderdelen in een programma. In de voorbeelden hierboven heb je bijvoorbeeld al reeksen letters en ook cijfers gezien. Tot nu toe zijn we alleen bezig geweest met **constante waarden**, die bij het schrijven van het programma al uitgespeld worden (in het bovenstaande geval ging het bijvoorbeeld om een tekstje `"Hello, world!"`). Maar als we bij het programmeren al weten wat het antwoord wordt, dan hebben we natuurlijk eigenlijk geen computer nodig! Laten we dus doen waar computers goed in zijn: rekenen.

Om resultaten van berekeningen te kunnen gebruiken in andere berekeningen, moeten we deze tijdelijk op zien te slaan. Als oplossing laat Python je namen toekennen aan waardes. Deze naam-waarde combinaties noemen we **variabelen**. Door middel van de `=` operator kunnen we een naam toekennen aan een waarde, en deze vervolgens ergens anders gebruiken. Hier is bijvoorbeeld een programma waar drie keer een `=` wordt gebruikt om een naam aan een waarde te koppelen:

	income = 230
	expense = 170
	profit = income - expense
	print profit

Op de derde regel wordt de nieuwe naam `profit` zelfs gekoppeld aan het resultaat van een berekening. Een berekening op basis van eerder gedefinieerde namen. Het is hierbij belangrijk om te letten op de **volgorde** van de regels code. Python interpreteert jouw code van boven naar beneden. Als je de laatste regel als eerste zou neerzetten, dan ziet het er zo uit:

	print profit
	income = 230
	expense = 170
	profit = income - expense

Nu krijg je een `NameError` zodra je het programma uitvoert. Want de naam `profit` is nog niet bekend (*defined*) op regel 1; die wordt pas bekend gemaakt op regel 4.

Ten slotte kun je een oude naam ook een nieuwe waarde geven:

	income = 170
	income = income - 10
	print income

In feite verander je dus op regel 2 van dit voorbeeld `income` door er 10 van af te trekken. Dat resultaat is dan ook zichtbaar als je het programma uitvoert.

## Types

Er zijn verschillende soorten waardes in Python; we noemen dat een **type**. In de tabel zie je drie belangrijke types:

| voorbeeld         | type  |                                                          |  
| ----------------- | ----- | -------------------------------------------------------- |  
| `'Hello, World!'` | str   | een reeks letters: een **string**                        |  
| `'3.2'`           | str   | wederom een string, want er staan aanhalingstekens       |  
| `17`              | int   | een geheel getal: een **integer**                        |  
| `3.2`             | float | een kommagetal: een **float**, een floating point number |  

Je kunt waarden ook **converteren** van het ene naar het andere type. Gebruik bijvoorbeeld `int()` om een waarde naar een integer om te zetten. Tenminste, als het kan, want anders wordt er geklaagd:

| conversie                | resultaat                                                      |  
| ------------------------ | -------------------------------------------------------------- |  
| `print int('32')`        | `32`                                                           |  
| `print int('Hello')`     | `ValueError: invalid literal for int(): Hello`                 |  
| `print int(3.99999)`     | `3` (let op! geen error, maar er gaat wel informatie verloren) |  
| `print int(-2.3)`        | `-2`                                                           |  
| `print float(32)`        | `32.0`                                                         |  
| `print float('3.14159')` | `3.14159`                                                      |  
| `print str(32)`          | `'32'`                                                         |  
| `print str(3.14159)`     | `'3.14159'`                                                    |  

Is het trouwens opgevallen dat kommagetallen op z'n Amerikaans worden geschreven? Met een punt dus! Dit is in vrijwel alle programmeertalen het geval.
