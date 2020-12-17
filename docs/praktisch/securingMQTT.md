> # Securing MQTT

Er zijn verschillende manieren om MQTT te beveiligen. Een eerste manier is gebruik te maken van clientIDs. De broker kan de toegang beperken tot clients met een vooraf ingestelde prefix. In Mosquitto kan dit door in `mosquitto.conf` gebruik te maken van bv.

```{}
clientid_prefixes ABC
```

Enkel clients waarvan hun clientID start met `ABC` krijgen toegang tot de broker. Dit is een eerste beperkt security mechanisme.

Een tweede manier om de toegang de beperken is door gebruik te maken van een username en password. Ook deze instelling gebeurt in `mosquitto.conf` door middel van

```{}
allow_anonymous false
password_file PATH_TO_PASSWORD_FILE
```

De user en paswoord kunnen geëncrypteerd worden toegevoegd aan deze paswoordfile. Belangrijkste probleem is hierbij dat de user en paswoord nog steeds ongeëcrypteerd worden verzonden over MQTT, dus deze gegevens kunnen we nog steeds makkelijk achterhalen door een MQTT-packet te bekijken met een tool als bv. Wireshark.

Een message "HELLO" in topic "/DEMO" ziet er dan zo uit.

![Wireshark MQTT](/img/wiresharkMQTT.png)

Beter zou dus zijn om ook de data in het MQTT-packetje te encrypteren en zo te verzenden. Dit kan door gebruik te maken van TLS (Transport Layer Security) waarbij de data op de transport laag tussen server en applicatie versleuteld wordt. Beide partijen maken gebruik van een certificaat waarbij elkaars identiteit kan geverifiëerd worden - op deze manier kunnen man-in-the-middle-attacks voorkomen worden. Deze certificaten worden uitgegeven door een CA (Certification Authority). Bij HTTPs worden deze uitgegeven door Trusted CA's. Bij IoT toepassingen kunnen we zelf als CA optreden, en certificaten opmaken. We spreken dan over [self-signed-certificates](https://en.wikipedia.org/wiki/Self-signed_certificate)

We pakken dit praktisch aan door op de een key aan te maken voor de Certification Authority.

```{bash}
openssl genrsa -out mosq-ca.key 2048
```

![CA key](/img/ca-key.png)

Volgende stap is dan met deze key een certificaat aan te maken. Dit zullen we later gebruiken om server- en clientcertificaten aan te maken.

```{bash}
openssl req -new -x509 -days 365 -key ca.key -out ca.crt
```

![CA certificate](/img/ca-crt.png)

Hierna maken we een key aan voor de server.

```{bash}
openssl genrsa -out server.key 2048
```

![Server key](/img/serv-key.png)

Volgende stap is om een CSR (Certificate Signing Request) aan te maken dat we kunnen doorsturen naar de CA. Belangrijk is om hier als common name de naam van de server in te geven (in mijn geval localhost)

```{bash}
openssl req -new -key server.key -out server.csr
```

![Server Certificate Signing Request](/img/serv-csr.png)

Laatste stap is dan om een certificaat voor de server aan te maken.

```{bash}
openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out server.crt -days 365 -sha256
```

![Server Certificate](/img/serv-crt.png)

Willen we ons certificaat bekijken kan dit met

```{bash}
openssl x509 -in server.crt -noout -text
```

![Server Certificate](/img/serv-crt2.png)

Nu kunnen we `configuration.yaml` aanpassen om gebruik te maken van TLS. 

```{}
listener 8883
cafile /home/pi/ssl-cert-mosq/ca.crt
certfile /home/pi/ssl-cert-mosq/serv.crt
keyfile /home/pi/ssl-cert-mosq/serv.key
```

In Wireshark verschijnt een identiek bericht nu als TLSv1.2-packetje met vermelding "Encryption Application Data" en "Application Data Protocol: MQTT". De gegevens zijn dus versleuteld.

![Wireshark TLSv1.2](/img/wiresharkTLS.png)

Willen we Zigbee2MQTT gebruik laten maken van TLS moeten ook voor deze applicatie een certificaat aanmaken, nu echter als client. Dit gebeurt op net dezelfde manier als key en certificaat voor de server. Enkele zaken die we in 'configuration.yaml' van Zigbee2MQTT nu nog moeten aanpassen zijn mqtts: ipv mqtt:, poort 8883 ipv 1883 en we voegen CA.crt, client.crt en client.key toe. Reject_unauthorized zetten we op false om in te stellen dat we self-signed-certificates accepteren. 

```{bash}
  base_topic: zigbee2mqtt
  server: 'mqtts://localhost:8883'
  ca: '/home/pi/ssl-cert-mosq/ca.crt'
  key: '/home/pi/ssl-cert-mosq/client.key'
  cert: '/home/pi/ssl-cert-mosq/client.crt'
  reject_unauthorized: false
```

Starten we Zigbee2MQTT opnieuw zien we dat de service nu gebruikt maakt van encryptie.

![Zigbee2MQTT MQTTS](/img/zigbee2mqtt_status.png)
