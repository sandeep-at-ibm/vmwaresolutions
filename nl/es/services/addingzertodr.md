---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Visión general de Zerto on IBM Cloud

El servicio Zerto on {{site.data.keyword.cloud}} ofrece funciones de réplica y de recuperación tras desastre, que se pueden integrar en las ofertas de despliegue para proteger y recuperar los datos del entorno virtual VMware en {{site.data.keyword.cloud_notm}}.

## Componentes del servicio Zerto on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio Zerto on {{site.data.keyword.cloud_notm}}:

* Una subred privada portátil de la infraestructura de {{site.data.keyword.cloud_notm}} para que la utilicen los dispositivos de réplica virtual de Zerto
* Una VSI (instancia de servicio virtual) de Microsoft Windows en la que se instala el servicio de réplica virtual de Zerto
* Los dispositivos de réplica virtual de Zerto que se van a desplegar y configurar en todos los servidores ESXi

**Nota**: los componentes de Zerto Virtual Manager (ZVM) se desplegarán únicamente en el clúster predeterminado.


## Enlaces relacionados

* [Acerca de {{site.data.keyword.vmwaresolutions_short}}](../vmonic/prod_overview.html)
* [Solicitud de Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Solicitud de servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Sitio web zerto.com](https://www.zerto.com){:new_window}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
