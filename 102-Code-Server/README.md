102 - Instalación de Code Server

En el siguiente video explico como tener tu propio servidor de Visual Studio Code en Kubernetes dentro del cluster de K3S:

Revisaros el Video en Youtube , además os dejo el código usado: https://youtu.be/DpgBXUe8CJo

Os dejo las instrucciones:

Ejecutar el código siguiente

```
kubectl apply -f code-server.yaml
```

Buscamos el nombre del pod

```
kubectl get pods -n codeserver
```

Sacamos la contraseña

```
kubectl exec -it -n codeserver NOMBRECONTENEDOR -- cat .config/code-server/config.yaml
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
