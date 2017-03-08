## Fitten: wat zijn de parameters in je model die het best de data beschrijven

Om de onderliggende fenomenen van verschijnselen bloot te leggen en mogelijke verbanden te 
achterhalen verzamelen wetenschappers data. Dat kan de massa van het Higgs boson zijn, de 
halfwaardetijd van radioactieve elementen, maar ook het aantal kinderen in een gezin als functie 
van de gemiddelde lengte van de ouders of je reistijd per fiets naar de universiteit als 
functie van het moment op de dag. Elk meetpunt komt met een onzekerheid die de precisie 
aangeeft. Zoals we al gezien hebben: hoe kleiner de fout, hoe nauwkeuriger de meting en 
hoe 'belangrijker' het meetpunt is in het bepalen of dat data met je verwachtingen (model) 
overeenkomen. Als je eenmaal een goede beschrijving hebt gevonden van de verzamelde data dan 
kan je met dat model vervolgens voorspellingen doen in gebieden waar je nog niet gemeten hebt 
en tegelijkertijd werken aan een interpretatie van de reden van de correlatie.

We gaan in dit stuk van de module de de resultaten van een bovengenoemde fictieve onderzoek in 
detail bestuderen: de lengte van vrouwen als functie van het inkomen van haar ouders. Is er nou 
wel of niet verband te zien in de data? Om dat te bestuderen moeten we eerst van de verschillende 
hypotheses (wel of niet een verband) de parameters en hun onzekerheid bepalen. Het is inzichtelijk 
om de discussie over de manier waarop je de beste waarde van je parameters bepaalt (en de onzekerheid 
daarop) te voeren aan de hand van een voorbeeld. Na het voorbeeld (het kookpunt van alcohol) zullen we 
de kennis toepassen in een concrete opdracht die gerelateerd is aan onze casus.

### [Voorbeeld]: Bepalen kookpunt van alcohol tijdens het prakticum

Tijdens een prakticum kregen groepjes studenten de opdracht het kookpunt van alcohol te bepalen. 
Door gebrek aan tijd had elke groep maar tijd voor 1 meting. Er waren zes thermometer in de 
zaal die de temperatuur tot op 1 graad Celcius nauwkeurig konden bepalen en vier die dat konden 
met een hogere precisie, namelijk 0.5 graden. De lijst met de metingen van de tien groepen studenten 
is de volgende en de grafiek met de waardes staat weergegeven in de grafiek onderaan dit voorbeeld.

groepnummer studenten (x)            |  1   |  2   |  3   |  4   |  5   |  6   |  7   |  8   |  9   | 10 
gemeten kookpunt in $$^\circ$$C (y)  | 78.2 | 80.2 | 78.7 | 78.9 | 77.5 | 79.7 | 78.1 | 79.0 | 79.6 | 78.4 
onzekerheid ($$\sigma$$, fout op y)  |  1   |  1   |  1   |  0.5 |  1   |  1   |  0.5 |  0.5 |  1   | 0.5


#### [voorbeeld stap 1]: model opstellen en doel van de exercitie
Het kookpunt van alcohol is een natuurconstante en hangt niet af van het groepje studenten dat de 
meting verricht. In dit geval is het 'model' dat we hebben een vlakke lijn en eigenijk proberen 
we dus de waarde van het kookpunt van alcohol te bepalen dat het best in overeenstemming is met 
de gemeten punten. Het is duidelijk dat 78$$^\circ$$ een betere schatting is dan 70$$^\circ$$ en 
79$$^\circ$$ een betere dan 81$$^\circ$$, maar wat is nou precies de 'beste' waarde? Kortom: wat 
is het gemiddelde van de hele klas?

#### [voorbeeld stap 2]: een maat voor 'hoe goed' het model de data beschrijft: de $$\chi^2$$-maat

Om de 'beste' waarde te vinden hebben we een maat (metriek) nodig die de *goedheid* van de fit beschrijft. 
We doen dat hier met de zogenaamde $$\chi^2$$-maat (chi-kwadraat): de som van de gemiddelde afwijking van de 
meetpunten tot het model gewogen met hun fout. Voor elk punt bepalen we de afstand van de meting (uitgedrukt 
in de meetfout op het punt) tot de waarde die het model voorspelt op die plek. De som die afwijkingen voor 
elk meetpunt noemen we de $$\chi^2$$.

Iets formeler:
$$\chi^2(\vec{\alpha}) = \sum_{i~ {\rm (datapunten)}}  \left(\frac{  y_i - f(x_i|\vec{\alpha}) }{\sigma_i}\right)^2$$

In deze uitdrukking is $$\vec{\alpha}$$ de vector met de parameters die je gebruikt in je
model. Voor elke keuze van de parameters in je model verandert de afstand van elk meetpunt 
tot je model en krijg je dus een nieuwe $$\chi^2$$. 

Deze uitdrukking ziet er ingewikkelder uit dan hij is:

   1. de $$\chi^2$$ is gewoon een getal

   2. in ons model is er maar 1 vrije parameter, namelijk het kookpunt van alcohol $$T_0$$.
      Ons model reduceert dan tot: $$f(x) = T_0$$ en de vector $$\vec{\alpha}$$ reduceert tot 1 parameter, de constante $$T_0$$. 
	  
#### [voorbeeld stap 3]: de beste waarde van de model-parameters vinden

In een fitprocedure zoek je naar de waarde van de parameters in het model die de kleinste $$\chi^2$$ opleveren, 
omdat met die waarde van de parameters de meetpunten gemiddeld het dichtst bij het model in de buurt liggen. 
Met behulp van de computer gaan we verschillende waardes van $$T_0$$ proberen en voor elk de 
$$\chi^2$$ uitrekenen.
 
