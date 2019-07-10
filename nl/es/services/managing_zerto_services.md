---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Zerto, request Zerto Orchestrated, Zerto managed service

subcollection: vmware-solutions


---

# Solicitud de servicios gestionados para Zerto on IBM Cloud
{: #managing_zerto_services}

El servicio Zerto on {{site.data.keyword.cloud}} proporciona funciones de réplica y recuperación tras desastre. Estas funciones se pueden integrar en las ofertas de despliegue para proteger y recuperar los datos del entorno virtual VMware en {{site.data.keyword.cloud_notm}}.

Cuando se solicitan servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}, se puede desplegar un entorno de recuperación tras desastre totalmente gestionado (DR) mediante el software Zerto DR y los IBM Resiliency Services.

Dispone de los siguientes modelos de servicios gestionados para Zerto on {{site.data.keyword.cloud_notm}}.

## IBM Orchestrated Managed Services for Zerto
{: #managing_zerto_services-orchestrated}

Este modelo resulta adecuado si utiliza la oferta Zerto on {{site.data.keyword.cloud_notm}}.

En este modelo, se suministra el servicio {{site.data.keyword.cloud_notm}} Resiliency Orchestration para Zerto on {{site.data.keyword.cloud_notm}}. Este modelo puede proteger continuamente las máquinas virtuales, sistemas operativos y datos en {{site.data.keyword.cloud_notm}}, con prueba de DR ininterrumpida, visibilidad de RTO/RPO (Recovery Time Objective/Recovery Point Objective) y capacidad de migración tras error y de restablecimiento.

IBM Resiliency Services Global Command Center gestiona todas las funciones mediante el panel de control de {{site.data.keyword.cloud_notm}} Resiliency Orchestration.

Para obtener más información, consulte [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration).

## IBM Managed Services para Zerto (sin coordinación)
{: #managing_zerto_services-without-orchestrated}

En este modelo, se suministra una solución de DR completamente gestionada para Zerto on {{site.data.keyword.cloud_notm}}. Este modelo resulta adecuado si desea un servicio gestionado solo para Zerto Virtual Replication, sin el servicio {{site.data.keyword.cloud_notm}} Resiliency Orchestration en {{site.data.keyword.cloud_notm}}.

Para obtener más información, consulte [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top).

## Procedimiento para solicitar servicios gestionados para Zerto on IBM Cloud
{: #managing_zerto_services-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Cómo comenzar** en el panel de navegación izquierdo.
2. Desplácese hacia abajo por la página y bajo **Pedido de servicios gestionados adicionales**, pulse la tarjeta **Servicios gestionados para Zerto on IBM Cloud**.
3. En la página **Zerto on IBM Cloud**, revise la descripción y las especificaciones técnicas para Zerto on {{site.data.keyword.cloud_notm}} como un servicio gestionado y, a continuación, pulse **Crear**.
4. Especifique los valores de configuración que se ajusten a sus necesidades o acepte los valores predeterminados.
5. Pulse **vCenter Server** para añadir el servicio a una de sus instancias.
6. Para añadir el servicio mientras solicita una nueva instancia, pulse **Añadir a nueva instancia** y, a continuación, continúe con el pedido de una nueva instancia de [vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance) o [vCenter Server con Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance).
7. Para añadir el servicio a una instancia existente, pulse **Añadir a instancia existente**, seleccione la instancia que desee en la lista y, a continuación, confirme que desea continuar con el pedido pulsando **Suministro**.

## Enlaces relacionados
{: #managing_zerto_services-related}

* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
