> # Conclusie

## Hoe groot is de kans op een externe aanval op een Zigbee-netwerk?

Een Zigbee-netwerk is het gevoeligst voor een externe aanval:

* Enerzijds wanneer een nieuw apparaat aan het netwerk wordt gekoppeld en de standaard Trust-Center sleutel wordt gebruikt om de netwerksleutel te encrypteren.
* Anderzijds wanneer een apparaat opnieuw verbinding maakt met het netwerk, en de netwerk-Setup het mogelijk maakt om opnieuw deel te nemen met behulp van de standaard TC-Sleutel.

Zelfs met een beperkte kans (korte tijdsperiode) om dit beveiligingslek te misbruiken, kunnen aanvallers hun kansen op succes maximaliseren door de gebruiker te manipuleren.
Een manier waarop ze dit kunnen doen, is door ruis naar het Zigbee kanaal te sturen om de communicatie te verstoren, in de hoop de gebruiker te misleiden om te proberen een apparaat opnieuw te koppelen om de sniffing-aanval uit te voeren.

## Conclusie

Ondanks alle veiligheidsfeatures (encryptie & authenticatie) die geïmplemeneerd zijn in de Zigbee-architectuur blijft ze gevoelig voor aanvallen van buitenaf, zeker wanneer de standaard TC-sleutel niet wordt veranderd.

Met dit in het achterhoofd geldt ook hier de aanbeveling om binnen een Zigbee-netwerk periodiek de netwerksleutel aan te passen en deze manueel in te voeren in een node, al is dit niet altijd mogelijk.

Ook het gebruik van Zigbee producten die gebruik maken van Zigbee Light Link - waar gebruik wordt gemaakt van een geheime TC-sleutel, in principe enkel bekend bij de fabrikant zelf - houdt een zeker risico in. Ook deze producten zijn reeds succesvol gehacked waar we de vraag moeten stellen in hoeverre deze TC-sleutels nog veilig zijn omdat ze reeds publiek circuleren. Door de groeiende populariteit van deze producten (Philips Hue, Ikea Trådfri,...) zal de architectuur mogelijks ook potentieel interessanter worden voor hackers.

