---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Visión general del diseño
{: #design_overview}

{{site.data.keyword.vmwaresolutions_full}} proporciona la automatización para desplegar componentes de tecnología VMware en {{site.data.keyword.CloudDataCents_notm}} en todo el mundo.

## Ofertas de soluciones
{: #design_overview-offerings}

Las ofertas de soluciones incluyen los siguientes productos de VMware vSphere dentro de un clúster desplegado y configurado automáticamente:
* VMware Cloud Foundation: vSphere ESXi, Platform Services Controller (PSC), VMware vCenter Server Appliance, SDDC Manager, VMware NSX y VMware vSAN.
* VMware vCenter Server: vSphere ESXi, Platform Services Controller (PSC), vCenter Server Appliance, NSX y opcionalmente vSAN.

En este diseño, se despliega una instancia en un solo pod de un {{site.data.keyword.CloudDataCent_notm}} en el orden inicial. Después del despliegue inicial, puede ampliar el entorno virtual a otros pods dentro del mismo centro de datos o en otros centros de datos.

El diseño también permite la expansión automatizada y la contracción de la capacidad virtual dentro de una instancia de Cloud Foundation o vCenter Server.

## Componentes de VMware on IBM Cloud
{: #design_overview-comp}

Figura 1. Componentes de VMware on {{site.data.keyword.cloud_notm}}
![Componentes de VMware on {{site.data.keyword.cloud_notm}}](design_overview.svg "La solución comprende la infraestructura física, la infraestructura virtual, la administración de infraestructuras y los servicios comunes.")

## Enlaces relacionados
{: #design_overview-related}

* [Diseño de infraestructura física](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure)
* [Diseño de infraestructura virtual](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure)
* [Diseño de servicios comunes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)
* [Diseño de gestión de infraestructura](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_infrastructuremgmt)
