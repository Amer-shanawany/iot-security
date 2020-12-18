> # Security issues


## Issue 1: 
De standaard Trust Center sleutel is openbaar! [bron](https://peeveeone.com/?p=135)
Meerdere secuirty onderzoeker hebben al geraporteerde dat de TC-sleutel wordt niet geupdate of veranderd.

```
The Default Trust Center Link Key is public: ZigBeeAlliance09 
    5A 69 67 42 65 65 41 6C 6C 69 61 6E 63 65 30 39
```
Vroeger werd de TC-sleutel openbaar overgedragen, nu is wel gencrypteerd maar met een default TC. 

## Issue 2: 
Er zijn bijna geen echte implementatie van Link-Sleutels, dit wil zeggen als iemand een van de sleutel heeft aanpakt dan kan hij de volledig network controlleren.
Deze sleutel kan uit getrokken worden van de toestel zelf, of tijdens de key-exchange.


## Issue 3:
Geen Key-Rotation.
Er zijn geen configuratie mogelijkhedien voor Zigbee Security, m.a.w. wij kunnen de Network-Sleutel niet veranderen, of een nieuwe sleutel aan te vragen. Als ene toestel wordt gecompromitteerd, moeten wij de volledig systeem weg gooien, en niuewe systeem kopen.

## Issue 4:
Het is bijna onmogelijk om de sleutel te verwijderen op een bepaalde toestel, omdat meest van de toestellen hebben geen reset machanisme, en de enige manier is het toestel te vernietigen, om zeker te zijn dat niemad kan aan uw sleutel.

Bv. Smart Hub, Philips Hue continue zoeken voor een netwerk om erbij aan te sluiten.


