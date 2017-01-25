# Levenshteinafstand

De Levenshteinafstand is gedefinieerd als het minimale aantal bewerkingen dat er
nodig is om van de ene string tot de andere te komen. Het geeft dus aan in welke
mate een string op een andere lijkt.

Deze maatstaf wordt bijvoorbeeld gebruikt in informatietheorie om berichten te
ontcijferen. Het kan ook gebruikt worden om spell checkers te verbeteren, of
de fouten van een optisch karakterherkenningsprogramma te verbeteren. In ons
geval kunnen we deze toepassen om uit te rekenen hoeveel de ene DNA-sequentie op
de andere lijkt, of om twee DNA-sequenties zo over elkaar te schuiven dat ze het
meest op elkaar lijken. Verdere toepassingen zijn te vinden in machine
vertaling, informatie extractie en spraakherkenning.

Bij de Levenshteinafstand zijn er zijn drie soorten bewerkingen op een string mogelijk:

* er kan een letter weggehaald worden  
* er kan een letter toegevoegd worden  
* er kan een letter gesubstitueerd worden  

De eerste twee bewerkingen hebben elk als "kosten" 1. De substitutie kost 2,
want dit is hetzelfde als één letter weghalen en vervolgens één letter
toevoegen.

---

We gaan een functie schrijven om de Levenshteinafstand te berekenen:
`Levenshteinafstand(a, b)`. Net als bij de fuzzy matching, delen we het
probleem op in kleinere stukken.

De afstand om van een lege string tot een een willekeurige string te komen is
simpelweg de lengte van de string. Dus

	Levenshteinafstand("", "pindakaas")

geeft 9, want je moet vier keer een letter toevoegen om de lege string naar het
woord "pindakaas" om te zetten.

Laten we vervolgens uitzoeken wat het verschil is tussen twee woorden,
bijvoorbeeld "majeur" en "mineur". Eerst beginnen met de kosten om van een lege
string tot `m` te komen (1 toevoeging), dan tot `ma` (2 toevoegingen), naar
`maj` te komen (3), tot we uiteindelijk `majeur` hebben (6). We schrijven dit op in een tabel:

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |

En we doen hetzelfde voor mineur:

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| m | 1 |
| i | 2 |
| n | 3 |
| e | 4 |
| u | 5 |
| r | 6 |

Hier kun je dus in de tabel in kolom $$x$$ en rij $$y$$ aflezen hoeveel het
kost om het woord `a` tot de $$x$$'e letter om te bouwen vanaf het woord `b`
tot de $$y$$'e letter. Uiteindelijk willen we helemaal rechts onderin komen
om te zien hoeveel het kost om het hele woord `a` om te bouwen tot `b` of
andersom.

> We gaan elk vakje invullen met de Levenshteinformule. Het idee is dat we, nu
we weten hoeveel het kost om een kleinere string om te bouwen, makkelijk kunnen
berekenen hoeveel het kost om een iets langere string om te bouwen, waarna we
weer een iets langere string kunnen opbouwen tot het einde.

Nu de Levenshteinformule. Het ziet er ingewikkelder uit dan het is, dus schrik
niet. De waarde die we in een vakje invullen is afhankelijk van wat de meest efficiënte manier is om er terecht te komen:

1. voor een toevoeging/verwijdering vanaf string `a` nemen we de waarde op plek $$(x-1, y) + 1$$

2. voor een toevoeging/verwijdering vanaf string `b` nemen de waarde op plek $$(x, y-1) + 1$$

3. we kunnen ook van plek $$(x-y, y-1)$$ komen; als karakter $$x$$ op plek `a` hetzelfde is als karakter $$y$$ op plek `b`, dan nemen we de de waarde op plek $$(x-1, y-1) + 0$$ want dan is er niets aan de hand; als deze niet gelijk is moeten we substitueren en nemen we de vorige waarde $$+2$$, dus $$(x-1, y-1) + 2$$

We nemen van bovenstaande opties het kleinste resultaat en die vullen we in.

---

We nemen het voorbeeld er weer bij. Gebruik dit om het algoritme en de formule goed te begrijpen. We kijken bij het eerste lege vakje of we de
string opbouwen:

- van `""` naar `"m"` (kosten: 1)
- van `""` naar `"m"` (kosten: 1)
- of dat er een substitutie nodig is (kosten: 2)
- of dat de letter al klopt (kosten: 0)

In ons voorbeeld klopt de letter al en vullen we een 0 in.

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| m | 1 | 0 
| i | 2 |
| n | 3 |
| e | 4 |
| u | 5 |
| r | 6 |

Volgende vakje (naar rechts).

- we komen van links; van `m` naar `ma` kost 1 toevoeging; samen met de eerdere kosten is dat: 1
- we komen van boven; van `ma` naar `m` kost 1 verwijdering; samen met de eerdere kosten is dat: 3
- we komen van linksboven; van `m` naar `ma` kost 2, dus totale kosten: 3

Kortom, we vullen 1 in:

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| m | 1 | 0 | 1
| i | 2 |
| n | 3 |
| e | 4 |
| u | 5 |
| r | 6 |

Zo gaan we door. Bij het volgende vakje kunnen we vanaf `ma` `maj` maken met 1
toevoeging:

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| m | 1 | 0 | 1 | 2
| i | 2 |
| n | 3 |
| e | 4 |
| u | 5 |
| r | 6 |

Rij compleet:

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| m | 1 | 0 | 1 | 2 | 3 | 4 | 5 |
| i | 2 |
| n | 3 |
| e | 4 |
| u | 5 |
| r | 6 |

`mi` van `m` maken:

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| m | 1 | 0 | 1 | 2 | 3 | 4 | 5 |
| i | 2 | 1 |
| n | 3 |
| e | 4 |
| u | 5 |
| r | 6 |

Nu is er weer een interessante. We moeten van `mi` naar `ma`. Alle drie de
kosten komen op 2 uit: 2 toevoegingen of 1 substitutie:

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| m | 1 | 0 | 1 | 2 | 3 | 4 | 5 |
| i | 2 | 1 | 2 |
| n | 3 |
| e | 4 |
| u | 5 |
| r | 6 |

En helemaal op het einde:

|   |   | m | a | j | e | u | r |
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| m | 1 | 0 | 1 | 2 | 3 | 4 | 5 |
| i | 2 | 1 | 2 | 3 | 4 | 5 | 6 |
| n | 3 | 2 | 3 | 4 | 5 | 6 | 7 |
| e | 4 | 3 | 4 | 5 | 4 | 5 | 6 |
| u | 5 | 4 | 5 | 6 | 5 | 4 | 5 |
| r | 6 | 5 | 6 | 7 | 6 | 5 | 4 |

De goedkoopste manier om van mineur naar majeur te komen is vier en dat lees je
af rechts onderin.
