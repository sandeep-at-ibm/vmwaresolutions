---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-02"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de Zerto on IBM Cloud
{: #addingzertodr}

El servicio Zerto on {{site.data.keyword.cloud}} integra las funciones de réplica y de recuperación en caso de desastre en las ofertas de despliegue para proteger y recuperar datos en el entorno virtual de VMware en {{site.data.keyword.cloud_notm}}.

La versión actual de Zerto on {{site.data.keyword.cloud_notm}} que se instala es la versión 6.5 actualización 4.
{:note}

## Antes de empezar
{: #addingzertodr-req}

* Asegúrese de que su cuenta de {{site.data.keyword.cloud_notm}} es facturable, y que esté enlazada a la
cuenta de infraestructura de {{site.data.keyword.cloud_notm}} en la que se ha desplegado la instancia. Para obtener más información,
consulte [Facturación para replicación Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).
* Este servicio sólo está disponible para las instancias desplegadas en la versión V1.2 o posterior. La versión actual de Zerto que se instala es la versión 6.5 actualización 3.

## Especificaciones técnicas para Zerto on IBM Cloud
{: #addingzertodr-specs}

Los siguientes componentes se solicitan y se incluyen en el servicio Zerto on {{site.data.keyword.cloud_notm}}.

Los componentes de Zerto Virtual Replication Appliance (VRA) se despliegan solo en el clúster predeterminado.
{:note}

### Instancias de servicio virtual
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

* VSI
  * Una dirección IP privada primaria
  * Enlace ascendente de red privada de 1 Gbps
* Dispositivos de replicación virtual (VRA)
  * Una subred portátil privada para el despliegue de VRA

### Licencias y tarifas
{: #addingzertodr-specs-licenses}

Licencia de Zerto Replication V6.5 actualización 3

## Enlaces relacionados
{: #addingzertodr-related}

* [Solicitud de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sitio web zerto.com](https://www.zerto.com){: external}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){: external}
