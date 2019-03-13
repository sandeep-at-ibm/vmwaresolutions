---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Requisitos y planificación de instancias de Cloud Foundation
{: #sd_planning}

Revise los siguientes requisitos antes de solicitar sus instancias de VMware Cloud Foundation. Planifique la instancia en función de la ubicación del {{site.data.keyword.CloudDataCent}}, de sus requisitos de capacidad de carga de trabajo y de los requisitos de servicio.

## Requisitos de la cuenta de IBM Cloud
{: #sd_planning-account-req}

La cuenta de {{site.data.keyword.cloud_notm}} que utilice debe cumplir ciertos requisitos. Para obtener más información, consulte [Requisitos para la cuenta de {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## Disponibilidad del centro de datos de IBM Cloud
{: #sd_planning-dc-availability}

El despliegue de Cloud Foundation impone requisitos estrictos en cuanto a la infraestructura física. Por lo tanto, en {{site.data.keyword.CloudDataCents_notm}} solo puede desplegar instancias que cumplan los requisitos. Están disponibles los siguientes {{site.data.keyword.CloudDataCents_notm}} para el despliegue de Cloud Foundation:

Tabla 1. {{site.data.keyword.CloudDataCents_notm}} y configuraciones de servidor nativo de {{site.data.keyword.cloud_notm}} disponibles para instancias de Cloud Foundation

| {{site.data.keyword.CloudDataCent_notm}} | Ubicación | Región | Configuraciones del servidor |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europa | Skylake, Broadwell |
| CHE01 | Chennai | Asia Pacífico | Skylake, Broadwell |
| DAL09 | Dallas | América del Norte sur | Skylake, Broadwell |
| DAL10 | Dallas | América del Norte sur | Skylake, Broadwell |
| DAL12 | Dallas | América del Norte sur | Skylake, Broadwell |
| DAL13 | Dallas | América del Norte sur | Skylake, Broadwell |
| FRA02 | Frankfurt | Europa | Skylake, Broadwell |
| FRA04 | Frankfurt | Europa | Skylake, Broadwell |
| HKG02 | Hong Kong | Asia Pacífico | Skylake, Broadwell |
| LON02 | Londres | Europa | Skylake, Broadwell |
| LON04 | Londres | Europa | Skylake, Broadwell |
| LON06 | Londres | Europa | Skylake, Broadwell |
| MEL01 | Melbourne | Asia Pacífico | Skylake, Broadwell |
| MEX01 | Queretaro | América del Norte sur | Skylake, Broadwell |
| MIL01 | Milán | Europa | Skylake, Broadwell |
| MON01 | Montreal | América del Norte este | Skylake, Broadwell |
| OSL01 | Oslo | Europa | Skylake, Broadwell |
| PAR01 | París | Europa | Skylake, Broadwell |
| SAO01 | Sao Paulo | América del Sur | Skylake, Broadwell |
| SEO01 | Seúl | Asia Pacífico | Skylake, Broadwell |
| SJC03 | San José | América del Norte oeste | Skylake, Broadwell |
| SJC04 | San José | América del Norte oeste | Skylake, Broadwell |
| SNG01 | Singapur | Asia Pacífico | Skylake, Broadwell |
| SYD01 | Sídney | Asia Pacífico | Skylake, Broadwell |
| SYD04 | Sídney | Asia Pacífico | Skylake, Broadwell |
| TOK02 | Tokio | Asia Pacífico | Skylake, Broadwell |
| TOR01 | Toronto | América del Norte este | Skylake, Broadwell |
| WDC04 | Washington, DC | América del Norte este | Skylake, Broadwell |
| WDC06 | Washington, DC | América del Norte este | Skylake, Broadwell |
| WDC07 | Washington, DC | América del Norte este | Skylake, Broadwell |

En función de la disponibilidad y del suministro de inventario, {{site.data.keyword.CloudDataCents_notm}} puede mostrar un indicador de estado en la consola de {{site.data.keyword.vmwaresolutions_short}} que le ayudará a planificar sus despliegues.

Tabla 2. Indicadores de estado para {{site.data.keyword.CloudDataCents_notm}} cuando se solicitan instancias de Cloud Foundation

| Estado | Detalles del estado |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | El {{site.data.keyword.CloudDataCent_notm}} no está disponible actualmente. |
| Temporarily Out of Inventory  | El {{site.data.keyword.CloudDataCent_notm}} no tiene disponibilidad actualmente. |
| Limited Inventory             | El {{site.data.keyword.CloudDataCent_notm}} ofrece disponibilidad limitada y es posible que el pedido no se complete. |

## Copia de seguridad de los componentes de gestión
{: #sd_planning-backup-mgmt-components}

El usuario es responsable de mantener y garantizar la disponibilidad de todos los componentes de instancia. Se recomienda planificar la copia de seguridad o la alta disponibilidad de todos los componentes de gestión. Para obtener más información, consulte [Copia de seguridad de componentes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Servicios para instancias de Cloud Foundation
{: #sd_planning-addon-services}

Puede solicitar servicios complementarios para su instancia en función de sus necesidades, por ejemplo, la recuperación tras desastre. Para obtener más información, consulte [Adición, visualización y eliminación de servicios para instancias de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices).

## Consideraciones de capacidad
{: #sd_planning-capacity-considerations}

Para obtener más información sobre la capacidad, consulte [Capacidad de escalado](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Enlaces relacionados
{: #sd_planning-related}

* [Visión general de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
* [Pedido de instancias de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Ampliación y reducción de la capacidad para instancias de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)
