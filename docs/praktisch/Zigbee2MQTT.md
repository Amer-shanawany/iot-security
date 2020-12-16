> # Zigbee2MQTT

## Inleiding

We maken gebruik van [zigbee2mqtt](https://www.zigbee2mqtt.io) om enkele security issues van Zigbee (en MQTT) te onderzoeken. Als Zigbee adapter maken we gebruik van een CC2531 USB sniffer. Deze is niet bijzonder krachtig (Small network (< 20 devices)) maar voldoet voor ons onderzoek.

![CC2531 USB sniffer](/img/149358506.jpg)

Installatie van Zigbee2MQTT en een MQTT broker - in ons geval Mosquitto - gebeurt op een RaspBerry Pi. 

## Flashen van de CC2532 USB sniffer

Voor we gebruik kunnen maken van de CC2531 is het nodig om deze te voorzien van de goede firmware. Instructies hiervoor vonden we op deze [pagina](https://www.zigbee2mqtt.io/information/flashing_the_cc2531.html).

## Installatie van Mosquitto 

Voor we Zigbee2MQTT installeren installeerden we een MQTT broker op de Raspberry Pi. Kort en bondig de stappen die we hiervoor gebruikten.

Installatie

```{bash}
sudo apt install mosquitto mosquitto-clients
```

Service activeren en automatisch laten starten bij reboot.

```{bash}
sudo systemctl enable mosquitto
```

Status van de service checken kan met volgend commando

```{bash}
sudo systemctl status mosquitto
```

En dit genereert de volgende output...

```{}
    ● mosquitto.service - Mosquitto MQTT v3.1/v3.1.1 Broker
   Loaded: loaded (/lib/systemd/system/mosquitto.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2020-11-27 20:52:16 CET; 2 weeks 1 days ago
     Docs: man:mosquitto.conf(5)
           man:mosquitto(8)
 Main PID: 462 (mosquitto)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/mosquitto.service
           └─462 /usr/sbin/mosquitto -c /etc/mosquitto/mosquitto.conf

nov 27 20:52:15 raspberrypi systemd[1]: Starting Mosquitto MQTT v3.1/v3.1.1 Broker...
nov 27 20:52:16 raspberrypi systemd[1]: Started Mosquitto MQTT v3.1/v3.1.1 Broker.
```

## Installatie van Zigbee2MQTT

Hierna hebben we Zigbee2MQTT geïnstalleerd volgens de instructies op deze [pagina](https://www.zigbee2mqtt.io/getting_started/running_zigbee2mqtt.html).

Een belangrijke stap die we zeker willen vermelden hierbij is om een nieuwe netwerk-key aan te maken bij de volgende heropstart. Dit in plaats van de default netwerk-key wat een veiligheidsrisico kan zijn. Dit kan door toevoeging van volgende lijnen aan `configuration.yaml`.

```{}
advanced:
    network_key: GENERATE
```

Na heropstart is de webinterface beschikbaar op poort 8080.

![Zigbee2MQTT webinterface](/img/Zigbee2MQTT_web.png)

In deze webinterface is het mogelijk om in te stellen of het mogelijk is om nieuwe Zigbee apparaten met het netwerk te laten verbinden (disable/permit join(all)). Dit kan ook ingesteld worden in de `configuration.yaml` d.m.v.

```{}
permit_join: true
```
Hierna is het mogelijk nieuwe apparaten te laten pairen met het Zigbee netwerk. Hoe we dit doen is specifiek voor elk apparaat. Meestal is er hiervoor een knop aanwezig. Na het pairen stelt het apparaat zich voor aan de Zigbee router en wordt de netwerk-key uitgewisseld.

Aangezien elk apparaat kan pairen met de router d.m.v. een Master Key is het nodig om wanneer alle apparaten binnen het netwerk zijn geconfigureerd in te stellen dat het niet toegelaten is nieuwe nodes toe te voegen aan het Zigbee netwerk. Dit kan eenvoudig door
```{}
permit_join: false
```
in te stellen. Dit is een zeer belangrijke veiligheidsissue.

Na het toevoegen van een node is deze beschikbaar in de webinterface en wordt de data van de node in het zigbee2mqtt topic gepubliceerd op de broker.

![Zigbee2MQTT webinterface](/img/Zigbee2MQTT_web2.png)