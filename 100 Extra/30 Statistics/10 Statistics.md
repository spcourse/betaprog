# Statistiek #

Als er een onderdeel is dat studenten van verschillende opleidingen verbindt is het wel de 
onterechte vrees voor statistiek. En toch is het in elke (wetenschappelijke) discipline een 
cruciaal onderdeel omdat het de sleutel is waarmee je inzichten uit gegevens kan halen. Wat 
is de 'waarheid' die verborgen ligt in de data en hoe kunnen verschillende hypotheses tegen 
elkaar afgewogen worden.

In deze opgave zullen we na een paar korte inleidende oefeningen proberen te achterhalen 
conclusies we kunnen trekken als we de data van een enkele studie bekijken: is er nou wel 
of niet een afhankelijkheid ?
 
## [1] De normaalverdeling in de natuur 

### Theorie: de normaalverdeling en het effect van het aantal metingen

In de natuur komt overal variatie voor: de lengte van mensen in een land, het aantal 
eitjes van een zeepaardje of het gewicht van apen in een populatie om er maar een paar 
te noemen. De afwijkingen van het gemiddelde wordt voor vaak beschreven volgens de 
zogenaamde normaalverdeling:

$$ f(x,|\mu,\sigma) = \frac{1}{\sigma\sqrt{2\pi}} exp^{-\frac{1}{2}\left( \frac{x-\mu}{\sigma} \right)^2}$$

![](ExampleLengte.png){:.inline}{: style="width:35%"}

Deze verdeling, ook wel de Gaussische distributie genoemd, beschrijft wat de relatieve frequentie 
is waarmee waarde $$x$$ voorkomt in de populatie van metingen. Het prettige aan deze verdeling is 
dat hij gekarakteriseerd wordt door maar twee parameters: het gemiddelde ($$\mu$$) en de maat 
voor de spreiding ($$\sigma$$). Er geldt dat ongeveer 68%(95%) van de waarden in het gebied 
$$\mu \pm 1(2) \sigma$$ liggen.

De lengte van mannen (vrouwen) in Nederland wordt bijvoorbeeld beschreven door een 
normaalverdeling met een gemiddelde = 184.0 (170.6) cm en sigma = 7.0 (6.5) cm. De 
(genormeerde) grafieken van de twee verdelingen staan in grafiek. Dit betekent dat 
34% van de mannen langer is dan 191 cm en dan 2.5% van de vrouwen kleiner is dan 
157.6 cm.

### Python: trekken van random getallen uit een normaalverdeling 

We hebben eerder gezien hoe je een random getal trekt in Python tussen 0 en 1. Het is ook mogelijk 
om een random getal te trekken uit een bepaalde verdeling. Omdat de normaalverdeling zo'n prominente 
plek inneemt is er een standaard functie in Python. 

{: .language-python}
    gemiddelde = 170.6
    breedte = 6.5
    x = numpy.random.normal(gemiddelde,breedte)

Als je dit heel vaak herhaalt zullen de waardes van $$x$$ verdeeld zijn volgens de rode grafiek 
hierboven.

### opdracht 1: verdeling lengtes van alle vrouwen.

Schrijf een programma `Statistiek1.py()` waarin je 100.000 random getallen trekt uit de 
normaalverdeling die de lengte van vrouwen in Nederland beschrijft. Maak een grafiek van 
al deze random lengtes. Gebruik hiervoor een histogram met bins die elk een breedte van 
0.5 cm hebben. Hou bij het trekken van de random lengtes welk percentage vrouwen een lengte hebben 
die meer dan 2 sigma boven het gemiddelde liggen en dus langer zijn dan 183.6 cm. Print 
deze fractie met 3 decimalen nauweurigheid.

## [2] Steekproeven (metingen) en nauwkeurigheid

In de echte wereld kunnen we nooit alles weten. We kunnen niet van elke vrouw in Nederland 
precies achterhalen hoe lang ze is, net zoals Maurice de Hond niet van elke Nederlander weet 
op welke politieke partij hij of zij zal stemmen. We kunnen wel met behulp van steekproeven 
proberen een idee te krijgen van de hele populatie: we bepalen de lengtes van een groep 
vrouwen of de politieke voorkeuren van een groep Nederlanders en maken daarmee een schatting 
van de eigenschappen van de volledige populatie.

Hoe groter de steekproef is, hoe groter de nauwkeurigheid van de schatting en dus een kleinere 
fout (onzekerheid). We gaan dit onderzoeken door met behulp van de computer nep-steekproeven 
te nemen uit de oorspronkelijke distributie en te kijken hoe goed de gemiddelde lengte van een 
kleine groep representatief is voor die van de hele populatie. 

