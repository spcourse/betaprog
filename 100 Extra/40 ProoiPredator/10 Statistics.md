# Prooi predator #

Als er een onderdeel is dat studenten van verschillende opleidingen verbindt is het wel de 

# Vossen en konijnen


#### twee konijnen op het scherm (stap 1)

    import matplotlib.pyplot as plt

    #--/ startpositie 2 konijnen (x-posities en y-posities op t=0)
    L_konijn_x = [10.,60.]  
    L_konijn_y = [ 2.,10.]  
    Aantal_konijnen = len(L_konijn_x)   
   
    #--/ neem stapjes in de tijd
    for i_time in range(10):
    
        #--/ doe elke tijdstap een stapje voor de konijnen (2 naar rechts en 3 naar boven)
        for i_konijn in range(Aantal_konijnen):
            L_konijn_x[i_konijn] = L_konijn_x[i_konijn] + 2 
            L_konijn_y[i_konijn] = L_konijn_y[i_konijn] + 3 
                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
        #--/ GRAFIEK (1): definieer een vast assenstelsel (het bos)
        fig=plt.figure(1)
        ax=fig.add_subplot(1,1,1)
        plt.axis([0,100,0,100])

        #--/ plot de positie van de konijnen (blauwe stip)
        plt.plot(L_konijn_x, L_konijn_y, 'o', color = 'blue')   

        #--/ PR (het oog wil ook wat): cirkels rond de posities van de konijnen
        for i_konijn in range(Aantal_konijnen):
            x = L_konijn_x[i_konijn]
            y = L_konijn_y[i_konijn]
            circ1=plt.Circle((x,y), radius=4, facecolor='blue', edgecolor ='none', alpha = 0.1)
            circ2=plt.Circle((x,y), radius=4, facecolor='none', edgecolor ='black') 
            ax.add_patch(circ1)
            ax.add_patch(circ2)
        
        #--/ GRAFIEK (2): update frames voor simpele animatie
        plt.draw()        #--/ Update de grafiek
        plt.pause(0.001)
        plt.clf()         #--/ Maak grafiek leeg bij elke tijdstap
        plt.show()

#### twee konijnen op het scherm (stap 3 - modulair / overzichtelijker)


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
             L_x[i_konijn] = L_x[i_konijn] + 2 
             L_y[i_konijn] = L_y[i_konijn] + 3 
  
         #--/ return de ge-update lijsten
         return L_x, L_y


    #--------------------------
    def Teken_het_bos(L_x,L_y):
    #--------------------------

         #--/ GRAFIEK (1): definieer een vast assenstelsel (het bos)
         fig=plt.figure(1)
         ax=fig.add_subplot(1,1,1)
         plt.axis([0,100,0,100])

         #--/ plot de positie van de konijnen (blauwe stip)
         plt.plot(L_x, L_y, 'o', color = 'blue')   

         #--/ PR (het oog wil ook wat): cirkels rond de posities van de konijnen
         Aantal_konijnen = len(L_x)   
         for i_konijn in range(Aantal_konijnen):
             x = L_x[i_konijn]
             y = L_y[i_konijn]
             circ1=plt.Circle((x,y), radius=4, facecolor='blue', edgecolor ='none', alpha = 0.1)
             circ2=plt.Circle((x,y), radius=4, facecolor='none', edgecolor ='black') 
             ax.add_patch(circ1)
             ax.add_patch(circ2)
        
         #--/ GRAFIEK (2): update frames voor simpele animatie
         plt.draw()        #--/ Update de grafiek
         plt.pause(0.001)
         plt.clf()         #--/ Maak grafiek leeg bij elke tijdstap
         plt.show()
 
         return











