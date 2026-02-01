95 - Instalación de Cilium en Raspberry Pi 5

En el siguiente video explico como instalar Cilium en K3S sobre Raspberry Pi 5, tanto en modo Standalone como en modo Cluster: 

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo las instrucciones:

INSTALACION BINARIO CILIUM

Utilizar este comando para instalar el binario de Cilium. Haced la instalación en la maquina donde gobernais el cluster de Kubernetes o desde uno de los nodos, a ser posible el Controlplane

```
CILIUM_CLI_VERSION=$(curl -s https://raw.githubusercontent.com/cilium/cilium-cli/main/stable.txt)
CLI_ARCH=amd64
if [ "$(uname -m)" = "aarch64" ]; then CLI_ARCH=arm64; fi
curl -L --fail --remote-name-all https://github.com/cilium/cilium-cli/releases/download/${CILIUM_CLI_VERSION}/cilium-linux-${CLI_ARCH}.tar.gz{,.sha256sum}
sha256sum --check cilium-linux-${CLI_ARCH}.tar.gz.sha256sum
tar xzvfC cilium-linux-${CLI_ARCH}.tar.gz /usr/local/bin
rm cilium-linux-${CLI_ARCH}.tar.gz{,.sha256sum}
```

INSTALAR CILIUM EN KUBERNETES

```
cilium install --version 1.18.6
```

COMPROBAR EL ESTADO DE CILIUM

```
cilium status
```

INSTALAR HUBBLE CON UI

```
cilium hubble enable --ui
```

AÑADIR EL LOADBALANCER, IPAM

```
cilium upgrade --set l2announcements.enabled=true --set externalIPs.enabled=true --set kubeProxyReplacement=false
```

PRUEBA DE USO

```
kubectl apply -f pruebadeuso.yaml
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