### opdracht 2: impact van meer metingen op de nauwkeurigheid

Schrijf een programma `Statistiek2.py` die uitrekent welke fractie van steekproeven meer dan 5 cm 
afwijkt van het echte gemiddelde. Doe dit voor $$N=2,3,5,10,100$$.

  - Trek N random waardes uit de oorspronkelijke verdeling: een steekproef
  - Bepaal voor elke steekproef het gemiddelde uit van de lengtes van de vrouwen in die 
      groep en bewaar die
  - Herhaal dit voor een groot aantal steekproeven (100.000 bijvoorbeeld)
  - Hou bij in hoeveel steekproeven het gemiddelde meer dan 5 cm afwijkt 
    van het `echte` gemiddelde. (170.6 cm).
    Let op: we bedoelen hier zowel groter dan 175.6 cm en kleiner dan 165.6 cm.
              
Print de fractie in procenten en gebruik 3 decimalen:
{: .language-python}
    Fractie afwijkende steekproeven voor N=2: x.xxx procent 
    Fractie afwijkende steekproeven voor N=5: x.xxx procent 
    ...

Het is zeer inzichtelijk om de distributies van de gemiddeldes te bekijken voor de verschillende keuzes 
van de steekproefgroottee. Gebruik hiervoor de histogram methode. Kies zelf een handige bin-grootte.

**Conclusie:** Hoe groter de steekproef hoe beter je de 'echte' waarde benadert. Dat klinkt logisch, 
want het  maakt nogal uit of Maurice de Hond 10 mensen hun politieke voorkeur vraagt of 10.000. Voor 
elk getal, meting of grafiek die je ziet in de rest van je leven moet je je goed afvragen wat de 
onzekerheid op die schatting is. Een getal zonder foutmarge kan je niet op waarde schatten. Hoe 
kleiner de fout/onzekerheid, hoe belangrijker de meting is en hoe 'zwaarder' je de meting moet 
meewegen als je verschillende resultaten naast elkaar legt en een conclusie probeert te trekken.

## [3] Parameters van je model bepalen uit een serie metingen: fitten

Om de onderliggende fenomenen van verschijnselen bloot te leggen en mogelijke verbanden te 
achterhalen verzamelen wetenschappers data. Dat kan de massa van het Higgs boson zijn, de 
vervaltijd van radioactieve elementen, maar ook het aantal kinderen in een gezin als functie 
van de gemiddelde lengte van de ouders of je reistijd per fiets naar de universiteit als 
functie van het moment op de dag. Elk meetpunt komt met een onzekerheid die de precisie 
aangeeft. Zoals we al gezien hebben: hoe kleiner de fout, hoe nauwkeuriger de meting en 
hoe 'belangrijker' het meetpunt is in het bepalen of dat date met je model overeenkomen. 
Als je eenmaal een goede beschrijving hebt gevonden kan je daarmee vervolgens voorspellingen 
doen en tegelijkertijd werken aan een interpretatie van de reden van de correlatie.

We gaan in dit stuk van de module de de resultaten van een onderzoek in detail bestuderen: de 
lengte van vrouwen als functie van het inkomen van haar ouders. Is er nou wel of niet verband 
te zien in de data? Om dat te bestuderen moeten we eerst van de verschillende hypotheses (wel 
of niet een verband) de parameters en hun onzekerheid bepalen. Het is inzichtelijk om de discussie 
over de manier waarop je de beste waarde van je parameters bepaald (en de onzekerheid) te voeren 
aan de hand van een voorbeeld. 

### Voorbeeld: Temperatuur van smeltend 

Een groep studenten heeft tijdens een praktikum het kookpunt van alcohol proberen 
te bepalen. De studenten hadden alleen genoeg tijd om 1 keer een meting te doen. Er 
waren zes thermometer die de temperatuur tot op 1 graad Celcius nauwkeurig konden bepalen 
en vier die dat konden met een hogere precisie, namelijk 0.5 graden. De lijst met 
metingen is de volgende:

groepnummer (x)         |  1   |  2   |  3   |  4   |  5   |  6   |  7   |  8   |  9   | 10 
gemeten kookpunt (y)    | 78.2 | 80.2 | 78.7 | 78.9 | 77.5 | 79.7 | 78.1 | 79.0 | 79.6 | 78.4 
$$\sigma$$ (fout op y)  |  1   |  1   |  1   |  0.5 |  1   |  1   |  0.5 |  0.5 |  1   | 0.5


