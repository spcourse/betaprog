# Design

Tot nu toe hebben we het gehad over twee aspecten van code: of het programma werkt, en de stijl/opmaak van code zelf. Een derde aspect is design of "ontwerp". Kijk eens naar dit programma, dat alle elementen uit een lijst print:

    L = [3,1,4,1,5,2,9]
    for pos in range(len(L)):
        print L[pos]

En dan een andere versie:

    L = [3,1,4,1,5,2,9]
    for number in L:
        print number

Je ziet dat het eerste programma loopt met de getallen 0 t/m 6, en dat alle getallen uit de lijst geprint worden. Het tweede programma print ook netjes, maar het gebruikt voor de loop direct de getallen uit de lijst. De formules worden daardoor minder ingewikkeld en het programma is sneller in één keer te lezen.

Design gaat over de structuur van je code: voor een programmeerprobleem bestaan vaak talloze oplossingen die in feite het zelfde werken. Toch kan het interessant zijn om de ene oplossing boven de andere te verkiezen. Hierboven zouden wij doorgaans de tweede variant kiezen. Maar dat betekent niet dat de eerste variant nooit voorkomt!

Design is tot op zekere hoogte subjectief. Er zijn heel veel keuzes die je kunt maken en soms heb je een voorkeur om iets op de ene of de andere manier te doen. Maar het is wel belangrijk om het doel in de gaten te houden! In deze cursus beperken we ons tot ontwerpkeuzes die er voor zorgen dat code zo eenvoudig mogelijk te begrijpen is. Vaak is dat korte code, of simpele code zonder ingewikkelde formules. Hieronder een paar vuistregels.

- Probeer **herhalende** structuren te vermijden. Tel je in je programma twee keer tot 10? Misschien kun je dat beperken tot één keer. Of heb je op twee verschillende plekken heel erg vergelijkbare `if`-structuren?

- Probeer **overbodige** elementen te verwijderen. Misschien heb je een `for`-loop geschreven die in feite maar één keer gaat. Of een `else` waar niet zoveel gebeurt. Die kun je dan weghalen.

- Probeer "**magic numbers**" te vermijden. Vaak heb je in een probleem een aantal elementen met een vaste waarde. Als je bijvoorbeeld de omtrek van de aarde berekent gebruik je daarvoor de straal die je hebt opgezocht. Gebruik zo'n constante niet direct in een formule, maar maak een variabele met een naam die de waarde goed omschrijft.

- Probeer je code zo **bondig** mogelijk te houden. Door goed gebruik te maken van de elementen van de programmeertaal, kun je sommige dingen korter opschrijven. Denk bijvoorbeeld aan de keuze voor een `for`- of een `while`-loop. **Let op:** in deze cursus ben je beperkt tot de taalelementen die wij introduceren. Als je al programmeerervaring hebt kan dat soms lastig zijn, maar ook dan kun je vaak creatief omgaan met de elementen die je gekregen hebt.

- Probeer blokjes code **apart** te zetten in functies met een duidelijke naam (decompositie). Als je code wat lang begint te worden kun je vaak stukjes code een eigen plek geven. Zelfs als je een functie maar één keer gebruikt kan het nuttig zijn om er een te maken. Zo'n functie heeft een eigen naam en als je de code snel doorleest hoef je de inhoud van de functie niet eens helemaal te lezen om 'm te begrijpen.
