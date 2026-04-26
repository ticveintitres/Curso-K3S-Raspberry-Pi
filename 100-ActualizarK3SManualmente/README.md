100 - Actualizar K3S Manualmente

En el siguiente video explico como actualizar manualmente nuestro cluster de K3s : https://youtu.be/QLMD-rl2tww

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo las instrucciones:

EN EL CONTROLPLANE

Para ello os he dejado el values.yaml oficial modificado para que nos permite usar una IP por LoadBalancer dada por Cilium.

Realizar un Backup de ETCD:

```
k3s etcd-snapshot save --name pre-upgrade-$(date +%Y%m%d)
```

Drenar el Controlplane

```
kubectl drain nodocontrolplane --ignore-daemonsets --delete-emptydir-data
```

Actualizar el Controlplane

```
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION="v1.XX.X+k3s1" sh -s - \
  --cluster-init \
  --disable=traefik \
  --disable=servicelb \
  --disable-network-policy \
  --flannel-backend=none
```

Uncordon del Controlplane

```
kubectl uncordon nodocontrolplane
```

AHORA LOS WORKERS

Desde el controlplane ejecutar estos comandos

Drenar el Worker

```
kubectl drain nodoworker --ignore-daemonsets --delete-emptydir-data
```

Sacar token

```
cat /var/lib/rancher/k3s/server/node-token
```

Ahora vamos a cada nodo worker para actualizarlos conectandonos por SSH.

Actualizar el Worker

```
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION="v1.XX.X+k3s1" sh -s - agent \
  --server https://192.168.88.10:6443 \
  --token churretedeltoken
```

Regresar al Controlplane y ejecutar los siguientes comandos

Uncordon del Worker

```
kubectl uncordon nodoworker
```

Ver los nodos

```
kubectl get nodes
```


El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