#### Model en doel van de exercitie
In dit geval is het 'model' dat we hebben een vlakke lijn. Het kookpunt van alcohol is een 
natuurconstante en hangt niet af van et groepje studenten dat de meting verricht. Eigenijk 
proberen we dus de waarde van het kookpunt van alcohol te bepalen dat het best in overeenstemming 
is met de gemeten punten. 

Het is duidelijk dat 78$$^\circ$$ een betere schatting is dan 70$$^\circ$$ of 81$$^\circ$$ , maar 
wat is nou precies de 'beste' waarde?

#### $$\chi^2$$: de metriek voor 'hoe goed' het model de data beschrijft 

Om de 'beste' waarde te vinden hebben we een maat (metriek) nodig die de
*goedheid* van de fit beschrijft. We doen dat hier met de $$\chi^2$$-maat: de
som van de gemiddelde afwijking van de meetpunten tot het model gewogen met hun
fout. Voor elk punt bepalen we dus de volgende vraag: *"Wat is de afstand van de meting 
(uitgedrukt in de meetfout op het punt) tot de waarde die het model voorspelt op die plek?"*

Iets formeler:
$$\chi^2 = \sum_{i~ {\rm (datapunten)}}  \left(\frac{  y_i - f(x_i|\vec{\alpha}) }{\sigma_i}\right)^2$$

In deze uitdrukking is $$\vec{\alpha}$$ de vector met de parameters die je gebruikt in je
model. Voor elke keuze van de parameters in je model verandert de afstand van elk meetpunt 
tot je model en krijg je dus een nieuwe $$\chi^2$$. Ter volledigheid: de $$\chi^2$$ is 
gewoon een getal.

#### De beste waarde van je model-parameters en de onzekerheid daarop

In de fitprocedure zoeken we naar de waarde van de parameters in je model die
de kleinste $$\chi^2$$ opleveren. Dat zijn namelijk de 'beste' waardes van het
model omdat met die waarde van de parameters je model de data het best
beschrijft.

Elke waarde van je parameters die anders is dat $$\alpha_{best}$$ zal de waarde
van de $$\chi^2$$ veranderen (die wordt groter wat een slechtere overeenkomst
met de data betekent). Het verschil tussen de waarde van de $$\alpha$$ waarbij
de $$\chi^2$$ precies 1 unit toeneemt en $$\alpha_{best}$$ noemen we de
onzekerheid.

Het resultaat van je fit presenteer je dan als volgt:

$$\alpha = \alpha_{best} \pm \Delta_{alpha}$$

Hoewel we hier aannemen dat de fout in $$\alpha$$ symmetrisch is hoeft dat niet
altijd het geval te zijn. Evalueer dus altijd de negatieve en positieve fout
afzonderlijk door te kijken hoe de $$\chi^2$$ verandert als je de parameters
respectievelijk kleiner en groter maakt.

### Voorbeeld: Wesley Sneijder

Iemand heeft heel keurig het percentage goede passes ($$y$$-waarde) bepaald die
Wesley Sneijder heeft gegeven tijdens de verschillende wedstrijden
($$x$$-waarde) tijdens de kwalificatie voor het WK voetbal. Omdat de
nauwkeurigheid waarmee het percentage bepaald wordt afhangt van het aantal
passes in een wedstrijd is de fout erop niet voor elke wedstrijd hetzelfde.

wedstrijdnummer (x)     |  1 |  2 |  3 |  4 |  5 |  6 |  7 |  8 |  9 | 10 
$$f_{goed}$$ (y)        | 55 | 50 | 39 | 58 | 54 | 57 | 78 | 66 | 62 | 82 
$$\sigma$$ (fout op y)  |  5 |  4 |  9 |  4 |  5 |  5 |  7 |  3 |  6 | 6

![](FitExampleCombined.png)

De data is weergegeven in de linker plot hieronder. We nemen aan dat zijn
prestaties constant zijn en nemen daarom aan dat het model dat deze data het
best beschrijft een constante is. Ons model heeft dus maar 1 parameter:
$$f(x)=c$$. De vraag is nu: *welke waarde van $$c$$ beschrijft de data het best
en welke onzekerheid moeten we aan die schatting toekennen?*

#### Wesley Sneijder: het uitrekenen van $$\chi^2$$ voor 1 bepaalde set parameters

We gaan verschillende waardes van $$c$$ proberen en rekenen voor elke de
$$\chi^2$$ uit. Als we bijvoorbeeld als hypothese $$c=56$$ nemen dan hoort daar
de volgende $$\chi^2$$ bij:

