---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud y supresión de la prueba de un solo nodo para instancias de VMware vCenter Server on IBM Cloud

La prueba de un solo nodo de VMware vCenter Server on {{site.data.keyword.cloud}} es una nube privada alojada de un solo arrendatario que proporciona la pila de VMware vSphere como servicio. Aunque el entorno gestionado por el cliente se suele desplegar con un mínimo de tres nodos, esta versión de prueba de un solo nodo proporciona un método de bajo coste para experimentar las ventajas de una implementación de nube híbrida.

Esta versión de prueba es ideal para una prueba de concepto que demuestra la velocidad de la automatización avanzada de IBM para el despliegue inicial y la facilidad de mover cargas de trabajo sencillas que no sean de producción a la nube. Mediante VMware Hybrid Cloud Extension (HCX), puede ampliar de forma segura su red de centro de datos local al {{site.data.keyword.CloudDataCent_notm}}, al tiempo que reduce la complejidad de configurar la interconexión en la red. HCX abstrae los recursos de red subyacentes para desplazarlos a través de Internet público de modo que pueda mover sin problemas las cargas de trabajo bidireccionalmente sin necesidad de volver a asignar IP a las máquinas virtuales (VM). Con HCX, no es necesario tener VMware NSX instalado de forma local y es compatible con versiones anteriores de vSphere.  

La prueba de un solo nodo solo es para prueba de concepto. No ejecute cargas de trabajo de producción en este entorno. Las funciones de gestión, como la adición y eliminación de hosts y clústeres, la solicitud de servicios complementarios adicionales y la aplicación de actualizaciones, no reciben soporte.
{:important}

Esta versión de prueba está pensada para utilizarla durante un máximo de 90 días. Cuando finalice el periodo de prueba, puede suprimir este entorno y luego suministrar un entorno de alta disponibilidad que se ajuste a sus necesidades de capacidad. Para obtener más información, consulte [Solicitud de vCenter Server con instancias de paquete híbrido (Hybridity)](vc_hybrid_orderinginstance.html).

## Especificaciones técnicas de la versión de prueba de un solo nodo de instancias de vCenter Server

En la versión de prueba de un solo nodo de la instancia de vCenter Server se incluyen los siguientes componentes:

La disponibilidad y los precios de las configuraciones estandarizadas de hardware pueden variar en función del {{site.data.keyword.CloudDataCent_notm}} seleccionado para el despliegue.
{:note}

### Servidor nativo

Un procesador Dual Intel Xeon Gold 5120 (28 núcleos, 2,20 GHz) con 384 GB de RAM.

### Redes

