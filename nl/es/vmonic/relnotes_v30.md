---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

keywords: release notes, what's new, version 3.0

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas del release para V3.0
{: #relnotes_v30}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Finalización del soporte para VMware Cloud Foundation on IBM Cloud
{: #relnotes_v30-vcf-eos}

Haciendo un esfuerzo por consolidar nuestras ofertas para ofrecer una mejor experiencia de cliente, la plataforma
{{site.data.keyword.vmwaresolutions_short}} ya no ofrecerá VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} a partir del 13 de mayo de 2019.

En el futuro, todos los clientes se dirigirán a VMware vCenter Server on {{site.data.keyword.cloud_notm}}, nuestra solución principal de centro de datos definido por el software de VMware en {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

Los clientes existentes que utilizan VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} recibirán ayuda para la conversión a VMware vCenter Server on {{site.data.keyword.cloud_notm}} antes de la fecha de fin de soporte, el 13 de mayo de 2019.

A partir del 13 de mayo, las capacidades de gestión de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} se congelarán en la consola de {{site.data.keyword.vmwaresolutions_short}} hasta que se hayan convertido a VMware vCenter Server on {{site.data.keyword.cloud_notm}}. Los clientes que hayan optado por no migrar ni convertir su instancia de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} a VMware vCenter Server on {{site.data.keyword.cloud_notm}} pueden acceder a sus instancias desde la consola de infraestructura de {{site.data.keyword.cloud_notm}}.

