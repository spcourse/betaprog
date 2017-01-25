# Controleren en debuggen

Met een simulatie wil je een reëel beeld van de werkelijkheid geven, zodat de uitkomsten gebruikt kunnen worden in de "echte wereld". Het is dus een *model*.

Het is vaak moeilijk om aan de uitkomst te zien of de simulatie goed werkt. In het geval van de appel hierboven, kun je de uitkomst ook nog analytisch berekenen. Maar dat wordt al snel bewerkelijk.

Daarom is het belangrijk om een simulatie systematisch te controleren. Hier geven we een paar punten die daarbij kunnen helpen:

1. Check met pen en papier of de basis van je berekening klopt: zit je in de goede richting? Als het te ingewikkeld wordt kun je misschien een grove schatting maken en dat vergelijken met je simulatie.

2. Heb je de juiste constanten en formules opgezocht? Controleer ze nog een keer. Zijn de constanten precies genoeg? Anders loopt de afrondingsfout snel op.

3. Neem je tijdstappen die voldoende klein zijn?

4. Staan de onderdelen van de simulatie wel in de juiste volgorde? Zorg dat je per stap alle nieuwe waarden berekent. Voer daarna pas controle uit of er misschien een interessant punt bereikt is.

Tenslotte nog een tip voor het debuggen van je simulatie. Je kunt per tijdstap alle waarden uitprinten die berekend worden. Dan kun je precies nalopen of er ergens een fout ontstaat. Of misschien zijn de beginwaarden wel al verkeerd!
