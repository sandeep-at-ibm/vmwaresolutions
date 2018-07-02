---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Requisitos y planificación de instancias de vCenter Server

Revise los siguientes requisitos antes de solicitar sus instancias de VMware vCenter Server. Planifique la instancia en función de la ubicación del {{site.data.keyword.CloudDataCent}}, de sus requisitos de capacidad de carga de trabajo y de los requisitos de servicios adicionales.

## Requisitos de la cuenta de IBM Cloud

La cuenta de {{site.data.keyword.cloud_notm}} que utilice debe cumplir ciertos requisitos. Para obtener más información, consulte [Requisitos de la cuenta de {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilidad del centro de datos de IBM Cloud

El despliegue de vCenter Server impone requisitos estrictos en cuanto a la infraestructura física. Por lo tanto, en {{site.data.keyword.CloudDataCents_notm}} solo puede desplegar instancias que cumplan los requisitos. Están disponibles los siguientes {{site.data.keyword.CloudDataCents_notm}} para el despliegue de vCenter Server:

Tabla 1. {{site.data.keyword.CloudDataCents_notm}} disponibles para instancias de vCenter Server

| {{site.data.keyword.CloudDataCent_notm}} | Ubicación | Región | Opciones servidor |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | Amsterdam | Europa | Personalizado |
| CHE01 | Chennai | Asia-Pacífico | Personalizado |
| DAL09 | Dallas | América del Norte sur | Personalizado |
| DAL10 | Dallas | América del Norte sur | Personalizado, Pequeño, Medio, Grande |
| DAL12 | Dallas | América del Norte sur | Personalizado |
| DAL13 | Dallas | América del Norte sur | Personalizado |
| FRA02 | Frankfurt | Europa | Personalizado, Pequeño, Medio, Grande |
| FRA04 | Frankfurt | Europa | Personalizado |
| HKG02 | Hong Kong | Asia-Pacífico | Personalizado |
| LON02 | Londres | Europa | Personalizado |
| LON04 | Londres | Europa | Personalizado |
| LON06 | Londres | Europa | Personalizado, Pequeño, Medio, Grande |
| MEL01 | Melbourne | Asia-Pacífico | Personalizado |
| MEX01 | Queretaro | América del Norte sur | Personalizado |
| MIL01 | Milán | Europa | Personalizado |
| MON01 | Montreal | América del Norte este | Personalizado |
| OSL01 | Oslo | Europa | Personalizado |
| PAR01 | París | Europa | Personalizado |
| SAO01 | Sao Paulo | América del Sur | Personalizado |
| SEO01 | Seúl | Asia-Pacífico | Personalizado |
| SJC03 | San José | América del Norte oeste | Personalizado, Pequeño, Medio, Grande |
| SJC04 | San José | América del Norte oeste | Personalizado |
| SNG01 | Singapur | Asia-Pacífico | Personalizado |
| SYD01 | Sídney | Asia-Pacífico | Personalizado |
| SYD04 | Sídney | Asia-Pacífico | Personalizado |
| TOK02 | Tokio | Asia-Pacífico | Personalizado |
| TOR01 | Toronto | América del Norte este | Personalizado, Pequeño, Medio, Grande |
| WDC04 | Washington, DC | América del Norte este | Personalizado, Pequeño, Medio, Grande |
| WDC06 | Washington, DC | América del Norte este | Personalizado |
| WDC07 | Washington, DC | América del Norte este | Personalizado |

Un pequeño subconjunto de {{site.data.keyword.CloudDataCents_notm}} de IBM Cloud ofrecen las opciones preconfiguradas de servidor nativo **Pequeño**, **Medio** y **Grande**. En función de la disponibilidad y del suministro de inventario, {{site.data.keyword.CloudDataCents_notm}} puede mostrar un indicador de estado en la consola de {{site.data.keyword.vmwaresolutions_full}} que le ayudará a planificar sus despliegues.

Tabla 2. Indicadores de estado para {{site.data.keyword.CloudDataCents_notm}} cuando se solicitan instancias de vCenter Server

| Estado | Detalles del estado |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | El {{site.data.keyword.CloudDataCent_notm}} no está disponible actualmente. |
| Temporarily Out of Inventory  | El {{site.data.keyword.CloudDataCent_notm}} no ofrece disponibilidad en este momento. |
| Limited Inventory             | El {{site.data.keyword.CloudDataCent_notm}} ofrece disponibilidad limitada y es posible que el pedido no se complete. |

## Servicios para instancias de vCenter Server

Puede solicitar servicios complementarios para su instancia en función de sus necesidades, por ejemplo, la recuperación tras desastre. Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](vc_addingremovingservices.html).

<!-- ## Capacity considerations

For capacity information and considerations, see the _Bill of
Materials_ document on the [Virtual reference architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page. -->

## Enlaces relacionados

* [Visión general de vCenter Server](vc_vcenterserveroverview.html)
* [Pedido de instancias de vCenter Server](vc_orderinginstance.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server](vc_addingremovingservers.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](vc_addingremovingservices.html)
