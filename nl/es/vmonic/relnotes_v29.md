---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-25"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Notas del release para V2.9
{: #relnotes_v29}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vCenter Server on IBM Cloud con NSX-T
{: #relnotes_v29-vcs-nsx-t}

Este release introduce la oferta VMware vCenter Server on {{site.data.keyword.cloud_notm}} con NSX-T como oferta de prueba de concepto o como oferta de prueba de recinto de pruebas. vCenter Server con NSX-T es una nube alojada de forma privada que le permite probar la plataforma de red de próxima generación de VMware, NSX-T.

Para obtener más información, consulte los temas siguientes:

* [Visión general de vCenter Server con NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [Solicitud de instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Finalización del soporte para VMware Cloud Foundation on IBM Cloud
{: #relnotes_v29-vcf-eos}

Para consolidar nuestras ofertas para una mejor experiencia del cliente, {{site.data.keyword.cloud_notm}} dejará de proporcionar soporte para VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} a partir del 13 de mayo de 2019.  
 
En el futuro, todos los clientes se dirigirán a VMware vCenter Server on {{site.data.keyword.cloud_notm}}, lo que ofrece más flexibilidad en las opciones de almacenamiento y licencias. 
 
Los clientes existentes que utilizan VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} recibirán ayuda para migrar a VMware vCenter Server on {{site.data.keyword.cloud_notm}} antes de la fecha de fin de soporte, el 13 de mayo de 2019.

A partir del 13 de mayo, las capacidades de gestión de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} se eliminarán de la consola de {{site.data.keyword.vmwaresolutions_short}}. A través de la consola de infraestructura de IBM Cloud se podrá acceder a las instancias que no se hayan migrado a VMware vCenter Server en {{site.data.keyword.cloud_notm}}.

El soporte de {{site.data.keyword.cloud_notm}} se pondrá en contacto con los clientes antes del 25 de marzo de 2019 para empezar la migración de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}. Para obtener más información sobre las opciones de migración para los clientes, consulte la [página de wiki de {{site.data.keyword.vmwaresolutions_short}}](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}.
 
Los clientes pueden ver su instancia existente de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} en la [consola de {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted).

## Soporte para VMware vSphere 6.7 Actualización 1
{: #relnotes_v29-vsphere}

Ahora dispone de la opción de solicitar VMware vSphere versión 6.7 Actualización 1 con las instancias de VMware vCenter Server, VMware vCenter Server con el paquete híbrido (Hybridity) y VMware vSphere on {{site.data.keyword.cloud_notm}}.

Además, las instancias de prueba de un solo nodo para la migración y la modernización de apps ahora se solicitan con vSphere Enterprise Plus 6.7u1.

vSphere Enterprise Plus 6.7u1 está disponible solo para {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} Broadwell y Skylake.

Para obtener más información, consulte las secciones _Valores de licencia_ en:

* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Finalización del soporte para la expansión de VLAN
{: #relnotes_v29-vlan}

A partir de agosto de 2019, {{site.data.keyword.vmwaresolutions_short}} ya no soportará la expansión de VLAN. Antes de finales de julio de 2019, debe convertir la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} a VRF (Virtual Routing and Forwarding) y habilitar los puntos finales de servicio para la cuenta.

Para obtener más información, consulte:

* [Visión general de Virtual Routing and Forwarding (VRF) en IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Habilite la cuenta para utilizar puntos finales de servicio mediante la CLI de IBM Cloud](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## Soporte para interfaces de programación de aplicaciones
{: #relnotes_v29-api}

Las interfaces de programación de aplicaciones (API) están ahora disponibles para desplegar instancias, suprimir instancias y añadir y eliminar servidores ESXi y clústeres.

La documentación de la API REST también está disponible en la sección *Referencia* de la documentación de usuario. Para obtener más información, consulte [API de {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/apidocs/vmware-solutions).

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v29-vcs}

Este release se aplica a las siguientes actualizaciones y mejoras:

* vSphere ESXi 6.7 Actualización 1 (build 6.7.0-11675023)
* vSphere ESXi 6.5 Actualización 2 (build 6.5.0-11925212)
* vSphere 6.7 vSwitch distribuido 6.6.0
* vSphere 6.5 vSwitch distribuido 6.5.0
* vCenter Server Appliance 6.7 U1 (build 6.7.0-10244745)
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4 (build 11197766)
* NSX-T for vSphere 2.4

Para obtener más información sobre la selección de los componentes de VMware, consulte [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Actualizaciones de centros de datos
{: #relnotes_v29-dc}

Los nuevos centros de datos siguientes están disponibles para el despliegue: **FRA-05 - Frankfurt** y **LON-05 - Londres**. Para obtener más información, consulte [Requisitos y planificación de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).

### Mejoras en el servidor ESXi
{: #relnotes_v29-vcs-esxi}

* El protocolo SSH (Secure Shell) está ahora inhabilitado para los servidores ESXi antes de la entrega de la instancia.
* A partir del release V2.9, están disponibles las siguientes operaciones de servidor ESXi:

   * Añada nuevos servidores ESXi a un clúster existente mientras los servidores están en modalidad de mantenimiento. Las máquinas virtuales no se migran a los nuevos servidores hasta que se eliminan de la modalidad de mantenimiento.
   * Añada o elimine simultáneamente servidores ESXi en varios clústeres en la instancia.

Para obtener más información, consulte [Ampliación y reducción de capacidad para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).

### Tamaño de almacenamiento de Network File System
{: #relnotes_v29-vcs-nfs}

Para los pedidos de instancias de vCenter Server, ahora puede añadir un máximo de 24 TB de almacenamiento compartido NFS (Network File System) para los niveles de rendimiento de 0,25, 2 y 4 IOPS/GB.

El nivel de rendimiento de 10 IOPS/GB sigue estando limitado a una capacidad máxima de 4 TB por compartición de archivo.
{:note}

## Actualizaciones de servicios complementarios
{: #relnotes_v29-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v29-services-caveonix}

El servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} ya está disponible para las instancias de VMware vCenter Server que se han desplegado o se han actualizado en la V2.9 o posteriores releases. Este servicio permite gestionar el riesgo cibernético y de conformidad con supervisión proactiva y controles de defensa automatizados para protegerse frente a amenazas y para cumplir las normativas gubernamentales y del sector.

Puede solicitar instancias de vCenter Server con el servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} incluido o puede añadir este servicio a las instancias existentes de vCenter Server más adelante desde el separador **Servicios** de la página de detalles de la instancia.

También puede solicitar una licencia autónoma de Caveonix RiskForesight sin asociarla a ninguna instancia de VMware para la obtención de licencias y la activación de las cargas de trabajo locales.

Para obtener más información, consulte:
* [Consideraciones sobre Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Solicitud de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Consideraciones sobre licencias de Caveonix](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [Solicitud de licencias de Caveonix](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

En el release actual, se ha instalado F5-BigIP VE V14.1.0.2 en todas las instancias recién desplegadas. Para obtener más información sobre las nuevas características de F5-BigIP VE V14.1.0.2, consulte [Nota del release: Novedades e instalación de BIG-IP 14.1.0](https://support.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window}.

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

En el release actual, se ha instalado HyTrust CloudControl 5.4.2 en todas las instancias recién desplegadas. Para obtener más información sobre las nuevas características de HyTrust CloudControl 5.4.2, consulte [Notas del release de HyTrust CloudControl Versión 5.4.2](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

Ahora hay disponibles dos nuevos puntos finales en Sídney para el servicio de KMIP for VMware on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Configuración de servicio de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config).

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

En el release actual, se ha instalado Veeam Backup and Replication 9.5 Actualización 4 en todas las instancias recién desplegadas. Para obtener más información sobre las nuevas características de Veeam 9.5u4, consulte [Información del release para Veeam Backup and Replication 9.5 Actualización 4](https://www.veeam.com/kb2878){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

En el release actual, se ha instalado Zerto Virtual Replication 6.5 actualización 3 en todas las instancias recién desplegadas. Para obtener más información sobre las nuevas características de Zerto Virtual Replication 6.5 actualización 3, consulte [Notas del release para Zerto Virtual Replication V6.5 Actualización 3](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window}.

## Actualizaciones y mejoras de la interfaz de usuario
{: #relnotes_v29-ui}

La interfaz de usuario se actualiza y proporciona las mejoras siguientes:

* En la página **Infraestructura**, una nueva tabla **Interfaz de red** proporciona detalles de VLAN, subred y dirección IP para el clúster.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
