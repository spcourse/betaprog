# Monopoly #

Bij banken, verzekeraars en het centraal planbureau worden modellen opgesteld die 
onze economie beschrijven. Alle facetten die een rol spelen krijgen een plek en met 
behulp van een computer worden verschillende scenario's doorgerekend (gesimuleerd) 
om zo risico's in te schatten op bepaalde gebeurtenissen of om het effect van bepaalde
maatregelen te bekijken. 

Door de onderlinge afhankelijkheid van de parameters wordt het al snel ondoenlijk 
om het met de hand door te rekenen, zeker als het effect van bepaalde maatregelen een 
random component heeft. Met behulp van een computer gaat dat snel en kan je zelfs de 
settings vinden waarin je dingen kan optimaliseren: dat kan het maximaliseren van je 
winstkansen zijn, maar ook het minimaliseren van de kans dat je failliet gaat of een 
mix ertussenin.

We zullen in deze module een simpel voorbeeld doorrekenen: Monopoly met twee spelers.
Omdat we niet veel tijd hebben zullen we dit stap voor stap opbouwen. Voor degene die 
de smaak te pakken heeft en nu al droomt van een baan op de Risk analysis van JP Morgen 
hebben we nog wat suggesties voor extra opgaves gemaakt.

blabla2


## Random integers

Het enige nieuwe Python element dat we nodig hebben is een manier om een dobbelsteen te 
gooien. Een random geheel getal tussen de 1 en de 6 dus. Dat zouden we zelf kunnen 
'bouwen' met behulp van de random() functie die we eerder hebben leren kennen, maar er 
is een speciale functie voor in Python, namelijk 'randint()'.

{: .language-python}
	# from random import *
	dobbelsteen = randint(1,6) 
	
### opgave 1: rare worpen met twee dobbelstenen

Met Monopoly gooi je met twee dobbelstenen. Schrijf een Python programma `Opdracht1` waarbij 
je een groot aantal worpen maakt en voor elke worp steeds twee dobbelstenen gooit. Zorgt dat 
op het scherm voor elke worp het aantal ogen geprint wordt en maak duidelijk aan de gebruiker 
als er een zogenaamde 'dubbel' gegooid wordt (het aantal ogen op beide dobbelstenen is gelijk).

{: .language-python}
	worp 1: totaal van 2 dobbelstenen = 13
	worp 2: totaal van 2 dobbelstenen =  8
	worp 3: totaal van 2 dobbelstenen = 12
	        Dubbel: 6+6
	


	
	
	
