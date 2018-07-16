
## Opdracht 3: populatie-dynamica (de dood - vossen eten konijnen)

In de natuur leven vossen en konijnen niet vredig naast elkaar. Als een vos een konijn tegenkomt zal hij het konijn opeten. Doel van deze opdracht is te onderzoeken hoe lang het (gemiddeld) duurt voordat de vossen de helft van de konijnen hebben opgegeten. We onderzoeken ook of het voor de konijnen verstandiger is om stil te zitten of om juist hard rond te rennen.

<b>Tip:</b> we gaan nu een aanpassing aan de bestaande code maken uit opdracht 1 en 2. Om te zorgen dat de code uit opdracht 1 bewaard blijft gaan we deze opdracht maken in een nieuw bestand. Sla je bestaande code op in een file `prooipredator_tm_opdracht2.py`. Maak daarna een nieuw Python bestand, `prooipredator_tm_opdracht3.py`, kopieer de code die je tot nu toe hebt gemaakt en ga verder in deze nieuwe file.

<br>

#### Deelopdracht (3a): verdwijnende konijnen

De eerste stap in deze opdracht is om in de simulatie te verwerken dat konijnen opgegeten worden als ze bij een vos in de buurt komen. Schrijf een nieuwe functie `etenstijd()` die in de 'hoofdfunctie' `prooipredator()` aan wordt geroepen na de functie `verplaats_de_konijnen()` en `verplaats_de_vossen()`. Taak van deze functie is om te evalueren, voor elk konijn, of hij zich in de buurt bevindt van een vos. Met 'in de buurt' wordt bedoeld: binnen 5 meter van de dichtstbijzijnde vos. Als dat zo is wordt het konijn opgegeten en zal hij verwijderd moeten worden uit de lijst met konijnen.

Gebruik de volgende Python syntax om een element $$i$$ uit een lijst $$L$$ weg te halen:

{: .language-python}   
     del L[i] 

<b>Let op:</b> 
Als je door een lijst van 20 elementen heenloopt en element 10 weghaalt dan schuiven alle elementen 1 positie op. Element 11 van de oorspronkelijke lijst wordt dan element 10 in de nieuwe lijst etc. De lijst is dan ook ineens 19 posities lang geworden en als je uiteindelijk bij konijn 20 aankomt bestaat dat niet meer. Een 'truc' om dit op te vangen is om de lijst in omgekeerd volgorde af te lopen. Begin dus bij konijn 20, vervolgens naar konijn 19 etc etc. De lijst wordt dan wel korter, maar je komt nooit in de problemen omdat je nooit element weghaalt dat je later nog wilt bekijken.

![](konijnenenvossenEtenstijd.gif){:.inline}{: style="width:30%"}

Om in omgekeerde volgorde door een lijst van 20 konijnen heen te gaan kan je de volgende syntax gebruiken (i_konijn loopt van 19 t/m 0, probeer maar):

{: .language-python}   
    for i_konijn in range(19,-1,-1):
         print (i_konijn)         

Extra tip: als een konijn opgegeten wordt haal dan het element weg uit **alle** lijsten, dus zowel de x-positie, de y-positie als de lijst met hoeken.

Zet ook de puntjes op de i door op elk moment op het scherm te zetten bij welk tijdstap we zitten en hoeveel vossen en konijnen er zich nog in het bos bevinden.

<br>
          
#### Deelopdracht (3b): Tijd berekenen waarop de konijnenpopulatie gehalveerd is (+ plot)

Als we de simulatie langer laten lopen komt er natuurlijk een moment dat de vossen de helft van de konijnen hebben opgegeten. Maar hoe lang duurt dat? Die vraag gaan we in deze opdracht beantwoorden.

<b>Tip voor we beginnen:</b> Het weergeven van bewegende en verdwijnende konijnen op het scherm is enorm tijdrovend. Tot 1000 tijdstappen werkt dit prima, maar bij langere of meerdere simulaties is het niet praktisch. Door de visualisatie weg te laten kan je enorm veel tijd winnen. Zorg dat je in de functie `prooipredator()` een variabele toevoegt waarmee je makkelijk kan kiezen of je wel/niet de functie `teken_het_bos()` aanroept. Vanaf nu gaan we de visualisatie niet meer aanroepen. Tenzij je iets wilt bekijken natuurlijk. 
En toch is het visualiseren van een enkele simulatie enorm belangrijk en meer dan 'gewoon leuk'. Het is een krachtige manier om fouten in je code op te sporen. Erg handig, zoals je waarschijnlijk eerder in de module al ervaren hebt toen je de bosrand of het opeten van de konijnen aan het implementeren was. 

