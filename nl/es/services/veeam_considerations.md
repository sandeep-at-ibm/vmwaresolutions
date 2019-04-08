---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-07"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de Veeam on IBM Cloud
{: #veeam_considerations}

El servicio Veeam on {{site.data.keyword.cloud}} se puede integrar de forma fácil y directa con sus hipervisores VMware para ayudar a la empresa a alcanzar un alto grado de disponibilidad. Este servicio proporciona objetivos de puntos de recuperación y de tiempo para sus datos y aplicaciones. Los objetivos de puntos de recuperación y de tiempo se pueden proporcionar menos de 15 minutos después de finalizar la configuración. Con este servicio, controla las copias de seguridad y las operaciones de restauración de todas las máquinas virtuales (VM) de la infraestructura directamente desde la consola de Veeam.

Este servicio sólo está disponible para las instancias desplegadas en la versión V1.8 o posterior. La versión actual de Veeam que está instalada es la 9.5u4.
{:note}

## Especificaciones técnicas para Veeam on IBM Cloud
{: #veeam_considerations-specs}

Los siguientes componentes se solicitan y se incluyen en el servicio Veeam on {{site.data.keyword.cloud_notm}}:

### VSI
{: #veeam_considerations-specs-vsi}

* VSI único con el complemento de sistema operativo Veeam Backup and Replication 9.5
* Windows Server 2016 Standard Edition (64 bits)
* 4 núcleos x 2,0 GHz
* 8 GB RAM
* Enlace ascendente de red privada de 1 Gbps
* Disco de 100 GB (SAN)

### Almacenamiento para copias de seguridad
{: #veeam_considerations-specs-storage}

* Almacenamiento iSCSI de resistencia (2000, 4000, 8000 o 12000 GB)
* Rendimiento del almacenamiento (0,25, 2 o 4 IOPS/GB)

### Redes
{: #veeam_considerations-specs-networking}

Una dirección IP privada primaria.

### Licencias y tarifas
{: #veeam_considerations-specs-licenses}

Veeam Backup and Replication 9.5 Enterprise Plus (licencia de 10, 25, 50, 100 o 200 máquinas virtuales).

### Gestión
{: #veeam_considerations-specs-mgmt}

Copias de seguridad de gestión configuradas de forma predeterminada con hasta 5 máquinas virtuales y 2000 GB de almacenamiento.

## Consideraciones al instalar Veeam on IBM Cloud
{: #veeam_considerations-install}

El repositorio del almacenamiento y del servidor Veeam están en el pod y en el centro de datos originales. Por lo tanto, el rendimiento de las operaciones de copia de seguridad para los clústeres remotos puede deteriorarse.

## Consideraciones al eliminar Veeam on IBM Cloud
{: #veeam_considerations-remove}

La eliminación del Veeam en el servicio {{site.data.keyword.cloud_notm}} detiene todas las copias de seguridad y elimina todas las anteriores. Las copias de seguridad de las VM de gestión se detienen y la supresión de copias de seguridad anteriores son irreversibles. Si las VM de gestión resultan dañadas, no se podrán restaurar.

## Enlaces relacionados
{: #veeam_considerations-related}

* [Solicitud de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Solicitud de servicios gestionados para Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sitio web de Veeam](https://www.veeam.com/){:new_window}
* [Centro de ayuda de Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
