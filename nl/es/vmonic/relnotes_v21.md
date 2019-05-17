---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas del release para V2.1
{: #relnotes_v21}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Corrección de Spectre y Meltdown
{: #relnotes_v21-spectre}

{{site.data.keyword.vmwaresolutions_short}} proporciona parches de VMware en respuesta a las vulnerabilidades conocidas como Spectre y Meltdown (CVE-2017-5753, CVE-2017-5715 y CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware HCX on IBM Cloud
{: #relnotes_v21-hcx}

El servicio HCX on {{site.data.keyword.cloud_notm}} solo está disponible para las instancias de VMware Cloud Foundation y las instancias de VMware vCenter Server que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.1 y posteriores releases o que se han actualizado a estos. Este servicio permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) bidireccionales entre sus centros de datos locales e {{site.data.keyword.cloud_notm}} sin realizar ningún cambio. Al establecer un puente de capa 2, HCX utiliza la optimización, deduplicación, compresión y cifrado de WAN para migrar datos de forma más rápida y segura sobre un enlace directo o un túnel VPN. La migración masiva de máquinas virtuales es compatible con VMware vSphere 5.1 o superior. Si utiliza vSphere 6.0 o superior local, puede ejecutar vMotion de las máquinas virtuales en directo (encendidas) a un {{site.data.keyword.CloudDataCent_notm}}. No es necesario tener VMware NSX instalado en el centro de datos cuando se utiliza HCX.

Puede solicitar instancias de Cloud Foundation o de vCenter Server con el servicio HCX on {{site.data.keyword.cloud_notm}} incluido al solicitar la instancia, o puede añadir este servicio a las instancias existentes más adelante desde el separador **Servicios** de la página de detalles de la instancia.

Puede solicitar una instancia local de HCX local para la obtención de licencias y la activación de la instalación local de HCX.

Para obtener más información, consulte los temas siguientes:
* [Consideraciones sobre HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [Gestión de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Consideraciones sobre instancias locales de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_considerations)
* [Solicitud de instancias locales de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances)

## Modelo de licencia Traer su propia licencia más flexible para VMware Cloud Foundation y vCenter Server
{: #relnotes_v21-byol}

Puede traer su propia licencia (BYOL) o adquirir licencias de suscripción proporcionadas por IBM cuando cree un nuevo clúster en instancias de VMware Cloud Foundation y de VMware vCenter Server V2.1 y posteriores. Estas opciones le permiten utilizar la clave de componente existente o bien alquilar la licencia de IBM. Antes de la V2.1, no podía adquirir licencias proporcionadas por IBM para un componente específico de VMware si utilizaba el sistema BYOL. En este momento, solo VMware vSphere y VMware vSAN están disponibles para licencias por clúster.

Además, cuando añada nodos a un clúster cuya licencia ha conseguido con su clave, la consola le solicita que especifique una nueva clave de licencia si el número de nodos supera la capacidad de la clave.

Para obtener más información, consulte los temas siguientes:

* [Adición, visualización y supresión de clústeres para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)
* [Preguntas frecuentes sobre BYOL](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_byol)

## Actualizaciones de componentes del servicio Zerto on IBM Cloud
{: #relnotes_v21-zerto}

Para el servicio Zerto on {{site.data.keyword.cloud_notm}} desplegado en instancias de Cloud Foundation y de vCenter Server de la V2.1 y posteriores, se suministra Zerto Virtual Replication 5.5u2. Ahora los dispositivos de réplica virtual (VRA) de Zerto se despliegan en el almacén de datos de gestión (que puede ser vSAN o Endurance) en lugar de en el almacén de datos local por motivos de rendimiento. Si tiene VRA existente, tenga en cuenta la posibilidad de migrar su almacenamiento al almacén de datos de gestión para mejorar su rendimiento.

Para obtener más información, consulte [Visión general de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr).

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v21-vcs}

### Valores de configuración de MTU de red
{: #relnotes_v21-mtu}

Para V2.1 o releases posteriores, las nuevas instancias de vCenter Server se solicitan con el valor de conmutador virtual distribuido (DVS) público MTU 1500 (predeterminado). Para obtener más información, consulte _Valores de configuración de MTU de red_ en [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Aplicación automática de parches y actualizaciones de VMware ESXi a hosts
{: #relnotes_v21-esxi-patches}

En las instancias de VMware vCenter Server de la V2.0 y anteriores, los parches no se aplicaban automáticamente a los hosts ESXi que se añadían a un clúster.

En las instancias de la V2.1 y posteriores, el sistema de automatización aplica los parches a los nuevos hosts ESXi, de modo que el nivel de parche coincide con el nivel de parche en el momento en el que se suministró la instancia inicial. El usuario es el responsable de aplicar manualmente los futuros parches y actualizaciones.
Cuando estén disponibles nuevos parches y actualizaciones de VMware en futuros releases, el sistema de automatización explora los hosts ESXi de las instancias existentes y le enviará por correo electrónico un recordatorio para que aplique manualmente los parches y actualizaciones más recientes.

Para obtener más información, consulte [Aplicación de actualizaciones a instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates).

### Estimaciones de precios para actualizaciones de licencia de VMware NSX
{: #relnotes_v21-nsx-license}

Ahora puede ver una estimación del precio antes de realizar un pedido para actualizar a la edición VMware NSX Advanced o Enterprise. Los precios dependen del número de hosts ESXi de la instancia de vCenter Server. Esta adquisición solo cambia la clave de licencia de NSX y actualiza la edición Base de VMware NSX a la edición Advanced o Enterprise. La adquisición no actualiza la versión de software de NSX.

Para obtener más información, consulte [Visión general de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview).

### Se ha aumentado el número máximo de servidores por clúster, 32
{: #relnotes_v21-max-clusters}

Para el clúster predeterminado de una instancia, puede desplegar o ampliar hasta 51 servidores. Para todos los siguientes clústeres de una instancia, puede desplegar o ampliar hasta 59 servidores. Para obtener más información, consulte [Adición, visualización y supresión de clústeres para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters).

Esta función solo está disponible para las instancias desplegadas en la versión V2.1 o posterior. Las instancias que se han actualizado a V2.1 desde releases anteriores a V2.1 no tienen esta opción.
{:note}

### Opciones de configuración personalizadas por el usuario de servidores nativos de IBM Cloud
{: #relnotes_v21-bare-metal}

La configuración de servidores nativos personalizada por el usuario ahora ofrece Dual Intel Xeon Gold 6140 con 36 núcleos en total y 2,3 GHz.

Para obtener más información, consulte los temas siguientes:
* [Visión general de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)

### Configuraciones de comparticiones de archivos NFS individuales
{: #relnotes_v21-nfs}

Ahora puede configurar comparticiones de archivos NFS de forma individual. Seleccione el tamaño de archivo y el nivel de rendimiento de cada compartición de archivos individual o seleccione el mismo tamaño de archivo y nivel de rendimiento para todas las comparticiones de archivos del pedido.

Para obtener más información, consulte los temas siguientes:
* [Visión general de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)

## Actualizaciones y mejoras de la interfaz de usuario
{: #relnotes_v21-ui}

Se han realizado mejoras en la interfaz de usuario:

* La opción **Solicitar instancia** ya no está disponible en el panel de navegación de la izquierda. Pulse **Cómo comenzar** para seguir los pasos para solicitar una instancia.
* Se ha cambiado el nombre del campo **Prefijo de subdominio** de la página **Aspectos básicos** cuando se solicita una instancia por **Etiqueta de subdominio**.
* Además de ver la estimación del coste en la página **Resumen** cuando solicite una instancia primaria o secundaria de vCenter Server o de Cloud Foundation, ahora puede calcular una estimación de coste en cualquier página a medida que especifica los detalles del pedido de la instancia.
* Se añade un rastro de navegación a la página **Recursos** como método de navegación alternativo, lo que reduce el número de pasos necesarios para llegar a las páginas padre.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.

## Documentación nueva y actualizada
{: #relnotes_v21-new-docs}

Dispone de una nueva receta de developerWorks con instrucciones paso a paso sobre cómo conectar almacenamiento dedicado a despliegues existentes de {{site.data.keyword.vmwaresolutions_full}} que utiliza NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Pasos para conectar almacenamiento dedicado a VMware Solutions on IBM Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/).
