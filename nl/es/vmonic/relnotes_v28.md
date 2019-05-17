---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-08"

subcollection: vmware-solutions


---

# Notas del release para V2.8
{: #relnotes_v28}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Instancias de prueba de un solo nodo para migración y modernización de apps
{: #relnotes_v28-single-node-trial}

La prueba de un solo nodo para la migración y modernización de apps constituye una forma sencilla de realizar una prueba de {{site.data.keyword.cloud_notm}} para migrar cargas de trabajo de VMware a {{site.data.keyword.cloud_notm}} y, a continuación, modernizar las cargas de trabajo utilizando contenedores. Esta versión de prueba es una versión de {{site.data.keyword.icpfull_notm}} Hosted on VMware vCenter Server on {{site.data.keyword.cloud_notm}} que proporciona la plataforma de gestión de Kubernetes para contenedores y la plataforma VMware de un solo arrendatario que se puede gestionar utilizando las mismas herramientas que se emplean en entornos locales.

Para obtener más información, consulte [Visión general de la prueba de un solo nodo para la migración y la modernización de apps](/docs/services/vmwaresolutions?topic=vmware-solutions-cloud_modern_bundle_overview#cloud_modern_bundle_overview).

## Adición y eliminación del almacenamiento del sistema de archivos de red
{: #relnotes_v28-nfs}

A partir del release V2.8, puede añadir comparticiones de almacenamiento del sistema de archivos de red (NFS) a un clúster NFS o vSAN vCenter Server existente, así como eliminar comparticiones de archivos NFS de un clúster de vCenter Server existente.

Ahora hay disponibles las siguientes opciones de almacenamiento a nivel de archivo compartido:

* Comparticiones NFS a partir de 20 GB hasta 12 TB en incrementos de un GB
* 0,25 IOPS/GB

Para obtener más información, consulte las secciones *Adición de almacenamiento NFS a instancias de vCenter Server* y *Eliminación de almacenamiento NFS de instancias de vCenter Server* en [Expansión y contracción de la capacidad de las instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).

## Soporte del servidor Broadwell E5-2690 y E7-8890 certificado por SAP
{: #relnotes_v28-broadwell-e5-e7}

A partir del release V2.8, están disponibles los siguientes nuevos modelos de CPU de {{site.data.keyword.baremetal_short_sing}} de {{site.data.keyword.cloud_notm}} para su despliegue en instancias y clústeres de VMware vCenter Server on {{site.data.keyword.cloud_notm}} y VMware vSphere on {{site.data.keyword.cloud_notm}}:

* Procesador Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,60 GHz / 512 GB de RAM
* Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,20 GHz / 1024 GB de RAM
* Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,20 GHz / 2048 GB de RAM
* Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,20 GHz / 4096 GB de RAM

Para obtener más información, consulte la sección *Configuración de {{site.data.keyword.baremetal_short_sing}}* en:
* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Soporte del servidor Broadwell E7-4820 y E7-4850
{: #relnotes_v28-broadwell-e7}

A partir del release V2.8, están disponibles los siguientes nuevos modelos de CPU de {{site.data.keyword.baremetal_short_sing}} de {{site.data.keyword.cloud_notm}} para su despliegue en instancias y clústeres de vCenter Server, vServer Center con el paquete híbrido (Hybridity), Cloud Foundation y vSphere on {{site.data.keyword.cloud_notm}}:

* Quad Intel Xeon E7-4820 v4 / 40 núcleos en total, 2,0 GHz
* Quad Intel Xeon E7-4850 v4 / 64 núcleos en total, 2,1 GHz

Para obtener más información, consulte la sección *Configuración de {{site.data.keyword.baremetal_short_sing}}* en:
* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#bare-metal-server-settings)
* [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Platform Services Controller incorporado
{: #relnotes_v28-psc}

A partir del release V2.8, vCenter Server se despliega con un PSC (Platform Services Controller) incorporado, es decir, vCenter Server, los componentes de vCenter Server y el PSC se despliegan en una sola máquina virtual. Este cambio se aplica a todas las instancias recién desplegadas de vCenter Server, vCenter Server con el paquete híbrido (Hybridity) y NetApp.

Para las instancias que se han actualizado desde un release anterior a V2.8, el PSC no está incorporado en vCenter Server. Si desea utilizar el PSC incorporado, debe convertir el PSC externo en incorporado.

En una configuración de varios sitios en la que la instancia primaria es una instancia actualizada para la que el PSC se ha convertido manualmente de externo en incorporado, cualquier instancia secundaria de V2.8 recién desplegada tendrá PSC incorporado.

Para obtener más información, consulte la sección *Arquitectura de vCenter Server* en [Visión general de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vcenter-server-architecture).

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v28-vcs}

Este release se aplica a las siguientes actualizaciones y mejoras:

* vSphere ESXi 6.5 Actualización EP11 (compilación 6.5.0-10719125)
* vCenter Server 6.5 U2d (compilación 6.5.0-10964411)
* Platform Services Controller 6.5 U2d (compilación 6.5.0-10964411)

## Actualizaciones de instancias de VMware Cloud Foundation
{: #relnotes_v28-cf}

Este release se aplica a las siguientes actualizaciones y mejoras:

* vSphere ESXi 6.5 Actualización EP11 (compilación 6.5.0-10719125)
* vCenter Server 6.5 U2c (compilación 6.5.0-9451637)
* Platform Services Controller 6.5 U2c (compilación 6.5.0-9451637)

## Actualizaciones de servicios complementarios
{: #relnotes_v28-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v28-spp}

El release actual instala IBM Spectrum Protect™ Plus V10.1.2 en todas las instancias recién desplegadas. Para obtener más información sobre las nuevas características de IBM Spectrum Protect Plus V10.1.2, consulte [Actualizaciones de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v28-kmip}

Antes podía solicitar una instancia de Cloud Foundation o de vCenter Server con el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} incluido o podía añadir el servicio a una instancia existente de Cloud Foundation o de vCenter Server después del despliegue inicial.

A partir del release V2.8, el servicio está disponible como un servicio autónomo sin que se asocie a una instancia de VMware. Cada instancia del servicio puede dar servicio a una o varias instancias de Cloud Foundation, instancias de vCenter Server o clústeres de vSphere.

Para obtener más información, consulte [Visión general de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations).

## Documentación de arquitectura de referencia
{: #relnotes_v28-ref}

(Actualizado el 8 de febrero de 2019) Los siguientes documentos técnicos son nuevos o se han actualizado en la sección *Consulta* de la documentación del usuario:

* [Arquitectura de {{site.data.keyword.vmwaresolutions_short}} (con NSX-V y NSX-T)
](/docs/services/vmwaresolutions/services?topic=vmware-solutions-solution_overview#solution_overview)
* [Arquitectura de referencia de Caveonix RiskForesight](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-on-vcs)
* [Guía de despliegue y operaciones de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/vcshcx?topic=vmware-solutions-vcshcx-intro)

## Actualizaciones y mejoras de la interfaz de usuario
{: #relnotes_v28-ui}

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:

* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
