# Populatiedynamica: prooi-predator model#

Een klassiek voorbeeld van een complex dynamisch systeem is het zogenaamde prooi-predator 
model. De basis van de wiskundige beschrijving van de populaties zijn de bekende 
[Lotka-Volterra vergelijkingen](https://en.wikipedia.org/wiki/Lotka–Volterra_equations) vergelijkingen. De wiskunde wordt al snel erg complex en het is ook niet altijd makkelijk om van tevoren in te schatten welke effecten een nieuw aspect van het gedrag heeft op de verschillende populaties in het systeem. 

In deze module zullen we zelf een simulatie schrijven van een overzichtelijk systeem: een bos van 100 bij 100 meter waarin 25 konijnen en 2 vossen leven. Door het zelf te programmeren kunnen we nieuwe fenomenen toevoegen. Door het systeem te visualiseren krijgen we direct feedback op onze code en zien we ook de consequenties van de nieuwe gedragselementen die we toegevoegd hebben. Doel van deze module is om steeds meer complexiteit in het gedrag van de konijnen en vossen in te bouwen in onze simulatie en om uiteindelijk te zien of de vossen of de konijnen als winnaar uit de bus zullen komen als we ze loslaten in dit ge&iuml;solerde stukje bos.


## Startpunt: twee bewegende konijnen op het scherm ##


> Let op: animaties kun je niet maken in de online Python IDE! Hiervoor heb je een installatie op je eigen computer nodig. Mail gerust als je dit wil doen en hulp nodig hebt.

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

   1. `prooipredator()`: definieert de startpositie van de konijnen, stuurt de simulatie door stapjes in de tijd te nemen (steeds een seconde) en roept voor elke stap in de tijd de functies `verplaats_de_konijnen()` en `teken_het_bos()` aan. Wordt aangeroepen vanuit het 'hoofdprogramma', helemaal onderaan het stuk code
    
   2. `verplaats_de_konijnen()`: verandert de positie van de konijnen 

   3. `teken_het_bos()`:  tekent de konijnen op het scherm
 
<b>Extra stukje Python: globale variabelen</b><br>
Als een variabele of lijst in meerdere functies in een programma gebruikt wordt is het soms handig om die variabel als zogenaamd 'globaal' te definieren. Alle functies in het programma kunnen aangeven dat ze die variabelen willen gebruiken. In ons stukje code zijn er twee lijsten die we graag delen/gebruiken in de verschillende functies: `posities_konijnen_x` en `posities_konijnen_y`. Deze lijsten worden gebruikt in elk van de drie functies: de startwaardes worden gedefini&euml;erd in `prooipredator()`, ze worden veranderd in de functie `verplaats_de_konijnen()` en daarna getekend in `teken_het_bos()`. De syntax om globale variabelen te defini&euml;ren en gebruiken is als volgt: de lijsten worden eerst in het hoofdprogramma (helemaal bovenaan) als globaal gedefini&euml;erd en vervolgens wordt aan het begin van elk van de drie functies vermeld dat we ze in die functie willen gebruiken.

Als je een variabele in een enkele functie gebruikt moet je die <b>niet</b> als globaal defini&euml;ren. 


## Opdracht 1: modelleren van de beweging van de konijnen 

We hebben in bovenstaand voorbeeld aangenomen dat de konijnen bij elke stap in de tijd (elke seconde) steeds 0,6 meter naar rechts opschuiven en 0,8 meter omhoog. Dit is nog erg ver weg van een realistisch systeem natuurlijk: konijnen bewegen niet synchroon, ze rennen ook niet in een rechte lijn en als we de tijd langer door zouden laten doorlopen zullen de konijnen vrolijk het bos uitlopen. Dat is niet de bedoeling in deze opgave. De konijnen bewegen elk in hun eigen richting en als de konijnen bij de rand van het bos komen zullen ze weer snel terug het (veilige) bos inlopen. In deze eerste opdracht zullen we deze eerste stappen op weg naar realistische konijnen doorvoeren in onze code. Maak een bestand `prooipredator_opdracht1.py` aan, kopieer bovenstaande code erin en volg de onderstaande deelopdrachten.

<br>

#### Deelopdracht (1a): nieuwe parametrisatie beweging konijnen

In de functie `verplaats_de_konijnen()` laten we nu de konijnen steeds een stapje opzij en een stapje omhoog doen. We hadden de verplaatsing van de twee konijnen in het stukje voorbeeldcode ook op een andere manier kunnen implementeren. Bijvoorbeeld door te zeggen dat konijnen allemaal met dezelfde snelheid bewegen (1 meter per seconde) en dat ze, in dit specifieke voorbeeld in ieder geval, ook nog eens bewegen onder eenzelfde hoek ten opzichte van de x-as, ongeveer 51 graden. In de rest van de opdracht gaan we inderdaad werken met een universele konijnen-snelheid, maar gaan wel zorgen dat elk konijn zijn eigen bewegingsrichting krijgt. 

Voeg in het hoofdprogramma een variabele `snelheid_konijnen` toe die de universele snelheid van de konijnen aangeeft. Voeg ook een lijst `hoeken_konijnen` toe waarbij je voor elk konijn bijhoudt onder welke hoek ten opzichte van de x-as hij beweegt. Omdat je de nieuw variabelen gebruikt in twee functies, namelijk zowel `prooipredator()` (kiezen van de initi&euml;le waardes) en in `verplaats_de_konijnen()` (uitrekenen nieuwe posities ) is het handig ook deze variabelen als globaal te defini&euml;ren.

Op de plek in de functie `verplaats_de_konijnen()` waar de nieuwe posities van de konijnen uitgerekend wordt moet je voor elk konijn de snelheid en de hoek eerst omrekenen naar een snelheid in de x- en y-richting zodat je daarmee de verplaatsing in de x- en y-richting kan uitrekenen. Dat zijn immers de posities die we bijhouden voor elk konijn. Voor elk konijn gebruiken we eerst:

{: .language-python}
       hoek = hoeken_konijnen[i_konijn]
       v_x = snelheid_konijnen * cos(hoek)
       v_y = snelheid_konijnen * sin(hoek)
    
En omdat de tijdstappen precies 1 seconde zijn kunnen we dan als volgt de nieuwe posities van het konijn uitrekenen:

{: .language-python}
       posities_konijnen_x[i_konijn] = posities_konijnen_x[i_konijn] + v_x
       posities_konijnen_y[i_konijn] = posities_konijnen_y[i_konijn] + v_y

Eigenlijk staat er in bovenstaande code v_x*dt, maar omdat de tijdstapjes 1 seconde zijn kunnen de dt weglaten. We hebben met deze implementatie nu de mogelijkheid om bij de start van de simulatie elk konijn een unieke bewegingsrichting te geven. Voer bovenstaande veranderingen door in je programma, geef elk van de konijnen een eigen richting en laat de simulatie 20 seconden lopen in plaats van 10. 

<b>Let op:</b> om de goniometrische functies (zo) in je programma te kunnen gebruiken moet je de wiskunde bibliotheek implementeren: `from math import *`

<br>

#### Deelopdracht (1b): de bosrand 

Onze konijnen, angsthazen dat het zijn, zullen nooit het bos verlaten. Zodra ze per ongeluk een stap buiten het bos doen draaien ze zich pijlsnel om en zullen daarna weer snel het bos inrennen in dezelfde richting als waar ze vandaan kwamen. Pas de functie `verplaats_de_konijnen()` zodanig aan dat de konijnen altijd in het bos blijven rondlopen.

Volg de volgende strategie als het konijn na een stap gezet te hebben buiten het bos is geraakt:

   1. neem een stap terug (zowel x als y) zodat het konijn weer in de oorspronkelijke positie zit
   2. zorg dat het konijn zich omdraait door de hoek waarin het konijn beweegt te veranderen naar een richting die precies tegenovergesteld is aan de huidige richting: 'hoek_nieuw = hoek +  $$\pi$$'. Stop deze nieuwe bewegingsrichting op in de lijst `hoeken_konijnen`. Bij de volgende stap rent het konijn dus weer terug het bos in
   
Probeer dit te testen door een van de konijnen (recht) naar de bosrand te laten bewegen en te kijken of hij inderdaad weer het bos in 'stuitert' zodra hij over de rand van het bos heengaat.

<br>

#### Deelopdracht (1c): random konijnen-gedrag

Iedereen die konijnen heeft zien lopen weet dat ze niet in een rechte lijn bewegen, maar af en toe ineens stilzitten om dan van richting te veranderen. Deze eigenschap gaan we ook implementeren in onze simulatie.

![](konijnen.gif){:.inline}{: style="width:30%"}

Pas de functie `verplaats_de_konijnen()` zo aan dat het konijn gemiddeld eens in de 20 seconden stilzit en daarna in een willekeurige andere richting verder wandelt. Praktisch betekent dit dat een konijn elke seconde een 5% kans heeft om stil te zitten en van richting te veranderen en 95% kans heeft om gewoon door te lopen in dezelfde richting. Een mogelijke implementatie van dit gedrag is door gebruik te maken van een random getal $$x$$ (tussen 0 en 1).

{: .language-python}
    x<0.05 (5% kans): geen stap, wel nieuwe hoek (0<hoek<2*pi) 
    x>0.05 (95% kans): zet een gewone stap

<b>Let op:</b> om een random getal te genereren heb je de random bibliotheek nodig. Zorgt dat je code die kent: `from random import *`

<br>

#### Deelopdracht (1d): simulatie met 25 konijnen 

Een wereld met twee konijnen is natuurlijk niet realistisch. Pas het begin van `prooipredator()` zo aan dat er 25 konijnen in de simulatie zijn. Maak de code zo dat de konijnen elk op een random positie geplaatst worden, maar wel in een vierkantje dat gegeven wordt door $$20<(x,y)<30$$. Geef elke van de konijnen ook een random startrichting: $$0<$$hoek$$<2\pi$$.

<b>Let op:</b> In de functie `prooipredator()` voeg je voor elk van de 25 konijnen de 
parameters (x-positie, y-positie en hoek) in de lijstlijsten. Let erop dat je voor je dat doet de lijsten als 'leeg' definieert. Dus: `posities_konijnen_x = []` etc. Deze 'schone lei' is belangrijk als we meerdere simulaties achter elkaar gaan maken. En dat willen we.

<br>
