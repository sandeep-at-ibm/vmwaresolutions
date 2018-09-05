---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Visión general de Zerto on IBM Cloud

El servicio Zerto on {{site.data.keyword.cloud}} proporciona funciones de réplica y recuperación tras desastre. Estas funciones se pueden integrar en las ofertas de despliegue para proteger y recuperar los datos del entorno virtual VMware en {{site.data.keyword.cloud_notm}}.

## Especificaciones técnicas para Zerto on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio Zerto on {{site.data.keyword.cloud_notm}}.

**Nota**: Los componentes de Zerto Virtual Manager (ZVM) se despliegan solo en el clúster predeterminado.

### VSI

* Una VSI (instancia de servicio virtual) - Zerto Virtual Manager
* 2 núcleos x 2.0 GHz
* 4 GB de RAM
* Windows Server 2012 R2 Standard Edition (64 bits)

### Almacenamiento

Disco: 100 GB (SAN)

### Redes

* Una dirección IP privada primaria
* Enlace ascendente de red privada de 1 Gbps

### Licencias y tarifas

Licencia de Zerto Replication V5.5

### Enlaces relacionados

* [Acerca de {{site.data.keyword.vmwaresolutions_short}}](../vmonic/prod_overview.html)
* [Solicitud de Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Solicitud de servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Sitio web zerto.com](https://www.zerto.com){:new_window}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
