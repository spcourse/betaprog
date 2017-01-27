# Statistiek #

Als er een onderdeel is dat studenten van verschillende opleidingen verbindt is het wel de 
onterechte vrees voor statistiek. En toch is het in elke (wetenschappelijke) discipline een  
cruciaal onderdeel omdat het de sleutel is waarmee je inzichten uit gegevens kan halen. Wat 
is de 'waarheid' die verborgen ligt in de data en hoe kunnen verschillende hypotheses tegen 
elkaar afgewogen worden.

In deze opgave zullen we na een paar korte inleidende oefeningen proberen te achterhalen 
conclusies we kunnen trekken als we de data van een enkele studie bekijken: is er nou wel 
of niet een afhankelijkheid van je studiesucces als functie van het aantal studiegenoten 
waarmee je een huis deelt?
 

## Theorie: de normaalverdeling en het effect van het aantal metingen

In de natuur komt overal variatie voor: de lengte van mensen in een land, het aantal 
eitjes van een zeepaardje of het gewicht van apen in een populatie om er maar een paar 
te noemen. De afwijkingen van het gemiddelde wordt voor vaak beschreven volgens de 
zogenaamde normaalverdeling:

$$ f(x,|\mu,\sigma) = \frac{1}{\sigma\sqrt{2\pi}} exp^{-\frac{1}{2}\left( \frac{x-\mu}{\sigma} \right)^2}$$

Het is een functie die beschrijft wat de relatieve frequentie is waarmee waarde $$x$$ 
voorkomt in de populatie van metingen. Het prettige aan deze verdeling is dat hij 
gekarakteriseerd wordt door maar twee parameters: het gemiddelde ($$\mu$$) en de maat 
voor de spreiding ($$\sigma$$). Er geldt dat ongeveer 68%(95%) van de waarden in het gebied 
$$\mu \pm 1(2) \sigma$$ liggen.

### voorbeeld: 

De lengte van mannen (vrouwen) in Nederland wordt bijvoorbeeld beschreven door een 
normaalverdeling met een gemiddelde = 184.0(170.6) cm en sigma = 7.0(6.5) cm. De 
(genormeerde) grafieken van de twee verdelingen staan in grafiek.

![](ExampleLengte.png){:.inline}{: style="width:35%"}

## opdracht 1: 

We zijn niet allemaal pre-cies even lang, we het KNMI heeft het 


### Voorbereiding: de normaalverdeling in de statistiek




### Voorbereiding: metingen simuleren in Python - een random getal trekken uit een normaalverdeling


Het enige nieuwe Python element dat we nodig hebben is een manier om een dobbelsteen te 



Doel van deze opdracht is om te bepalen wat het gemiddeld aantal worpen is waarna alle straten 
zijn verkocht. Schrijf in een bestand `Monopoly_opdracht1.py` een functie waarin je  

{: .language-python}
	Monopoly simulator: 1 speler, Trump mode 
    We hebben XXX potjes gesimuleerd
    Gemiddeld duurde het XXX worpen voor de speler alle straten in zijn bezit had
	
Om je te helpen deze opdracht te maken is het handig de volgende tussenstappen door te nemen.

### Tussenstap 1: dobbelsten in Python - random integers

Het enige nieuwe Python element dat we nodig hebben is een manier om een dobbelsteen te 

## Hypotheses testen

Er is een nieuwe




## Samenvatting

De simulatie die we hier gedaan hebben is een versimpelde versie van de vaak zeer complexe 
modellen waarmee grote financiele partijen risico's inschatten en strategieen bepalen. 
Tegelijkertijd worden deze simulaties ook gebruikt door politieke partijen om de effecten 
van hun keuzes door te rekenen in verschillende scenario's.










	
	
	
