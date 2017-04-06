# Fuzzy matching

Bij zoeken in strings is het nuttig om *bijna-matches* te vinden. Bij DNA doen we dat ook vaak, omdat de nucleotiden niet altijd goed gemeten kunnen worden; een deel van de informatie is dus net niet helemaal correct. We making dan gebruik van *fuzzy* matching.

We kijken weer naar de voorbeeldstring `atgacatgcacaagtatgcat` en de needle
`atgc`. Als er één letter verschil mag zijn, vinden we op index 0 al direct een
match. We kunnen namelijk de laatste C van de `needle` in een A veranderen om
een fuzzy match te vinden!

We beschrijven nu een algoritme dat precies dit soort matches zoekt. We hergebruiken daarbij onze eerder geschreven zoekfuncties. (De uitleg is wat lastig. Neem de tijd om het te lezen en begrijpen.)

1. Omdat er steeds één letter uitgezonderd kan worden van de match, gaan we de needle opbreken in twee delen (*substrings*). Vanaf het begin tot het uitgezonderde karakter wordt deel `a`, en erna wordt deel `b`. Bijvoorbeeld:

	"balk" geeft "ba" en "k" (als we de letter "l" uitzonderen)

2. Dan gaan we op zoek naar de plekken waarop er exacte matches zijn van `a` in de haystack en waar de exacte matches zijn van `b` in de haystack (bijvoorbeeld door middel van de eerder gemaakte functie `exact_matches`).

	We nemen als voorbeeld voor de haystack `"atgacatgca"` voor de needle `"atgc"`. Voor deel `a` kiezen we `"a"` en voor deel `b` kiezen we `"gc"`. Zo krijgen we twee lijsten: `[0, 3, 5, 9]` en `[7]`.

3. Nu kunnen we de fuzzy matches vinden door het verschil van de gevonden indices te vergelijken. Als $$n$$ de positie is waar `a` matcht, $$m$$ is lengte van `a`, en $$k$$ is de positie waar `b` matcht, dan weten we dat er een fuzzy match op index $$n$$ te vinden is wanneer $$n + m + 1 = k$$. Probeer goed te begrijpen waarom!

Merk op dat we dit moeten doen voor elk mogelijk paar `a` en `b` om alle fuzzy matches te vinden!

Het lijkt misschien lastig of veel werk om dit te programmeren. Een belangrijke
vaardigheid bij het programmeren is een groot en moeilijk probleem opdelen in
kleinere problemen die makkelijker op te lossen zijn. Dit noemen we
probleem*decompositie*. Voor dit algoritme zien we twee duidelijke delen: eerst
moet je alle mogelijke waarden voor `a` en `b` genereren, en vervolgens kun je
die gebruiken om de fuzzy matches te vinden.

Om de functies te gebruiken die je in exactMatches.py hebt gebruikt moet je deze nog importeren.
Dit kan op dezelfde manier als waarop we alles van de strings module importeren:

    from findmatches import *

Let er op dat je alle bestanden in dezelfde map hebt staan!

