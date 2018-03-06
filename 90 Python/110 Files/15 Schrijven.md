# Schrijven naar een bestand

Hoewel we dat in deze cursus niet tegen zullen komen is het belangrijk dat je weet hoe je gegevens naar een file schrijft in plaats van ze alleen maar in te lezen. Het is vrij eenvoudig zoals je in de volgende 2 voorbeelden zult zien. Belangrijkste is dat je bij het gebruik van het `open()` commando nu de extra parameter `'w'` (write) meegeeft.

## Voorbeeld: tekst schrijven naar een file

Dit stuk code opent een file 'Mijnfile.txt', schrijft daar 1 regel tekst in weg  en sluit de file weer.

    output_file = open('outputfile.txt', 'w')
    output_file.write("Het vak Inleiding Programmeren is bere-interessant")
    output_file.close()

## Voorbeeld: extra tekst achter bestaande regel plakken

Dit stuk code opent de file inputfile, plakt voor elke regel de letters "XXX" en schrijft deze nieuwe regel vervolgens weg in een outputfile.

    input_file = open('inputfile.txt', 'r')
    output_file = open('outputfile.txt', 'w')
    for line in input_file:
        newline = "XXX " + line
        output_filehandle.write(newline)

    input_file.close()
    output_file.close()
