---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-03"

subcollection: vmware-solutions


---

# Integración, direccionamiento de IP y flujos de red
{: #vcsnsxt-overview-integration}

## Integración de IBM Cloud Private y VMware vCenter Server en IBM Cloud
{: #vcsnsxt-overview-integration-icp-vcs-integration}

{{site.data.keyword.cloud}} Private se instala en varias máquinas virtuales (VM) de una instancia de vCenter Server. Dentro de la instancia de vCenter Server, la instancia de {{site.data.keyword.icpfull_notm}} se despliega con NSX Edge Services Gateway (ESG) y Distributed Logical Router (DLR) dedicados y utiliza una VXLAN.

El ESG se configura con una regla NAT de origen (SNAT) para permitir el tráfico de salida, lo que permite la conectividad a Internet para descargar los requisitos previos de {{site.data.keyword.icpfull_notm}} y para conectarse a GitHub y Docker. De forma alternativa, puede utilizar un proxy web para la conectividad de Internet. El ESG se configura con conectividad privada para acceder a los servicios DNS y NTP. El ESG también se configura con una regla DNAT para permitir que se acceda a las vIP de {{site.data.keyword.icpfull_notm}} maestro y proxy desde la red de {{site.data.keyword.cloud_notm}} 10.x.

## Integración de IBM Cloud Kubernetes Service y vCenter Server
{: #vcsnsxt-overview-integration-iks-vcs-integration}

Actualmente existen los siguientes modelos para integrar {{site.data.keyword.containerlong_notm}} y la red de vCenter Server:
- **VLAN común**: requiere que los nodos trabajadores de {{site.data.keyword.containerlong_notm}} se desplieguen en la misma VLAN que la instancia de vCenter Server. La VLAN común permite que un ESG sea un igual de BGP en los nodos trabajadores.
- **strongSwan VPN**: este modelo utiliza la solución estándar de conectividad entre {{site.data.keyword.containerlong_notm}} y la empresa. Un contenedor strongSwan proporciona una pasarela VPN para el clúster que reenvía paquetes a las redes remotas a través de un túnel de IPSec a la pasarela remota. Esta pasarela remota es un ESG en la instancia de vCenter Server. En las pasarelas, las rutas se configuran enviando todos los rangos de IP de clúster y de servicio al contenedor strongSwan y todas las direcciones BYOIP de vCenter Server al ESG. Las direcciones IP de destino para las pasarelas son la dirección IP portátil privada del servicio de equilibrador de carga que está asignado al contenedor strongSwan y la dirección IP portátil privada del ESG.
- **Rutas estáticas y NAT**.
- **BGP Peering**: BGP Peering no es una oferta predeterminada de {{site.data.keyword.cloud_notm}} y se debe solicitar y aprobar. Una vez habilitado, BGP permite a Calico vRouters y a ESG anunciar rutas a BCR.

## Integración de IBM Cloud Kubernetes Service e IBM Cloud Private
{: #vcsnsxt-overview-integration-iks-icp-integration}

En la integración de {{site.data.keyword.containerlong_notm}} e {{site.data.keyword.icpfull_notm}} se utiliza conectividad strongSwan VPN con un contenedor strongSwan en {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}.

## Asignación de direcciones IP
{: #vcsnsxt-overview-integration-ip-address-allocation}

Desde una perspectiva administrativa, la arquitectura de referencia tiene los siguientes rangos de red conceptual:
-	**Red de pod de {{site.data.keyword.containerlong_notm}}**: todos los pods que se despliegan en un nodo trabajador tienen asignada una dirección IP privada en el rango 172.30.0.0/16 y se direccionan entre los nodos trabajadores. Para evitar conflictos, no utilice este rango de IP en ninguno de los nodos que se comuniquen con los nodos trabajadores. Los nodos trabajadores y los pods se pueden comunicar de forma segura en la red privada utilizando direcciones IP privadas. Sin embargo, cuando un pod se cuelga o cuando es necesario volver a crear un nodo trabajador, se asigna una nueva dirección IP privada.
-	**Red del servicio {{site.data.keyword.containerlong_notm}}**: {{site.data.keyword.containerlong_notm}} utiliza 172.21.0.0/16 para las direcciones de servicio del clúster. Estos son los otros dos rangos de direcciones IP:
    - Público: una subred portátil pública con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}. Este rango de direcciones IP se utiliza para exponer apps a Internet a través de los servicios ALB o Ingress.
    - Privado: una subred portátil privada con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}. Este rango de direcciones IP se utiliza para exponer apps a la red privada a través de los servicios ALB o Ingress.
- **Red de nodos trabajadores de {{site.data.keyword.containerlong_notm}}**: hay dos rangos de direcciones IP de red de nodo trabajador:
    - Público: una subred primaria pública con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
    - Privado: una subred primaria privada con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
-	**Red de hosts de vCenter Server**: hay dos rangos de direcciones IP de red de hosts de vCenter Server:
    - Público: una subred primaria pública con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
    - Privado: una subred primaria privada con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
-	**Red de ESG de vCenter Server**: hay dos rangos de direcciones IP de red de ESG de vCenter Server:
    - Público: una subred portátil pública con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
    - Privado: una subred portátil privada con un rango de direcciones IP proporcionado por {{site.data.keyword.cloud_notm}}.
-	**Red de VM de vCenter Server**: un rango de direcciones IP de empresa que utiliza un rango de BYOIP que no entra en conflicto con ninguna subred proporcionada por {{site.data.keyword.cloud_notm}}.
-	**Red de pod de {{site.data.keyword.icpfull_notm}}**: un rango de direcciones IP de empresa que utiliza un rango de BYOIP que no entra en conflicto con ninguna subred proporcionada por {{site.data.keyword.cloud_notm}}. Los rangos de direcciones IP de pod y de servicio se pueden configurar en clúster/config.yaml.
-	**Red de servicio de {{site.data.keyword.icpfull_notm}}**: un rango de direcciones IP de empresa que utiliza un rango de BYOIP que no entra en conflicto con ninguna subred proporcionada por {{site.data.keyword.cloud_notm}}. Los rangos de direcciones IP de pod y de servicio se pueden configurar en clúster/config.yaml.
-	**Red de nodos trabajadores de {{site.data.keyword.icpfull_notm}}**: un rango de direcciones IP de empresa que utiliza un rango de BYOIP que no entra en conflicto con ninguna subred proporcionada por {{site.data.keyword.cloud_notm}}.

## Flujos de tráfico de red
{: #vcsnsxt-overview-integration-net-traffic-flows}

A continuación se describen los siguientes flujos de tráfico:
-	De usuario externo en internet a nivel web alojado en un contenedor en {{site.data.keyword.containerlong_notm}}.
-	De usuario externo en internet a nivel web alojado en un contenedor en {{site.data.keyword.icpfull_notm}}.
-	De nivel web alojado en un contenedor en {{site.data.keyword.containerlong_notm}} a nivel de base de datos alojado en una VM en vCenter Server.
-	De nivel web alojado en un contenedor en {{site.data.keyword.icpfull_notm}} a nivel de base de datos alojado en una VM en vCenter Server.
-	De usuario de empresa en el acceso de red corporativa a una VM en vCenter Server.

### De usuario externo en internet a nivel web alojado en un contenedor en IBM Cloud Kubernetes Service
{: #vcsnsxt-overview-integration-web-tier-iks}

1.	El usuario externo realiza una solicitud al nivel web utilizando el URL.
2.	Se utiliza DNS para determinar la dirección IP. Esta dirección IP es una dirección pública de {{site.data.keyword.cloud_notm}} en una subred portátil que se ha asignado al servicio ALB o Ingress.
3.	La red pública reenvía automáticamente la solicitud al nodo trabajador que aloja el servicio ALB o Ingress.
4.	El nodo trabajador reenvía la solicitud a la dirección IP del clúster interno y al número de puerto del servicio ALB o Ingress. Solo se puede acceder a esta dirección IP de clúster interno dentro del clúster.
5.	Dentro del nodo trabajador, kube-proxy direcciona la solicitud al ALB o al servicio Ingress.
6.	Si la aplicación está en el mismo nodo trabajador, se utilizan iptables para determinar qué interfaz interna se utiliza para reenviar la solicitud. Si la aplicación está en otro nodo trabajador, Calico vRouter la dirige al nodo trabajador aplicable, utilizando la encapsulación de tipo IP en IP, solo si el nodo trabajador está en otra subred.

### De usuario externo en internet a nivel web alojado en un contenedor en IBM Cloud Private
{: #vcsnsxt-overview-integration-web-tier-icp}

1.	El usuario externo realiza una solicitud al nivel web utilizando el URL.
2.	Se utiliza DNS para determinar la dirección IP. Esta dirección IP es una dirección pública de {{site.data.keyword.cloud_notm}} en una subred portátil que se asigna a la instancia de vCenter Server.
3.	La red pública reenvía automáticamente la solicitud al host vSphere ESXi que aloja el ESG.
4.	El ESG reenvía la solicitud a la dirección IP del clúster interno y al número de puerto del servicio ALB o Ingress. El paquete IP se encapsula en una trama VXLAN si el ESG y el ALB o el servicio Ingress se encuentran en distintos hosts de ESXi de vSphere. Solo se puede acceder a esta dirección IP de clúster interno dentro del clúster.
5.	Dentro del nodo trabajador, kube-proxy direcciona la solicitud al ALB o al servicio Ingress.
6.	Si la aplicación está en el mismo nodo trabajador, se utilizan iptables para determinar qué interfaz interna se utiliza para reenviar la solicitud. Si la aplicación está en otro nodo trabajador, Calico vRouter la dirige al nodo trabajador aplicable, utilizando la encapsulación de tipo IP en IP. El paquete IP en IP se encapsula en una trama VXLAN para su transporte al host vSphere ESXi donde se encuentra el nodo trabajador.

### De nivel web alojado en un contenedor en IBM Cloud Kubernetes Services a nivel de base de datos alojado en una VM en vCenter Server
{: #vcsnsxt-overview-integration-iks-db-tier-vcs}

El modo en que se llenan las tablas de rutas en el ESG y en los vRouters depende del método de integración. Consulte el apartado sobre integración de {{site.data.keyword.containerlong_notm}} y vCenter Server.
1.	El nivel web que se ejecuta en un contenedor en {{site.data.keyword.containerlong_notm}} realiza una solicitud a una base de datos que se ejecuta en una VM en la instancia de vCenter Server.
2.	Se utiliza DNS para resolver la solicitud destinada a la dirección IP de la base de datos.
3.	El contenedor envía la solicitud a Calico vRouter.
4.	El vRouter tiene su tabla de rutas, que contiene los rangos de direcciones IP alojadas en la instancia de vCenter Server.
5.	El vRouter reenvía la solicitud, pero utiliza SNAT para cambiar la dirección IP de origen de la dirección IP del pod a la dirección IP del nodo de trabajador.
6.	El nodo trabajador que aloja el vRouter envía la solicitud al BCR.
7.	El BCR reenvía la solicitud al ESG.
8.	El ESG la reenvía al DLR.
9.	El DLR coloca la solicitud en el VXLAN necesario.
10.	La VM de base de datos recibe la solicitud.

### De nivel web alojado en un contenedor en IBM Cloud Private a nivel de base de datos alojado en una VM en vCenter Server
{: #vcsnsxt-overview-integration-icp-db-tier-vcs}

El modo en que se llenan las tablas de rutas en el ESG y en los vRouters depende del método de integración. Consulte el apartado sobre integración de {{site.data.keyword.icpfull_notm}} y vCenter Server.
1.	El nivel web que se ejecuta en un contenedor en {{site.data.keyword.icpfull_notm}} realiza una solicitud a una base de datos que se ejecuta en una VM en la misma instancia de vCenter Server.
2.	Se utiliza DNS para resolver la solicitud destinada a la dirección IP de la base de datos.
3.	El contenedor envía la solicitud a Calico vRouter.
4.	El vRouter tiene su tabla de rutas, que contiene los rangos de direcciones IP alojadas en la instancia de vCenter Server.
5.	El vRouter reenvía la solicitud, pero utiliza SNAT para cambiar la dirección IP de origen de la dirección IP del pod a la dirección IP del nodo de trabajador.
6.	El nodo trabajador que aloja el vRouter envía la solicitud al ESG.
7.	El ESG la reenvía al DLR.
8.	El DLR coloca la solicitud en el VXLAN necesario.
9.	La VM de base de datos recibe la solicitud.

### De usuario de empresa en el acceso de red corporativa a una VM en vCenter Server
{: #vcsnsxt-overview-integration-corporate-network-vcs}

1.	Un usuario de la empresa conectado a la red interna de la empresa realiza una solicitud de un recurso que está en una VM alojada en vCenter Server.
2.	Se utiliza DNS para determinar la dirección IP de la VM. Esta dirección IP se encuentra en una red que se ha extendido a {{site.data.keyword.cloud_notm}}.
3.	El direccionador local direcciona el tráfico al host vSphere que aloja el concentrador L2.
4.	El concentrador L2 encapsula la solicitud en un túnel seguro y la reenvía al concentrador L2 remoto alojado en {{site.data.keyword.cloud_notm}} utilizando la dirección IP de subred portátil privada asignada al dispositivo, mediante el direccionador local.
5.	La ruta local busca en su tabla de direccionamiento y detecta que la dirección IP correspondiente al concentrador L2 remoto se debe enviar a la interfaz WAN y la reenvía a través de la WAN, mediante el direccionador XCR de {{site.data.keyword.cloud_notm}}, vía BCR.
6.	El concentrador L2 recibe la solicitud y la coloca en la VXLAN que aloja la red extendida.
7.	La VM recibe la solicitud.

## Enlaces relacionados
{: #vcsnsxt-overview-integration-related}

* [Centros de datos globales de {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/data-centers/)
* [Documento sobre contenedores](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (descarga de PDF)
* [Blog de VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [Hoja de datos de VMware HCX on {{site.data.keyword.cloud_notm}}](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Máximos de la configuración de NSX for vSphere 6.4.3](https://configmax.vmware.com/guest)
* [Documentación de la plataforma {{site.data.keyword.cloud_notm}}](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started#getting-started)
* [Proyecto Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)
