---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vSphere, vSphere component, tech specs vSphere

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de VMware vSphere on IBM Cloud
{: #vs_vsphereclusteroverview}

VMware vSphere on {{site.data.keyword.cloud}} es una plataforma de solicitud racional y optimizada para VMware. Con esta plataforma, puede crear su propio entorno de VMware alojado por IBM personalizando y solicitando el hardware compatible con VMware en función de los componentes de VMware seleccionados.

La consola de {{site.data.keyword.vmwaresolutions_short}} filtra el hardware automáticamente, en función de los componentes de VMware ha seleccionado. Por ejemplo, cuando se crea un nuevo clúster all-flash VMware vSAN, solo se presenta el hardware validado según la [Guía de compatibilidad de VMware](https://www.vmware.com/resources/compatibility/search.php){:external}. Además, se necesita un mínimo de cuatro servidores ESXi.

VMware vSphere on {{site.data.keyword.cloud_notm}} no automatiza la instalación, la configuración ni la activación de los componentes opcionales de VMware. La plataforma permite el máximo de flexibilidad para diseñar y crear su entorno VMware alojado mientras incorpora hardware compatible con VMware.

Utilice esta oferta para crear un nuevo clúster de servidores ESXi o para escalar un clúster existente de servidores ESXi en un {{site.data.keyword.CloudDataCent_notm}}. Dependiendo de los componentes de VMware que seleccione, puede empezar con un solo servidor ESXi y luego escalar el clúster más adelante cuando sea necesario.

## Especificaciones técnicas para clústeres de VMware vSphere on IBM Cloud
{: #vs_vsphereclusteroverview-specs}

Revise los componentes de VMware vSphere on {{site.data.keyword.cloud_notm}}.

La disponibilidad y los precios de las configuraciones estandarizadas de hardware pueden variar en función del {{site.data.keyword.CloudDataCent_notm}} seleccionado para el despliegue.
{:note}

### Componentes de VMware
{: #vs_vsphereclusteroverview-specs-vmware-components}

Seleccione licencias (proporcionadas por IBM o BYOL) para los siguientes componentes de VMware:
* VMware vSphere Enterprise Plus 6.7 U1 o 6.5 U2
* Los siguientes componentes de VMware son opcionales:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced o Enterprise)
   * VMware vSAN (Advanced o Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Servidor nativo
{: #vs_vsphereclusteroverview-specs-bare-metal}

Puede solicitar uno o varios {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} con una de las siguientes configuraciones:
* **Skylake**: servidores de generación Intel Skylake de 2 CPU (Intel Xeon serie 4100/5100/6100) con el modelo de CPU y el tamaño de RAM que seleccione.
* **Certificado por SAP**: servidores de generación Intel Skylake o Intel Broadwell (Intel Xeon serie 6140/E5-2690/E7-8890) con el modelo de CPU que elija.
* **Broadwell**: servidores de generación Intel Broadwell de 4 CPU (Intel Xeon serie E7-4800) con el modelo de CPU y el tamaño de RAM que seleccione.

Las opciones disponibles dependen de si ha seleccionado el componente vSAN de VMware.

Adicionalmente, las siguientes especificaciones de disco y de red:
* Enlaces ascendentes de red pública y privada de 10 Gbps
* Un controlador de disco RAID

### Redes
{: #vs_vsphereclusteroverview-specs-network}

* Una VLAN (LAN virtual) pública y dos VLAN privadas
* (Opcional) Un par de alta disponibilidad de dispositivos FortiGate Security Appliance

### Almacenamiento
{: #vs_vsphereclusteroverview-specs-storage}

Almacenamiento personalizado por el usuario para la configuración de vSAN cuando se selecciona el componente VMware vSAN:
* Opciones de disco de almacenamiento de SSD SED de 960 GB, SSD SED de 1,9 TB o SSD SED de 3,8 TB
* Opciones de cantidad de disco de 2, 4, 6 u 8

  Además, también se solicitan dos discos de memoria caché de 960 GB por host.

  Las unidades SSD (disco de estado sólido) de 3,8 TB reciben soporte cuando están disponibles a nivel general en un centro de datos.
  {:note}
* Opción de Intel Optane de alto rendimiento, que proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad. Esta opción depende del modelo de CPU.

## Especificaciones técnicas para nodos de expansión de clúster de vSphere
{: #vs_vsphereclusteroverview-expansion-node-specs}

Cada nodo de expansión de clúster de vSphere desplegará e incurrirá en cargos por los siguientes componentes en su cuenta de {{site.data.keyword.slportal}}.

### Hardware para nodos de expansión
{: #vs_vsphereclusteroverview-expansion-node-specs-hardware}

Un servidor nativo de {{site.data.keyword.cloud_notm}} con la configuración de hardware presentada en [Especificaciones técnicas para clústeres de VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

### Sistema de redes para nodos de expansión
{: #vs_vsphereclusteroverview-expansion-node-specs-network}

Un servidor nativo de {{site.data.keyword.cloud_notm}} con la configuración de red presentada en [Especificaciones técnicas para clústeres de VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

### Componentes de VMware para nodos de expansión
{: #vs_vsphereclusteroverview-expansion-node-specs-vmware-components}

* Un servidor nativo {{site.data.keyword.cloud_notm}} con VMware vSphere Enterprise Plus 6.7u1 o 6.5u2.  
* Componentes opcionales de VMware que se presentan en [Especificaciones técnicas para clústeres de VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

Debe gestionar los servidores ESXi, los componentes opcionales de VMware y el hardware adicional solicitados y distribuidos a su cuenta de {{site.data.keyword.cloud_notm}} solo desde el {{site.data.keyword.slportal}}. Después de crear un nuevo clúster en la consola de {{site.data.keyword.vmwaresolutions_short}}, puede volver a la consola y utilizar la información guardada para escalar el nuevo clúster. Para obtener más información, consulte [Escalado de clústeres existentes de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters).
{:important}

## Enlaces relacionados
{: #vs_vsphereclusteroverview-related}

* [Lista de materiales de software de VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
* [Planificación de clústeres de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [Solicitud de clústeres de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Escalado de clústeres existentes de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
