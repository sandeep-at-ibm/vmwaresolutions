---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-29"

---

# Visión general de VMware vSphere on IBM Cloud

VMware vSphere on {{site.data.keyword.cloud}} es una plataforma de solicitud racional y optimizada para VMware, que le permite crear su propio entorno de VMware alojado en IBM personalizando y solicitando el hardware compatible con VMware que necesita en función de los componentes de VMware seleccionados.

La consola de {{site.data.keyword.vmwaresolutions_short}} filtra el hardware automáticamente, en función de los componentes de VMware ha seleccionado. Por ejemplo, cuando se crea un nuevo clúster all-flash VMware vSAN, solo se presenta el hardware validado según la [Guía de compatibilidad de VMware](https://www.vmware.com/resources/compatibility/search.php) y se necesita un mínimo de cuatro servidores ESXi.

VMware vSphere on {{site.data.keyword.cloud_notm}} no automatiza la instalación, configuración y activación de los componentes opcionales de VMware, lo que permite una máxima flexibilidad para diseñar y crear su entorno VMware alojado mientras incorpora hardware compatible con VMware.

Utilice esta oferta para crear un nuevo clúster de servidores ESXi o para escalar un clúster existente de servidores ESXi en un {{site.data.keyword.CloudDataCent_notm}}. Dependiendo de los componentes de VMware que seleccione, puede empezar con un solo servidor ESXi y luego escalar el clúster más adelante cuando sea necesario.

## Componentes de VMware vSphere on IBM Cloud

Revise los componentes de VMware vSphere on {{site.data.keyword.cloud_notm}}.

**Nota**: la disponibilidad y los precios de las configuraciones estandarizadas de hardware pueden variar en función del {{site.data.keyword.CloudDataCent_notm}} seleccionado para el despliegue.

### Componentes de VMware

Licencias (proporcionadas por IBM o BYOL) para los siguientes componentes de VMware:
* VMware vSphere Enterprise Plus 6.0u2 o 6.5u1
* Componentes opcionales de VMware:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced o Enterprise)
   * VMware vSAN (Advanced o Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Servidor nativo

Uno o varios {{site.data.keyword.baremetal_short}} de {{site.data.keyword.cloud_notm}} con el modelo de CPU y el tamaño de RAM seleccionados:
* 2-CPU Intel Broadwell generation (Intel Xeon E5-2600 v4 series)
* 2-CPU Intel Skylake generation (Intel Xeon 4100/5100/6100 series)

Las opciones disponibles dependen de si ha seleccionado el componente vSAN de VMware.

Además, las siguientes especificaciones de disco y de red:
* Enlaces ascendentes de red pública y privada de 10 Gbps
* Un controlador de disco RAID

### Redes

* Tres VLAN (LAN virtuales): una VLAN pública y dos VLAN privadas
* (Opcional) Un par de alta disponibilidad de dispositivos de seguridad FortiGate

### Almacenamiento

Almacenamiento personalizado por el usuario para la configuración de vSAN cuando se selecciona el componente VMware vSAN:
* Opciones de disco de almacenamiento: SSD SED de 960 GB, SSD SED de 1,9 TB o SSD SED de 3,8 TB
* Opciones de cantidad de discos: 2, 4, 6 u 8

**Nota:** las unidades SSD (disco de estado sólido) de 3,8 TB recibirán soporte cuando estén disponibles a nivel general en un centro de datos.

## Componentes de nodos de expansión de clúster de vSphere

Cada nodo de expansión de clúster de vSphere desplegará e incurrirá en cargos por los siguientes componentes en su cuenta de {{site.data.keyword.slportal}}.

### Hardware para nodos de expansión

Un servidor nativo IBM Cloud con la configuración de hardware que se presenta en [Componentes de VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

### Sistema de redes para nodos de expansión

Un servidor nativo IBM Cloud con la configuración de red que se presenta en [Componentes de VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

### Componentes de VMware para nodos de expansión

* Un servidor nativo IBM Cloud con VMware vSphere Enterprise Plus 6.0u2 o 6.5u1  
* Componentes opcionales de VMware que se presentan en [Componentes de VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

**Importante**: debe gestionar los servidores ESXi, los componentes opcionales de VMware y el hardware adicional solicitados y distribuidos a su cuenta de {{site.data.keyword.cloud_notm}} solo desde el {{site.data.keyword.slportal}}. Después de crear un nuevo clúster en la consola de {{site.data.keyword.vmwaresolutions_short}}, puede volver a la consola para escalar el nuevo clúster utilizando la configuración guardada. Para obtener más información, consulte [Escalado de clústeres existentes](vs_scalingexistingclusters.html).

## Enlaces relacionados

* [Lista de materiales de software de VMware vSphere](vs_bom.html)
* [Planificación de clústeres de vSphere](vs_planning.html)
* [Solicitud de clústeres de vSphere](vs_orderinginstances.html)
* [Escalado de clústeres existentes de vSphere](vs_scalingexistingclusters.html)
