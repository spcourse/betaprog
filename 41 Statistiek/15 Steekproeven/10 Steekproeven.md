## Opdracht 2: hoe representatief is een steekproef

In de echte wereld kunnen we vaak helaas niet alles weten. We kunnen niet van elke vrouw in Nederland 
precies achterhalen hoe lang ze is, net zoals Maurice de Hond niet van elke Nederlander weet 
op welke politieke partij hij of zij zal stemmen. We kunnen wel met behulp van steekproeven 
proberen een idee te krijgen van de hele populatie: we bepalen de lengtes van een groep 
vrouwen of de politieke voorkeuren van een groep Nederlanders en maken daarmee een schatting 
van de eigenschappen van de volledige populatie. 

We gaan in deze opdracht onderzoeken hoeveel nauwkeuriger de schatting van het 'echte' gemiddelde 
is bij een toenemend aantal mensen in de steekproef door met behulp van de computer nep-steekproeven 
te nemen. We selecteren dus random waardes uit de oorspronkelijke 'echte' distributie. Door van 
elk van deze steekproeven de gemiddelde lengte te bekijken kunnen we bekijken hoe vaak zo'n 
steekproef in de buurt zit van de echte waarde en hoe dit percentage afhangt van het aantal mensen 
in de steekproef zelf.

#### Opdracht 2: impact van meer metingen op de nauwkeurigheid

Schrijf een programma `statistiek_opdracht2.py` dat uitrekent welk percentage van groepen vrouwen 
(steekproeven) meer dan 5 cm afwijkt van het echte gemiddelde (170.6 cm). Doe dit voor 
verschillende groottes van de steekproef (het aantal mensen in de steekproef): $$N=2,3,5,10,100$$. 

Volg voor het bepalen van de fractie voor een specifieke waarde van $$N$$ het volgende 
stappenplan:

  - Trek N random waardes uit de oorspronkelijke verdeling: een steekproef
  - Bepaal voor elke steekproef het gemiddelde van de lengtes van de vrouwen 
    in die groep en bewaar die
  - Herhaal dit voor een groot aantal steekproeven (100000 bijvoorbeeld)
  - Hou bij in hoeveel steekproeven het gemiddelde meer dan 5 cm afwijkt 
    van het 'echte' gemiddelde (170.6 cm)
    Let op: we bedoelen hier zowel groter dan 175.6 cm en kleiner dan 165.6 cm
              
Print de percentages op het scherm en gebruik 2 decimalen:
{: .language-python}
    Fractie afwijkende steekproeven voor N =   2: x.xx procent 
    Fractie afwijkende steekproeven voor N =   3: x.xx procent 
    Fractie afwijkende steekproeven voor N =   5: x.xx procent 
    Fractie afwijkende steekproeven voor N =  10: x.xx procent 
    Fractie afwijkende steekproeven voor N = 100: x.xx procent 

Extra: probeer de user te helpen door de getallen netjes uitgelijnd onder elkaar op het scherm te krijgen

Het is zeer inzichtelijk om de distributies van de gemiddeldes te bekijken voor de verschillende 
keuzes van de steekproefgrootte. Gebruik hiervoor de histogram methode die we ook in opgave 1 
gebruikt hebben. Kies zelf een geschikte bin-grootte.

**Conclusie:** Hoe groter de steekproef hoe beter het gemiddelde daarvan de 'echte' waarde 
benadert. Dat klinkt logisch, want het  maakt nogal uit of Maurice de Hond 10 mensen hun 
politieke voorkeur vraagt of 100000. Voor elk getal, meting of grafiek die je voortaan ziet, 
of dat nou in de krant, op de televisie of in een wetenschappelijk publicatie is, moet je 
je altijd afvragen wat de onzekerheid op die schatting is. Hoe kleiner de fout/onzekerheid, 
hoe belangrijker de meting is en hoe 'zwaarder' je de meting moet meewegen als je verschillende 
resultaten naast elkaar legt en een conclusie probeert te trekken. Een schatting zonder een 
foutmarge zegt dus niet zoveel.
