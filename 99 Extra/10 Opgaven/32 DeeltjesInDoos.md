# Deeltjes in een doos

In een doos (afmeting $$0\leq x \leq 1$$ en $$0\leq y \leq 1$$) worden op een plek $$(x_{\rm source},y_{\rm source}) = (0.25,0.75)$$ een aantal deeltjes geproduceerd met een random snelheid en richting. Voor elk deeltje $$i$$ geldt dus:

   - snelheid($$v_i$$):  $$0<v_i<0.10$$

   - hoek ($$\alpha_i$$):  $$0<\alpha_i<2\pi$$

Het is met behulp van de computer mogelijk de positie van een groot aantal deeltjes in de tijd te volgen. 

![](DeeltjesInDoos.png)

Genereer een beginsituatie door voor een groot aantal punten $$i$$ de snelheid $$v_i$$ en $$\alpha_i$$ te kiezen. 

### Inzicht aan het begin van de opgave:
   - De evolutie in $$x$$ en $$y$$ is afzonderlijk te beschrijven. Bepaal daarom gelijk aan het begin voor elk deeltje zijn snelheid in x en y afzonderlijk. De grootte van die snelheid zal namelijk niet veranderen (in het eerste deel van de opgave). Let wel op: het teken van de snelheid kan *wel* veranderen als het deeltje tegen een wand botst.

   - Op elk moment in de tijd verandert de positie van deeltje $$i$$ volgens: $$x_{i+1}= x_i+v_{i(x)}\Delta t$$.
   
   - Hou van elk deeltje op elk tijdstip *alleen* zijn positie (x,y) en zijn snelheid (vx, vy) bij. Je hoeft dat dus niet te doen als functie van de tijd. Dat is alleen nodig als je een baan van een deeltje zou willen plotten op het scherm

## Deeltjes in de doos (deel 1): deeltjes botsen niet onderling

In het begin van de opgave zullen we de natuurkunde een beetje vereenvoudigen, maar het zal ons toch in staat stellen een aantal fenomenen te onderzoeken.

Onze aannames in dit deel van de opgave:

   - de deeltjes ketsen elastisch tegen de wanden en kunnen de doos niet uit

   - de deeltjes hebben geen afmeting en kunnen niet botsen
   
### Vraag 1a)

Maak een grafiek van het aantal deeltjes aan de rechter kant van de doos ($$x_i>0/5$$) als functie van de tijd.

### Vraag 1b)

Maak een grafiek van de gemiddelde afstand tussen de deeltjes als functie van de tijd. 

## Deeltjes in de doos (deel 2): gat in een van de wanden

Stel nou eens dat er een gat in een van de wanden van de doos zit: $$y_{\rm gat} = 0.00$$ en $$0.8<x_{\rm gat}<0.9$$. Het is nu mogelijk dat deeltjes uit de doos ontsnappen.

### Vraag 1c) positie deeltjes

Maak een grafiek van het aantal deeltjes in de doos als functie van de tijd. Bepaal ook de gemiddelde tijd waarop de helft van de deeltjes uit de doos is ontsnapt: $$t_{1/2}$$. Probeer ook zelf een schatting te maken zonder gebruik te maken van een computerprogramma.

### Vraag 1d) 

Stel nou dat de deeltjes gemiddeld met een 2x hogere snelheid beginnen in de beginsituatie: $$0 < v_i< 0.20$$. Maak weer dezelfde grafiek als bij c) en bepaal opnieuw $$t_{1/2}$$. Hoe verschilt deze van je antwoord bij c) ? Wat verwachttte je ?


## Deeltjes in de doos (deel 3): realisme toevoegen

De aanname dat de deeltjes geen afmeting hebben en niet botsen is natuurlijk wel erg kort door de bocht omdat juist die fenomenen zorgen voor de eigenschappen van een gas. Het is ook inzichtelijk om de evolutie van dit systeem te visualiseren met een animatie. Niet alleen leuk om te zien, maar het legt ook snel programmeerfouten bloot die soms niet gelijk opvallen als je naar de vergelijkingen zelf kijkt. We zullen in dit deel van de opgave de deeltjes ook een afmeting geven.

### Vraag 1e)

Maak een animatie zodat je de deeltjes door de doos kan zien bewegen als functie 
van de tijd. Gebruik hiervoor het template uit de cursus.

### Vraag 1f)

Geef de deeltjes een afmeting en laat ze netjes van de wand ketsen als de rand van het deeltje de wand raakt. Implementeer dit ook in de animatie.

### Vraag 1g)

Laat de deeltjes realistisch botsen, dus met de echte afmeting. Hier een korte afleiding van de botsingskinematica in 2-dimensies:
[2d-botsing kinematics](http://www.vobarian.com/collisions/2dcollisions2.pdf)

### Vraag 1h)

Geef 1 van de deeltjes een andere afmeting en zorg dat de massa van dat deeltje evenredig is met zijn oppervlak. Dat zal de botsing met de lichtere deeltjes beinvloeden. Bestudeer verschillende scenario's.

![](BouncingBallsGif.gif)

## Deeltjes in de doos (deel 4): Maxwell-Boltzmann verdeling

Zodra twee deeltjes botsen veranderen zowel de snelheid als de bewegingsrichting
van de deeltjes. Interessant is dat de snelheidsverdeling uiteindelijk de Maxwell-Boltzmannverdeling zal volgen, onafhankelijk van de begincondities. We willen dat graag bewijzen door de verdeling te bekijken na een tijd lang botsen.

### Vraag 1i)

Begin met dezelfde condities als in vraag a) en maak een grafiek van de
snelheidsverdeling na 100 en na 1000 botsingen.

### Vraag 1j)

Verzin een manier om fluctuaties te voorkomen. Je zou bijvoorbeeld een 'gemiddelde' snelheidsverdeling kunnen maken maken door het gemiddelde profiel tussen botsing tijdstap 95 en 105, maar er zijn vast ook andetre manieren.

### Vraag 1k)

De claim is dat de snelheidsverdeling de Maxwell-Boltzmann zal worden *onafhankelijk* van de begincondities. Test die claim door met varierende begincondities te werken. Begin eens met een beginsituatie waarin alle deeltjes dezelfde snelheid hebben en vergelijk de uiteindelijke snelheidsverdeling met die uit de vorige vraag. Wat valt je op ? Wat is de gemiddelde snelheid ? Zijn ze inderdaad hetzelfde ? Een ander optie is om alle deeltjes stil te zetten, op 1 deeltje na dat een heel hoge snelheid heeft.  