## Se ha eliminado el soporte para servidores Broadwell de 2 CPU
{: #relnotes_v30-broadwell}

A partir del release V3.0, los servidores Broadwell de 2 CPU ya no estarán disponibles para el despliegue para los nuevos clústeres e instancias de vCenter Server, vCenter Server con el paquete híbrido (Hybridity), vCenter Server con NSX-T, y vSphere on {{site.data.keyword.cloud_notm}}. Podrá seguir añadiendo servidores a clústeres existentes.

## Mejoras en el funcionamiento de NFS (Network File System)
{: #relnotes_v30-nfs}

A partir del release V3.0, puede añadir o eliminar de forma simultánea almacenamiento NFS y servidores ESXi en los clústeres que tengan el estado
**Listo para su uso**. Por ejemplo, puede añadir o eliminar un servidor ESXi en un clúster y añadir o eliminar almacenamiento NFS en otro clúster. Esto se aplica a todas las instancias de vCenter Server y vCenter Server con NSX-T.

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v30-vcs}

Este release se aplica a las siguientes actualizaciones y mejoras:

* vSphere ESXi 6.7 Actualización 1 (compilación 6.7.0-13004448)
* vSphere ESXi 6.5 Actualización 2 (build 6.5.0-13004031)
* vCenter Server Appliance 6.7 Actualización 1b (compilación 6.7.0-11727113)
* Platform Services Controller 6.7 Actualización 1b (compilación 6.7.0-11727113) 

Para obtener más información, consulte [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

El software de Windows que se solicita para los servicios de Microsoft Active Directory (AD) y DNS (sistema de nombres de dominio) se ha actualizado a Windows Server 2016 para ambas opciones de configuración: las instancias de servidor virtual (VSI) y las dos máquinas virtuales de Windows de alta disponibilidad. Para obtener más información sobre cómo seleccionar los componentes de VMware, consulte
[Lista de materiales de software para instancias de vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software).

### Mejoras en el almacenamiento vSAN
{: #relnotes_v30-vcs-vsan}

* Al utilizar almacenamiento vSAN, el número de servidores nativos que puede solicitar ahora puede ser mayor que cuatro. Esto se aplica a todas las instancias de vCenter Server, vCenter Server con el paquete híbrido (Hybridity) y vCenter Server con NSX-T.
* A partir del release V3.0, se solicita una unidad de estado sólido M.2 con su instancia de almacenamiento vSAN. Puede solicitar hasta 10 discos de capacidad o un total de 12 discos de capacidad si selecciona la opción **Alto rendimiento con Intel Optaine**.

Para obtener más información, consulte la sección *Valores de almacenamiento* en:
* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [Solicitud de instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## Actualizaciones de servicios complementarios
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

En el release actual, se ha instalado HyTrust CloudControl 5.5 en todas las instancias recién desplegadas. Para obtener más información sobre las nuevas características de HyTrust CloudControl 5.5, consulte [Novedades de HyTrust CloudControl Versión 5.5](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

El release actual instala HyTrust DataControl 4.3 en todas las instancias desplegadas recientemente. Para obtener más información sobre las nuevas características de HyTrust DataControl 4.3, consulte [Novedades de KeyControl y DataControl Versión 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

El release actual instala HyTrust KeyControl 4.3 en todas las instancias desplegadas recientemente. Para obtener más información sobre las nuevas características de HyTrust KeyControl 4.3, consulte [Novedades de KeyControl y DataControl Versión 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

El release actual instala {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 junto con
{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 en todas las instancias recién desplegadas.

Para obtener más información sobre las nuevas características de
{{site.data.keyword.cloud_notm}} Private v3.1.2, consulte [Novedades de {{site.data.keyword.cloud_notm}} Private v3.1.2](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}.
Para obtener más información sobre las nuevas características de
{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, consulte [Novedades de {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

Ahora hay disponibles dos nuevos puntos finales en Londres y EE.UU. este para el servicio de KMIP for VMware on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Configuración de servicio de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config).

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

El release actual instala IBM Spectrum Protect™ Plus V10.1.3 en todas las instancias recién desplegadas. Para obtener más información sobre las nuevas características de IBM Spectrum Protect Plus V10.1.3, consulte [Actualizaciones de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

Ahora puede añadir Zerto on {{site.data.keyword.cloud_notm}} en instancias que sean solo privadas. Si decide instalar Zerto en instancias solo privadas, debe configurar su propio servidor proxy, además de configurar la característica de llamada a servicio técnico para Zerto. Para obtener más información, consulte
[Solicitud de Zerto on {{site.data.keyword.cloud_notm}} para instancias que solo sean de red privada](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only).

## Documentación nueva y actualizada

* Ahora hay documentación disponible para ayudarle a actualizar componentes de
{{site.data.keyword.vmwaresolutions_short}} a VMware vSphere 6.7. Esta actualización es necesaria si desea seguir beneficiándose de la automatización de
{{site.data.keyword.vmwaresolutions_short}}. Para obtener más información, consulte
[Actualización del software de vSphere de vCenter Server de VMware vSphere 6.5 a 6.7](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade).
* Ahora hay documentación de referencia disponible para proporcionarle ID de usuario que {{site.data.keyword.vmwaresolutions_short}} mantiene para su uso en la automatización de {{site.data.keyword.cloud_notm}}. También tiene la posibilidad de revisar posibles mensajes que se muestran en los registros de historial de instancias. Para obtener más información, consulte
[ID de usuario de IBM](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) y
[Mensajes de historial de instancias](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages).
* Se ha añadido el permiso **Rearrancar/Controlar** a la tabla que describe los permisos necesarios para la cuenta de infraestructura de IBM Cloud. Para obtener más información, consulte [Permisos para la cuenta de infraestructura de {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-cloud-infra-acct-req#cloud-infra-acct-req-permissions).
* Hay nueva documentación de referencia disponible para las API siguientes. Para obtener más información, consulte [Referencia de API](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}.
  * Mostrar una lista de todos los mensajes de historial para una instancia de VMware vCenter Server especificada
  * Añadir almacenamientos compartidos a un clúster especificado
  * Suprimir almacenamientos NFS de un clúster especificado

## Actualizaciones y mejoras de la interfaz de usuario
{: #relnotes_v30-ui}

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:

* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
