# Fuzzy matching

Bij zoeken naar overeenkomstig DNA is het nuttig om *bijna-matches* te vinden.
Bijvoorbeeld als er maar 1 letter verschil is tussen de `needle` en een deel
van de `haystack`. Zoiets noemen we ook *fuzzy* matching.

We kijken weer naar de voorbeeldstring, `atgacatgcacaagtatgcat` en de needle
`atgc`. Als er één letter verschil mag zijn, vinden we op index 0 al direct een
match. We kunnen namelijk de laatste C van de `needle` in een A veranderen om
een fuzzy match te vinden!

We beschrijven nu een algoritme dat precies dit soort matches zoekt. We hergebruiken daarbij onze eerder geschreven zoekfuncties. (De uitleg is wat lastig. Neem de tijd om het te lezen en begrijpen.)

1. Omdat er steeds één letter uitgezonderd kan worden van de match, gaan we de needle opbreken in twee delen (*substrings*). Vanaf het begin tot het uitgezonderde karakter wordt deel `a`, en erna wordt deel `b`. Bijvoorbeeld:

	"needle" geeft "nee" en "le" (als "d" niet meetelt)

2. Dan gaan we op zoek naar de plekken waarop er exacte matches zijn van `a` in de haystack en waar de exacte matches zijn van `b` in de haystack (bijvoorbeeld door middel van de eerder gemaakte functie).

	We nemen als voorbeeld voor de haystack `"atgacatgca"` voor de needle `"atgc"`. Voor deel `a` kiezen we `"a"` en voor deel `b` kiezen we `"gc"`. Zo krijgen we twee lijsten: `[0, 3, 5, 9]` en `[7]`.

3. Nu kunnen we de fuzzy matches vinden door het verschil van de gevonden indices te vergelijken. Als $$n$$ is de positie waar `a` matcht, $$m$$ is lengte van `a`, en $$k$$ is de positie waar `b` matcht, dan weten we dat er een fuzzy match op index $$n$$ te vinden is wanneer $$n + m + 1 = k$$.

Merk op dat we dit moeten doen voor elk mogelijk paar tussen de matches van `a` en `b` om alle fuzzy matches te vinden!
