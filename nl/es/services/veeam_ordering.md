---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: Veeam, Veeam configuration, order Veeam

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de Veeam on IBM Cloud
{: #veeam_ordering}

Puede solicitar el servicio de Veeam on {{site.data.keyword.cloud}} al pedir una instancia nueva incluida con el servicio o añadiendo el servicio a la instancia existente.

## Solicitud de Veeam on IBM Cloud para una instancia nueva
{: #veeam_ordering-new}

Puede solicitar una instancia nueva con Veeam on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **Veeam on IBM Cloud** en la sección **Servicios**.
* En el catálogo de {{site.data.keyword.cloud_notm}}, pulse el icono **VMware** en el panel de navegación de la izquierda y, a continuación, pulse la tarjeta **Veeam on IBM Cloud** en la sección **Servicios de VMware**. Especifique los valores del servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de Veeam on IBM Cloud para una instancia existente
{: #veeam_ordering-existing}

Puede añadir el servicio de Veeam on {{site.data.keyword.cloud_notm}} en una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* En el catálogo de {{site.data.keyword.cloud_notm}}, pulse el icono **VMware** en el panel de navegación de la izquierda y, a continuación, pulse la tarjeta **Veeam on IBM Cloud** en la sección **Servicios de VMware**. Especifique los valores del servicio y seleccione **Añadir a instancia existente**.

## Configuración de servicio de Veeam on IBM Cloud
{: #veeam_ordering-config}

Al solicitar el servicio, proporcione los valores siguientes:

### Número de máquinas virtuales para licencia
{: #veeam_ordering-config-vms}

Se necesitan como mínimo 10 máquinas virtuales para la gestión de licencias.

### Tamaño de almacenamiento
{: #veeam_ordering-config-storage-size}

La capacidad que cumpla sus necesidades de almacenamiento. Para ver más información sobre cómo calcular el tamaño de almacenamiento, consulte [Estimación de la capacidad del repositorio](https://bp.veeam.expert/repository_server/repository_planning/repository_planning_sizing){:external}.

### Rendimiento de almacenamiento
{: #veeam_ordering-config-storage-performance}

El valor de IOPS (operaciones de entrada/salida por segundo) por GB en función de los requisitos de carga de trabajo.

## Enlaces relacionados
{: #veeam_ordering-related}

* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Servicios gestionados para Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Sitio web de Veeam](https://www.veeam.com/){:external}
* [Centro de ayuda de Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:external}
