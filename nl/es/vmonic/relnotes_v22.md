---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-19"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas del release para V2.2
{: #relnotes_v22}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Corrección de Spectre y Meltdown
{: #relnotes_v22-spectre}

{{site.data.keyword.vmwaresolutions_short}} proporciona parches de VMware en respuesta a las vulnerabilidades conocidas como Spectre y Meltdown (CVE-2017-5753, CVE-2017-5715 y CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Actualización de máquina virtual IBM CloudDriver
{: #relnotes_v22-cloud-driver}

Durante el proceso de actualización a V2.2, la máquina virtual IBM CloudDriver es vuelve a desplegar con CentOS Linux release 7.4.1708. Además, todas las nuevas instancias suministradas incluyen CentOS Linux release 7.4.1708 en IBM CloudDriver.

**Importante:**

* Si utiliza una solución de copia de seguridad que hace referencia a la máquina virtual IBM CloudDriver, después de actualizar a V2.2, asegúrese de que la solución de copia de seguridad haga referencia a la nueva máquina virtual IBM CloudDriver.
* Antes de actualizar a V2.2, asegúrese de sustituir la VSI Legacy Veeam por el servicio Veeam on {{site.data.keyword.cloud_notm}}. Legacy Veeam ya no recibe soporte en V2.2 y futuros releases, por lo que las copias de seguridad de componentes de gestión asociadas a Legacy Veeam no se pueden restaurar.

Para obtener más información sobre cómo utilizar el servicio Veeam on {{site.data.keyword.cloud_notm}}, consulte:
* [Componentes y consideraciones sobre Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## Valores de configuración avanzada en servidores ESXi
{: #relnotes_v22-config-esxi}

Para V2.2 o releases posteriores, se solicitan nuevas instancias con un nuevo conjunto de valores de configuración avanzada para servidores ESXi.
Para las instancias que se actualizan desde un release anterior a V2.2 o releases posteriores, algunos valores requieren que se rearranquen los servidores ESXi. Por lo tanto, solo se aplica automáticamente un subconjunto de valores de configuración.

Se recomienda cambiar los valores de configuración restantes por los nuevos valores para mantener la coherencia entre todas las instancias y permitir un soporte adecuado para la ampliación de almacenamiento. IBM tiene intención de realizar pruebas solo con estos nuevos valores para todos los futuros releases de {{site.data.keyword.cloud_notm}} for VMware Solutions.

Para obtener más información, consulte _Valores de configuración avanzada para servidores ESXi_ en [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#advanced-configuration-settings-for-esxi-servers).

## Soporte para un máximo de 51 servidores ESXi para un clúster inicial y un máximo de 59 servidores ESXi para clústeres adicionales
{: #relnotes_v22-esxi-cluster}

Para V2.2 y releases posteriores, ahora puede aumentar el número de servidores ESXi hasta un máximo de 51 para un clúster inicial y hasta 59 para clústeres adicionales.

Para instancias desplegadas en V2.1 o releases anteriores, debe habilitar el soporte de vSAN necesario para aumentar el tamaño del clúster por encima de 32. Para obtener más información sobre los pasos a seguir para aumentar el número de servidores ESXi, consulte _¿Cuántos servidores ESXi puedo añadir a un clúster?_ en [Preguntas frecuentes sobre servidores ESXi](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi#how-many-esxi-servers-can-i-add-to-a-cluster-).
{:important}

## Más opciones de configuración de red para instancias de vCenter Server y de Cloud Foundation
{: #relnotes_v22-network-config}

Para los pedidos de instancias de vCenter Server y de Cloud Foundation, ahora puede reutilizar las VLAN públicas y privadas existentes para la configuración de red. Cuando las VLAN existentes no están disponibles, puede solicitar una nueva VLAN pública y dos nuevas VLAN privadas.

Para ver consideraciones importantes antes de seleccionar las VLAN existentes, consulte las secciones *Valores de interfaz de red* de [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v22-vcs}

### Actualizaciones de los valores de configuración del componente NSX y de grupos de puertos
{: #relnotes_v22-nsx}

El release actual aplica la actualización del componente VMware NSX for vSphere 6.3.5. Para obtener más información sobre los componentes, consulte [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

Para instancias de VMware vCenter Server desplegadas en V2.2 o releases posteriores, los valores de configuración de NSX y de grupos de puertos han cambiado. Para obtener más información, consulte la sección *Valores de configuración de grupos de puertos y NSX* en [Lista de material de software de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#nsx-and-port-group-configuration-settings).

### Nueva opción para la configuración de DNS
{: #relnotes_v22-dns}

Ahora puede seleccionar el despliegue de una sola instancia de servidor virtual (VSI) de Microsoft Windows Server para Microsoft Active Directory (AD) o dos máquinas virtuales Microsoft Windows de alta disponibilidad en el clúster de gestión. Para releases anteriores a V2.2, se despliega de forma predeterminada y automáticamente una sola VSI Microsoft Windows para Microsoft AD. La nueva opción de seleccionar dos máquinas virtuales Microsoft Windows proporciona más privacidad y la opción de hacer copia de seguridad y restaurar las máquinas virtuales mediante el servicio Veeam.

Debe proporcionar 2 licencias de Microsoft Windows Server 2012 R2 si configura la instancia de modo que utilice las dos máquinas virtuales Microsoft Windows. Utilice la licencia de Microsoft Windows Server 2012 R2 Standard Edition y/o la licencia de Microsoft Windows Server 2012 R2 Datacenter Edition. Tiene 30 días para activar las máquinas virtuales.
{:note}

Para obtener más información, consulte la sección *Valores del sistema* del apartado [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#system-settings).

### Aumento del número de clústeres por instancia
{: #relnotes_v22-clusters-per-inst}

Ahora puede añadir un máximo de 10 clústeres a las instancias de VMware vCenter Server que se han desplegado en la V2.2 o posteriores o que se han actualizado a las mismas. Para obtener más información, consulte [Adición y visualización de clústeres para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters).

## Actualizaciones de clústeres de VMware vSphere
{: #relnotes_v22-vss}

### Paquetes de licencias de componentes disponibles para los clientes Business Partner
{: #relnotes_v22-license-bundles}

Ahora los usuarios de Business Partners pueden seleccionar entre cuatro paquetes de licencias de componentes cuando realicen un pedido de un nuevo clúster de vSphere. Puede elegir entre las opciones Standard with Management, Advanced, Advanced with Networking o Advanced with Networking and Management. También puede incluir componentes adicionales de VMware a su pedido. Sin embargo, la opción de traer su propia licencia no está disponible.

Para obtener más información, consulte la sección *Valores de licencia* del apartado [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).

## Actualizaciones de instancias de NetApp ONTAP Select
{: #relnotes_v22-netapp}

El release actual aplica la actualización de NetApp ONTAP Select 9.3.

### Aumento en el número de unidades SATA para servidores nativos IBM Cloud de alta capacidad
{: #relnotes_v22-sata-drives}

Ahora dispone de treinta y cuatro unidades SATA para {{site.data.keyword.baremetal_short}} NetApp ONTAP Select de alta capacidad. Para obtener más información, consulte [Especificaciones técnicas para instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs).

## Actualizaciones de servicios complementarios
{: #relnotes_v22-services}

### Aumento de la opción de ancho de banda para F5 on IBM Cloud
{: #relnotes_v22-bandwidth}

Ahora puede seleccionar un ancho de banda máximo de 10 Gbps al instalar el servicio F5 on {{site.data.keyword.cloud_notm}} para las instancias de Cloud Foundation y vCenter Server. Para obtener más información, consulte [Consideraciones sobre F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations).

### KMIP for VMware on IBM Cloud
{: #relnotes_v22-kmip}

Ahora puede solicitar una instancia de Cloud Foundation o de vCenter Server con el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} incluido o puede añadir el servicio a una instancia existente de Cloud Foundation o de vCenter Server después del despliegue inicial.

Este servicio ofrece un servicio altamente disponible de tipo 24x7 para gestionar las claves de cifrado que utiliza VMware en {{site.data.keyword.cloud_notm}}. Este servicio ofrece capacidad de tiempo de ejecución que permite a los clientes crear, recuperar, activar, revocar y suprimir las claves de cifrado. Además, este servicio proporciona capacidad de gestión para mantener las asociaciones entre las credenciales del cliente y aquellas claves de cifrado.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v22-spp}

El servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} ya está disponible para las instancias que se han desplegado en la V2.2 y posteriores releases o que se han actualizado a estos.

Este servicio proporciona una solución eficiente y escalable para la protección de datos, la reutilización de datos y la recuperación de datos para entornos virtuales. Puede implementarlo como una solución autónoma o integrarlo con su entorno IBM Spectrum Protect&trade; Plus para descargar copias para su almacenamiento y gestión de datos a largo plazo.

El servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} proporciona protección de datos solo para las VM de carga de trabajo.

Para obtener más información, consulte [Gestión de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp).

### Servicios gestionados
{: #relnotes_v22-managed-services}

Los servicios gestionados para Veeam on {{site.data.keyword.cloud_notm}} y para Zerto on {{site.data.keyword.cloud_notm}} a están disponibles para instancias de VMware vCenter Server y de VMware Cloud Foundation. Solicite estos servicios gestionados si no desea gestionar la complejidad de su propia solución y entorno.

El servicio Veeam on {{site.data.keyword.cloud_notm}} se puede integrar fácilmente con sus hipervisores VMware para ayudar a la empresa a alcanzar un alto grado de disponibilidad (HA). Se puede desplegar un entorno de copia de seguridad completamente gestionado mediante software de copia de seguridad de Veeam e IBM Resiliency Backup as a Service.

El servicio Zerto on {{site.data.keyword.cloud_notm}} ofrece funciones de réplica y de recuperación tras desastre, que se pueden integrar en las ofertas de despliegue para proteger y recuperar los datos del entorno virtual VMware en {{site.data.keyword.cloud_notm}}. Se puede desplegar un entorno de recuperación tras desastre (DR) completamente gestionado mediante el software Zerto DR e IBM Resiliency Services.

Puede solicitar servicios gestionados para sus instancias desde la página **Cómo comenzar**, ya sea realizando un pedido de una nueva instancia o añadiendo el servicio a una instancia existente.

Para obtener más información, consulte los temas siguientes:
* [Solicitud de servicios para Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Solicitud de servicios para Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)

## Documentación nueva y actualizada
{: #relnotes_v22-new-docs}

* En la documentación encontrará una tabla de comparaciones con las funciones soportadas para las instancias de Cloud Foundation y de vCenter Server, así como para los clústeres de VMware vSphere. Puede ver, de un vistazo, las diferencias entre las funciones que proporciona cada tipo de instancia. Para obtener más información, consulte [Gráfico de comparación de ofertas](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

* En la documentación se proporciona las VLAN y la Lista de materiales (BOM) de software para los clústeres de Cloud Foundation, vCenter Server y VMware vSphere.

  Para obtener más información, consulte los temas siguientes:

  * [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
  * [Lista de materiales de VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)

## Actualizaciones y mejoras de la interfaz de usuario
{: #relnotes_v22-ui}

Se han realizado mejoras en la interfaz de usuario:

* Cuando se solicita una instancia, ahora todas las opciones de hardware están filtradas por ubicación y las opciones no disponibles se muestran en el estado inhabilitado.
* Ahora la configuración de **{{site.data.keyword.baremetal_short}}** se especifica automáticamente cuando se solicita un clúster de vSphere basado en las configuraciones existentes. Puede actualizar la configuración según sus necesidades.
* Hay varios mensajes de error y mejoras de ayuda contextual disponibles para ayudarle a seleccionar el valor adecuado en la interfaz de usuario.
