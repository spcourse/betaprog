# Populatiedynamica: prooi-predator model#

Een klassiek voorbeeld van een complex dynamisch systeem is het zogenaamde prooi-predator 
model. De basis van de wiskundige beschrijving van de populaties zijn de bekende 
[Lotka-Volterra vergelijkingen](https://en.wikipedia.org/wiki/Lotka–Volterra_equations) vergelijkingen. De wiskunde wordt al snel erg complex en het is ook niet altijd makkelijk om van tevoren in te schatten welke effecten een nieuw aspect van het gedrag heeft op de verschillende populaties in het systeem. 

In deze module zullen we zelf een simulatie schrijven van een overzichtelijk systeem: een bos van 100 bij 100 meter waarin 25 konijnen en 2 vossen leven. Door het zelf te programmeren kunnen we nieuwe fenomenen toevoegen. Door het systeem te visualiseren krijgen we direct feedback op onze code en zien we ook de consequenties van de nieuwe gedragselementen die we toegevoegd hebben.

## Startpunt: twee bewegende konijnen op het scherm

We beginnen deze module, een beetje tegen de filosofie van de cursus in, niet met een leeg scherm, maar met het onderstaande stukje code. Niet omdat het erg moeilijk is, maar omdat we dan een gemeenschappelijk startpunt hebben en we op dezelfde manier stukken code toevoegen.

{: .language-python}
    import matplotlib.pyplot as plt

    # lijsten waarvan je wilt dat ze overal in je programma 'zichtbaar' zijn
    global posities_konijnen_x, posities_konijnen_y

    #-------------------
    def prooipredator():
    #-------------------

        # zorg dat je de 'gedeelde' lijsten kan gebruiken
        global posities_konijnen_x, posities_konijnen_y

        # definieer startpositie konijnen (x-posities en y-posities op t=0)
        posities_konijnen_x = [10.,60.]  
        posities_konijnen_y = [ 2.,10.]  
   
        # neem stapjes in de tijd
        for i_time in range(10):

            # verplaats de konijnen
            verplaats_de_konijnen()    

            # plot de positie van de konijnen
            teken_het_bos()
        
        # einde functie                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
        return
  
  
    #---------------------------
    def verplaats_de_konijnen():
    #---------------------------

        # zorg dat je de 'gedeelde' lijsten kan gebruiken
        global posities_konijnen_x, posities_konijnen_y

        # verplaats de konijnen (1.2 naar rechts en 1.6 naar boven)
        Aantal_konijnen = len(posities_konijnen_x)   
        for i_konijn in range(Aantal_konijnen):
            posities_konijnen_x[i_konijn] = posities_konijnen_x[i_konijn] + 0.6 
            posities_konijnen_y[i_konijn] = posities_konijnen_y[i_konijn] + 0.8 
    

    #--------------------------
    def teken_het_bos():
    #--------------------------

        # zorg dat je de 'gedeelde' lijsten kan gebruiken
        global posities_konijnen_x, posities_konijnen_y

        # definieer vast assenstelsel (het bos)
        plt.axis([0,100,0,100])

        # teken de konijnen (blauwe stip)
        plt.plot(posities_konijnen_x, posities_konijnen_y, 'o', color = 'blue', markersize = 6)   
        
        # update de frames (voor simpele animatie)
        plt.draw()        
        plt.pause(0.001)
        plt.show()
        plt.clf()
 

    #====================
    #== hoofdprogramma ==
    #====================
    prooipredator()

Het stukje code hieronder bestaat uit 3 functies:

   1. `prooipredator()`: definieert de startpositie van de konijnen, stuurt de simulatie door stapjes in de tijd te nemen (steeds een seconde) en roept voor elke stap in de tijd de functies `verplaats_de_konijnen()` en `teken_het_bos()` aan. Wordt aangeroepenen vanuit het 'hoofdprogramma', helemaal onderaan het stuk code.
    
   2. `verplaats_de_konijnen()`: verandert de positie van de konijnen 

   3. `teken_het_bos()`:  tekent de konijnen op het scherm
 
##### Extra stukje Python: globale variabelen
Als een variabele of lijst in meerdere functies in een programma gebruikt wordt is het soms handig om die variabel als zogenaamd 'globaal' te definieren. Alle functies in het programma kunnen aangeven dat ze die variabelen willen gebruiken. Deze variabelen worden daarmee gedeeld. In ons stukje code zijn dat twee lijsten: `posities_konijnen_x` en `posities_konijnen_y`. Deze lijsten worden namelijk gebruikt in elk van de drie functies: de startwaardes worden gedefini&euml;erd in `prooipredator()`, ze worden veranderd in de functie `verplaats_de_konijnen()` en daarna getekend in `teken_het_bos()`. De syntax om globale variabelen te defini&euml;ren en gebruiken is als volgt: de lijsten worden eerst in het hoofdprogramma (helemaal bovenaan) als globaal gedefini&euml;erd en vervolgens wordt aan het begin van elk van de drie functies vermeld dat we ze in die functie willen gebruiken.

Als je een variabele in maar 1 functie gebruikt moet je die <b>niet</b> als globaal definieren. 


## Opdracht 1: modelleren van de beweging van de konijnen 

We hebben in bovenstaand voorbeeld aangenomen dat de konijnen bij elke stap in de tijd (elke seconde) steeds 0,6 meter naar rechts opschuiven en 0,8 meter omhoog. Dit is nog erg ver weg van een realistisch systeem natuurlijk: konijnen bewegen niet synchroon, ze rennen ook niet in een rechte lijn en als we de tijd langer door zouden laten doorlopen zullen de konijnen vrolijk het bos uitlopen. Dat is niet de bedoeling in deze opgave. Als de konijnen bij de rand van het bos komen zullen ze weer snel terug het (veilige) bos inlopen. In opdracht 1 zullen we deze eerste stappen op weg naar realistische konijnen doorvoeren in onze code. Maak een bestand `Prooipredator_opdracht1.py` aan, kopieer bovenstaande code erin en volg de onderstaande deelopdrachten. 

#### [deelopdracht 1a]: nieuwe parametrisatie beweging konijnen

We hadden de verplaatsing van de twee konijnen in het stukje voorbeeldcode ook kunnen representeren door te stellen dat konijnen niet alleen met dezelfde snelheid bewegen (1 m/s), maar in dit specifieke geval ook nog eens onder dezelfde hoek ten opzichte van de x-as: ongeveer 51 graden. We gaan in de rest van de opgave werken met een universele konijnen-snelheid, maar gaan zorgen dat elk konijnen zijn eigen bewegingsrichting krijgt. 

Voeg in het hoofdprogramma een variabele `snelheid_konijnen` toe die de universele snelheid van de konijnen aangeeft. Voeg ook een lijst `hoeken_konijnen` toe waarbij je voor elk konijn bijhoudt onder welke hoek ten opzichte van de x-as hij beweegt. Omdat je de nieuw variabelen gebruikt in twee functies, namelijk zowel `prooipredator()` (kiezen van de initi&euml;le waardes) en in `verplaats_de_konijnen()` (uitrekenen nieuwe posities ) is het handig ook deze variabelen als globaal te defini&euml;ren.

Op de plek in de functie `verplaats_de_konijnen()` waar de nieuwe posities van de konijnen uitgerekend wordt moet je voor elk konijn de snelheid en de hoek eerst omrekenen naar een snelheid in de x- en y-richting zodat je daarmee de verplaatsing in de x- en y-richting kan uitrekenen. Voor elk konijn gebruiken we eerst:

{: .language-python}
       hoek = hoeken_konijnen[i_konijn]
       v_x = snelheid_konijnen * cos(hoek)
       v_y = snelheid_konijnen * sin(hoek)
    
En omdat de tijdstappen precies 1 seconde zijn kunnen we dan als volgt de nieuwe posities van het konijn uitrekenen:

{: .language-python}
       posities_konijnen_x[i_konijn] = posities_konijnen_x[i_konijn] + v_x
       posities_konijnen_y[i_konijn] = posities_konijnen_y[i_konijn] + v_y

Eigenlijk staat er in bovenstaande code v_x*dt, maar omdat de tijdstapjes 1 seconde zijn kunnen de dt weglaten. We hebben met deze implementatie nu de mogelijkheid om bij de start van de simulatie elk konijn een unieke bewegingsrichting te geven. Voer bovenstaande veranderingen in in de code, geef elk van de konijnen een eigen richting en laat de simulatie 20 seconden lopen in plaats van 10. 

<b>Let op:</b> om de goniometrische functies (zo) in je programma te kunnen gebruiken moet je de wiskunde bibliotheek implementeren: `from math import *`

#### [deelopdracht 1b]: de bosrand 

Onze konijnen, angsthazen dat het zijn, zullen nooit het bos verlaten. Zodra ze per ongeluk een stap buiten het bos doen draaien ze zich pijlsnel om en zullen daarna weer snel het bos inrennen in dezelfde richting als waar ze vandaan kwamen. Pas de functie `verplaats_de_konijnen()` zodanig aan dat de konijnen altijd in het bos blijven rondlopen.

Volg de volgende strategie als het konijn na een stap gezet te hebben buiten het bos is geraakt:

   1. neem een stap terug (zowel x als y) zodat het konijn weer in de oorspronkelijke positie zit
   2. zorg dat het konijn zich omdraait door de hoek waarin het konijn beweegt te veranderen naar een richting die precies tegenovergesteld is aan de huidige richting: 'hoek_nieuw = hoek +  $$\pi$$'. Stop deze nieuwe bewegingsrichting op in de lijst `hoeken_konijnen`. Bij de volgende stap rent het konijn dus weer terug het bos in. 
   
Probeer dit te testen door een van de konijnen (recht) naar de bosrand te laten bewegen en te kijken of hij inderdaad weer het bos in 'stuitert' zodra hij over de rand van het bos heengaat.


#### [deelopdracht 1c]: random konijnen-gedrag

Iedereen die konijnen heeft zien lopen weet dat ze niet in een rechte lijn bewegen, maar af en toe ineens stilzitten om dan van richting te veranderen. Deze eigenschap gaan we ook implementeren in onze simulatie.

![](konijnen.gif){:.inline}{: style="width:30%"}

Pas de functie `verplaats_de_konijnen()` zo aan dat het konijn gemiddeld eens in de 20 seconden stilzit en daarna in een willekeurige andere richting verder wandelt. Praktisch betekent dit dat een konijn elke seconde een 5% kans heeft om stil te zitten en van richting te veranderen en 95% kans heeft om gewoon door te lopen in dezelfde richting. Een mogelijke implementatie van dit gedrag is dor gebruik te maken van een random getal $$x$$ (tussen 0 en 1).

{: .language-python}
    x<0.05 (5% kans): geen stap, kies wel nieuwe hoek (0<hoek<2*pi) 
    x>0.05 (95% kans): zet een gewone stap

<b>Let op:</b> om een random getal te genereren heb je de random bibliotheek nodig. Zorgt dat je code die kent: `from random import *`

<br>

#### Deelopdracht (1d): startsituatie: 25 'random' konijnen 

Een wereld met twee konijnen is natuurlijk niet realistisch. Pas het begin van `prooipredator()` zo aan dat er 25 konijnen in de simulatie zijn. Maak de code zo dat de konijnen elk op een random positie geplaatst worden, maar wel in een vierkantje dat gegeven wordt door $$20<(x,y)<30$$. Geef elke van de konijnen ook een random startrichting: $$0<\alpha<2\pi$$.

<b>Let op:</b> In de functie `prooipredator()` voeg je voor elk van de 25 konijnen de 
parameters (x-positie, y-positie en hoek) in de lijstlijsten. Let erop dat je voor je dat doet de lijsten als 'leeg' definieert. Dus: `posities_konijnen_x = []` etc. Dit is belangrijk in het geval we meerdere simulaties achter elkaar gaan maken omdat je dan steeds met een blanco situatie wilt beginnen.

## Opdracht 2: Harde realiteit voor de konijnen: vossen

Je kan natuurlijk de hele middag kijken naar 25 konijnen die over je scherm door een fictief bos rennen, maar daar is verder niks spannends of ingewikkelds aan. Laten we wat spektakel toevoegen.
<br>

#### [deelopdracht 2a]: introduceren van vossen

Naast konijnen zijn er ook vossen in het bos. Pas de code zo aan de er ook (twee) vossen in de simulatie meedoen en op het scherm verschijnen. In grote lijnen kan je dezelfde structuur volgen die we ook voor de konijnen gebruikt hebben. Maak eerst lijsten die de positie en bewegingsrichtingen van de vossen beschrijven en maak ook een nieuwe functie `verplaats_de_vossen()`. Net als de konijnen zal ook de vos nooit het bos verlaten. Zorg dat je voor de vossen eenzelfde implementatie maakt voor het ontwijken van de bosrand als  voor de konijnen in opgave 1b). Als laatste moet je ook de functie `teken_het_bos()` aanpassen zodat ook de vossen op het scherm getoond worden. 

