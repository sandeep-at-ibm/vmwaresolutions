---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-08"

subcollection: vmware-solutions


---

# Redes e infraestructura de IBM Cloud
{: #vcsiks-arch-overview-infrastructure}

## Direccionamiento virtual y reenvío
{: #vcsiks-arch-overview-infrastructure-vrf}

Las cuentas de {{site.data.keyword.cloud}} se pueden configurar como cuentas de direccionamiento virtual y reenvío (VRF). Las cuentas VRF habilitan el direccionamiento global automático entre bloques de IP de subred. Todas las cuentas con las conexiones de Direct-Link deben convertirse a, o crearse como, una cuenta de VRF.

## Direct Link
{: #vcsiks-arch-overview-infrastructure-direct-link}

{{site.data.keyword.cloud_notm}} Direct Link Connect ofrece acceso privado a su infraestructura de {{site.data.keyword.cloud_notm}} y a cualquier otra nube enlazada a su proveedor de servicios de red, a través de su {{site.data.keyword.CloudDataCent_notm}}. Esta opción es perfecta para crear conectividad multinube en un entorno único.
Conectamos a los clientes con la red {{site.data.keyword.cloud_notm}} Private, utilizando una topología de ancho de banda compartida. Al igual que sucede con todos los productos de Direct-Link, puede añadir direccionamiento global, que permite el tráfico de red privada a todas las ubicaciones de {{site.data.keyword.cloud_notm}}.

## Redes privadas virtuales
{: #vcsiks-arch-overview-infrastructure-virt-private-network}

### strongSwan VPN
{: #vcsiks-arch-overview-infrastructure-strongswan}

El servicio strongSwan IPSec VPN ofrece un canal de comunicación seguro de extremo a extremo sobre internet que se basa en la suite de protocolos Internet Protocol Security (IPSec) estándar del sector.

### Hybridity (HCX)
{: #vcsiks-arch-overview-infrastructure-hcx}

VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity) permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) de {{site.data.keyword.cloud_notm}} y al mismo sin realizar ninguna conversión ni cambio.

## Estructura física
{: #vcsiks-arch-overview-infrastructure-physical-structure}

La infraestructura física necesaria para desplegar un clúster de vCenter Server requiere la siguiente especificación mínima.

Tabla 1. Especificaciones de vCenter Server

  | Despliegue de NFS | Despliegue de VSAN
---|---|---
Número de servidores | 3 | 4
CPU | 28 núcleos 2,2 GHZ | 28 núcleos 2,2 GHZ
Memoria | 384 GB | 384 GB
Almacenamiento|Gestión: 2 TB 2 IOPS, Carga trabajo: 2 TB 4 IOPS|SSD mín: 960 GB(x2)   

Las opciones de despliegue de {{site.data.keyword.containerlong_notm}} varían en función de los requisitos del nodo trabajador.

Tabla 2. Especificaciones de {{site.data.keyword.containerlong_notm}}

  | máquina virtual | Nativa
--|---|--
Número de servidores | 3 | 3
CPU | 2 – 56 núcleos | 4 – 28 núcleos
Memoria | 4 GB - 242 GB | 32 GB - 512 GB
Almacenamiento | 100 GB |  SATA: 2 TB / SSD: 960 GB

## Estructura virtual
{: #vcsiks-arch-overview-infrastructure-virtual-structure}

![Diagrama de la estructura física del despliegue de {{site.data.keyword.containerlong_notm}} y
{{site.data.keyword.icpfull_notm}}](../../images/vcsiks-phy-ics-iks-deployment.svg "Diagrama de la estructura física del despliegue de
{{site.data.keyword.containerlong_notm}} y {{site.data.keyword.icpfull_notm}}"){: caption="Figura 1. Estructura física de los despliegues {{site.data.keyword.containerlong_notm}} e {{site.data.keyword.icpfull_notm}}" caption-side="bottom"}

Dentro de la instancia de vCenter Server, las VMS del cliente se despliegan en NSX Edge Services Gateways (ESG) y Distributed Logical Routers (DLR) dedicados.

El ESG se configura con una regla NAT de origen (SNAT) para permitir el tráfico de salida, lo que permite la conectividad a Internet para descargar los requisitos previos de {{site.data.keyword.icpfull_notm}} y para conectarse a GitHub y Docker. De forma alternativa, puede utilizar un proxy web para la conectividad de Internet. El ESG se configura para acceder a los servicios DNS y NTP a través de la red privada. La integración con la instancia de {{site.data.keyword.containerlong_notm}} está disponible a través de la red de {{site.data.keyword.cloud_notm}} entre la instancia de vCenter Server e {{site.data.keyword.containerlong_notm}}.

## Componentes de vCenter Server
{: #vcsiks-arch-overview-infrastructure-vcs-comp}

![Diagrama del entorno de vCenter Server](../../images/vcsiks-vcs-env.svg "Diagrama del entorno de vCenter Server")

### Controlador de servicios de la plataforma
{: #vcsiks-arch-overview-infrastructure-psc}

El despliegue de vCenter Server utiliza un único controlador externo de servicios de la plataforma (PSC) instalado en una subred portátil en la VLAN privada asociada a las VM de gestión. Su pasarela predeterminada se establece en el direccionador del cliente de fondo (BCR).

### vCenter Server
{: #vcsiks-arch-overview-infrastructure-vcs}

Al igual que el PSC, vCenter Server se despliega como un dispositivo.
Además, el vCenter se instala en una subred portátil en la VLAN privada que está asociada con las VM de gestión. Su pasarela predeterminada se establece en BCR.

### NSX Manager
{: #vcsiks-arch-overview-infrastructure-nsx-manager}

NSX Manager se despliega en el clúster inicial de vCenter Server. Además se asigna a NSX Manager una dirección IP desde el bloque de direcciones portátiles privadas, que está destinado a los componentes de gestión.

### Controladores NSX
{: #vcsiks-arch-overview-infrastructure-nsx-controllers}

La automatización de {{site.data.keyword.cloud_notm}} despliega tres controladores NSX dentro del clúster inicial. Se asigna a los controladores direcciones IP desde la subred portátil privada que está destinada para los componentes de gestión.

### NSX ESG / DLR
{: #vcsiks-arch-overview-infrastructure-nsx-esg}

Se despliegan pares NSX Edge Services Gateway (ESG). En todos los casos, se utiliza un par de pasarela para el tráfico de salida de los componentes de automatización que residen en la red privada. Para vCenter Server e {{site.data.keyword.icpfull_notm}}, una segunda pasarela, conocida como el borde gestionado por el cliente, se despliega y se configura con un enlace ascendente a la red pública y una interfaz asignada a la red privada.
El administrador puede configurar los componentes NSX necesarios como, por ejemplo, el direccionador lógico distribuido (DLR), los conmutadores lógicos y los cortafuegos. Para obtener más información sobre los NSX Edges que se despliegan como parte de la solución, consulte la [Guía de red de vCenter Server](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro).

En la tabla siguiente se resumen las especificaciones de {{site.data.keyword.icpfull_notm}} ESG/DLR.

Tabla 3. Especificaciones de ESG de {{site.data.keyword.icpfull_notm}}

Atributo |  Especificación
--|--
Edge Service Gateway | Dispositivo virtual
Edge tamaño grande | Número de vCPU	2
Memoria	| 1 GB
Disco	| 1000 GB en almacén de datos local

Tabla 4. Especificaciones de DLR de {{site.data.keyword.icpfull_notm}}

Atributo  |  Especificación
--|--|
Direccionador lógico distribuido |	Dispositivo virtual
Edge tamaño Compacto | Número de vCPU	1
Memoria	| 512 MB
Disco	| 1000 GB en almacén de datos local

## Componentes del servicio IBM Cloud Kubernetes
{: #vcsiks-arch-overview-infrastructure-iks-comp}

![Diagrama de componentes de {{site.data.keyword.containerlong_notm}}](../../images/vcsiks-iks-components.svg "Diagrama de componentes de {{site.data.keyword.containerlong_notm}}")

### Kubernetes maestro
{: #vcsiks-arch-overview-infrastructure-kube-master}

El nodo maestro de Kubernetes se encarga de gestionar todos los recursos de cálculo, de red y de almacenamiento del clúster. El nodo maestro de Kubernetes garantiza que las apps y servicios contenerizados se despliegan de forma equitativa en los nodos de trabajador del clúster.

###	Nodo trabajador
{: #vcsiks-arch-overview-infrastructure-worker-node}

Cada nodo trabajador es una máquina física (nativa) o una máquina virtual que se ejecuta en el hardware físico en el entorno de nube. Cuando suministra un nodo trabajador, determina los recursos que están disponibles para los contenedores que están alojados en dicho nodo trabajador. De forma automática, los nodos trabajadores se configuran con un motor de Docker gestionado por IBM, recursos de cálculo independientes, redes y un servicio de volúmenes. Las características integradas de seguridad ofrecen aislamiento, funciones de gestión de recursos y conformidad con la seguridad de los nodos trabajadores.

## Enlaces relacionados
{: #vcsiks-arch-overview-infrastructure-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
