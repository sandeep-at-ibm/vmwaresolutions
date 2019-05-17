---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de Zerto on IBM Cloud
{: #addingzertodr}

El servicio Zerto on {{site.data.keyword.cloud}} integra las funciones de réplica y de recuperación en caso de desastre en las ofertas de despliegue para proteger y recuperar datos en el entorno virtual de VMware en {{site.data.keyword.cloud_notm}}.

Este servicio sólo está disponible para las instancias desplegadas en la versión V1.2 o posterior. La versión actual de Zerto que se instala es la versión 6.5 actualización 3.
{:note}

## Especificaciones técnicas para Zerto on IBM Cloud
{: #addingzertodr-specs}

Los siguientes componentes se solicitan y se incluyen en el servicio Zerto on {{site.data.keyword.cloud_notm}}.

Los componentes de Zerto Virtual Replication Appliance (VRA) se despliegan solo en el clúster predeterminado.
{:note}

### VSI
{: #addingzertodr-specs-vsi}

* Una VSI (instancia de servicio virtual) - Zerto Virtual Manager
* 2 núcleos x 2.0 GHz
* 4 GB de RAM
* Windows Server 2016 Standard Edition (64 bits)

### Almacenamiento
{: #addingzertodr-specs-storage}

Disco de 100 GB (SAN)

### Redes
{: #addingzertodr-specs-network}

* Una dirección IP privada primaria
* Enlace ascendente de red privada de 1 Gbps

### Licencias y tarifas
{: #addingzertodr-specs-licenses}

Licencia de Zerto Replication V6.5 actualización 3

## Enlaces relacionados
{: #addingzertodr-related}

* [Solicitud de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Solicitud de servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sitio web zerto.com](https://www.zerto.com){:new_window}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
