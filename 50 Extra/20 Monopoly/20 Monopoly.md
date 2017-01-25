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

Het enige nieuwe Python element dat we nodig hebben is 




{: .language-python}
    # This function consists of 4 lines of code and
	# 2 lines of commenting.
    def sum(arrayOfNumbers):
        result = 0
        # This for loop contains exactly 1 line that is repeated.
        # The next line after is unindented.
        for number in arrayOfNumbers:
            result = result + number
        return result

