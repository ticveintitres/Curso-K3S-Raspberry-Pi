99 - Victoria Metrics Basics

En el siguiente video explico como configurar una instalación simple de Victoria Metrics para nuestro cluster de k3s : https://youtu.be/3KVf24iHGC8

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

Añadir los repositorios

```
helm repo add vm https://victoriametrics.github.io/helm-charts/
helm repo update
```

Instalar Victoria Metrics

```
helm install victoria-tic23 vm/victoria-metrics-single -n monitoring -f values-victoria.yaml
```

Los ID de los DASHBOARD para Grafana son los siguientes:

- 1860
- 315
- 10229

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
