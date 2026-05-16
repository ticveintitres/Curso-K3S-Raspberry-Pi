103 - Tu propia IA en tu Raspberry Pi

En el siguiente video explico como tener tu propia IA, con N8N y su interfaz Web dentro del cluster de K3S:

Revisaros el Video en Youtube , además os dejo el código usado: https://youtu.be/LqbrHk96w34

Os dejo las instrucciones:

PRIMERO, activar Ingress en Cilium

```
cilium upgrade --set ingressController.enabled=true --set ingressController.loadbalancerMode=shared
cilium status
```

DESPLEGAR las Aplicaciones. Copiar todos los ficheros a un directorio y dentro del directorio ejecutad este comando:

```
kubectl apply -f .
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
