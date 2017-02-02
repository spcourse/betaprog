# Statistiek #

Als er een onderdeel is dat studenten van verschillende opleidingen verbindt is het wel de 
onterechte vrees voor statistiek. En toch is het in elke (wetenschappelijke) discipline een  
cruciaal onderdeel omdat het de sleutel is waarmee je inzichten uit gegevens kan halen. Wat 
is de 'waarheid' die verborgen ligt in de data en hoe kunnen verschillende hypotheses tegen 
elkaar afgewogen worden.

In deze opgave zullen we na een paar korte inleidende oefeningen proberen te achterhalen 
conclusies we kunnen trekken als we de data van een enkele studie bekijken: is er nou wel 
of niet een afhankelijkheid ?
 
 

## De normaalverdeling


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
    x_mean = 170.6
    x_sigma = 6.5
    lengte = numpy.random.normal(mean,sigma)

Als je dit heel vaak herhaalt zullen de waardes van $$x$$ verdeeld zijn volgens de rode grafiek 
hierboven.

### opdracht 1: verdeling lengtes van alle vrouwen.

Schrijf een programma `Statistiek1.py()` waarin je 100.000 random getallen trekt uit de 
normaalverdeling die de lengte van vrouwen in Nederland beschrijft. Maak een grafiek van 
al deze random lengtes met behulp van een histogram met bins die elk breedte van 0.5 cm 
hebben. Hou bij het trekken van de random lengtes welk percentage vrouwen een lengte hebben 
die meer dan 2 sigma boven het gemiddelde liggen en dus langer zijn dan 183.6 cm. Print 
deze fractie met 3 decimalen nauweurigheid.



## Steekproeven (metingen) en nauwkeurigheid

In de echte wereld kunnen we nooit alles weten. We kunnen niet van elke vrouw in Nederland 
precies achterhalen hoe lang ze is, net zoals Maurice de Hond niet van elke Nederlander weet 
op welke politieke partij hij of zij zal stemmen. We kunnen met behulp van steekproeven 
wel een idee krijgen wat de eigenschappen zijn van een gedeelte van de hele populatie: de 
lengtes van een groep vrouwen of de politieke voorkeuren van een kleine groep Nederlanders. 
De eigenschappen van de groep worden vervolgens vertaald naar een schatting van de eigenschappen 
van de volledige populatie.

Er geldt dat hoe groter de steekproef is, hoe groter de nauwkeurigheid van de schatting van de 
eigenschappen van de populatie en dus een kleinere fout (onzekerheid). We gaan een paar dingen 
onderzoeken. 


### Theorie: spreiding

Een maat voor de spreiding van de individuele metingen in de data-set is de zogenaamde standaard 
deviatie:

$$ \sigma = \sqrt{ \frac{1}{N}  \sum_{i=1}^{n} (x_i-\mu)^2   }$$, waarbij $$\mu$$ het gemiddelde is van 
de data-set.

Voorbeeld: Stel dat we een kleine steekproef hebben genomen en van 5 vrouwen de lengte hebben gemeten.
x = {1.75, 1.69, 1,81, 1.76, 1.79}. Voor deze data-set geldt: 
$$ \mu = 1.76 $$ en $$ \sigma = 0.041 $$. Reken dit na zodat je zeker weet dat de formule 
duidelijk is. 



### opdracht 2: impact van meer metingen op de nauwkeurigheid

Schrijf een programma `Statistiek2.py` dat Wat is de opdracht 


Grafiek: 10000 keer 5 vrouwen, 10 vrouwen, 20 vrouwen, 50 vrouwen.

Bepaal ook de RMS rond het gemiddelde steeds.


# Fitten van data en foutenbepaling 

![embed](https://player.vimeo.com/video/138378099)

Om de onderliggende fenomenen van (natuurkundige) verschijnselen te achterhalen
wordt data verzameld om afhankelijkheden te onderzoeken. Dat kan de massa van
het Higgs boson zijn, de vervaltijd van uranium, maar ook het aantal kinderen
in een gezin als functie van de gemiddelde lengte van de ouders. Je kan dan
zoeken naar een (causaal) verband: lineair, exponentieel,etc. en daarbij ook de
bijbehorende parameters bepalen met hun onzekerheid. Als je een goede
beschrijving hebt gevonden kan je daarmee vervolgens ook voorspellingen doen.
Elk meetpunt komt met een onzekerheid die de precisie aangeeft waaramee een
grootheid gemeten is. Hoe kleiner de fout, hoe nauwkeuriger de meting en hoe
'belangrijker' hij is als je gaat kijken of de meetpunten wel met je model
overeenkomen.

Om de 'beste' waarde te vinden hebben we een maat (metriek) nodig die de
*goedheid* van de fit beschrijft. We doen dat hier met de $$\chi^2$$-maat: de
som van de gemiddelde afwijking van de meetpunten tot het model gewogen met hun
fout.

Voor elk punt bepalen we dus *hoeveel standaardafwijkingen ligt dit punt weg van mijn model/voorspelling?*

$$\chi^2 = \sum_{i~ {\rm (datapunten)}}  \left(\frac{  y_i - f(x_i|\vec{\alpha}) }{\sigma_i}\right)^2$$

Hierbij is $$\vec{\alpha}$$ de vector met de parameters die je gebruikt in je
model. Voor elke keuze van de parameters in je model verandert de afstand van
elk meetpunt tot je model en krijg je dus een nieuwe $$\chi^2$$. Ter
volledigheid: de $$\chi^2$$ is gewoon een getal.

## De beste waarde van je model en de onzekerheid

De beste waarde van je model ($$\alpha_{best}$$) en de onzekerheid daarop ($$\Delta_{alpha}$$).

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

## Voorbeeld: Wesley Sneijder

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

## Het uitrekenen van $$\chi^2$$

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

Je kan nu verschillende waardes van $$c$$ proberen en voor elk de $$\chi^2$$
berekenen. De distributie is getekend in de rechterplot hierboven. Er is een
duidelijk minimum zichtbaar: bij $$c=60.3$$ is de $$\chi^2$$ minimaal, namelijk
$$\chi^2_{min} = 38.87$$. De waarde $$c=60.3$$ beschrijft de data het best.

Bij het berekenen van de $$\chi^2$$ zien we dat er een gebied is $$ 58.8 < c <61.8$$ waarvoor de $$\chi^2$$ 
minder dan 1 unit verschilt van $$\chi^2_{min}$$. De linkergrens en rechtergrens in hypotheses van $$c$$ 
zijn beide 1.5 van  $$c_{best}$$ verwijderd. De onzekerheid op $$c$$ is dus 1.5.

Het resultaat van de fit van ons model aan de data is als volgt:
percentage goede passes = $$ 60.3 \pm1.5$$

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










	
	
	
