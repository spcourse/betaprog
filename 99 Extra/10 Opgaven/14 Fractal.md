
# Fractal: Mandelbrot set

We gaan proberen de meest beroemde fractal, de Mandelbrot set, te tekenen op het scherm. Deze opgave vereist kennis van complexe getallen.

Voor elk punt in het complexe vlak ($$z_0$$) definieren we sequentie waarbij een functie, een polynoom, aangeeft naar welk punt (complex getal $$z_1$$) het startpunt $$z_0$$ zich verplaatst. Een belangrijke set polynomen wordt gegeven door:

$$f(z) = z^2 + c$$

Elk punt $$z_0$$ dat je definieert geeft je een nieuw punt: $$z_1 = f(z_0) = z_0^2 + c$$. Het is zo steeds mogelijk een volgend punt te berekenen, immers $$z_2 = f(z_1) = z_1^2 + $$ etc etc. Meer algemeen geldt $$z_n = f^{(n)}(z_0)$$. Er zijn nu 2 mogelijkheden:

   - De reeks convergeert naar 1 punt $$\rightarrow$$ het punt is *wel* onderdeel van de set

   - De reeks divergeert $$\rightarrow$$ het punt is *geen* onderdeel van de set

Elke keuze van $$c$$ geeft een uniek patroon van punten die wel/niet in de set zitte. Als je vervolgens de snelheid waarmee punten wel/niet convergeren koppelt aan een bepaalde kleur dan krijg je de karakteristieke plaatjes die je kent.

## De Mandelbrot set

De Mandelbrot set is speciaal omdat in dat geval geldt dat $$c$$ het startpunt zelf is: $$c = z_0$$. De tekening van de MandelBrot set is hierbeneden getekend.

![](MandelBrot.png)

## Opgave 1: Mandelbrot set

Bepaal voor elk punt $$z_0$$ in het complexe vlak of het convergeert of divergeert onder de polynoom $$f(z)=z^2+z_0$$. Als het convergeert teken je het punt blauw, als het divergeert teken je het wit.

Let op:

   - bestudeer de reeks een paar punten en bedenk een maat waarmee je bepaalt of een punt convergeert of juist divergeert. Bijvoorbeeld de afstand tussen 2 opeenvolgende punten $$z_i$$ en $$z_{i+1}$$.
   
   - in deze opgave krijg je niet zo'n glossy figuur als hierboven. In dat soort figuren wordt de kleur bepaald door de convergetiesnelheid waarmee een punt divergeert (of convergeert).

   - Voor specifieke waardes van $$c$$ in de functie $$f(z) = z^2 + c$$ zijn er zogenaamde Julia sets. probeer er een paar van te tekenen.

  

