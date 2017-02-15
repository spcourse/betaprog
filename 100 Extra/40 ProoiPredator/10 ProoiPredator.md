# Prooi predator #

Als er een onderdeel is dat studenten van verschillende opleidingen verbindt is het wel de 

# Vossen en konijnen



#### Startpunt: twee konijnen op het scherm

We beginnen deze module, een beetje tegen de filosofie van de cursus in, niet met een leeg scherm, maar met het volgende stukje code. Niet omdat het erg moeilijk is, maar omdat we dan een gemeenschappelijk startpunt hebben en we op dezelfde manier stukken code toevoegen.

Het stukje code hieronder bestaat uit 3 functies. De hoofdfunctie is `ProoiPredator()`. Deze functie definieert de startpositie van twee konijnen in het bos en neemt stapjes in de tijd. Voor elk stapje in de tijd doen we twee dingn: a) 

    #-------------------
    def ProoiPredator():
    #-------------------

       #--/ startpositie 2 konijnen (x-posities en y-posities op t=0)
       L_konijn_x = [10.,60.]  
       L_konijn_y = [ 2.,10.]  
   
       #--/ neem stapjes in de tijd
       for i_time in range(10):

           #--/ verplaats de konijnen
           VerplaatsKonijnen(L_konijn_x,L_konijn_y)    

           #--/ plot de positie van de konijnen
           Teken_het_bos(L_konijn_x,L_konijn_y)
            
       #--/ einde functie                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
       return


    #--------------------------------------------
    def VerplaatsKonijnen(L_konijn_x,L_konijn_y):
    #--------------------------------------------

         #--/ doe elke tijdstap een stapje voor de konijnen (2 naar rechts en 3 naar boven)
         Aantal_konijnen = len(L_konijn_x)   
         for i_konijn in range(Aantal_konijnen):
             L_konijn_x[i_konijn] = L_konijn_x[i_konijn] + 1.2 
             L_konijn_y[i_konijn] = L_konijn_y[i_konijn] + 1.6 
  
         #--/ einde functie
         return


    #--------------------------
    def Teken_het_bos(L_x,L_y):
    #--------------------------

         #--/ GRAFIEK (1): definieer een vast assenstelsel (het bos)
         fig=plt.figure()
         ax=fig.add_subplot()
         plt.axis([0,100,0,100])

         #--/ plot de positie van de konijnen (blauwe stip)
         plt.plot(L_x, L_y, 'o', color = 'blue')   

         #--/ PR (het oog wil ook wat): cirkels rond de posities van de konijnen
         Aantal_konijnen = len(L_x)   
         for i_konijn in range(Aantal_konijnen):
             x = L_x[i_konijn]
             y = L_y[i_konijn]
             circ1=plt.Circle((x,y), radius=2, facecolor='blue', edgecolor ='None', alpha = 0.1)  
             circ2=plt.Circle((x,y), radius=2, facecolor='None', edgecolor ='black', alpha = 1.0)
             ax.add_patch(circ1)
        
         #--/ GRAFIEK (2): update frames voor simpele animatie
         plt.draw()        #--/ Update de grafiek
         plt.pause(0.001)
         plt.clf()         #--/ Maak grafiek leeg bij elke tijdstap
         plt.show()
 
         #--/ einde functie
         return




#### Opgave 1: Toevoegen realiteit: andere variabelen en de langere termijn

We hebben in bovenstaand voorbeeld aangenomen dat de konijnen bij elke stap in de tijd (elke seconde) drie stappen naar rechts opschuiven en vier omhoog gaan. We hadden dit ook kunnen representeren door te stellen dat de konijnen bewegen met een snelheid van 2 meter per seconde bewegen onder een hoek van ongeveer 51 graden met de x-as. Als we de tijd langer laten doorlopen zullen we ook zien dat onze konijnen het bos uitlopen. Dat is niet de bedoeling. Als de konijnen bij de rand van het bos komen zullen ze weer het bos inlopen. In deze opgave zullen we deze eerste stappen op weg naar realistische konijnen doorvoeren in onze code.

##### deelopdracht (1a): nieuwe parametrisatie beweging konijnen

Voeg in het hoofdprogramma een extra variabele `v_konijn` toe die de snelheid van de konijnen aangeef (2 m/s) en voeg een lijst `L_konijn_hoek` toe waarbij je voor elk konijn bijhoudt onder welke hoek ten opzichte van de x-as hij beweegt. Geef de konijnen allemaal de bovenstaande hoek (atan(1.6/1.2)). Pas ook de code zo aan dat op de plek waar de nieuwe positie van de konijnen uitgerekend wordt gebruik wordt gemaakt van deze twee variabelen. In de hoofd code `PooiPredator()` moet dus verschijnen:

       VerplaatsKonijnen(L_konijn_x,L_konijn_y, L_konijn_hoek, v_konijn)    

Op de plek waar de nieuwe posities van de konijnen uitgerekend worden moet je de snelheid en de hoek waaronder de konijnen bewegen eerst omrekenen naar een  snelheid in de x- en y-richting. Gebruik hiervoor $$v_x = v \cos(\alpha)$$ en $$v_x = v \sin(\alpha)$$.

Voor de nieuwe positie van elk konijn krijgen we dan ook:
    L_x[i_konijn] = L_x[i_konijn] + vx


##### deelopdracht (1b): de bosrand 

