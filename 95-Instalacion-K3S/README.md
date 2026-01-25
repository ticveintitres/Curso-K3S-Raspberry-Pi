95 - Instalación de K3S en Raspberry Pi 5

En el siguiente video explico como instalar K3S sobre Raspberry Pi 5, tanto en modo Standalone como en modo Cluster, ambas opciones se instalan sin CNI, sin LoadBalancer y sin NetworkPolicy, para posteriormente instalar el CNI Cilium ( o el que mas os guste): https://youtu.be/gAjsqaTF0oE

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo las instrucciones:

INSTALACION STANDALONE

Si solo tienes una Raspberry Pi utiliza este comando para instalar K3S en modo Standalone

```
curl -sfL https://get.k3s.io | sh -s - --disable=traefik --disable=servicelb --disable-network-policy --flannel-backend=none
```

INSTALACION CLUSTER

Si quieres un Cluster, ejecuta este primer comando en el primer nodo a instalar, ten en cuenta, que aqui se esta declarando la versión a instalar, cambiala revisando las RELEASE NOTES en la documentación oficial:

```
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION="v1.34.1+k3s1" sh -s - --cluster-init --disable=traefik --disable=servicelb --disable-network-policy --flannel-backend=none
```

Luego hay que sacar el TOKEN en el primer nodo recién instalado:

```
cat /var/lib/rancher/k3s/server/node-token
```

Por último añadir el resto de nodos Worker al cluster usando el TOKEN

```
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION="v1.34.1+k3s1" sh -s - agent --server https://direccionIP:6443 --token aqui-se-escribe-el-token
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
