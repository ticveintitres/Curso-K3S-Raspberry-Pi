101 - Actualizaciones Automáticas

En el siguiente video explico como actualizar de forma planificada y automática nuestro cluster de K3s : https://youtu.be/16XXwIpyVXs

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo las instrucciones:

DESDE EL CONTROLPLANE

Instalar System Upgrade Controller de K3S:

```
kubectl apply -f https://github.com/rancher/system-upgrade-controller/releases/latest/download/crd.yaml -f https://github.com/rancher/system-upgrade-controller/releases/latest/download/system-upgrade-controller.yaml
```

Crear el Plan de Actualización:

Usad el yaml que os dejo llamado upgrade-plan.yaml. Este yaml tiene el server-plan y el agent-plan, donde hay que indicar el versionado al cuál se quiere actualizar. Aplicarlo

```
kubectl apply -f upgrade-plan.yaml
```

Revisar el proceso de actualización

```
watch kubectl get nodes
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
