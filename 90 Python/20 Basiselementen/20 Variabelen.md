# Variabelen

Tot nu toe zijn we alleen bezig geweest met constante waarden, die bij het schrijven van het programma al uitgespeld worden (in het bovenstaande geval ging het om een tekstje: `"Hello, world!"`). Maar als we bij het programmeren al weten wat het antwoord wordt, dan hebben we natuurlijk eigenlijk geen computer nodig! Laten we dus doen waar computers goed in zijn: rekenen.

Om resultaten van berekeningen te kunnen gebruiken in andere berekeningen, moeten we deze tijdelijk op zien te slaan. Als oplossing laat Python je *namen* toekennen aan waardes. Deze naam-waarde combinaties noemen we *variabelen*. Door middel van de `=` operator kunnen we een naam toekennen aan een waarde, en deze vervolgens ergens anders gebruiken. Zie bijvoorbeeld hieronder:

	income = 230
	expense = 170
	profit = income - expense
	print profit

Het is hierbij belangrijk om te letten op de *volgorde* van de regels code. Python interpreteert jouw code van boven naar beneden. Zou je de laatste regel als eerste neerzetten, dan krijg je een `NameError`. Want de naam `profit` is nog niet bekend (*defined*), die wordt pas bekend gemaakt op regel 3.

Continu nieuwe namen introduceren voor elke berekening is soms niet wat je wilt. In Python kan je ook oude, al gebruikte namen toekennen aan nieuwe waarden. Bijvoorbeeld:

	income = 170
	income = income - 10
	income -= 30
	print income

(Hier is de `-=` operator op regel drie simpelweg een verkorting voor `a = a - ...`.)
