# Format

We hebben al gezien hoe je variabelen kan printen. Bijvoorbeeld:

    temperature = 1000
    print("De temperatuur is", temperature, "graden.")

Je kan dit ook op een andere manier te doen:

    print("De temperatuur is {} graden.".format(temperature))

De accolades, `{}`, in de string geven aan dat er nog een waarde ingevuld moet worden. Met `format` geef je vervolgens aan welke waarde dat moet zijn.

Dit kan vooral handig zijn voor het printen van meerdere variabelen:

    temperature = 1000
    pressure = 1.013
    print("Het is {} graden en de luchtdruk is {} bar.".format(temperature, pressure))

In dit geval zijn er twee placeholders, `{}`, die door `format` worden ingevuld.

