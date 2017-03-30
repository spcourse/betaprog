# Levenshtein

Maak een nieuw bestand aan genaamd `levenshtein.py`.
Maak een functie `levenshtein_distance()` die twee strings als invoer krijgt en de
Levenshteinafstand berekent en teruggeeft.

	>> levenshtein_distance("majeur", "mineur")
	4

## Specificatie

Schrijf zelf een functie `levenshtein_distance` die twee strings als argumenten accepteert. 
Vervolgens de levenshtein afstand tussen de strings uitrekent, en deze afstand `return`-ed.

## Hints

Er zijn een paar stappen om zover te komen.

1. Zorg eerst dat de invoer-strings klaar zijn om het algoritme mee uit te
voeren. Om ze mooi op de tabel te laten passen, is het handig om een spatie aan
de voorkant van de string in te voegen.

2. Maak vervolgens de tabel aan, waarbij je de lengtes van de invoerstrings als
afmeting aanhoudt. De waarden in de tabel kun je in het begin allemaal op nul
zetten.

3. Nu vul je de eerste rij en kolom in, zodat ze als basis kunnen dienen voor
de verdere berekeningen. Deze rij en kolom geven de afstand weer vanaf een lege
string, dus die zijn het makkelijkst om in te vullen. Neem `n` voor de lengte
van invoerwoord `a` en `m` als lengte voor invoerwoord `b`. De formule is dan:

    `table[0][x] = x`, waar x = 0 ... n  
    `table[y][0] = y`, waar y = 0 ... m  

    In Python kun je dit mooi doen met een `for`-loop.

4. Nu komt het moeilijke gedeelte: het invullen van de resterende vakjes. Je
kunt hiervoor een dubbele `for`-loop gebruiken. De eerste telt de kolommen, de
tweede telt de rijen. Dit levert je een stel coördinaten op die door de hele
tabel heenlopen. Vervolgens moet je de drie waardes berekenen zoals eerder
omschreven in de Levenshtein uitleg. De kleinste van de waardes die je berekent zet je steeds in de tabel.

	    Voor de duidelijkheid:

	                        table[y-1][x] +1
	    table[y][x] = min ( table[y][x-1] +1                                )
	                        table[y-1][x-1] + (0 if a[i] == b[j], else 2)

5. Uiteindelijk return je dan de waarde van de tabel die rechts onderin staat.

## Testen

	checkpy levenshtein
