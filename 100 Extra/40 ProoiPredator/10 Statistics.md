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
           L_konijn_x,L_konijn_y = VerplaatsKonijnen(L_konijn_x,L_konijn_y)    

           #--/ plot de positie van de konijnen
           Teken_het_bos(L_konijn_x,L_konijn_y)
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
       return


    #------------------------------
    def VerplaatsKonijnen(L_x,L_y):
    #------------------------------

         #--/ doe elke tijdstap een stapje voor de konijnen (2 naar rechts en 3 naar boven)
         Aantal_konijnen = len(L_x)   
         for i_konijn in range(Aantal_konijnen):
             L_x[i_konijn] = L_x[i_konijn] + 1.2 
             L_y[i_konijn] = L_y[i_konijn] + 1.6 
  
         #--/ return de ge-update lijsten
         return L_x, L_y


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
 
         return




#### Opgave 1: Toevoegen realiteit: andere variabelen en de langere termijn

We hebben in bovenstaand voorbeeld aangenomen dat de konijnen bij elke stap in de tijd (elke seconde) drie stappen naar rechts opschuiven en vier omhoog gaan. We hadden dit ook kunnen representeren door te stellen dat de konijnen bewegen met een snelheid van 2 meter per seconde bewegen onder een hoek van ongeveer 51 graden met de x-as. Als we de tijd langer laten doorlopen zullen we ook zien dat onze konijnen het bos uitlopen. Dat is niet de bedoeling. Als de konijnen bij de rand van het bos komen zullen ze weer het bos inlopen. In deze opgave zullen we deze eerste stappen op weg naar realistische konijnen doorvoeren in onze code.

#####  [1a]:

Voeg in het hoofdprogramma een extra variabele `v_konijn` toe die de snelheid van de konijnen aangeef (2 m/s) en voeg een lijst `L_konijn_hoek` toe waarbij je voor elk konijn bijhoudt onder welke hoek ten opzichte van de x-as hij beweegt. Geef de konijnen allemaal de bovenstaande hoek (atan(1.6/1.2)). Pas ook de code zo aan dat op de plek waar de nieuwe positie van de konijnen uitgerekend wordt gebruik wordt gemaakt van deze twee variabelen. In de hoofd code `PooiPredator()` moet dus verschijnen:

       L_konijn_x,L_konijn_y = VerplaatsKonijnen(L_konijn_x,L_konijn_y, L_konijn_hoek, v_konijn)    








