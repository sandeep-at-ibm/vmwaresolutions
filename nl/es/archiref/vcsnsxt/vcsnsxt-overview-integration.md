---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-12"

---

# Integración, direccionamiento de IP y flujos de red

## Integración de ICP y VCS

{{site.data.keyword.cloud}} Private se instala en varias máquinas virtuales en una instancia de VCS. Dentro de la instancia de VCS, la instancia de ICP se despliega con NSX Edge Services Gateway (ESG) y Distributed Logical Router (DLR) dedicados y utiliza una VXLAN.

El ESG se configura con una regla SNAT para permitir el tráfico de salida, permitiendo la conectividad a Internet para descargar los requisitos previos de ICP y la conectividad con GitHub y Docker. Se puede utilizar un servidor proxy web para proporcionar conectividad a internet si se desea. El ESG se configura con conectividad privada para acceder a los servicios DNS y NTP. El ESG también se configura con una regla DNAT para permitir que se acceda a las vIP de ICP maestro y proxy desde la red de {{site.data.keyword.cloud_notm}} 10.x.

## Integración de IKS y VCS

Actualmente existen los siguientes modelos de integración de red IKS y VCS:
- **VLAN común**: requiere que los nodos trabajadores de IKS estén desplegados en la misma VLAN que la instancia de VCS. Esto permite que un ESG sea un igual de BGP en los nodos trabajadores.
- **strongSwan VPN**: este modelo utiliza la solución estándar de conectividad entre IKS y la empresa. Un contenedor strongSwan proporciona una pasarela VPN para el clúster que reenvía paquetes a las redes remotas a través de un túnel de IPSec a la pasarela remota. Esta pasarela remota es un ESG en la instancia de VCS. En las pasarelas, las rutas se configuran enviando todos los rangos de IP de clúster y de servicio al contenedor strongSwan y todas las direcciones VCS BYOIP al ESG. Las direcciones IP de destino para las pasarelas son la dirección IP portátil privada del servicio de equilibrador de carga que está asignado al contenedor strongSwan y la dirección IP portátil privada del ESG.
- **Rutas estáticas y NAT**.
- **BGP Peering**: BGP Peering no es una oferta predeterminada de {{site.data.keyword.cloud_notm}} y se debe solicitar y aprobar. Una vez habilitado, BGP permite a Calico vRouters y a ESG anunciar rutas a BCR.

## Integración de IKS e ICP

La integración de IKS e ICP utiliza la conectividad VPN de strongSwan con un contenedor strongSwan en ICP e IKS.

## Asignación de direcciones IP

Desde una perspectiva administrativa, la arquitectura de referencia tiene los siguientes rangos de red conceptual:
-	**Red de pod IKS**: todos los pods que se despliegan en un nodo trabajador tienen asignada una dirección IP privada en el rango 172.30.0.0/16 y se direccionan entre los nodos trabajadores. Para evitar conflictos, no utilice este rango de IP en ninguno de los nodos que se comuniquen con los nodos trabajadores. Los nodos trabajadores y los pods se pueden comunicar de forma segura en la red privada utilizando direcciones IP privadas. Sin embargo, cuando un pod se cuelga o cuando es necesario volver a crear un nodo trabajador, se asigna una nueva dirección IP privada.
-	**Red de servicio IKS**: IKS utiliza 172.21.0.0/16 para las direcciones de servicio dentro del clúster. Hay otros dos rangos de direcciones IP:
    - Público: una subred portátil pública con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}. Este rango de direcciones IP se utiliza para exponer apps a internet a través de los servicios ALB o Ingress.
    - Privado: una subred portátil privada con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}. Este rango de direcciones IP se utiliza para exponer apps a la red privada a través de los servicios ALB o Ingress.
- **Red de nodos trabajadores de IKS**: hay dos rangos de direcciones IP de red de nodo trabajador:
    - Público: una subred primaria pública con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
    - Privado: una subred primaria privada con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
-	**Red de hosts de VCS**: hay dos rangos de direcciones IP de red de hosts de VCS:
    - Público: una subred primaria pública con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
    - Privado: una subred primaria privada con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
