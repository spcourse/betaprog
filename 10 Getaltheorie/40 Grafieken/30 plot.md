# Plot

## Specificatie

* Maak een file `plot.py` en schrijf daarin een programma dat de grafiek van de functie $$f(x) = x^x$$ tussen x = 0 en x = 1.5 in stapjes van 0.01 plot. Gebruik hiervoor een blauwe lijn.

* Zorg dat het minimum in de grafiek wordt aangegeven door middel van een rode stip.

* Laat je programma uitprinten, in de terminal, waar dit minimum zich bevindt.

![](plotje4.png)

## Hints


	import matplotlib
	matplotlib.use('Agg')
	import matplotlib.pyplot as plt


* Let op, om `matplotlib` goed te importeren binnen de CS50 IDE, moet je gebruik maken van bovenstaande drie regels in je code. Heb je Python geïnstalleerd staan op je computer, dan voldoet enkel `import matplotlib.pyplot as plt`.

* Kijk goed naar [de voorbeelden](/python/plot).

* Bij het gebruiken van libraries/bibliotheken is het heel nuttig om Google te gebruiken. Wil je weten hoe je iets voor elkaar speelt met pyplot? Google maar! Tip: gebruik het woord "example" om naar voorbeelden te zoeken.

## Testen

Testen is voor deze opdracht wat lastiger, want checkpy kan niet beoordelen hoe je grafiek er uit ziet. Of deze grafiek correct is moet je dus zelf nagaan. Checkpy kan wel testen of je überhaupt een grafiek maakt, en of de gevonden minpunten kloppen.

    checkpy plot
