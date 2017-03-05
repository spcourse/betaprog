# Populatiedynamica: prooi-predator model#

Een klassiek voorbeeld van een complex dynamisch systeem is het zogenaamde prooi-predator 
model. De basis van de wiskundige beschrijving van de populaties zijn de bekende 
[Lotka-Volterra vergelijkingen](https://en.wikipedia.org/wiki/Lotka–Volterra_equations) vergelijkingen. De wiskunde wordt al snel erg complex en het is ook niet altijd makkelijk om van tevoren in te schatten welke effecten een nieuw aspect van het gedrag heeft op de verschillende populaties in het systeem. 

In deze module zullen we zelf een simulatie schrijven van een overzichtelijk systeem: een bos van 100 bij 100 meter waarin 25 konijnen en 2 vossen leven. Door het zelf te programmeren kunnen we nieuwe dingen 
proberen en met de visualisatie krijgen we ook gelijk feedback en inzicht.

## Startpunt: twee konijnen op het scherm

We beginnen deze module, een beetje tegen de filosofie van de cursus in, niet met een leeg scherm, maar met het volgende stukje code. Niet omdat het erg moeilijk is, maar omdat we dan een gemeenschappelijk startpunt hebben en we op dezelfde manier stukken code toevoegen.

Het stukje code hieronder bestaat uit 3 functies. De hoofdfunctie, die wordt aangeroepen vanuit het hoofdprogramma helemaal onderaan, is `prooipredator()`. Deze functie definieert de startpositie van twee konijnen en neemt stapjes in de tijd (steeds een seconde) en roept voor elk tijdstip dan twee functies aan: `verplaats_de_konijnen()` die de positie van de konijnen verandert en `teken_het_bos()` die de konijnen vervolgens op het scherm tekent.

##### Extra stukje Python: globale variabelen
Als een variabele of lijst in meerdere functies in een programma gebruikt wordt is het soms handig om die variabel als zogenaamd 'globaal' te definieren. Alle functies in het programma kunnen aangeven dat ze die variabelen willen gebruiken. Deze variabelen worden daarmee gedeeld. In ons stukje code zijn dat twee lijsten: `posities_konijnen_x` en `posities_konijnen_y`. Deze lijsten worden namelijk gebruikt in elk van de drie functies: de startwaardes worden gedefini&euml;erd in `prooipredator()`, ze worden veranderd in de functie `verplaats_de_konijnen()` en daarna getekend in `teken_het_bos()`. De syntax om globale variabelen te defini&euml;ren en gebruiken is als volgt: de lijsten worden eerst in het hoofdprogramma (helemaal bovenaan) als globaal gedefini&euml;erd en vervolgens wordt aan het begin van elk van de drie functies vermeld dat we ze in die functie willen gebruiken.

Als je een variabele in maar 1 functie gebruikt moet je die <b>niet</b> als globaal definieren. 


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

In de natuur leven vossen en konijnen niet vredig naast elkaar. Als een vos een konijn tegenkomt zal hij het konijn opeten. 

<b>Let op:</b> we gaan nu een aanpassing aan de bestaande code maken uit opdracht 1 en 2. Om te zorgen dat de code uit opdracht 1 bewaard blijft gaan we deze opdracht maken in een nieuw bestand. Sla je bestaande code op in een file `prooipredator_tm_opdracht2.py`. Maak daarna een nieuw Python bestand, `prooipredator_tm_opdracht3.py`, kopieer de code die je tot nu toe hebt gemaakt en ga verder in deze nieuwe file.

#### [deelopdracht 3a]: verdwijnende konijnen

Schrijf een nieuwe functie `Etenstijd()` die in de 'hoofdfunctie' `prooipredator()` wordt aangeroepen na de functie `verplaats_de_konijnen()`. Deze functie heeft als taak te evalueren, voor elk konijn, of hij zich in de buurt bevindt van een vos. Met 'in de buurt' wordt trouwens bedoeld: binnen 5 meter van de dichtstbijzijnde vos. Als dat zo is sterft het konijn en moet hij verwijderd worden uit de lijst met konijnen.

Gebruik de volgende Python syntax om een element $$i$$ uit een lijst $$L$$ weg te halen:

{: .language-python}   
     del L[i] 

<b>Let op:</b> 
Als je door een lijst van 20 elementen heenloopt en element 10 weghaalt dan schuiven alle elementen 1 positie op. Element 11 van de oorspronkelijke lijst wordt dan element 10 in de nieuwe lijst etc. De lijst is dan ook ineens 19 posities lang geworden. Een slimme 'truc' om dit op te vangen is om de lijst in omgekeerd volgorde af te lopen. Begin dus bij konijn 20, vervolgens naar konijn 19 etc etc. De lijst wordt dan wel korter, maar je komt nooit in de problemen omdat je nooit element weghaalt die je later nog wilt bekijken.

![](konijnenenvossenEtenstijd.gif){:.inline}{: style="width:30%"}

Om in omgekeerde volgorde door een lijst van 20 konijnen heen te gaan kan je de volgende syntax gebruiken:

{: .language-python}   
    for i_konijn in range(19,-1,-1):
         print i_konijn         

Extra tip: als een konijn opgegeten wordt haal dan het element weg uit **alle** lijsten, dus zowel de x-positie, de y-positie als de bewegingsrichting.

Zet ook de puntjes op de i door op elk moment op het scherm te zetten bij welk tijdstap we zitten en hoeveel vossen en konijnen er zich nog in het bos bevinden.
<br><br>
          
#### [deelopdracht 3b]: Gemiddelde halfwaardetijd konijnenpopulatie

Het weergeven van bewegende en verdwijnende konijnen op het scherm is enorm tijdrovend. Als je met de opzet zoals hierboven 100 tijdstapjes wilt doen kan je daar nog op wachten, maar tienduizend stapjes is al niet meer te doen. Door de visualisatie weg te laten kan je enorm veel tijd winnen en het stelt je in staat wat langere scenario's door te rekenen of juist veel verschillende simulaties. En toch is het visualiseren van een enkele simulatie enorm belangrijk en meer dan 'gewoon leuk om te zien'. Visualiseren is een goede techniek om fouten in je code op te sporen. Erg handig, zoals je waarschijnlijk in de bovenstaande 
opgave al ervaren hebt toen je de implementatie van de bosrand of het opeten van de konijnen aan het implementeren was.

Zorg dat je in de hoofdfunctie `prooipredator()` een variabele toevoegt waarmee je makkelijk kan kiezen of je wel/niet de functie `teken_het_bos()` aanroept. Vanaf nu gaan we de visualisatie niet meer aanroepen. Tenzij je iets wilt bekijken natuurlijk.

Verander de functie `prooipredator()` zodanig dat je aan het eind van de functie weet bij welke tijdstap er voor het eerst minder dan 50% van het oorspronkelijk aantal konijnen nog levend in het bos rondloopt. In navolging van radioactief verval noemen we dit de halfwaardetijd van de konijnen. Hieronder vind je een paar grafieken van het aantal konijnen als functie van de tijd. probeer deze grafieken na te maken om te kijken of je inderdaad de goede gegevens uit je simulatie haalt.

 ![](halfwaarde3x.png){: style="width:65%"}

Ons programma is nu opgezet om een enkele simulatie te runnen door de functie `prooipredator()` aan te roepen, maar zoals je ziet is er een vrij grote spreiding in de precieze halfwaarde tijd. Om de gemiddelde halfwaardetijd te bepalen zullen we de een groot aantal simulaties moeten uitvoeren, voor elk de halfwaardetijd bepalen om dan uiteindelijk uit al die getallen het gemiddelde te bepalen.

Schrijf een nieuwe functie `GemiddeldeHalfwaardetijd()` die een groot aantal keer (500) de functie `prooipredator()` aanroept en steeds de halfwaarde tijd opslaat in een lijst om uiteindelijk het gemiddelde te berekenen en op het scherm te print. Zorg dat de functie `prooipredator()` als return-waarde de halfwaardetijd teruggeeft.

Op het scherm moet uiteindelijk verschijnen:

{: .language-python}   
    Een gesimuleerde wereld met: Nkonijn=25 (v=2), Nwolf=2 (v=4), Nsimulaties = 100:
    Gemiddelde halfwaardetijd konijnen = x.xx seconde


#### Deelopdracht (3c): Strategie konijnen: snelheid aanpassen

We hebben in de vorige opdracht gekeken wat de gemiddelde halfwaardetijd is van de konijnenpopulatie voor een specifieke snelheid van de konijnen. De konijnen willen natuurlijk niet dood en moeten iets bedenken. Discussiepunt onder de konijnen is nu of ze juist beter heel hard kunnen gaan lopen of juist stil moeten gaan zitten en hopen dat de wolven ze niet vinden. Aan ons om de optimale strategie te bepalen voor de konijnen.

Run de functie `GemiddeldeHalfwaardetijd()` met een aantal waardes van de snelheid voor de konijnen en maak een grafiek van de gemiddelde halfwaardetijd als functie van de snelheid. Je mag in deze opdracht de snelheid van de konijnen `snelheid_konijn` in de  functie `prooipredator()` steeds met de hand veranderen. Probeer verschillende snelheden voor de konijnen: snelheden van 0 tot en met 5 in stapjes van 0.5 en maak een grafiek van de gemiddelde halfwaardetijd als functie van de snelheid. Wat zie je? Logisch?

<br>

### Opgave 4: Reproducerende konijnen en overbevolking

We hebben in de vorige opgave bestudeerd hoe (snel) het aantal konijnen afneemt als er twee vossen in het bos rondlopen. Het aantal konijnen kan echter ook toenemen natuurlijk omdat konijnen zich kunnen voortplanten. We gaan kijken wat het effect is van reproductie als we dat als element meenemen in onze populatie-simulaties. Tegelijk met een mogelijke 
toename van het aantal konijnen is het ook belangrijk om mee te nemen dat ons bos maar voedsel biedt voor een beperkt aantal konijnen. Beide aspecten gaan we meenemen in onze simulatie.

Voeg in de hoofdfunctie `prooipredator()` twee nieuwe functies toe: `BeschuitMetMuisjes()` en `Overbevolking()` toe die deze fenomenen gaat implementeren.

**Stap 1:** reproducerende muizen

Zorgt dat de functie `BeschuitMetMuisjes()` (die trouwens wordt aangeroepen na het verplaatsen van de konijnen, de wolven en het opeten van de konijnen door de wolven) op elke stap in de tijd kijkt of er konijnen dicht bij elkaar zitten en vervolgens nieuwe konijnen in het bos neerzet.

Ga hierbij als volgt te werk:

  1. Roep de functie pas aan na 100 seconden. De konijnen beginnen al erg dicht bij elkaar namelijk en zijn in het begin nog te jong om zich voort te planten.

  2. Bepaal eerst hoeveel paren konijnen er dicht bij elkaar zitten (afstand < 1). Dit bepaalt het aantal nestjes. Let op: vermijd hierbij dubbeltellen. 

  3. Genereer vervolgens voor elk nestje 4 nieuwe konijnen, geef ze een random positie in het bos, een random bewegingsrichting en voeg ze toe aan de lijst van konijnen.
  
**Stap 2:** maximum aantal konijnen in het bos

De functie `Overbevolking()` heeft als doel te zorgen dat er op moment in de tijd nooit meer dan 50 konijnen in het bos aanwezig zijn. Roep de functie aan gelijk na `BeschuitMetMuisjes()`, kijk hoe lang de lijst met konijnen is en verwijder elk element in de lijst van konijnen boven de 50.

#### De opdracht: winstkansen konijnen

Het systeem is vrij instabiel en je zal zien dat na 1000 seconden of de konijnen winnen (konijnen zitten tegen het maxmimum van 50 aan) of de vossen winnen (alle konijnen zijn opgegeten). De onderstaande grafieken, gemaakt met bijna dezelfde routine die we in opdracht 3b gebruikt hebben, laten het aantal konijnen zien als functie van de tijd voor twee simulaties die elk een extremum gevonden hebben.

 ![](DynamicaWinstVossen.png){: style="width:40%"}
 ![](DynamicaWinstKonijnen.png){: style="width:40%"}

De opdracht luidt als volgt: wat is de winstkans van de konijnen? Concreter: in welk percentage van de simulaties zijn er na 1000 seconden meer dan 45 konijnen in het bos? 

Schrijf een functie `WinstkansenKonijnen()` die steeds 200 simulaties draait en van elke simulatie bijhoudt hoeveel konijnen er nog in het bos rondlopen op tijdstip 1000. Bepaal hoe vaak de konijnen winnen (meer dan 45 konijnen), hoe vaak de wolven winnen (minder dan 5 konijnen) en hoe vaak er geen winnaar is (alle andere gevallen). Bereken de gevraagde fractie en print uiteindelijk de winstkansen voor de konijnen als volgt op het scherm:

{: .language-python}   
     Een gesimuleerde wereld met: Nkonijn=25 (v=2), Nwolf=2 (v=4), Nsimulaties = 200:     
     In x.x procent van de gevallen winnen de konijnen






