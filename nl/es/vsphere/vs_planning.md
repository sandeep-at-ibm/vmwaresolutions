---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-01"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requisitos y planificación de VMware vSphere on IBM Cloud
{: #vs_planning}

Revise los siguientes requisitos antes de solicitar VMware vSphere on {{site.data.keyword.cloud}}. Planifique los clústeres de VMware vSphere en función de la ubicación del {{site.data.keyword.CloudDataCent_notm}} y de sus requisitos de capacidad de la carga de trabajo.

El usuario es el responsable de configurar el entorno y de instalar y configurar diversos componentes de VMware después de que se desplieguen los servidores ESXi. Los ejemplos siguientes son los componentes de VMware: VMware vCenter Server, VMware NSX y VMware vSAN.
{:note}

## Requisitos de la cuenta de IBM Cloud
{: #vs_planning-account-req}

La cuenta de {{site.data.keyword.cloud_notm}} que utilice debe cumplir ciertos requisitos. Para obtener más información, consulte [Requisitos para la cuenta de {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## Disponibilidad del centro de datos de IBM Cloud
{: #vs_planning-dc-availability}

El despliegue de vSphere impone requisitos estrictos en cuanto a la infraestructura física. Por lo tanto, en {{site.data.keyword.CloudDataCents_notm}} solo puede desplegar clústeres que cumplan los requisitos. Están disponibles los siguientes {{site.data.keyword.CloudDataCent_notm}} para el despliegue de vSphere.

Si selecciona un componente vSAN, la lista de ubicaciones se filtra por disponibilidad de SSD (disco en estado sólido).
{:note}

Tabla 1. {{site.data.keyword.CloudDataCents_notm}} disponibles para clústeres de vSphere

| {{site.data.keyword.CloudDataCent_notm}} | Ubicación | Región |
|:----------------------|:---------|:---------------|
| AMS03 | Amsterdam | Europa |
| CHE01 | Chennai | Asia Pacífico |
| DAL09 | Dallas | América del Norte sur |
| DAL10 | Dallas | América del Norte sur |
| DAL12 | Dallas | América del Norte sur |
| DAL13 | Dallas | América del Norte sur |
| FRA02 | Frankfurt | Europa |
| FRA04 | Frankfurt | Europa |
| FRA05 | Frankfurt | Europa |
| HKG02 | Hong Kong | Asia Pacífico |
| LON02 | Londres | Europa |
| LON04 | Londres | Europa |
| LON05 | Londres | Europa |
| LON06 | Londres | Europa |
| MEL01 | Melbourne | Asia Pacífico |
| MEX01 | Queretaro | América del Norte sur |
| MIL01 | Milán | Europa |
| MON01 | Montreal | América del Norte este |
| OSL01 | Oslo | Europa |
| PAR01 | París | Europa |
| SAO01 | Sao Paulo | América del Sur |
| SEO01 | Seúl | Asia Pacífico |
| SJC03 | San José | América del Norte oeste |
| SJC04 | San José | América del Norte oeste |
| SNG01 | Singapur | Asia Pacífico |
| SYD01 | Sídney | Asia Pacífico |
| SYD04 | Sídney | Asia Pacífico |
| TOK02 | Tokio | Asia Pacífico |
| TOK04 | Tokio | Asia Pacífico |
| TOR01 | Toronto | América del Norte este |
| WDC04 | Washington, DC | América del Norte este |
| WDC06 | Washington, DC | América del Norte este |
| WDC07 | Washington, DC | América del Norte este |

## Enlaces relacionados
{: #vs_planning-related}

* [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Escalado de clústeres existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Escalado de clústeres existentes creados fuera de la consola](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