Er zijn een paar verschillen tussen de vossen en de konijnen:

   - vossen zijn twee keer zo snel als konijnen (`snelheid_vossen = 2`) en ze staan nooit stil
   - teken de vossen in rood (size=10 i.p.v de size=6 voor de konijnen)

Laat de vossen starten op posities (70,70) en (80,80) en laat bij de start vos 1 naar links en vos 2 naar beneden bewegen. 

<br>

#### [deelopdracht 2b]: specifiek wandelgedrag van wolven

![](konijnenenvossen.gif){:.inline}{: style="width:30%"}

Net als de konijnen hebben ook vossen een eigen unieke manier van voortbewegen. De vos heeft de neiging om rechtdoor te lopen, maar kan na elke stap besluiten daarna iets naar links of rechts af te buigen. De kans op een bepaalde verandering ten opzichte van de oorspronkelijke bewegingsrichting neemt sterk af hoe groter de richtingsverandering is. De verdeling van de kansen volgt een zogenaamde normaal-verdeling. De vos volgt hiermee een soort pseudo-random walk waarbij er toch een voorkeur is om in de oorspronkelijke richting te blijven lopen. Implementeer dit gedrag in je simulatie.

Python input: Om een 'random' nieuwe richting te kiezen vanuit een normaalverdeling heb je een functie nodig die zich in de numpy bibliotheek bevindt. Zorgt dat je code die kent: `import numpy as np` en voor de specifieke implementatie waarin je wilt dat het random getal gecentreerd is rond de oorspronkelijke bewegingsrichting kan je de volgende syntax gebruiken:

