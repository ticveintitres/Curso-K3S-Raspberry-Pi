99 - Victoria Metrics Basics

En el siguiente video explico como configurar una instalación simple de Victoria Metrics para nuestro cluster de k3s : 

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo las instrucciones:

INSTALAR VICTORIA METRICS

Para ello os he dejado el values.yaml oficial modificado para que nos permite usar una IP por LoadBalancer dada por Cilium.

Crear el CiliumLoadBalancer:

```
kubectl apply -f victoriametrics-ip.yaml
```

Creación del namespace Monitoring

```
kubectl create ns monitoring
```

Para la instalación seguiremos los pasos de la documentacion oficial usando HELM.

Instalacion de Victoria Metrics usando el values.yaml modificado:

```
helm install vmagent vm/victoria-metrics-agent -n monitoring -f values-victoria.yaml
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