-	**Red de ESG de VCS**: hay dos rangos de direcciones IP de red de ESG de VCS:
    - Público: una subred portátil pública con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
    - Privado: una subred portátil privada con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
-	**Red de VM de VCS**: un rango de direcciones IP de empresa que utiliza un rango de BYOIP que no entra en conflicto con ninguna subred proporcionada por {{site.data.keyword.cloud_notm}}.
-	**Red de pod de ICP**: un rango de direcciones IP de empresa que utiliza un rango de BYOIP que no entra en conflicto con ninguna subred proporcionada por {{site.data.keyword.cloud_notm}}. Los rangos de direcciones IP de pod y de servicio se pueden configurar en clúster/config.yaml.
-	**Red de servicio de ICP**: un rango de direcciones IP de empresa que utiliza un rango de BYOIP que no entra en conflicto con ninguna subred proporcionada por {{site.data.keyword.cloud_notm}}. Los rangos de direcciones IP de pod y de servicio se pueden configurar en clúster/config.yaml.
-	**Red de nodos trabajadores de ICP**: un rango de direcciones IP de empresa que utiliza un rango de BYOIP que no entra en conflicto con ninguna subred proporcionada por {{site.data.keyword.cloud_notm}}.

## Flujos de tráfico de red

A continuación se describen los siguientes flujos de tráfico:
-	De usuario externo en Internet a nivel web alojado en un contenedor en IKS.
-	De usuario externo en Internet a nivel web alojado en un contenedor en ICP.
-	De nivel web alojado en un contenedor en IKS a nivel de base de datos alojado en una VM en VCS.
-	De nivel web alojado en un contenedor en ICP a nivel de base de datos alojado en una VM en VCS.
-	De usuario de empresa en el acceso de red corporativa a una VM en VCS.

### De usuario externo en internet a nivel web alojado en un contenedor en IKS

1.	El usuario externo realiza una solicitud al nivel web utilizando el URL.
2.	Se utiliza DNS para determinar la dirección IP. Esta dirección IP es una dirección pública de {{site.data.keyword.cloud_notm}} en una subred portátil que se ha asignado al servicio ALB o Ingress.
3.	La red pública reenviará automáticamente la solicitud al nodo trabajador que aloja el servicio ALB o Ingress.
4.	El nodo trabajador reenviará la solicitud a la dirección IP del clúster interno y al número de puerto del servicio ALB o Ingress. Solo se puede acceder a esta dirección IP de clúster interno dentro del clúster.
5.	Dentro del nodo trabajador, kube-proxy direcciona la solicitud al ALB o al servicio Ingress.
6.	Si la aplicación está en el mismo nodo trabajador, se utilizan iptables para determinar qué interfaz interna se utiliza para reenviar la solicitud. Si la aplicación está en otro nodo trabajador, Calico vRouter la dirige al nodo trabajador aplicable, utilizando la encapsulación de tipo IP en IP, solo si el nodo trabajador está en otra subred.

### De usuario externo en internet a nivel web alojado en un contenedor en ICP

1.	El usuario externo realiza una solicitud al nivel web utilizando el URL.
2.	Se utiliza DNS para determinar la dirección IP. Esta dirección IP será una dirección pública de {{site.data.keyword.cloud_notm}} en una subred portátil que se ha asignado a la instancia de VCS.
3.	La red pública reenviará automáticamente la solicitud al host vSphere ESXi que aloja el ESG.
4.	El ESG reenviará la solicitud a la dirección IP del clúster interno y al número de puerto del servicio ALB o Ingress. El paquete IP se encapsulará en una trama VXLAN si el ESG y el ALB o el servicio Ingress se encuentran en distintos hosts de ESXi de vSphere. Solo se puede acceder a esta dirección IP de clúster interno dentro del clúster.
5.	Dentro del nodo trabajador, kube-proxy direcciona la solicitud al ALB o al servicio Ingress.
6.	Si la aplicación está en el mismo nodo trabajador, se utilizan iptables para determinar qué interfaz interna se utiliza para reenviar la solicitud. Si la aplicación está en otro nodo trabajador, Calico vRouter la dirige al nodo trabajador aplicable, utilizando la encapsulación de tipo IP en IP. El paquete IP en IP se encapsula en una trama VXLAN para su transporte al host vSphere ESXi donde se encuentra el nodo trabajador.

