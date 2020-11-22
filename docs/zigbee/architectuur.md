# Architectuur

> #### IEEE 802.15.4 Protocol

De fysieke laag van ZigBee zorgt voor de modulatie en demodulatie van data, verzending- en ontvangst management en opereert op een lage en hoge frequentie. In Europa is de lage frequentie 868.0-868.6 MHz, in de US en Australie is dit 902-928 MHz. De hoge frequentie is wereldwijd 2400-2483.5 MHZ.

> #### MAC Layer

De MAC Layer controleert de toegang tot de fysieke laag gebruik makend van een [CSMA-CA](https://nl.wikipedia.org/wiki/CSMA/CA). De coördinator van het netwerk zorgt ervoor dat pakketjes data tijdens een gegarandeerd tijdsslot worden verzonden en op die manier een gegarandeerde verbinding.

> #### IEEE 802.15.4 Network Model

De standaard maakt gebruik van 2 types netwerk apparaten.

- ###### Full-Function Device (FFD)

  Een FFD is in staat om een netwerk te creëren, configuren en berichten te routeren binnenin het netwerk. Een FFD kan op 3 manieren opereren: als PAN coordinator, als coordinator en als End Device. Verder kan het zowel communiceren met andere FFD's als mes RFD's.

- ###### Reduced-Function Devices (RFD)

  Een RFD is meestal een eenvoudig apparaat - vaak batterijgevoed - met een eenvoudige taak. Ze kunnen enkel opereren als End Device omdat ze geen routing functionaliteiten bezitten en kunnen enkel communiceren met FFD's. RFD's kunnen dus onderling niet met elkaar communiceren.

>#### IEEE 802.15.4 topologiëen

De standaard definiëert 2 mogelijke topologiëen.

![](/img/ieee-topology.png)

- ###### Star

  Een FFD maakt een PAN identifier aan en creëert op die manier zijn eigen netwerk en roept zich uit als PAN coordinator. Andere apparaten kunnen nu met het netwerk verbinden maar de FFD blijft steeds de enigste PAN coordintor en het middelpunt van dit gestructureerd netwerk. 

- ###### Peer-to-peer

  Net zoals bij de star-topologie is er slechts een enkele PAN coordinator, maar elk toestel kan met elk toestel communiceren binnen hetzelfde netwerk.

> #### Adressering

Er zijn 2 types van adressering. Een toestel krijgt een extended address (64-bits) van de producent en een uniek short address (16-bits) dat hij krijgt van de coordinator van het netwerk.

> #### ZigBee device types

Een ZigBee device kan opereren in 3 verschillende modi of node types.

- ###### ZigBee Coordinator (ZC)

  Een ZigBee Coordinator is een FFD device dat opereert als centrale node of hoofd van andere nodes in het netwerk. Slechts één per netwerk is verantwoordelijk voor de creatie, configuratie en management vanhet netwerk. De ZC houdt een lijst bij van geconnecteerde devices en ondersteund services als connecteren en deconnecteren, orphan scan, rejoin. De ZC is altijd actief binnen het netwerk.

- ###### ZigBee Router (ZR)

  Een ZigBee Router is een FFD dat mee datapakketjes kan doorsturen tussen ZED's (end devices) en ZC's (End Devices). End devices kunnen ook via een ZR verbinding maken met een ZC.

- ###### ZigBee End Device (ZED)

  Een ZigBee End Device kan zowel een FFD als RFD zijn. Wanneer een FFD is geconfigureerd als end device zal deze geen pakketjes routeren.

> #### ZigBee topologiëen

De ZigBee network layer maakt gebruik van 3 verschillende topologiëen

![](/img/zigbee-topology.png)

- ###### Star

  Centraal in deze topologie is de ZigBee coordinator die het netwerk controleert. Alle apparaten in het netwerk communiceren rechtstreeks met de ZC. In deze topologie is de ZC de bottleneck voor het routeren van pakketjes.

- ###### Tree

  In deze topologie is de ZC verantwoordelijk voor het starten van het netwerk en controleren, maar wordt de topologie verlengd door ZigBee routers. Wanneer er probleem met een router is kan dit leiden tot wegvallen van een segment in het netwerk.

- ###### Mesh

  Ook in deze topologie is de ZC verantwoordelijk voor het starten van het netwerk en controleren, en wordt de topologie verlengd door ZigBee routers. Echter is het nu mogelijk om volledige peer-to-peer te verbinden. Dit type network wordt ook wel self-healing genoemd. Wanneer een coordinator wegvalt leidt dit niet onmiddelijk tot falen van andere devices.

> #### Zigbee addressering

- ###### IEEE Address

  Dit 64-bit adres wordt geconfigureerd door de fabrikant en wordt doorgaans enkel gebruikt wanneer de ZigBee layer de verbinding crëeert tussen een device (met IEEE address) en een Network Address.

- ###### Network Address

  Dit uniek 16-bit adres dat wordt ingesteld door de ZigBee layer wordt meegegeven aan een device in het netwerk. Via dit adres is het mogelijk om een bepaald device te benaderen.

> #### Zigbee Network Identity

- ###### PAN Identifier (PAN ID)

  Deze 16-bit identifier wordt bepaald door de PAN coordinator en wordt gecommuniceerd naar de end devices. Packetjes van andere netwerken die worden ontvangen worden weggefilterd door deze devices.

- ###### Extended PAN ID (EPID)

  Deze 64-bits identifier wordt gebruikt wanneer meerdere PAN een bepaalde ruimte actief zijn. Deze extra identifier verhelpt conflicten zijn tussen overlappende networks met dezelfde PAN ID.

>#### Application level addressing

- ###### End Point Address

  Elke node kan meerdere applicaties ondersteunen - dit doormiddel van een endpoint 1-240. Broadcasten is mogelijk d.m.v. endpoint 255

- ###### Cluster Identifier (Cluster ID)

  Deze 16-bit ID addresseert een specifieke cluster binnen een netwerk.