---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de Zerto on IBM Cloud

El servicio Zerto on {{site.data.keyword.cloud}} integra las funciones de réplica y de recuperación en caso de desastre en las ofertas de despliegue para proteger y recuperar datos en el entorno virtual de VMware en {{site.data.keyword.cloud_notm}}.

Este servicio sólo está disponible para las instancias desplegadas en la versión V1.2 o posterior. La versión actual de Zerto que se instala es la versión 6.0 actualización 3.
{:note}

## Especificaciones técnicas para Zerto on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio Zerto on {{site.data.keyword.cloud_notm}}.

Los componentes de Zerto Virtual Replication Appliance (VRA) se despliegan solo en el clúster predeterminado.
{:note}

### VSI

* Una VSI (instancia de servicio virtual) - Zerto Virtual Manager
* 2 núcleos x 2.0 GHz
* 4 GB de RAM
* Windows Server 2016 Standard Edition (64 bits)

### Almacenamiento

Disco de 100 GB (SAN)

### Redes

* Una dirección IP privada primaria
* Enlace ascendente de red privada de 1 Gbps

### Licencias y tarifas

Licencia de Zerto Replication V6.0 actualización 3

### Enlaces relacionados

* [Acerca de {{site.data.keyword.vmwaresolutions_short}}](../vmonic/prod_overview.html)
* [Solicitud de Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Solicitud de servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Sitio web zerto.com](https://www.zerto.com){:new_window}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