### De nivel web alojado en un contenedor en IKS a nivel de base de datos alojado en una VM en VCS

El modo en que se llenan las tablas de rutas en el ESG y en los vRouters depende del método de integración. Consulte el apartado sobre integración de IKS y VCS.
1.	El nivel web que se ejecuta en un contenedor en IKS realiza una solicitud a una base de datos que se ejecuta en una VM en la instancia de vCenter Server.
2.	Se utiliza DNS para resolver la solicitud destinada a la dirección IP de la base de datos.
3.	El contenedor envía la solicitud a Calico vRouter.
4.	El vRouter tiene su tabla de rutas, que contiene los rangos de direcciones IP alojadas en la instancia de VCS.
5.	El vRouter reenvía la solicitud, pero utiliza SNAT para cambiar la dirección IP de origen de la dirección IP del pod a la dirección IP del nodo de trabajador.
6.	El nodo trabajador que aloja el vRouter envía la solicitud al BCR.
7.	El BCR reenvía la solicitud al ESG.
8.	El ESG la reenvía al DLR.
9.	El DLR coloca la solicitud en el VXLAN necesario.
10.	La VM de base de datos recibe la solicitud.

### De nivel web alojado en un contenedor en ICP a nivel de base de datos alojado en una VM en VCS

El modo en que se llenan las tablas de rutas en el ESG y en los vRouters depende del método de integración. Consulte el apartado sobre integración de ICP y VCS.
1.	El nivel web que se ejecuta en un contenedor en ICP realiza una solicitud a una base de datos que se ejecuta en una VM en la misma instancia de VCS.
2.	Se utiliza DNS para resolver la solicitud destinada a la dirección IP de la base de datos.
3.	El contenedor envía la solicitud a Calico vRouter.
4.	El vRouter tiene su tabla de rutas, que contiene los rangos de direcciones IP alojadas en la instancia de VCS.
5.	El vRouter reenvía la solicitud, pero utiliza SNAT para cambiar la dirección IP de origen de la dirección IP del pod a la dirección IP del nodo de trabajador.
6.	El nodo trabajador que aloja el vRouter envía la solicitud al ESG.
7.	El ESG la reenvía al DLR.
8.	El DLR coloca la solicitud en el VXLAN necesario.
9.	La VM de base de datos recibe la solicitud.

### De usuario de empresa en el acceso de red corporativa a una VM en VCS

1.	Un usuario de la empresa conectado a la red interna de la empresa realiza una solicitud de un recurso situado en una VM alojada en VCS.
2.	Se utiliza DNS para determinar la dirección IP de la VM. Esta dirección IP se encuentra en una red que se ha extendido a {{site.data.keyword.cloud_notm}}.
3.	El direccionador local direcciona el tráfico al host vSphere que aloja el concentrador L2.
4.	El concentrador L2 encapsula la solicitud en un túnel seguro y la reenvía al concentrador L2 remoto alojado en {{site.data.keyword.cloud_notm}} utilizando la dirección IP de subred portátil privada asignada al dispositivo, mediante el direccionador local.
5.	La ruta local busca en su tabla de direccionamiento y detecta que la dirección IP correspondiente al concentrador L2 remoto se debe enviar a la interfaz WAN y la reenvía a través de la WAN, mediante el direccionador XCR de {{site.data.keyword.cloud_notm}}, vía BCR.
6.	El concentrador L2 recibe la solicitud y la coloca en la VXLAN que aloja la red extendida.
7.	La VM recibe la solicitud.

### Otros recursos

* [Red de {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [Documento sobre contenedores](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (descarga de PDF)
* [Blog de VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [Hoja de datos de VMware HCX on {{site.data.keyword.cloud_notm}}](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Máximos de la configuración de NSX for vSphere 6.4.3](https://configmax.vmware.com/guest)
* [Documentación de la plataforma {{site.data.keyword.cloud_notm}}](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [Servicio Kubernetes de {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/containers/container_index.html#container_index)
* [Proyecto Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)
