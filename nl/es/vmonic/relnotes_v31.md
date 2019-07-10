---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: release notes, what's new, version 3.1

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas del release de V3.1
{: #relnotes_v31}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Instancia de prueba de un solo nodo para instancias de protección de datos y recuperación tras desastre
{: #relnotes_v31-dr-bundle}

La Prueba de un solo nodo de Protección de datos y Recuperación tras desastre es una forma rápida de probar {{site.data.keyword.cloud_notm}} para migrar y recuperar cargas de trabajo de VMware a {{site.data.keyword.cloud_notm}}. Esta prueba es una versión de VMware vCenter Server on IBM Cloud, una plataforma VMware de un solo arrendatario que se puede gestionar utilizando las mismas herramientas conocidas, como entornos en instalaciones locales. Esta prueba incluye los servicios Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX on {{site.data.keyword.cloud_notm}} y Zerto on {{site.data.keyword.cloud_notm}}. 

Para obtener más información, consulte [Visión general de la Prueba de un solo nodo para recuperación tras desastre](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview).

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

Ahora puede incorporarse a IBM Expert Services para trabajar de forma conjunta con su equipo interno para el despliegue, la migración y el mantenimiento de su propia solución {{site.data.keyword.cloud_notm}} de la planificación a la modernización, o de cualquier etapa intermedia. 

Puede añadir {{site.data.keyword.cloud_notm}} Expert Services a su pedido de instancia en cualquier momento solicitando una consulta desde la página **Cómo empezar**. Para obtener más información, consulte [Solicitud de {{site.data.keyword.cloud_notm}} Expert Services](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices).

## Integración con IBM Cloud Cost Estimator

Ahora puede estimar el coste de los recursos {{site.data.keyword.vmwaresolutions_short}} en la herramienta de estimación unificada proporcionada por la infraestructura de {{site.data.keyword.cloud_notm}}. Con esta función, puede guardar una instantánea de los recursos en el Catálogo de {{site.data.keyword.cloud_notm}} y almacenarla bajo un único archivo PDF que puede descargarse como referencia posteriormente. El estimador de costes no es un contrato ni un presupuesto firme; es solo una estimación del coste total. 

Para obtener más información sobre el Estimador de costes, consulte [estimación de sus costes](/docs/billing-usage?topic=billing-usage-cost). 

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v31-vcs}

Este release se aplica a las siguientes actualizaciones y mejoras para instancias, clústeres y hosts recién desplegados:

* vSphere ESXi 6.5 Actualización 2 (build 6.5.0-13635690)
* vCenter Server Appliance 6.5 Actualización 2g (build 6.5.0-13638625)

Para obtener más información, consulte [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Configuración de servidor ESXi alternativo para clústeres
{: #relnotes_v31-esxi-config}

Ahora puede añadir nuevos servidores ESXi a un clúster existente seleccionando una configuración existente o una configuración alternativa a la de los hosts existentes en el clúster. Cuando se solicitan de nuevos servidores desde la ventana **Añadir servidor**, se puede seleccionar instantáneamente una configuración existente en el clúster o elegir un nuevo	{{site.data.keyword.baremetal_short_sing}} configuración. Esto se aplica a todas las instancias de vCenter Server, vCenter Server con el paquete híbrido (Hybridity) y vCenter Server con NSX-T.

Para evitar problemas de rendimiento o estabilidad, se recomienda que los clústeres utilicen la misma configuración o una configuración similar con respecto a la CPU, la RAM y el almacenamiento. Esta funcionalidad es útil para actualizaciones de hardware dentro del mismo clúster. 

Para obtener más información, consulte [Ampliación y reducción de capacidad para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers).

### Actualizaciones para configuraciones de directiva
{: #relnotes_v31-policy-config}

La contraseña de vCenter generada para las instancias primarias de vCenter Server tiene ahora 15 caracteres de longitud y tiene las siguientes configuraciones de políticas de contraseña y bloqueo: 

* La longitud mínima para la política de contraseñas de vCenter tiene ahora 15 caracteres.
* La política de bloqueo de vCenter ahora permite un máximo de 3 intentos de inicio de sesión fallidos.
* La política de bloqueo de vCenter ahora permite un intervalo de 900 segundos entre anomalías.

La contraseña del gestor de NSX generada para las instancias primarias de vCenter Server tiene ahora 15 caracteres de longitud. Anteriormente, la contraseña generada tenía ocho caracteres de longitud. 

 Para obtener más información, consulte [Información de conformidad para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config). 

## Actualizaciones de servicios complementarios
{: #relnotes_v31-services}

### Renovación automática de licencias de HyTrust
{: #relnotes_v31-services-ht}

{{site.data.keyword.vmwaresolutions_short}} proporciona ahora soporte de renovación automática para licencias de HyTrust que tienen habilitada la función de llamada al centro de soporte. Este soporte se proporciona a partir de:

* HyTrust CloudControl 5.5.1 y posterior
* HyTrust DataControl 4.3.2 y posterior
* HyTrust KeyControl 4.3.2 y posterior

Debe completar el procedimiento para habilitar el acceso a Internet para las máquinas virtuales de HyTrust (VM) para garantizar la renovación automática de la licencia. Si no completa este procedimiento, su licencia sigue caducando anualmente. {:important}

Para obtener más información, consulte:

* [Habilitación del acceso a Internet para las VM de HyTrust CloudControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [Habilitación del acceso a Internet para las VM de HyTrust DataControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [Habilitación del acceso a Internet para las VM de HyTrust KeyControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### Veeam on IBM Cloud
{: #relnotes_v31-services-veeam}

En el release actual, se ha instalado Veeam Availability Suite 9.5 en todas las instancias recién desplegadas. Además, se realizan varias actualizaciones a los depósitos de configuración de Veeam VSIs y Veeam. Para obtener más información, consulte [Visión general de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations). 

### Zerto on IBM Cloud
{: #relnotes_v31-services-zerto}

Para las nuevas instancias desplegadas en v3.1 y posteriores, las instalaciones de Zerto on {{site.data.keyword.cloud_notm}} requieren una cuenta facturable de {{site.data.keyword.cloud_notm}}. El coste de la replicación de máquina virtual utiliza ahora un plan facturable de {{site.data.keyword.cloud_notm}} en lugar de la facturación de la infraestructura {{site.data.keyword.cloud_notm}}. 

Para pedir Zerto on {{site.data.keyword.cloud_notm}}, la cuenta de {{site.data.keyword.cloud_notm}} debe cumplir requisitos específicos. Si ya dispone de una instalación Zerto on {{site.data.keyword.cloud_notm}}, puede convertir el tipo de facturación de máquinas virtuales de Zerto a facturable. Para obtener más información, consulte [Facturación para replicación Zerto](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing). 

## Documentación nueva y actualizada
{: #relnotes_v31-updated-doc}

* Se actualizan los sucesos de gestión de la instancia Activity Tracker y los sucesos para el servicio KMIP for VMware on IBM Cloud. Para obtener más información, consulte [Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events). 
* La documentación de referencia de los ID de usuarios se ha actualizado con los ID utilizados para la instalación y configuración de servicios mediante la automatización de servicios de {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte la sección *ID de usuario de servicio* en [ID de usuarios de IBM](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids). 
* La documentación de referencia está disponible para la nueva API ``Recuperar la interfaz de red detallada de un clúster``. Para obtener más información, consulte [Referencia de API](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}.
* Los siguientes documentos técnicos son nuevos en la sección *Consulta* de la documentación del usuario: 
  * [Gestión de operaciones](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [Procedimientos operativos del Día 2](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## Actualizaciones y mejoras de la interfaz de usuario
{: #relnotes_v31-ui}

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:
* La página de detalles **Clústeres** ahora muestra el tipo de almacenamiento que utiliza el clúster. 
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
