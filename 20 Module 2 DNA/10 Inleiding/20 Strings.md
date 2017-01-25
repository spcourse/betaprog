# Strings

Een *string* is een datatype waarmee we in programma's kunnen werken met
reeksen letters en andere tekens, en kan gebruikt worden om woorden en zinnen
te representeren in code.. In deze opdracht gaan we strings toepassen om
DNA-sequenties te matchen.

In de editor van de IDE kun je strings herkennen doordat deze groen weergegeven
worden. Maar laten we eerst een string aanmaken in de Python Shell (weet je nog
hoe je deze moet starten?).

Om aan te geven dat een string begint zet je aanhalingstekens `"` neer.
Vervolgens zet je het woord of de zin neer die je in de string wil hebben. Je
eindigt weer met aanhalingstekens `"`. Om `abcde` in een string te zetten doen
we dus:

    >>> my_string = "abcde"

Je kunt een willekeurig teken (character) uit de string pakken door de string
te indexeren:

    >>> print my_string[0]
    'a'
    >>> print my_string[1]
    'b'