{: .language-python}   
     nieuwe_hoek = np.random.normal(hoeken_vossen[i_vos], 0.2)  

Laat de vos eerst een stap zetten en kies dan een nieuwe random richting en sla die op in `hoeken_vossen`. Bij de volgende stap zal de vos in deze nieuwe richting bewegen. De waarde 0.2 is de bovenstaande uitdrukking is de zogenaamde breedte van de normaal-verdeling. Het bepaalt hoe makkelijk (of niet) de vos van zijn oorspronkelijke bewegingsrichting af kan wijken.

## Opdracht 3: populatie-dynamica (de dood - vossen eten konijnen)

In de natuur leven vossen en konijnen niet vredig naast elkaar. Als een vos een konijn tegenkomt zal hij het konijn opeten. Doel van deze opdracht is te onderzoeken hoe lang het (gemiddeld) duurt voordat de vossen de helft van de konijnen heeft opgegeten. Als laatste zullen we kijken of het voor de konijnen verstandiger is te zitten om stil te zitten of juist keihard rond te rennen.

<b>Let op:</b> we gaan nu een aanpassing aan de bestaande code maken uit opdracht 1 en 2. Om te zorgen dat de code uit opdracht 1 bewaard blijft gaan we deze opdracht maken in een nieuw bestand. Sla je bestaande code op in een file `prooipredator_tm_opdracht2.py`. Maak daarna een nieuw Python bestand, `prooipredator_tm_opdracht3.py`, kopieer de code die je tot nu toe hebt gemaakt en ga verder in deze nieuwe file.

