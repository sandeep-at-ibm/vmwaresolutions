---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de Zerto on IBM Cloud
{: #zerto_ordering}

Puede solicitar el servicio de Zerto on {{site.data.keyword.cloud}} al pedir una instancia nueva incluida con el servicio o añadiendo el servicio a la instancia existente.

## Facturación para la replicación de Zerto
{: #zerto_ordering-billing}

Las métricas de las máquinas virtuales que se replican utilizando Zerto las realizan Zerto y {{site.data.keyword.cloud_notm}}. Su factura de este uso se carga a través de una cuenta facturable de {{site.data.keyword.cloud_notm}} en lugar de una cuenta de infraestructura de {{site.data.keyword.cloud_notm}}.

Antes de solicitar Zerto on {{site.data.keyword.cloud_notm}}, asegúrese de que su cuenta de {{site.data.keyword.cloud_notm}} es facturable, y que esté enlazada a la misma cuenta de infraestructura de {{site.data.keyword.cloud_notm}} en la que se ha desplegado la instancia.

Si tiene una instalación de Zerto on {{site.data.keyword.cloud_notm}} desde la v3.0 o anterior, los costes de duplicación de la máquina virtual se siguen facturando mediante la utilización de la facturación de infraestructura de {{site.data.keyword.cloud_notm}}. Si los valores de cuentas y de facturación cumplen los requisitos listados anteriormente, puede convertir el método de facturación de Zerto en facturable.

En la consola de {{site.data.keyword.vmwaresolutions_short}}, se le solicita que se convierta del plan de infraestructura de {{site.data.keyword.cloud_notm}} en un plan facturable y que actualice la cuenta {{site.data.keyword.cloud_notm}} a una cuenta facturable, si es necesario.

* Para obtener información sobre cuentas libres y facturables, consulte [Tipos de cuenta](/docs/account?topic=account-accounts).
* Para obtener información sobre la actualización a una cuenta facturable, consulte [Actualización de su cuenta](/docs/account?topic=account-upgrading-account).
* Para obtener información sobre el enlace a sus cuentas de infraestructura de {{site.data.keyword.cloud_notm}} y {{site.data.keyword.cloud_notm}}, consulte [Cambio a IBMid y cuentas enlazadas](/docs/account?topic=account-unifyingaccounts).

## Solicitud de Zerto on IBM Cloud para una instancia nueva
{: #zerto_ordering-new}

Puede solicitar una instancia nueva con Zerto on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **Zerto on IBM Cloud** en la sección **Servicios**.
* En el catálogo de {{site.data.keyword.cloud_notm}}, pulse el icono **VMware** en el panel de navegación de la izquierda y, a continuación, pulse la tarjeta **Zerto on IBM Cloud** en la sección **Servicios de VMware**. Especifique los valores del servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de Zerto on IBM Cloud para una instancia existente
{: #zerto_ordering-existing}

Puede añadir el servicio de Zerto on {{site.data.keyword.cloud_notm}} en una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* En el catálogo de {{site.data.keyword.cloud_notm}}, pulse el icono **VMware** en el panel de navegación de la izquierda y, a continuación, pulse la tarjeta **Zerto on IBM Cloud** en la sección **Servicios de VMware**. Especifique los valores del servicio y seleccione **Añadir a instancia existente**.

Si añade Zerto on {{site.data.keyword.cloud_notm}} a una instancia de vCenter Server que tiene un servidor ESXi que está en modalidad de mantenimiento, debe utilizar la consola de Zerto Virtual Manager (ZVM) y la dirección IP de Zerto Virtual Replication Appliance (VRA) llenada previamente para desplegar de forma manual la máquina virtual (VM) del VRA.
{:note}

## Solicitud de Zerto on IBM Cloud para instancias solo privadas
{: #zerto_ordering-private-only}

Si desea añadir Zerto on {{site.data.keyword.cloud_notm}} en una instancia que solo sea privada, asegúrese de que se cumplen los requisitos siguientes:
* Usted es responsable de configurar su propio servidor proxy para conectarse a Internet. Para obtener más información, consulte [Conectividad de red pública](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* También debe configurar la característica de llamada a servicio técnico para Zerto. Para obtener más información sobre la llamada a servicio técnico de Zerto, consulte [Informes de Zerto para entornos empresariales (llamada a servicio técnico)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:external}.

## Enlaces relacionados
{: #zerto_ordering-related}

* [Visión general de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sitio web zerto.com](https://www.zerto.com){:external}
* [Documentación técnica de Zerto](https://www.zerto.com/myzerto/technical-documentation/){:external}
