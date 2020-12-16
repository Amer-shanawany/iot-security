> # Securing Mosquitto

We starten met een key aan te maken voor de Certification Authority.

```{bash}
openssl genrsa -out mosq-ca.key 2048
```

LOCALHOST
```{bash}
openssl req -new -x509 -days 365 -key ca.key -out ca.crt
```

```{bash}
openssl genrsa -out server.key 2048
```
```{bash}
openssl req -new -key server.key -out server.csr
```

```{bash}
openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out server.crt -days 365 -sha256
```

```{bash}
openssl x509 -in server.crt -noout -text
```
CLIENT KEY AANMAKEN MET LOCALHOST


```{}
listener 8883
cafile /home/pi/ssl-cert-mosq/ca.crt
certfile /home/pi/ssl-cert-mosq/serv.crt
keyfile /home/pi/ssl-cert-mosq/serv.key
```


(https://en.wikipedia.org/wiki/Self-signed_certificate)

```{bash}
  base_topic: zigbee2mqtt
  server: 'mqtts://localhost:8883'
  ca: '/home/pi/ssl-cert-mosq/ca.crt'
  key: '/home/pi/ssl-cert-mosq/client.key'
  cert: '/home/pi/ssl-cert-mosq/client.crt'
  reject_unauthorized: false
```



http://www.steves-internet-guide.com/mqtt-security-mechanisms/

https://github.com/eclipse/mosquitto/issues/852