#### [deelopdracht 3a]: verdwijnende konijnen

De eerste stap in deze opdracht is om in de simulatie te verwerken dat konijnen opgegeten worden als ze bij een vos in de buurt komen. Schrijf een nieuwe functie `etenstijd()` die in de 'hoofdfunctie' `prooipredator()` aan wordt geroepen na de functie `verplaats_de_konijnen()` en `verplaats_de_vossen()`. Taak van deze functie is om te evalueren, voor elk konijn, of hij zich in de buurt bevindt van een vos. Met 'in de buurt' wordt bedoeld: binnen 5 meter van de dichtstbijzijnde vos. Als dat zo is wordt het konijn opgegeten en zal hij verwijderd moeten worden uit de lijst met konijnen.

Gebruik de volgende Python syntax om een element $$i$$ uit een lijst $$L$$ weg te halen:

{: .language-python}   
     del L[i] 

<b>Let op:</b> 
Als je door een lijst van 20 elementen heenloopt en element 10 weghaalt dan schuiven alle elementen 1 positie op. Element 11 van de oorspronkelijke lijst wordt dan element 10 in de nieuwe lijst etc. De lijst is dan ook ineens 19 posities lang geworden en als je uiteindelijk bij konijn 20 aankomt bestaat dat niet meer. Een 'truc' om dit op te vangen is om de lijst in omgekeerd volgorde af te lopen. Begin dus bij konijn 20, vervolgens naar konijn 19 etc etc. De lijst wordt dan wel korter, maar je komt nooit in de problemen omdat je nooit element weghaalt dat je later nog wilt bekijken.

