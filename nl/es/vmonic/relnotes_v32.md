---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas del release para V3.2
{: #relnotes_v32}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## Disponibilidad de VMware HCX para IBM Cloud
{: #relnotes_v32-HCX}

A partir del release 3.2, ahora tiene la opción de solicitar el servicio VMware HCX on {{site.data.keyword.cloud_notm}} con instancias de VMware vCenter Server. Anteriormente, sólo podía solicitar el servicio HCX on {{site.data.keyword.cloud_notm}} a través de la instancia de VMware vCenter Server con el paquete híbrido (Hybridity). La instancia de vCenter Server con el paquete híbrido (Hybridity) ya no está disponible.

Se exige un compromiso de 12 meses al hacer un pedido del servicio HCX on {{site.data.keyword.cloud_notm}}. Cuando vence el compromiso de 12 meses, puede instalar y desinstalar el servicio HCX on {{site.data.keyword.cloud_notm}} y puede añadir y eliminar hosts y clústeres sin restricciones. A partir de entonces, se realiza un cargo en su cuenta cada mes y puede cancelarlo en cualquier momento.

Para obtener más información, consulte [Visión general de VMware HCX on IBM Cloud](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations).

## Soporte para VMware vSphere 6.7 Actualización 2
{: #relnotes_v32-vsphere-v67}

Ahora tiene la opción de solicitar VMware vSphere versión 6.7 Actualización 2 con instancias de VMware vCenter Server, VMware vCenter Server con NSX-T y VMware vSphere on IBM Cloud. vSphere Enterprise Plus 6.7u2 sustituye la opción de solicitar vSphere Enterprise Plus 6.7u1 con nuevas instancias. Además, ahora las instancias de prueba de un solo nodo para migración y modernización de apps y las instancias de prueba de un solo nodo para instancias de protección de datos y recuperación tras desastre se solicitan con vSphere Enterprise Plus 6.7u2.

vSphere Enterprise Plus 6.7u2 está disponible para {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloud_notm}} Skylake, Cascade Lake y Broadwell.

Si tiene una instancia existente con vSphere Enterprise Plus 6.7u1, tiene la opción de añadir nuevos hosts con vSphere Enterprise Plus 6.7u1 o con vSphere Enterprise Plus 6.7u2. Sin embargo, añadir un nuevo host de 6,7u1 es inseguro. Se recomienda actualizar los hosts a la versión más reciente del servidor ESXi lo antes posible.
{:note}

## Soporte para Cascade Lake
{: #relnotes_v32-cascade}

A partir del release V3.2, están disponibles los siguientes nuevos modelos de CPU de {{site.data.keyword.baremetal_short_sing}} para su despliegue en instancias y clústeres con VMware vSphere 6.7 Update 2. Esto se aplica para vCenter Server, vCenter Server con NSX-T y VMware vSphere.

* Dual Intel Xeon Gold Procesador 4210 / 20 núcleos en total, 2,3 GHz
* Dual Intel Xeon Gold Procesador 5218 / 32 núcleos en total, 2,3 GHz
* Dual Intel Xeon Gold Procesador 6248 / 40 núcleos en total, 2,5 GHz

Cascade Lake {{site.data.keyword.baremetal_short}} está disponible en las regiones multizona de
{{site.data.keyword.CloudDataCents_notm}}. Para obtener más información, consulte [Visión general de regiones multizona (MZR)
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

Para obtener más información sobre los valores de {{site.data.keyword.baremetal_short_sing}}, consulte:

* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [Solicitud de instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v32-vcs}

Este release se aplica a las siguientes actualizaciones y mejoras para instancias, clústeres y hosts recién desplegados:

* VMware NSX para vSphere 6.4.5 (build 13282012)
* vSphere ESXi 6.7 EP 10 (build 6.7.0-13981272)
* vCenter Server Appliance 6.7 Actualización 2b (6.7.0.-13843469)
* Platform Services Controller 6.7 Actualización 2b (6.7.0.-13843469)

Para obtener más información, consulte [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Denominación del clúster inicial
{: #relnotes_v32-vcs-initial-cluster}

Puede especificar el nombre del clúster inicial que se va a crear al mismo tiempo que realiza el pedido de la instancia. Para obtener más información, consulte:

* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Solicitud de instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Actualizaciones de instancias de VMware vSphere
{: #relnotes_v32-vss}

Ya no es necesaria una VLAN pública al solicitar un nuevo clúster de vSphere sólo con red privada.

Para obtener más información, consulte la sección *Valores de interfaz de red* en [Solicitud de clústeres nuevos de vSphere
](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings).

## Actualizaciones de servicios complementarios
{: #relnotes_v32-services}

Este release instala las siguientes versiones de servicios en las instancias recién desplegadas:

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Actualización 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Actualización 4

### VMware vRealize Operations y vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

El servicio vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} ya está disponible para las instancias de VMware vCenter Server que se han desplegado o se han actualizado en la V3.2 o releases posteriores.

Este servicio ofrece VMware vRealize Log Insight (vRLI) integrado con vRealize Operations Manager (vROps), para ayudarle a supervisar y gestionar de forma proactiva el estado y el rendimiento de su entorno virtualizado, así como para realizar análisis de causas raíz de un problema filtrando y buscando en los registros.

Ahora puede solicitar instancias de vCenter Server con el servicio vRealize Operations y vRealize Log Insight on {{site.data.keyword.cloud_notm}} incluido, o puede añadir este servicio después a las instancias existentes desde el separador Servicios de la página de detalles de la instancia.

También puede traer sus licencias de empresa de vRealize Operations y vRealize Log Insight a la nube (por CPU u OSI) o bien puede contratar licencias desde IBM Cloud.

Para obtener más información, consulte [Visión general de VMware vRealize Operations y vRealize Log Insight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview).

## Documentación nueva y actualizada
{: #relnotes_v32-updated-doc}

* La documentación de Activity Tracker se ha actualizado. Para obtener más información, consulte [Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).

## Actualizaciones y mejoras de la interfaz de usuario
{: #relnotes_v32-ui}

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:

* Los requisitos para los nombres de instancia han cambiado. Para obtener más información, consulte el tema adecuado para el tipo de instancia que solicita.
* El formato para el nombre completo de servidor ESXi ha cambiado. Para obtener más información, consulte el tema adecuado para el tipo de instancia que solicita.
* Se han añadido ceros a la izquierda en los nombres de host y de clúster para permitir una ordenación adecuada.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