Om de tijd te berekenen waarop de helft van de konijnen opgegeten is gaan we twee dingen aanpassen in het programma:

   1. Laat de simulatie 1000 seconden lopen en hou in de functie `prooipredator()` een lijst bij die voor elke tijdstap het aantal konijnen opslaat en zorg dat de functie `prooipredator()` deze lijst als return-value teruggeeft aan het eind van het programma.
   
   2. Schrijf een nieuwe functie `gemiddelde_halfwaardetijd()` die een enkele keer de functie `prooipredator()` aanroept. Omdat deze functie `prooipredator()` nu de lijst met aantal konijnen op elke tijdstap teruggeeft kan je hiermee uitrekenen op welk moment er voor het eerst minder dan de helft van de konijnen rondlopen in het bos. 
   
De tijd die de vossen daarvoor nodig hebben zal voor elke nieuwe simulate anders zijn. Hieronder vind je een paar grafieken van het aantal konijnen als functie van de tijd voor twee simulaties. Voor we van 1000 simulaties de gemiddelde tijd waarbij 50% van de konijnen verdwenen is is het belangrijk om zeker te weten dat de waardes die je hebt bepaald ook echt kloppen. Probeer dus eerst deze grafieken na te maken om te kijken of je inderdaad de goede gegevens uit je simulatie haalt.

 ![](halfwaarde3x.png){: style="width:65%"}

Aan het eind van de simulatie moet op het scherm verschijnen:

{: .language-python}   
    Na x.xx seconde is meer dan de helft van de konijnen opgegeten

<br>

#### Deelopdracht (3c): Gemiddelde tijd waarbij de konijnenpopulatie gehalveerd is

Onze nieuwe functie `gemiddelde_halfwaardetijd()` is nu zo opgezet dat de functie `prooipredator()` maar een enkele keer wordt aangeroepen. Er wordt dus steeds een enkele simulatie gedaan. Maar zoals je gezien hebt is er een vrij grote spreiding in de halfwaardetijd tussen verschillende simulaties. Om de <b>gemiddelde</b> halfwaardetijd te bepalen zullen we de een groot aantal simulaties moeten uitvoeren, voor elk de halfwaardetijd bepalen om dan uiteindelijk uit al die getallen het gemiddelde te bepalen.

<b>Let op:</b> De grafieken van het aantal konijnen als functie van de tijd zoals we die in de vorige deelopdracht hebben gemaakt hebben we gemaakt om te kijken of onze berekening van de halfwaardetijd correct was. Nu we daarvan overtuigd zijn kunnen we de grafiek weglaten. Zorgt dus dat de grafiek alleen op het scherm getoond wordt als we in onze functie maar 1 keer `prooipredator()` aanroepen. In de rest van de opdracht kijken we naar de waardes voor meerdere simulaties en doen plots er niet meer toe.

Pas de functie `gemiddelde_halfwaardetijd()` aan zodat die niet 1 keer, maar een groot aantal keer (500 keer) de functie `prooipredator()` aanroept, steeds de halfwaardetijd opslaat, om uiteindelijk het gemiddelde te berekenen. Dit duurt wel even, dus zorg dat elke 25e simulatie op het scherm geprint wordt welke simulatie nu uitgevoerd wordt.

Op het scherm moet na de laatste simulatie het volgende verschijnen:
{: .language-python}   
    Een gesimuleerde wereld met: Nkonijn=25 (v=1), Nvos=2 (v=2), Nsimulaties = 500:
    Gemiddelde halfwaardetijd konijnen = x.xx seconde

<br>

#### Deelopdracht (3d): Strategie konijnen: helpt het om onze snelheid aan te passen?

We hebben in de vorige opdracht gekeken wat de gemiddelde halfwaardetijd is van de konijnenpopulatie voor een specifieke snelheid van de konijnen. De konijnen willen natuurlijk niet dood en moeten iets bedenken. Discussiepunt onder de konijnen is nu of ze juist beter heel hard kunnen gaan lopen of juist stil moeten gaan zitten en hopen dat de vossen ze niet vinden. Aan ons om de optimale strategie te bepalen voor de konijnen.

Om deze vraag te beantwoorden gaan we de functie `gemiddelde_halfwaardetijd()` laten werken met verschillende waardes van de snelheid voor de konijnen. Je mag in deze opdracht de snelheid van de konijnen `snelheid_konijn` in de functie `prooipredator()` steeds met de hand veranderen en ook de antwoorden zelf opschrijven. Probeer verschillende snelheden voor de konijnen: snelheden van 0.0, 0.5, 1.0, 1.5, 2.0, 2.5 en 5.0 meter per seconde en maak uiteindelijk een grafiek van de gemiddelde halfwaardetijd als functie van de snelheid van de konijnen. Welke trend zie je en is het nou handiger voor de konijnen om juist langzamer of sneller te bewegen?

Print de waardes die je hebt gevonden ook op het scherm:
{: .language-python}   
     Een gesimuleerde wereld met: Nkonijn=25, Nvos=2 (v=2), Nsimulaties = 500:     
     snelheid konijnen = 0.0 m/s -> gemiddelde halfwaardetijd = XXX.X seconde
     snelheid konijnen = 0.5 m/s -> gemiddelde halfwaardetijd = XXX.X seconde
     snelheid konijnen = 1.0 m/s -> gemiddelde halfwaardetijd = XXX.X seconde
     ...     

<br>
