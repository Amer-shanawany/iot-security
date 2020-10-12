# Deelproblemen

1. XY-positie invoeren en verplaatsen: na ingave van de XY-positie moet de camera verplaatst worden naar de gewenste positie - wanneer de positie bereikt is moet er een bevestiging terug worden verstuurd. De elektronische aansturing van de motors zal afhankelijk zijn van de mechanische uitwerking van het XY-systeem.

2. Mechanische uitwerking XY-systeem: het XY-systeem zal werken met 2 steppermotors, in welke mechanische configuratie deze worden opgesteld zal bepalend zijn voor de aansturing van de beide motors. De mechanische configuratie moet gekozen worden met nauwkeurigheid en schaalbaarheid in het achterhoofd maar minder met snelheid. 

3. Teruggaan naar 0-positie: het moet mogelijk zijn om (bijvoorbeeld na een stroomstoring) terug te gaan naar een 0-positie en het systeem te calibreren. Dit kan gerealiseerd worden met sensoren of knoppen die een signaal doorgeven wanneer een bepaalde positie bereikt is zodat de XY-posities consistent zijn.
4. PCB opdelen: de PCB van de huidige labfarm moet worden opgedeeld in deelsystemen, we zullen het XY-systeem dan ook ontwikkelen als lostaand systeem dat wordt aangestuurd door een centrale controller.

5. Aansturing XY-systeem: de controller van het XY-systeem moet aangestuurd door een centrale unit – wat zijn de mogelijkheden hiervoor? Google Coral, Raspberry PI, ESP…

6. Instellingen XY-systeem: het moet mogelijk zijn de mechanische eigenschappen van het systeem in te voeren of te wijzigen – lengte, breedte, beweegsnelheid. Verder moet het XY-systeem opnieuw in te stellen zijn.

7. Gebruik camera: wanneer het XY-systeem een bepaalde positie heeft bereikt moet de camera een foto nemen van de plant. De foto moet ergens bewaard worden (database, kaart,…) en hierna geanalyseerd worden door een Google Coral cluster.

8. Posities van de planten: de posities van de planten moeten vastgelegd in het systeem – bij voorkeur automatiseren we dit, het systeem scant de hele omgeving. Hoe kunnen we planten herkennen? Labelen we elke plant met een (QR-)code? Op die manier kunnen we bij herinrichten van de kast planten ook terugvinden.

9. Back-end ontwikkeling: data moet kunnen worden opgeslagen en verwerkt worden (bv. code, naam, datum/uur van foto, nummer van Labfarm, positie in de Labfarm,…)

10. Front-end ontwikkeling: het geheel moet door middel van een (web)interface (Angular, NodeRed,…) aanstuurbaar zijn.