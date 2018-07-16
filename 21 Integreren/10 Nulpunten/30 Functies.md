# Nulpunten

Schrijf een programma dat de nulpunten berekent van de polynoom $$f(x)=x^2+2x-10$$.

    # python nulpunten.py
    De nulpunten zijn -4.32 en 2.32

![](PolynoomAnalyse.png)


## Specificatie

- Noem je programma `nulpunten.py`.

- Maak één functie `nulpunten(a, b, c)` die als taak heeft de nulpunten van de polynoom $$f(x)=ax^2+bx+c$$ te berekenen.

- Er zijn twee mogelijkheden voor het resultaat van de functie:

    - een lege lijst `[]` als er geen nulpunten zijn
    - een lijst met twee elementen `[n1, n2]` waarin `n1` en `n2` de nulpunten van de polynoom zijn

- Plot in alle gevallen de functie, en geef de nulpunten uit de berekening duidelijk aan in de grafiek.

## Hints

- Bereken de nulpunten met behulp van de $$abc$$-formule.

- Om te zorgen dat je het resultaat netjes kunt printen, roep je de functie aan met ons voorbeeld, en sla je het resultaat op:

        resultaat = nulpunten(1, 2, -10)

- Test later ook met een polynoom die geen nulpunten heeft (check dan of de lijst leeg is). Het programma moet in dat geval netjes printen dat de nulpunten ontbreken:

        Deze functie heeft geen nulpunten.

## Testen

Als je hier `checkpy` gebruikt, dan wordt niet meer getest of je programma de juiste uitvoer geeft, maar of de functie `nulpunten()` het juiste resultaat geeft.

    checkpy nulpunten.py

(Werkt het niet? Update dan nog eens met `checkpy -u`.)