![](konijnenenvossenEtenstijd.gif){:.inline}{: style="width:30%"}

Om in omgekeerde volgorde door een lijst van 20 konijnen heen te gaan kan je de volgende syntax gebruiken:

{: .language-python}   
    for i_konijn in range(19,-1,-1):
         print i_konijn         

Extra tip: als een konijn opgegeten wordt haal dan het element weg uit **alle** lijsten, dus zowel de x-positie, de y-positie als de bewegingsrichting.

Zet ook de puntjes op de i door op elk moment op het scherm te zetten bij welk tijdstap we zitten en hoeveel vossen en konijnen er zich nog in het bos bevinden.

<br><br>
          
#### [deelopdracht 3b]: Tijd berekenen waarop de konijnenpopulatie gehalveerd is (+ plot)

Als we de simulatie langer laten lopen zullen we zien dat er een moment komt dat de vossen de helft van de konijnen opgegeten hebben. Maar hoe lang duurt dat ?

<b>Tip voor we beginnen:</b> Het weergeven van bewegende en verdwijnende konijnen op het scherm is enorm tijdrovend. Tot 1000 tijdstappen werkt dit prima, maar bij langere of meerdere simulaties is het niet praktisch. Door de visualisatie weg te laten kan je enorm veel tijd winnen. Zorg dat je in de functie `prooipredator()` een variabele toevoegt waarmee je makkelijk kan kiezen of je wel/niet de functie `teken_het_bos()` aanroept. Vanaf nu gaan we de visualisatie niet meer aanroepen. Tenzij je iets wilt bekijken natuurlijk. 
En toch is het visualiseren van een enkele simulatie enorm belangrijk en meer dan 'gewoon leuk'. Het is een krachtige manier om fouten in je code op te sporen. Erg handig, zoals je waarschijnlijk eerder in de module al ervaren hebt toen je de bosrand of het opeten van de konijnen aan het implementeren was. 


Om de tijd te berekenen waarop de helft van de konijnen opgegeten is gaan we twee dingen aanpassen in het programma:

   1. Laat de simulatie 1000 seconden lopen en hou in de functie `prooipredator()` een lijst bij die voor elke tijdstap het aantal konijnen bijhoudt en zorg dat de functie `prooipredator()` deze lijst als return-value teruggeeft aan het eind van het programma.
   
   2. Schrijf een nieuwe functie `gemiddelde_halfwaardetijd()` die een enkele keer de functie `prooipredator()` aanroept. Omdat deze functie de hele lijst met aantal konijnen op elke tijdstap teruggeeft kan je hiermee uitrekenen op welk moment er voor het eerst minder dan de helft van de konijnen rondlopen in het bos. 
   
