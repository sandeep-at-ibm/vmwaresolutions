---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de Zerto on IBM Cloud
{: #zerto_ordering}

Puede solicitar el servicio de Zerto on {{site.data.keyword.cloud}} al pedir una instancia nueva incluida con el servicio o añadiendo el servicio a la instancia existente.

## Solicitud de Zerto on IBM Cloud para una instancia nueva
{: #zerto_ordering-new}

Puede solicitar una instancia nueva con Zerto on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **Zerto on IBM Cloud** en la sección **Servicios**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **Zerto on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de Zerto on IBM Cloud para una instancia existente
{: #zerto_ordering-existing}

Puede añadir el servicio de Zerto on {{site.data.keyword.cloud_notm}} en una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **Zerto on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia existente**.

Si añade Zerto para {{site.data.keyword.cloud_notm}} a una instancia de vCenter Server que tiene un servidor ESXi que está en modalidad de mantenimiento, debe utilizar la consola de Zerto Virtual Manager (ZVM) y la dirección IP de Zerto Virtual Replication Appliance (VRA) llenada previamente para desplegar de forma manual la máquina virtual (VM) del VRA.
{:note}

## Solicitud de Zerto on IBM Cloud para instancias solo privadas
{: #zerto_ordering-private-only}

Si desea añadir Zerto on {{site.data.keyword.cloud_notm}} en una instancia que solo sea privada, asegúrese de que se cumplen los requisitos siguientes:
* Usted es responsable de configurar su propio servidor proxy para conectarse a Internet. Para obtener más información, consulte [Conectividad de red pública](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* También debe configurar la característica de llamada a servicio técnico para Zerto. Para obtener más información sobre la llamada a servicio técnico de Zerto, consulte [Informes de Zerto para entornos empresariales (llamada a servicio técnico)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window}.

## Enlaces relacionados
{: #zerto_ordering-related}

* [Visión general de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Solicitud de servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sitio web zerto.com](https://www.zerto.com){:new_window}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