Se solicitan los siguientes componentes del sistema de redes:
*  Enlaces ascendentes de red pública y privada de 10 Gbps
*  Tres VLAN (LAN virtuales): una VLAN pública y dos VLAN privadas
*  Se despliega una VXLAN (LAN extensible virtual) con DLR (direccionador lógico distribuido) para una potencial comunicación este-oeste entre cargas de trabajo locales conectadas a redes de la capa 2 (L2). La VXLAN se despliega como una topología de direccionamiento de ejemplo, que puede modificar o eliminar o a la que puede añadir componentes. También puede añadir zonas de seguridad por conectar VXLAN adicionales a las nuevas interfaces lógicas del DLR.
*  Dos VMware NSX Edge Services Gateways:
  * Una Edge Services Gateway (ESG) de NSX de VMware de servicios de gestión segura para el tráfico de gestión de HTTPS saliente, desplegado por IBM como parte de la topología del sistema de redes de gestión. Las VM de gestión de IBM utilizan esta ESG para comunicarse con componentes externos específicos de gestión de IBM que están relacionados con la automatización. Para obtener más información, consulte [Configuración de la red para que utilice la ESG gestionada por el cliente](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    El usuario no puede acceder ni utilizar esta ESG. Si lo modifica, es posible que no pueda gestionar la instancia de vCenter Server con el paquete híbrido (Hybridity) desde la consola de {{site.data.keyword.vmwaresolutions_short}}. Además, tenga en cuenta que el uso de un cortafuegos o la inhabilitación de las comunicaciones ESG con componentes externos de gestión de IBM harán que {{site.data.keyword.vmwaresolutions_short}} quede inutilizable.
    {:important}
  * Una Edge Services Gateway de NSX de VMware gestionada por el cliente para el tráfico de salida y de entrada de carga de trabajo HTTPS, que IBM despliega como plantilla que puede modificar para proporcionar acceso VPN o acceso público. Para obtener más información, consulte [¿Representa NSX Edge gestionado por el cliente un riesgo para la seguridad?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

Para obtener más información sobre los componentes de red solicitados al desplegar el servicio de HCX on {{site.data.keyword.cloud_notm}}, consulte [Visión general de HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### Instancias de servidor virtual

Se solicitan las siguientes instancias de servidor virtual (VSI):

* Una VSI para IBM CloudBuilder, que se cierra una vez completado el despliegue de la instancia.
* Se despliega y se puede consultar una VSI de Microsoft Windows Server para Microsoft Active Directory (AD). La VSI funciona como el DNS para la instancia en la que se han registrado los hosts y las máquinas virtuales.

### Licencias proporcionadas por IBM y tarifas

En la versión de prueba de un solo nodo de la solicitud de una instancia de vCenter Server se incluyen las siguientes licencias:

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

La versión de prueba de un solo nodo de instancias de vCenter Server no admiten la opción de traer su propia licencia.
{:note}

Puede que se apliquen tarifas de servicio y soporte adicionales.

## Especificaciones técnicas para HCX on IBM Cloud

Para obtener información sobre las especificaciones técnicas y las consideraciones sobre HCX on {{site.data.keyword.cloud_notm}}, consulte [Visión general de VMware HCX on IBM Cloud](../services/hcx_considerations.html).

## Requisitos y planificación para solicitar una versión de prueba de un solo nodo para instancias de vCenter Server

Asegúrese de llevar a cabo las tareas siguientes:
* La cuenta de {{site.data.keyword.cloud_notm}} que utilice debe cumplir ciertos requisitos. Para obtener más información, consulte [Requisitos para la cuenta de {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).
*  Configure las credenciales de la infraestructura {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Gestión de cuentas y valores de usuario](../vmonic/useraccount.html).
* Revise los requisitos del nombre de la instancia:  
 * Solo se permiten caracteres alfanuméricos y el guión (-).
 * El nombre de instancia debe empezar y terminar por un carácter alfanumérico.
 * La longitud máxima del nombre de instancia es de 10 caracteres.
 * El nombre de instancia debe ser exclusivo dentro de su cuenta.
* Revise los {{site.data.keyword.CloudDataCents_notm}} que se ajustan a los requisitos de la infraestructura física. Para obtener más información, consulte la sección sobre *Disponibilidad de {{site.data.keyword.CloudDataCent_notm}}* en [Requisitos y planificación de vCenter Server con instancias de paquete híbrido (Hybridity)](../vcenter/vc_hybrid_planning.html#ibm-cloud-data-center-availability).
<!--* Ensure the that you meet the following prerequisites for the on-premises HCX instance:
 * VMware vSphere and vCenter 5.5 or higher
 * The VMware HCX Manager must reside in the same security zone as the on-premises vSphere environment
 * The VMware HCX Manager must be able to reach the public Internet to update firewall rules to allow outbound traffic
 * The vSphere environment must have distributed switches-->

## Procedimiento para solicitar la versión de prueba de un solo nodo para instancias de vCenter Server

1. En la página **Prueba de un solo nodo para VMware vCenter Server on {{site.data.keyword.cloud_notm}}**, pulse la tarjeta **vCenter Server** y pulse **Continuar**.
2. En la página **Prueba de un solo nodo para VMware vCenter Server**, siga los pasos para solicitar una cuenta de la infraestructura {{site.data.keyword.cloud_notm}} o especifique su **Nombre de usuario** y **Clave de API** existentes y pulse **Recuperar**.
3. Escriba el nombre de la instancia.
4. Seleccione el {{site.data.keyword.CloudDataCent_notm}} que va a alojar la instancia.  

 El {{site.data.keyword.CloudDataCent_notm}} aparece preseleccionado. Seleccione otra ubicación de {{site.data.keyword.CloudDataCent_notm}} si es necesario.
 {:note}
5. En el panel **Resumen del pedido**, verifique la configuración de la instancia antes de realizar el pedido.
   1. Revise los valores de la instancia.
   2. Revise el coste estimado de la instancia. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de solicitar la instancia.
   4. Pulse **Suministro**.

### Resultados

El despliegue de la instancia comienza automáticamente y solicita la clave de activación del servicio HCX on {{site.data.keyword.cloud_notm}} local.

#### Proceso de despliegue de HCX on IBM Cloud

El despliegue de HCX on {{site.data.keyword.cloud_notm}} es automático. El proceso de automatización de {{site.data.keyword.vmwaresolutions_short}} lleva a cabo los siguientes pasos:
1. Se solicitan tres subredes para HCX desde la infraestructura de {{site.data.keyword.cloud_notm}}:
   * Una subred portátil privada para la gestión de HCX.
   * Una subred portátil privada para interconexiones HCX. Esta subred se utiliza cuando se selecciona la opción **Red privada** para el **tipo de interconexión HCX**.
   * Una subred portátil pública para la activación y mantenimiento con VMware. Si se selecciona la opción **Red pública** para el **tipo de interconexión HCX**, esta subred también se utiliza para interconexiones HCX.

   Las direcciones IP de las subredes solicitadas para HCX están pensadas para que las gestione el proceso automático de VMware en {{site.data.keyword.cloud_notm}}. Estas direcciones IP no se pueden asignar a recursos de VMware, como VM y NSX Edges, creados por el cliente. Si necesita direcciones IP adicionales para los artefactos de VMware, debe solicitar sus propias subredes de {{site.data.keyword.cloud_notm}}.
   {:important}
2. Si se ha seleccionado **Red privada** como **Tipo de interconexión de HCX**, se crea un grupo de puertos llamado **SDDC-DPortGroup-HCX-Private** en el conmutador virtual distribuido (DVS).
3. Se solicita a VMware una clave de activación de HCX.
4. Se crean tres agrupaciones de recursos y carpetas de VM para HCX, que son necesarias para las interconexiones de HCX, los componentes locales de HCX y los componentes remotos de HCX.
5. Se despliega y se configura un par de VMware NSX Edge Services Gateways (ESG) para el tráfico de gestión de HCX:
   * Se configuran interfaces de enlaces ascendentes públicos y privados utilizando las subredes solicitadas.
   * Se configuran los ESG como un par de dispositivos de extremo extra grandes con alta disponibilidad (HA) habilitada.
   * Se configuran reglas de cortafuegos y reglas de conversión de direcciones de red (NAT) para permitir el tráfico HTTPS de entrada y de salida procedente y destinado a HCX Manager.
   * Se configuran las agrupaciones de recursos y las reglas del equilibrador de carga. Estas reglas son agrupaciones de recursos que se utilizan para reenviar el tráfico de entrada relacionado con HCX a los dispositivos virtuales adecuados de HCX Manager, vCenter Server y de Platform Services Controller (PSC).
   * Se aplica el certificado SSL para cifrar el tráfico HTTPS de entrada relacionado con HCX que llega a través de los ESG.

   El extremo de gestión HCX se dedica al tráfico de gestión HCX entre los componentes locales de HCX y los componentes en la nube de HCX. No modifique el extremo de gestión de HCX ni lo utilice para extensiones de red de HCX. En su lugar, crear otros extremos para extensiones de red. Además, el uso de un cortafuegos o la inhabilitación de las comunicaciones del extremo de gestión de HCX con componentes de gestión privados de IBM o con internet pública pueden afectar negativamente a las funciones de HCX.
   {:important}

6. Se despliega, se activa y se configura HCX Manager on {{site.data.keyword.cloud_notm}}:
   * Se registra HCX Manager con vCenter Server.
   * Se configuran los componentes HCX Manager, vCenter Server, PSC y NSX Manager.
   * Se configura la flota HCX.
   * Se configuran contenedores de despliegue de HCX locales y remotos.
7. Se registra el nombre de host y la dirección IP de HCX Manager con el servidor DNS de VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Visualización de detalles de una instancia

Puede comprobar el estado del despliegue visualizando los detalles de la instancia. Para obtener información sobre la visualización de detalles de una instancia, consulte:

* [Visualización de instancias de vCenter Server](vc_viewinginstances.html)
* [Visualización de instancias locales de VMware HCX on IBM Cloud](../services/standalone_viewingserviceinstances.html)

Cuando la instancia se despliega correctamente, los componentes que se describen en las secciones *Especificaciones técnicas* de este tema se instalan en la plataforma virtual de VMware y la clave de activación del servicio HCX on {{site.data.keyword.cloud_notm}} local está disponible en la página de detalles de HCX on {{site.data.keyword.cloud_notm}} local.

El estado de la instancia pasa a ser **Listo para su uso** y el usuario recibe una notificación por correo electrónico.

### Qué hacer a continuación

Configure el servicio HCX on {{site.data.keyword.cloud_notm}} e instale la clave de activación local.

1. Localice la clave de activación local en la página **Instancias desplegadas**.
  1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
  2. En la tabla **Instancias de vCenter Server**, revise la columna **Tipo** para localizar la instancia de prueba de un solo nodo y anote el nombre de la instancia.
  3. Desplácese hasta la tabla **Instancias de HCX local** y examine la columna **Nombre** para localizar la instancia que tiene el mismo nombre que la instancia de un solo nodo.
  4. Anote la clave del campo **Clave de activación**.
2. Vaya a [VMware HCX](https://hcx.vmware.com/#/vm-documentation) y utilice la clave de activación para instalar la instancia de VMware HCX on {{site.data.keyword.cloud_notm}} local y lleve a cabo el proceso de configuración. Para obtener más información, consulte *Procedimiento disponible próximamente*.

Solo debe gestionar los componentes de la infraestructura {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no a través del {{site.data.keyword.slportal}} ni por ningún otro medio fuera de la consola.
Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola y pueden hacer que el entorno sea inestable.
{:important}

## Procedimiento para suprimir la versión de prueba de un solo nodo para instancias de vCenter Server

Para liberar los componentes que ha solicitado en una versión de prueba de un solo nodo de una instancia de vCenter Server, suprima la instancia.

Para obtener más información, consulte [Supresión de instancias de vCenter Server](vc_deletinginstance.html).

### Enlaces relacionados

* [Registro de una cuenta de {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Glosario de términos de HCX](../services/hcx_glossary.html)
* [Documentación de VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Visión general de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_overview.html)
* [Consideraciones sobre red para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_networkingonvcenterserver.html)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_orderinginstance.html)
