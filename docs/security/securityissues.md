> # Security issues


## Issue 1: 
De standaard Trust Center sleutel is openbaar! [bron](https://peeveeone.com/?p=135)
Meerdere security-onderzoekers hebben al geraporteerd dat de TC-sleutel niet wordt geupdate of veranderd.

```
The Default Trust Center Link Key is public: ZigBeeAlliance09 
    5A 69 67 42 65 65 41 6C 6C 69 61 6E 63 65 30 39
```
Vroeger werd de TC-sleutel openbaar overgedragen, nu is wel gencrypteerd maar met een default TC. 

## Issue 2: 
Er is bijna geen echte implementatie van Link-Sleutels, dit wil zeggen als iemand een van de sleutel heeft, het het volledig network kan controleren.
Deze sleutel kan getrokken worden uit het toestel zelf, of tijdens de key-exchange.

## Issue 3:
Geen Key-Rotation.
Er zijn geen configuratie mogelijkhedien voor Zigbee Security, m.a.w. we kunnen de Network-Sleutel niet veranderen, of een nieuwe sleutel aan te vragen. Als een toestel wordt gecompromitteerd, moeten wij de volledig systeem weg gooien, en nieuw systeem kopen.

## Issue 4:
Het is bijna onmogelijk om de sleutel te verwijderen op een bepaald toestel, omdat meest van de toestellen geen reset machanisme hebben, en de enige manier is het toestel te vernietigen, om zeker te zijn dat niemand aan uw sleutel kan.

Bv. Smart Hub, Philips Hue continue zoeken voor een netwerk om erbij aan te sluiten.


