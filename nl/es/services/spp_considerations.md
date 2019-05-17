---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations}

El servicio de {{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} proporciona una solución eficiente y escalable para la protección de datos, la reutilización de datos y la recuperación de datos para entornos virtuales. Puede implementar el servicio como una solución autónoma o integrarlo con su entorno IBM Spectrum Protect para descargar copias para su almacenamiento y gestión de datos a largo plazo.

Este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en, o que se han actualizado a, V2.2 o releases posteriores. La versión actual de {{site.data.keyword.IBM}} Spectrum Protect Plus que está instalada es la V10.1.3.
{:note}

## Especificaciones técnicas para IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-specs}

Los siguientes componentes se solicitan y se incluyen en el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}:

### Recursos de vCenter
{: #spp_considerations-vcenter}

* VM de servidor que ejecuta el servidor de IBM Spectrum Protect Plus
   * Sistema operativo Linux 3.10.0-693.11.1.el7.x86_64
   * 4 núcleos x 2,0 GHz
   * 32 GB de RAM
   * Disco de 370 GB
* VM secundarias que ejecutan el servidor de IBM Spectrum Protect Plus vSnap y el proxy VADP
   * Sistema operativo Linux 3.10.0-693.11.1.el7.x86_64
   * CPU y RAM configuradas en función del tamaño de almacenamiento seleccionado y de la guía de dimensionamiento de [IBM Spectrum Protect Plus Blueprint](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)
   * Disco de 150 GB

### Almacenamiento para copias de seguridad
{: #spp_considerations-backup-storage}

Almacenamiento personalizable para copias de seguridad con las opciones siguientes:
* Número de almacenamiento de archivos: de 1 a 10
* Cada almacenamiento de archivo de resistencia: 500, 1000, 2000, 4000, 8000 o 12000 GB
* Rendimiento de almacenamiento: 0,25, 2 o 4 IOPS/GB

Consulte la publicación [Herramienta de dimensionamiento y de blueprint IBM Spectrum Protect Plus](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) para la planificación y el dimensionamiento.

### Almacenamiento para gestión
{: #spp_considerations-mgmt-storage}

Un almacenamiento de archivos de resistencia de 1000 GB, 2 IOPS/GB que aloja la máquina virtual de IBM Spectrum Protect Plus y que se ejecuta en la misma subred que el almacenamiento de copia de seguridad.

### Redes
{: #spp_considerations-network}

Dos direcciones IP privadas portátiles.

### Licencias y tarifas
{: #spp_considerations-license}

* IBM Spectrum Protect Plus (10 hasta un máximo de 1000 licencias de máquina virtual en incrementos de 10)
* Licencia de IBM Spectrum Protect Plus ofrecida mediante la consola de {{site.data.keyword.vmwaresolutions_short}} (número de VM en los paquetes de 10) o como BYOL

## Consideraciones al instalar IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-install}

Revise las siguientes consideraciones antes de instalar el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

* Asegúrese de que la CPU y la memoria del clúster predeterminado de la instancia sean suficientes para la máquina virtual de IBM Spectrum Protect Plus.
* Asegúrese de que los montajes de NFS disponibles en los servidores ESXi sean suficientes en función de la versión de los servidores ESXi.

  Las instancias que se despliegan o actualizan en la V2.2 o posteriores tienen un valor del parámetro `NFS.MaxVolumes` en VMware. Este parámetro define el número máximo de montajes de NFS de un servidor ESXi y se puede establecer en un máximo de 256 que es específico de la versión del servidor ESXi. Para obtener más información, consulte [Cómo aumentar el valor predeterminado que define el número máximo de montajes de NFS en un host ESXi/ESX](https://kb.vmware.com/s/article/2239).

  El servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} puede utilizar un máximo de 11 de los volúmenes de NFS en cada servidor de ESXi en el clúster predeterminado de la instancia. Además, el servicio crea montajes de NFS transitorios para realizar copias de seguridad y restauraciones. Por lo tanto, debe establecer el número de montajes de NFS en un mínimo de 64 para asegurarse de que el servicio pueda instalarse y funcionar correctamente.

## Consideraciones al eliminar IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-remove}

Revise las siguientes consideraciones antes de eliminar el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}:
* Asegúrese de que todas las configuraciones de trabajo de copia de seguridad se han eliminado junto con las operaciones de copia de seguridad o restauración activas.
* Cuando elimine el servicio, el almacenamiento del repositorio de copia seguridad se elimina de la VM de IBM Spectrum Protect Plus y el pedido de almacenamiento se cancela, lo cual suprime de forma permanente los datos del repositorio de copia de seguridad.
* Cuando se elimina el servicio, también se elimina el almacenamiento de copia de seguridad que se solicita para el servicio. Todas las copias de seguridad pasan a ser inaccesibles durante la eliminación del servicio.

## Enlaces relacionados
{: #spp_considerations-related}

* [Planificación del servicio preventivo de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestión de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)
* [Solicitud de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [Documentación de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
