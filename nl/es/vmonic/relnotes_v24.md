---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas del release para V2.4
{: #relnotes_v24}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Corrección de Spectre y Meltdown
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} proporciona parches de VMware en respuesta a las vulnerabilidades conocidas como Spectre y Meltdown (CVE-2017-5753, CVE-2017-5715 y CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Soporte multilingüístico
{: #relnotes_v24-nls}

Desde el release V2.4, Soporte multilingüístico (National Language Support, NLS) está disponible para {{site.data.keyword.vmwaresolutions_short}}.
Todas las características de la consola, incluida la documentación de usuario, están disponibles en varios idiomas.

Están soportados los siguientes idiomas, además del inglés:
* Alemán
* Español
* Francés
* Italiano
* Japonés
* Coreano
* Portugués de Brasil
* Chino simplificado
* Chino tradicional

## Soporte de CPU Skylake Xeon
{: #relnotes_v24-skylake}

A partir del release V2.4, están disponibles los siguientes modelos nuevos de CPU de servidor nativo para su despliegue para las instancias y clústeres de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} y VMware vSphere on {{site.data.keyword.cloud_notm}}:

* Procesador Dual Intel Skylake Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz
* Procesador Dual Intel Skylake Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz
* Procesador Dual Intel Skylake Xeon Gold 6140 / 36 núcleos en total, 2,3 GHz

Para obtener más información, consulte la sección *Valores de Servidor nativo* en [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings).

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v24-vcs}

### Mejora del rendimiento de Network File System
{: #relnotes_v24-nfs}

El nivel de rendimiento de 10 IOPS/GB, diseñado para los tipos de cargas de trabajo más exigentes, ya no está limitado a {{site.data.keyword.CloudDataCent_notm}} específicos, pero ahora está disponible para todo el mundo. Para obtener más información, consulte la sección *Almacenamiento* en [Visión general de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#technical-specifications-for-vcenter-server-instances).

## Actualizaciones de servicios complementarios
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

El release actual instala IBM Spectrum Protect&trade; Plus V10.1.1 Parche 1 en todas las instancias desplegadas recientemente. Para obtener más información sobre las nuevas características de IBM Spectrum Protect Plus V10.1.1 Parche 1, consulte [Actualizaciones de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

Ahora hay disponible una opción nueva para que elija entre la red pública y la red privada para interconexiones de HCX cuando solicite este servicio. Para obtener más información, consulte [Solicitud de VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering).

## Documentación nueva y actualizada
{: #relnotes_v24-new-docs}

### Documentación de arquitectura de referencia
{: #relnotes_v24-ref-archi}

El documento de arquitectura de {{site.data.keyword.vmwaresolutions_short}} ahora está disponible en la sección *Referencia* de la documentación de usuario. Para obtener más información, consulte [Visión general de la solución](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

### Documentación de servicios
{: #relnotes_v24-docs-services}

La información de servicios se reestructura y la navegación se mejora para localizar fácilmente la información relevante al solicitar servicios.

Para obtener más información, consulte los temas siguientes:

* [Solicitud de F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [Solicitud de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Solicitud de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [Solicitud de Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Solicitud de Hytrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Solicitud de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [Solicitud de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Solicitud de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## Actualizaciones y mejoras de la interfaz de usuario
{: #relnotes_v24-ui}

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:

* Los paneles Añadir clúster y Añadir servicio ahora utilizan un formato de página, con un diseño mejor organizado, que le permite completar tareas de forma más eficiente.
* La funcionalidad de la página **Recursos** se ha mejorado con características de búsqueda, paginación y clasificación. Estas mejoras le permiten localizar las instancias rápidamente.
* La página de detalles de instancias ahora utiliza un menú de navegación izquierdo, que le permite acceder a la información de la instancia de forma sencilla y rápida.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