Zoals we al eerder gemeld hebben zijn konijnen vrij angstige beesten. Onze konijnen zullen nooit vanuit zichzelf het bos verlaten. 
In de functie `VerplaatsKonijnen()` reken je de nieuwe positie uit van de konijnen. Gelijk erna kan je bekijken of je misschien per ongeluk het bos uit bent gestapt. Als dat niet het geval is ben je klaar, maar als dat niet zo is dan weten we dat de stap die je gemaakt hebt in de simulatie 'ongeldig' is. We moeten dan de volgende stappen doorlopen:

   1. neem een stap terug (in zowel x als y) zodat het konijn weer in de oorspronkelijke positie zit
   2. verander de richtjng waarin het konijn beweegt. Kies een random hoek tussen 0 en $$2\pi$$ en 
    stop die in de lijst `L_konijn_hoek`. 
   3. Neem een nieuwe stap
   
Dit moet je herhalen tot het konijn een stap gezet heeft die weer in het bos uitkomt. De structuur die je gaat bouwen heeft dus de onderstaande opzet. 

Voor elk konijn waarvoor je de nieuwe positie uitrekent dus:

    NeemNogEenStap = 1
    while ( NeemNogEenStap == 1 ):    

          # bereken stap in x en y (mbv L_konijn_hoek)
          # bereken nieuwe x-positie
          # bereken nieuwe y-positie

          if( Nieuwe_positie_buiten_het_bos ):
              # zet x terug op de oude positie
              # zet y terug op de oude positie
              # kies random hoek en zet die in L_konijn_hoek          
          else:    
              NeemNogEenStap = 0    

probeer dit te testen door een konijn naar rechts te laten bewegen en te kijken of hij inderdaad weer het bos in 'stuitert' zodra hij over de rand van het bos heengaat.


##### deelopdracht (1c): random konijnen-gedrag

![](konijnen.gif){:.inline}{: style="width:30%"}

Iedereen die konijnen heeft ziet lopen weet dat het ze op random momenten ineens stilzitten en dan van richting veranderen in een random richting. Die eigenschap gaan we implementeren in de simulatie.

Pas de functie `VerplaatsKonijnen()` zo aan dat er in 5% van de stappen een konijn helemaal geen stap zet, maar waarbij wel de richting waarin het konijn zich voortbeweegt een nieuwe random waarde krijgt (tussen 0 en $$2\pi$$). Een oplossing die je zou kunnen kiezen is om een random getal te trekken (tussen 0 en 1) en de variabele NeemNogEenStap de waarde 0 te geven (zie deelopdracht 1c) als de waarde van het random getal kleiner is dan 0.05.

##### deelopdracht (1d): startsituatie: N konijnen op random posities

De twee waar we nu mee gewerkt hebben is wel heel erg weinig. Pas het begin van `ProoiPredator()`zo aan dat er 25 konijnen in de simulatie zijn. Maak de code zo dat de konijnen elk op een random positie geplaatst worden ($$25<x<75$$ en $$25<y<75$$) en ook elk een unieke richting krijgen waarin ze bewegen ($$0<\alpha<2\pi$$).


#### Opgave 2:Harde realiteit voor de konijnen: vossen

##### deelopdracht (2a): introduceren van wolven

Naast konijnen zijn er ook vossen in het bos. Pas de code zo aan de er ook vossen (twee) op het scherm verschijnen. Maak een nieuwe functie `VerplaatsWolven()` en pas de functie `Teken_het_bos()` zo aan dat ook de wolven op het scherm getoond worden.

Er zijn een paar verschillen tussen de vossen en de konijnen:

   - teken de vossen in rood (zelfde grootte als de konijnen, radius = 2)
   - teken om de vossen ook een rode cirkel met straat r=5.
   
     Deze cirkel zal fungeren als de "circle-of-death" voor konijnen
   - De vossen bewegen met snelheid 5 i.p.v 2

Zorg dat de vossen beginnen op posities (10,10) en (90,90) en respectievelijk recht omhoog en recht naar beneden starten met lopen. Net als de konijnen hebben ook vossen een eigen manier van voortbewegen.

   - De vos staat nooit even stil
   - Ook de vos zal nooit het bos verlaten. Zorg dat je voor de vossen eenzelfde implementatie maakt als voor de 
     konijnen in opgave 1b).


##### deelopdracht (2b): specifiek gedrag van wolven

![](konijnenenvossen.gif){:.inline}{: style="width:30%"}

De vos heeft de neiging om bij elk stap ongeveer in dezelfde richting te blijven bewegen. Hij kan daarvan afwijken, maar de kans op de hoek met de oorspronkelijke richting neemt sterk af als de afwijking groter is. De verdeling van de kansen volgt een zogenaamde normaalverdeling (centrale waarde is de huidige richting en de breedte = 0.5 radialen).De vos volgt hiermee een soort random walk waarbij er toch een voorkeur is om in de oorspronkelijke richting te blijven lopen. Implementeer dit gedrag in je simulatie.

Python input:
Om een nieuwe richting voor de vos te kiezen kan je de volgende syntax gebruiklen
   
     new_angle = numpy.random.normal(L_vos_hoek[i_vos], 0.2)  

Sla die richting op in `L_vos_hoek`. 
     

### Populatie-dynamica (I): Wolven eten de konijnen op

In de natuur leven vossen en konijnen niet vredig naast elkaar. Als een 
vos een konijn tegenkomt zal hij de konijn opeten. Schrijf een nieuwe 
functie `Etenstijd()` die in de hoofdfunctie ProoiPredator wordt aangeroepen 
voor elke stap in de tijd nadat de konijnen en vossen een stap hebben gemaakt. 
Deze functie heeft als taak te evalueren voor elk konijn of hij zich in de 
buurt bevindt van een wolf. Als dat zo is moet hij weggehaald worden uit de lijst.

**Tip:** slkh;slvkh