$$
\begin{eqnarray}
   \chi^2(c=56)&=&    
   \tiny{
   \left( \frac{(55-56)}{5} \right)^2+
   \left( \frac{(50-56)}{4} \right)^2+
   \left( \frac{(39-56)}{9} \right)^2+
   \left( \frac{(58-56)}{4} \right)^2+
   \left( \frac{(54-56)}{5} \right)^2+
   \left( \frac{(57-56)}{5} \right)^2+
   \left( \frac{(78-56)}{7} \right)^2+
   \left( \frac{(66-56)}{3} \right)^2+
   \left( \frac{(62-56)}{6} \right)^2+
   \left( \frac{(82-56)}{6} \right)^2
   }\\
   &=&47.07
\end{eqnarray}
$$

#### Wesley Sneijder: de beste waarde van de vrije parameter in het model

Je kan nu verschillende waardes van $$c$$ proberen en voor elk de $$\chi^2$$
berekenen. De distributie is getekend in de rechterplot hierboven. Er is een
duidelijk minimum zichtbaar: bij $$c=60.3$$ is de $$\chi^2$$ minimaal, namelijk
$$\chi^2_{min} = 38.87$$. De waarde $$c=60.3$$ beschrijft de data het best.

#### Wesley Sneijder: de onzekerheid op de vrije parameter in het model

Bij het berekenen van de $$\chi^2$$ zien we dat er een gebied is $$ 58.8 < c <61.8$$ waarvoor de $$\chi^2$$ 
minder dan 1 unit verschilt van $$\chi^2_{min}$$. De linkergrens en rechtergrens in hypotheses van $$c$$ 
zijn beide 1.5 van  $$c_{best}$$ verwijderd. De onzekerheid op $$c$$ is dus 1.5.

Het resultaat van de fit van ons model aan de data is als volgt:
percentage goede passes = $$ 60.3 \pm1.5$$


### opdracht 3: Gemiddelde lengte vrouwen in Belgie

Schrijf een programma `Statistiek3.py()` waarin je 100.000 random getallen trekt uit de 
normaalverdeling die de lengte van vrouwen in Nederland beschrijft. Maak een grafiek van 

## Opgave: fitten van een model aan de data

Schrijf een programma **fit.py** dat het bovenstaande resultaat verifieert.

1. Maak een plot van deze data met fouten

    Tip: gebruik de functie `plt.errorbar(x,y, yerr=yerror)`. 

    Zoek op internet op hoe je deze functie moet gebruiken.

2. Bereken de beste waarde van c en de bijbehorende onzekerheid $$\Delta_c$$

3. Hoe verandert het resultaat als de fout op elk van de metingen 2x zo groot wordt?


## Sanity check

Je kunt deze opgaven allemaal maken met de Python-onderdelen die je kent uit modules 1 en 2!


## Extra informatie (niet voor deze cursus)

Het fitten van een model aan metingen is een standaard procedure die je als 
onderzoeker vaak tegen zult komen. Hoewel we in deze cursus deze functionaliteit
en alle bijbehorende details zullen gebruiken door gebrek aan tijd willen we 
hier toch een klein voorbeeld geven waarin je ziet hoe dat in de praktijk gaat. 

Hieronder dezelfde fit die jullie hierboven gedaan hebben, maar dan op de Python 
manier.

    # import the module that contains the fit-tool
    from scipy.optimize import curve_fit

    # Define our model. In our case a constant function: f(x) = a 
    def MyFitFunction(x, a):
        return a

    # define data and errors
    L_data_x       = [1,2,3,4,5,6,7,8,9,10]
    L_data_y       = [55,50,39,58,54,57,78,66,62,82]
    L_data_y_error = [5,4,9,4,5,5,7,3,6,6]

    # do fit (using our own function f(x) = a)
    popt, pcov = curve_fit(MyFitFunction, L_data_x, L_data_y, None, L_data_y_error)
    print "Best value: f(x) = %5.2f" % popt[0]

De laatste regel blijft nu nog magie, maar *popt* is een lijst met de 'optimale' 
parameters van de functie die je aan de data hebt gefit. In ons geval is dat maar 
1 parameter omdat we een constante functie aanhouden als model. Je kan zelf in de 
documentatie opzoeken hoe je zelf uit *pcov* de onzekerheid op de parameter kan bepalen. 

Als je nu in plaats van een constante functie een lineaire functie wilt fitten 
$$f(x) = ax+b$$ en je wilt de resultaten printen dan hoef je op 2 plekken een 
verandering aan te brengen:

1) verander de functie die je aanhoudt als model

    # Define our model. In our case a constant function: f(x) = a x + b 
    def MyFitFunction(x, a, b):
        return a * x + b

2) verander de regel waarin je het resultaat op het scherm print

    print "Best value: f(x) = %5.2f * x + %5.2f" % (popt[0], popt[1])










	
	
	
