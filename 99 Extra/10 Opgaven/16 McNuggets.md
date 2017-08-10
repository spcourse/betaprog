
# Diophantische McNuggets


In de wiskunde bestaat er een klasse vergelijkingen die bekend zijn onder diophantische vergelijkingen. Het zijn vergelijkingen waar de variabelen alleen 
geheeltallig kunnen zijn. De bekendste diophantische vergelijking is:
$$x^n + y^n = z^n$$.
Voor n=2 zijn er oneindig veel oplossingen (x,y,z allen geheeltallig): Pythagoras. De beroemde stelling van Fermat, waar in 1995 eindelijk
[Andrew Wiles](https://en.wikipedia.org/wiki/Andrew_Wiles)
het 
[bewijs](https://www.youtube.com/watch?v=SccDUpIPXM0)
voor vond, zegt dat voor waarden groter dan 2 er geen geheeltallige oplossing is. 

![](McDonaldsLogo.png)

## Opgave 1: doosjes McNuggets vullen

Ook McDonalds gebruikt diophantische vergelijkingen. Ze verkopen namelijk McNuggests in verpakkingen van 6, 9 of 20 McNuggets waardoor het wel mogelijk is om exact 15 McNuggets te kopen (1x6+1x9), maar onmogelijk om er 16 McNuggets te kopen. We gaan in deze opgave berekenen wat het grootste aantal McNuggets is dat je kan bestellen dat niet precies ’past’. Om te kijken of je precies n McNuggets kan kopen moet je een diophantische vergelijking oplossen, nl.: vind positieve gehele getallen a, b en c zodanig dat: $$6a + 9b + 20c = n$$


Voor we gaan bepalen wat het grootste aantal McNuggets is dat niet precies besteld kan worden is het belangrijk twee strategie-hints uit te werken.

## Vraag 1a

Laat zien dat het mogelijk is om precies 50, 51, 52, 53, 54 en 55 McNuggets te bestellen (met pen en papier of eigen programma). Laat steeds zien hoeveel doosjes van 6,9 en 20 McNuggets je krijgt.

Theorema: Als het mogelijk is exact x, x+1, ... en x+5 McNuggets te bestellen dan betekent dat dat je elk aantal McNuggets $$\geq$$ x kan bestellen als de McNuggets komen in doosjes van 6, 9 en 20. 

## Vraag 1b

Beschrijf waarom bovenstaand theorema waar is (in tekst) en overtuig jezelf dat het antwoord uit vraag 3 (50, 51, ..., 55) betekent dat ook (56, 57, ... 61) een oplossing zijn. Sterker: alle aantallen boven de 50.

Dit is cruciaal, want dat betekent dat er een moment is waarop je als programmeur weet dat *alle* aantallen boven deze reeks te maken zijn. Het is goed om je te realiseren dat een computer dat zelf nooit bedenkt.

## Vraag 1c:

Dan komen we bij de eigenlijke hoofdvraag: schrijf een programma `McNuggets.py` dat het grootste aantal McNuggets bepaalt dat niet precies past in doosjes van 6, 9 en 20.

## Het antwoord:

Hier is een Youtube film met het goede antwoord: [McDonalds medewerker pesten](https://www.youtube.com/watch?v=vNTSugyS038&list=UUoxcjq-8xIDTYp3uz647V5A&index=5&feature=plcp)