Als we bijvoorbeeld als hypothese $$T_0=78.0$$ nemen dan hoort daar de 
volgende $$\chi^2$$ bij:
$$
\begin{eqnarray}
   \chi^2(T_0=78.0)&=&    
   \tiny{
   \left( \frac{(78.2-78.0)}{1.0} \right)^2+
   \left( \frac{(80.2-78.0)}{1.0} \right)^2+
   \left( \frac{(78.7-78.0)}{1.0} \right)^2+
   \left( \frac{(78.9-78.0)}{0.5} \right)^2+
   \left( \frac{(77.5-78.0)}{1.0} \right)^2}\\
   &~& 
   \tiny{
  +\left( \frac{(79.7-78.0)}{1.0} \right)^2+
   \left( \frac{(78.1-78.0)}{0.5} \right)^2+
   \left( \frac{(79.0-78.0)}{0.5} \right)^2+
   \left( \frac{(79.6-78.0)}{1.0} \right)^2+
   \left( \frac{(78.4-78.0)}{0.5} \right)^2
   }\\
   &=&19.0
\end{eqnarray}
$$

Je kan nu verschillende waardes van $$T_0$$ proberen en voor elk de $$\chi^2$$
berekenen. De distributie is getekend in de rechterplot hieronder. Er is een
duidelijk minimum zichtbaar en de waarde van $$T_0$$ waarvoor de $$\chi^2$$ 
minimaal is noemen we $$T_0^{\rm best}=78.2$$.

#### [voorbeeld stap 4]: de onzekerheid op de parameters in je model

Elke waarde van je parameters die anders is dat $$T_0^{\rm best}$$ zal de waarde
van de $$\chi^2$$ veranderen (die wordt groter wat een slechtere overeenkomst
met de data betekent). Het verschil tussen de waarde van de $$T_0$$ waarbij
de $$\chi^2$$ precies 1 unit toeneemt en $$T_0^{\rm best}$$ noemen we de
onzekerheid op $$T_0$$. Dit wordt vaak omschreven als $$\Delta T_0$$. 
Bij het berekenen van de $$\chi^2$$ zien we dat er is het gebied is $$ 78.5 < T_0 <78.9$$ 
waarvoor de $$\chi^2$$ minder dan 1 unit verschilt van $$\chi^2_{min}$$. Het resultaat 
van de fit, en dus het result van de gecombineerde schattig van het kookpunt van alcohol 
door de hele groep  studenten samen wordt gegeven door:

   Kookpunt alcohol = $$78.2 \pm 0.2 ^\circ C$$
   
**Let op:** Hoewel we hier aannemen dat de fout in $$T_0$$ symmetrisch is hoeft dat niet
altijd het geval te zijn. Evalueer dus altijd de negatieve en positieve fout afzonderlijk 
door te kijken hoe de $$\chi^2$$ verandert als je de parameters respectievelijk kleiner en 
groter maakt.

#### [voorbeeld stap 5]: de bijbehorende plots

![](FitExampleWebsite.png){: style="width:90%"}

Het voorbeeld dat we hier hebben uitgewerkt is het zogenaamd 'fitten' van een simpel 
model met 1 parameter aan de data. Ook als we een ingewikkelder model hebben, bijvoorbeeld 
een eerstegraads polynoom, $$f(x)=ax+b$$ bijvoorbeeld, vinden we de beste waarde van de twee 
parameters door $$a$$ en $$b$$ te varieren en te kijken voor welke waarden de $$\chi^2$$ 
minimaal is.

## Opdracht 3: gemiddelde lengte vrouwen in Denemarken

Terug naar de casus in deze module. In Denemarken is een onderzoeksgroep dus aan het onderzoeken of de lengte 
van vrouwen afhangt van het inkomen van hun ouders. Er is gekozen voor 10 inkomenscategorieen en hoewel er 
geprobeerd is zoveel mogelijk gelijke aantallen vrouwen per categorie op te nemen in de studie is het aantal 
vrouwen met ouders in de extremen van de inkomstengroepen (erg rijk en erg arm) helaas beperkt. Dit is duidelijk 
door de grotere fout op de schatting van de gemiddelde lengte in die groepen.

Categorie (x)        |  1 (arm)   |  2    |  3    |  4    |  5    |  6    |  7    |  8    |  9    | 10 (rijk)
Gem. lengte (y)      | 171.1 | 169.1 | 170.8 | 169.4 | 173.0 | 171.0 | 174.0 | 174.0 | 173.0 | 176.0 
Fout ($$\Delta y$$)  |  4    |  4    |  2    |  2    |  2    |  2    |  2    |  2    |  4    |  4

Schrijf een programma `statistiek_opdracht3.py()` waarin je het gemiddelde vindt van de lengte van vrouwen 
in Denemarken door een fit te maken aan de hierboven gegeven data met de functie $$f(x) = C$$. Je neemt dus 
aan in deze opgave dat er geen correlatie is tussen het inkomen van de ouders en de lengte van hun dochters. 
Volg hierbij de stappen in het voorbeeld over het meten van het kookpunt van alcohol zoals hierboven is besproken. 
Zorg dat je programma de data (met fouten) op het scherm weergeeft en ook de beste waarde van de fit die je 
gevonden hebt. Dus net zoals de linkerplot in het voorbeeld hierboven. Gebruik voor het plotten van de data met 
fouten de Python functie `plt.errorbar(x,y, yerr=yerror)`. Zoek op internet op hoe je deze functie moet gebruiken. 

Print je resultaat, met 1 decimaal precisie, op de volgende manier naar het scherm:
{: .language-python}
    De fit (vlakke lijn) geeft een gemiddelde lengte van xxx.x cm
