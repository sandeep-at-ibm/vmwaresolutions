---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Diseño de la infraestructura de almacenamiento adjunto
{: #storage-infra-design}

{{site.data.keyword.vmwaresolutions_full}} proporciona tecnología de VMware que se despliega de forma automatizada en los {{site.data.keyword.CloudDataCents_notm}} de todo el mundo. En el conjunto de soluciones {{site.data.keyword.cloud_notm}}, el VMware vCenter Server base de la oferta {{site.data.keyword.cloud_notm}} consta de hasta 10 clústeres que contiene cada uno hasta 59 hosts vSphere, un solo controlador de servicios de la plataforma (PSC) y un dispositivo vCenter Server capaz de gestionar hasta 400 hosts y 4.000 máquinas virtuales.

La arquitectura que se presenta aquí complementa la solución de vCenter Server añadiendo almacenamiento adjunto como un dispositivo de almacenamiento compartido para el entorno. El dispositivo de almacenamiento adjunto se encuentra en el mismo {{site.data.keyword.CloudDataCent_notm}} que el despliegue de vCenter Server y consiste en un solo recurso de sistema de archivos de red (NFS) compartido o de varias exportaciones de NFS de {{site.data.keyword.cloud_notm}}.

En el siguiente gráfico se muestra la arquitectura general del almacenamiento adjunto en el despliegue de vCenter Server.

Figura 1. Arquitectura de alto nivel del almacenamiento conectado en {{site.data.keyword.cloud_notm}}

![Arquitectura de almacenamiento conectado](../solution/vcsv4radiagrams-ra-nfs-shares.svg "Arquitectura de alto nivel de almacenamiento conectado en IBM Cloud")

## Diseño de infraestructura física
{: #storage-infra-design-phys-infra-design}

La infraestructura física consta de tres componentes principales: cálculo físico, almacenamiento físico y red física. La infraestructura física incluye la red de servicios de {{site.data.keyword.cloud_notm}} y el almacenamiento físico que utiliza la infraestructura.

## Diseño de red física
{: #storage-infra-design-phys-net-design}

La red física la gestiona {{site.data.keyword.cloud_notm}}. En la siguiente sección se describe la red física que proporciona {{site.data.keyword.cloud_notm}} y su relación con el almacenamiento adjunto.

### Visión general de la red de IBM Cloud
{: #storage-infra-design-ibm-cloud-net-ovw}

La red física de {{site.data.keyword.cloud_notm}} está separada en tres redes distintas: pública, privada y de gestión. Para obtener más información sobre las redes pública, privada y de gestión, consulte [Visión general de la solución](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

Para obtener más información sobre la red de {{site.data.keyword.cloud_notm}}, consulte
[Centros de datos globales de {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/data-centers/){:new_window}.

Revise la información siguiente para ver una descripción de la red de servicios que forma parte de la red privada.

### Red de servicios privados
{: #storage-infra-design-private-net}

{{site.data.keyword.cloud_notm}} tiene una red de servicios privados que ofrece servicios comunes, como almacenamiento en bloque, almacenamiento de archivos, almacenamiento de objetos, programas de resolución de DNS y servidores NTP. Esta red privada es independiente de la red privada del cliente y permite que los entornos se conecten sin problemas a los servicios que se encuentran en {{site.data.keyword.cloud_notm}}. La red privada tiene varios niveles en la forma en que los servidores y otras infraestructuras están conectados a los conmutadores de cliente de fondo (BCS) agregados. Estos conmutadores agregados están conectados a un par de direcciones separados, como direccionadores de clientes de fondo o BCR, para redes L3. La red privada también da soporte a la capacidad de utilizar tramas Jumbo, como MTU 9000, para las conexiones de host físicas.

### VLAN
{: #storage-infra-design-vlans}

Para obtener más información acerca de las VLAN, consulte la sección _Diseño de la red física_ en el tema sobre [Diseño de la infraestructura física](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure).

## Diseño de almacenamiento físico
{: #storage-infra-design-phys-storage-design}

En la siguiente sección se describe la configuración del dispositivo de almacenamiento adjunto que se encuentra en {{site.data.keyword.cloud_notm}}. El dispositivo de almacenamiento adjunto complementa la solución de servidor vCenter existente. Como resultado, los discos conectados localmente que son internos de los hosts físicos no se muestran.

## Rendimiento del almacenamiento adjunto
{: #storage-infra-design-perf}

El almacenamiento de rendimiento y el resistente son soluciones de almacenamiento de {{site.data.keyword.cloud_notm}} diseñadas para dar soporte a aplicaciones con gran cantidad de E/S que requieren niveles de rendimiento predecibles. Este rendimiento predecible se consigue con la asignación de operaciones de entrada/salida de nivel de protocolo por segundo (IOPS) a volúmenes individuales.

Se puede solicitar un IOPS comprendido entre 100 y 96 000 con tamaños de almacenamiento que oscilan entre 20 GB y 24 TB. Los volúmenes de almacenamiento de rendimiento y resistentes están disponibles tanto para almacenamiento en bloque como para almacenamiento de archivos.

En este diseño, la solución de vCenter Server ofrece almacenamiento resistente para el almacenamiento adjunto. Como resultado, puede seleccionar y adjuntar (mediante automatización) exportaciones de NFS resistente comprendidas entre 20 GB y 24 TB. {{site.data.keyword.cloud_notm}} permite conectar un máximo de 64 hosts ESXi de vSphere a una sola exportación de NFS resistente.

La resistencia está disponible en tres niveles de rendimiento de IOPS para dar soporte a requisitos de aplicaciones variables.

Después de que se solicite un recurso compartido NFS, se puede redimensionar o volver a configurar para permitir más o menos IOPS.
{:note}

Para ver las opciones de IOPS detalladas, consulte la sección _Valores de almacenamiento_ del tema [Solicitud de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

Además de los niveles de almacenamiento, el almacenamiento resistente de {{site.data.keyword.cloud_notm}} da soporte a un amplio abanico de requisitos de aplicaciones, que incluyen instantáneas, réplica y cifrado de datos inactivos en las ubicaciones del {{site.data.keyword.CloudDataCent_notm}}.

## Enlaces relacionados
{: #storage-infra-design-related}

* [Visión general de la solución](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
