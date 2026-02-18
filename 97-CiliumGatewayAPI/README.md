97 - Cilium GateWay API en Raspberry Pi 5

En el siguiente video explico como configurar el Gateway API de Cilium en K3S sobre Raspberry Pi 5, tanto en modo Standalone como en modo Cluster: 

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo las instrucciones:

INSTALAR CILIUM GATEWAY API

```
kubectl apply --server-side -f https://github.com/kubernetes-sigs/gateway-api/releases/download/v1.4.1/standard-install.yaml
cilium upgrade --set gatewayAPI.enabled=true
cilium status
```

CONFIGURAR GATEWAY API

```
kubectl apply -f gatewayapi.yaml
```

CREAR SECRETOS TLS PARA LOS EJEMPLOS

```
kubectl create secret tls nginx-tls --cert nginx.crt --key nginx.key
kubectl create secret tls httpd-tls --cert httpd.crt --key httpd.key
```


LEVANTAR EJEMPLO CON NGINX

```
kubectl apply -f nginx.yaml
```

LEVANTAR EJEMPLO CON HTTPD

```
kubectl apply -f httpd.yaml
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