De tijd die de vossen daarvoor nodig hebben zal voor elke nieuwe simulate anders zijn. Hieronder vind je een paar grafieken van het aantal konijnen als functie van de tijd voor twee simulaties. Voor we van 1000 simulaties de gemiddelde tijd waarbij 50% van de konijnen verdwenen is is het belangrijk om zeker te weten dat de waardes die je hebt bepaald ook echt kloppen. Probeer dus eerst deze grafieken na te maken om te kijken of je inderdaad de goede gegevens uit je simulatie haalt.

 ![](halfwaarde3x.png){: style="width:65%"}

Aan het eind van de simulatie moet op het scherm verschijnen:

{: .language-python}   
    Na x.xx seconde is meer dan de helft van de konijnen opgegeten

#### Deelopdracht (3c): <b>Gemiddelde</b> tijd waarbij de konijnenpopulatie gehalveerd is

Ons programma is nu opgezet om een enkele simulatie te runnen door de functie `prooipredator()` aan te roepen, maar zoals je ziet als je verschillende simulaties bekijkt is er een vrij grote spreiding in de precieze halfwaarde tijd. Om de gemiddelde halfwaardetijd te bepalen zullen we de een groot aantal simulaties moeten uitvoeren, voor elk de halfwaardetijd bepalen om dan uiteindelijk uit al die getallen het gemiddelde te bepalen.

<b>Let op:</b> De grafieken van het aantal konijnen als functie van de tijd zoals we die in de vorige deelopdracht hebben gemaakt hebben we gemaakt om te kijken of onze berekening klopte. Nu we daarvan overtuigd zijn kunnen we die weglaten. Zorgt dat de grafiek alleen gemaakt wordt als we in onze functie maar 1 keer `prooipredator()` aanroepen. In de rest van de opdracht kijken we naar de waardes en doen plots er niet meer toe.

Pas de functie `gemiddelde_halfwaardetijd()` aan zodat die niet 1 keer, maar een groot aantal keer (500 keer) de functie `prooipredator()` aanroept, steeds de halfwaardetijd opslaat, om uiteindelijk het gemiddelde te berekenen. Dit duurt wel even, dus zorg dat elke 25e simulatie op het scherm geprint wordt welke simulatie nu uitgevoerd wordt.

Op het scherm moet na de laatste simulatie het volgende verschijnen:

{: .language-python}   
    Een gesimuleerde wereld met: Nkonijn=25 (v=1), Nwolf=2 (v=2), Nsimulaties = 100:
    Gemiddelde halfwaardetijd konijnen = x.xx seconde

#### Deelopdracht (3d): Strategie konijnen: helpt het om onze snelheid aan te passen?

We hebben in de vorige opdracht gekeken wat de gemiddelde halfwaardetijd is van de konijnenpopulatie voor een specifieke snelheid van de konijnen. De konijnen willen natuurlijk niet dood en moeten iets bedenken. Discussiepunt onder de konijnen is nu of ze juist beter heel hard kunnen gaan lopen of juist stil moeten gaan zitten en hopen dat de wolven ze niet vinden. Aan ons om de optimale strategie te bepalen voor de konijnen.

De vraag in deze opdracht is: run de functie `gemiddelde_halfwaardetijd()` aan met verschillende waardes van de snelheid voor de konijnen en maak een grafiek te maken van de gemiddelde halfwaardetijd als functie van de snelheid van de konijnen. Probeer verschillende snelheden voor de konijnen: snelheden van 0.0, 0.5, 1.0, 1.5, 2.0, 2.5 en 5.0 meter per seconde.

Je mag in deze opdracht de snelheid van de konijnen `snelheid_konijn` in de functie `prooipredator()` steeds met de hand veranderen en ook de antwoorden zelf opschrijven voor je uiteindelijk een grafiek maakt van de gemiddelde halfwaardetijd als functie van de snelheid van de konijnen. Welke trend zie je? Is het nou handiger voor de konijnen om juist langzamer of sneller te bewegen?

