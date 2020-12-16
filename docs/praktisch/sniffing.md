> # Sniffing ZigBee Traffic

Door middel van een tweede CC2531 USB sniffer is het mogelijk om het zigbee netwerk te sniffen. Hiervoor moeten we de CC2531 flashen met geschikte firmware hiervoor. Dit wordt in de detail beschreven op deze [pagina](https://www.zigbee2mqtt.io/how_tos/how_to_sniff_zigbee_traffic.html).

## Wireshark

Als software gebruiken we Wireshark. Dit kan geïnstalleerd worden met onderstaande code.

```{bash}
cd /opt
sudo apt-get install -y libusb-1.0-0-dev wireshark
curl -L https://github.com/homewsn/whsniff/archive/v1.1.tar.gz | tar zx
cd whsniff-1.1
make
sudo make install
```