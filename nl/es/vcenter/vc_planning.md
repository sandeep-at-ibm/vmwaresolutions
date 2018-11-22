---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# Requisitos y planificación de instancias de vCenter Server

Revise los siguientes requisitos antes de solicitar sus instancias de VMware vCenter Server. Planifique la instancia en función de la ubicación del {{site.data.keyword.CloudDataCent}}, de sus requisitos de capacidad de carga de trabajo y de los requisitos de servicio adicionales.

## Requisitos de la cuenta de IBM Cloud

La cuenta de {{site.data.keyword.cloud_notm}} que utilice debe cumplir ciertos requisitos. Para obtener más información, consulte [Requisitos para la cuenta de {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilidad del centro de datos de IBM Cloud

El despliegue de vCenter Server impone requisitos estrictos en cuanto a la infraestructura física. Por lo tanto, en {{site.data.keyword.CloudDataCents_notm}} solo puede desplegar instancias que cumplan los requisitos. Están disponibles los siguientes {{site.data.keyword.CloudDataCents_notm}} para el despliegue de vCenter Server:

Tabla 1. {{site.data.keyword.CloudDataCents_notm}} disponibles para instancias de vCenter Server

| {{site.data.keyword.CloudDataCent_notm}} | Ubicación | Región | Opciones servidor |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | Amsterdam | Europa | Skylake, Broadwell |
| CHE01 | Chennai | Asia-Pacífico | Skylake, Certificado por SAP, Broadwell |
| DAL09 | Dallas | América del Norte sur | Skylake, Certificado por SAP, Broadwell |
| DAL10 | Dallas | América del Norte sur | Skylake, Certificado por SAP, Broadwell |
| DAL12 | Dallas | América del Norte sur | Skylake, Certificado por SAP, Broadwell |
| DAL13 | Dallas | América del Norte sur | Skylake, Certificado por SAP, Broadwell |
| FRA02 | Frankfurt | Europa | Skylake, Certificado por SAP, Broadwell |
| FRA04 | Frankfurt | Europa | Skylake, Certificado por SAP, Broadwell |
| HKG02 | Hong Kong | Asia-Pacífico | Skylake, Broadwell |
| LON02 | Londres | Europa | Skylake, Broadwell |
| LON04 | Londres | Europa | Skylake, Certificado por SAP, Broadwell |
| LON06 | Londres | Europa | Skylake, Certificado por SAP, Broadwell |
| MEL01 | Melbourne | Asia-Pacífico | Skylake, Certificado por SAP, Broadwell |
| MEX01 | Queretaro | América del Norte sur | Skylake, Certificado por SAP, Broadwell |
| MIL01 | Milán | Europa | Skylake, Certificado por SAP, Broadwell |
| MON01 | Montreal | América del Norte este | Skylake, Certificado por SAP, Broadwell |
| OSL01 | Oslo | Europa | Skylake, Broadwell |
| PAR01 | París | Europa | Skylake, Broadwell |
| SAO01 | Sao Paulo | América del Sur | Skylake, Certificado por SAP, Broadwell |
| SEO01 | Seúl | Asia-Pacífico | Skylake, Certificado por SAP, Broadwell |
| SJC03 | San José | América del Norte oeste | Skylake, Broadwell |
| SJC04 | San José | América del Norte oeste | Skylake, Broadwell |
| SNG01 | Singapur | Asia-Pacífico | Skylake, Broadwell |
| SYD01 | Sídney | Asia-Pacífico | Skylake, Broadwell |
| SYD04 | Sídney | Asia-Pacífico | Skylake, Certificado por SAP, Broadwell |
| TOK02 | Tokio | Asia-Pacífico | Skylake, Certificado por SAP, Broadwell |
| TOR01 | Toronto | América del Norte este | Skylake, Certificado por SAP, Broadwell |
| WDC04 | Washington, DC | América del Norte este | Skylake, Certificado por SAP, Broadwell |
| WDC06 | Washington, DC | América del Norte este | Skylake, Certificado por SAP, Broadwell |
| WDC07 | Washington, DC | América del Norte este | Skylake, Certificado por SAP, Broadwell |

En función de la disponibilidad y del suministro de inventario, {{site.data.keyword.CloudDataCents_notm}} puede mostrar un indicador de estado en la consola de {{site.data.keyword.vmwaresolutions_short}} que le ayudará a planificar sus despliegues.

Tabla 2. Indicadores de estado para {{site.data.keyword.CloudDataCents_notm}} cuando se solicitan instancias de vCenter Server

| Estado | Detalles del estado |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | El {{site.data.keyword.CloudDataCent_notm}} no está disponible actualmente. |
| Temporarily Out of Inventory  | El {{site.data.keyword.CloudDataCent_notm}} no tiene disponibilidad actualmente. |
| Limited Inventory             | El {{site.data.keyword.CloudDataCent_notm}} ofrece disponibilidad limitada y es posible que el pedido no se complete. |

## Copia de seguridad de los componentes de gestión

El usuario es responsable de mantener y garantizar la disponibilidad de todos los componentes de instancia. Se recomienda encarecidamente que planee la copia de seguridad o la alta disponibilidad de todos los componentes de gestión. Para obtener más información, consulte [Copia de seguridad de componentes](../archiref/solution/solution_backingup.html).

## Servicios para instancias de vCenter Server

Puede solicitar servicios complementarios para su instancia en función de sus necesidades, por ejemplo, la recuperación tras desastre. Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](vc_addingremovingservices.html).

## Consideraciones de capacidad

Para obtener más información sobre las consideraciones sobre la capacidad, consulte [Capacidad de escalado](../archiref/solution/solution_scaling.html).

### Enlaces relacionados

* [Visión general de vCenter Server](vc_vcenterserveroverview.html)
* [Pedido de instancias de vCenter Server](vc_orderinginstance.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server](vc_addingremovingservers.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](vc_addingremovingservices.html)