## Opdracht 4: Reproducerende konijnen en overbevolking

We hebben in de vorige opdracht bestudeerd hoe (snel) het aantal konijnen afneemt als er twee vossen in het bos rondlopen. Het aantal konijnen kan echter ook toenemen, want konijnen zich ook voortplanten. We gaan kijken wat het effect is van reproductie als we dat als element meenemen in onze populatie-simulaties. Tegelijk met een mogelijke 
toename van het aantal konijnen is het ook belangrijk om mee te nemen dat ons bos maar voedsel biedt voor een beperkt aantal konijnen. Beide aspecten gaan we meenemen in onze simulatie.

Het systeem is vrij instabiel en je zal zien dat na 1000 seconden of de konijnen winnen (konijnen zitten tegen het maxmimum aantal aan) of de vossen winnen (alle konijnen zijn opgegeten). De vraag die we in deze opdracht gaan beantwoorden is de volgende: 'hoe vaak winnen de konijnen en hoe vaak winnen de vossen?' Aan het eind van deze opdracht moet op het scherm verschijnen:

{: .language-python}   
     Een gesimuleerde wereld met: Nkonijn=25 (v=1), Nwolf=2 (v=2), Nsimulaties = 200:     
     In x.x procent van de gevallen winnen de konijnen

We gaan deze vraag in stapjes beantwoorden. Voeg in de functie `prooipredator()` twee nieuwe functies toe: `reproduceren_konijnen()` en `overbevolking()` toe die deze fenomenen gaat implementeren. Tijdens het implementeren van beide nieuwe functies doen we dit steeds voor een enkele simulatie. Het is ook mogelijk om in deze eerste stappen van de opdracht de visualisatie weer 'aan' te zetten.

<b>Let op:</b> we gaan nu een aanpassing aan de bestaande code maken uit. Om te zorgen dat de huidige werkende code goed bewaard blijft gaan we deze opdracht maken in een nieuw bestand. Maak daarna een nieuw Python bestand, `prooipredator_tm_opdracht4.py`, kopieer de code die je tot nu toe hebt gemaakt en ga verder in deze nieuwe file.

#### Deelopdracht 4a: reproducerende muizen

Het eerste aspect dat we in gaan voeren is het vermogen van de muizen om zich voort te planten. Maak een nieuwe functie `reproduceren_konijnen()` die wordt aangeroepen na de bestaande functies (het verplaatsen van de konijnen, het verplaatsen van de wolven en het opeten van de konijnen door de wolven) en die steeds kijkt of er konijnen dicht bij elkaar zitten. Als dat het geval is moet het programma de nieuwe jongen konijnen op een random plek in het bos neerzetten.

Ga hierbij als volgt te werk:

  1. Roep de functie pas aan na 200 seconden. De konijnen beginnen al erg dicht bij elkaar en zijn in het begin nog te jong om zich voort te planten. Dit is een aanpassing in de functie `prooipredator()` zelf die bepaalt welke functies aangeroepen worden voor elke tijdstap.

  2. Bepaal eerst hoeveel paren konijnen er dicht bij elkaar zitten (afstand < 1). Dit bepaalt het aantal nestjes. <b>Let op:</b> vermijd hierbij dubbeltellen. 

  3. Genereer vervolgens voor elk nestje 4 nieuwe konijnen, geef ze een random positie in het bos, een random bewegingsrichting en voeg ze toe aan de lijst van konijnen.
  
Als je een paar simulaties bekijkt zal je zien dat het een erg instabiel systeem is. Als de vossen nog niet genoeg konijnen hebben opgegeten op het moment dat de konijnen gaan reproduceren kan het aantal konijnen exponentieel groeien. En zo je programma vast laten lopen. In de volgende opdracht gaan we deze ongewenste en onrealistische effecten repareren.
  
#### [deelopdracht 4b]: maximum aantal konijnen in het bos

De tweede functionaliteit die we toe gaan voegen is het beperken van het aantal konijnen dat in het bos kan bestaan. De hoeveelheid voedsel in het bos is maar genoeg voor 50 konijnen. Maak een nieuwe functie `overbevolking()` die na `reproduceren_konijnen()` aangeroepen wordt. Het doel van deze functie is om te zorgen dat er nooit meer dan 50 konijnen in het bos aanwezig zijn. Kijk dus hoe lang de lijst met konijnen is en verwijder elk element in de lijst van konijnen boven de 50. Let op dat je die konijnen uit alle drie de konijnenlijsten haalt: x-positie, y-positie en hoek.

Zoals je al gezien hebt is het systeem vrij instabiel. Na 1000 seconden zal je (meestal) in een stabiele toestand belanden. Of de konijnen hebben gewonnen (konijnen zitten tegen het maxmimum van 50 aan) of de vossen hebben gewonnen (bijna alle konijnen zijn opgegeten). De onderstaande grafiekenl aten het aantal konijnen zien als functie van de tijd voor twee simulaties die elk een extremum gevonden hebben. Deze grafieken zijn gemaakt met bijna vrijwel dezelfde functie die we in deelopdracht 3c om het de fractie levende konijnen als functie van de tijd te zien, 

 ![](DynamicaWinstVossen.png){: style="width:40%"}
 ![](DynamicaWinstKonijnen.png){: style="width:40%"}

De opdracht van deze stap is om dit type grafiek te maken voor een enkele simulatie. Je kan jezelf zo overtuigen dat de functie `overbevolking()` echt werkt en dat we inderdaad in een instabiele situatie zitten. Schrijf een nieuwe functie `winstkans_konijnen()` die een enkele simulatie maakt door de functie `prooipredator()` aan te roepen en een plot maakt voor die simulatie net als de plots hierboven.

<b>Tip:</b> de functie die we hier moeten maken lijkt sterk op de functie `gemiddelde_halfwaardetijd()` die we in opgave 3b en 3c hebben gebruikt. Kopieer die functie en gebruik dat als de 'basis' die je vervolgens aan kan passen. De functie `prooipredator()` gaf als return-waarde al het aantal konijnen op elk moment in de tijd. Gebruik dat ook hier als basis voor je plot.

Naast het tekenen van de plot is het ook belangrijk om de conclusie te trekken of de konijnen of de vossen gewonnen hebben. Als op tijdstap 1000 het aantal konijnen groter is dan 45 hebben de konijnen gewonnen, als het minder is dan 5 hebben de vossen gewonnen. Elk andere hoeveelheid konijnen betekent dat het een gelijkspel is.

Aan het eind van de simulatie moet de functie op het scherm printen wie gewonnen heeft.

{: .language-python}   
     Het aantal konijnen na 100 stappen was XXX.     
     Dit betekent dat de XXX gewonnen heeft.
     
#### De opdracht: winstkansen konijnen

We zijn nu in staat de originele vraag in deze opdracht te beantwoorden: wat is de winstkans van de konijnen? Concreter: in welk percentage van de simulaties zijn er na 1000 seconden meer dan 45 konijnen in het bos? Pas de functie `winstkans_konijnen()` uit deel opdracht 4b zo aan dat er nu 200 simulaties gedraaid worden en hou voor elk van de simulaties bij of de konijnen hebben gewonnen (meer dan 45 konijnen), of de vossen hebben gewonnen (minder dan 5 konijnen) of dat er een gelijkspel was (alle andere gevallen).

<b>Let op:</b> de plot die je gemaakt hebt in deelopdracht 4b hoef je nu niet meer te maken voor elk van de 200 simulaties. Zorg dan ook dat de plot alleen gemaakt wordt als de functie `winstkans_konijnen()` maar 1 simulatie draait. 

Bereken na alle simulaties gerund te hebben de gevraagde fractie en print de winstkansen voor de konijnen als volgt op het scherm:

{: .language-python}   
     Een gesimuleerde wereld met: Nkonijn=25 (v=1), Nwolf=2 (v=2), Nsimulaties = 200:     
     In x.x procent van de gevallen winnen de konijnen






