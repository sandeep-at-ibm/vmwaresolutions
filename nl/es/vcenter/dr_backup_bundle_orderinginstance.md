---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: single-node trial, data protection DR, order data protection DR

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud, visualización y supresión de instancias de prueba de un solo nodo para Protección de datos y Recuperación tras desastre.
{: #dr_backup_bundle_orderinginstance}

Revise los requisitos de planificación antes de solicitar una instancia de prueba de un solo nodo para
Protección de datos y Recuperación tras desastre.

Esta versión de prueba se suprime automáticamente después de 90 días. En la página de detalles de la instancia se muestra una cuenta atrás de caducidad para la instancia de prueba de nodo único para la protección de datos y la recuperación tras desastre.
{:important}

## Requisitos y planificación para solicitar instancias de prueba de un solo nodo para Protección de datos y Recuperación tras desastre.
{: #dr_backup_bundle_orderinginstance-req}

Asegúrese de cumplir con los siguientes requisitos y de haber completado las tareas siguientes.

### Requisitos para instancias locales de HCX
{: #dr_backup_bundle_orderinginstance-hcx-req}

* Requiere VMware vSphere y vCenter 5.5 o superior.
* El entorno de vSphere debe tener conmutadores distribuidos para las VM que se van a migrar a {{site.data.keyword.cloud_notm}}.
* El dispositivo virtual de HCX Manager debe poder desplegarse en una red privada en el entorno local y debe tener permiso para acceder a Internet público.

### Cuenta de la infraestructura IBM Cloud
{: #dr_backup_bundle_orderinginstance-account-req}

* Para utilizar {{site.data.keyword.vmwaresolutions_short}} para solicitar instancias, debe tener una cuenta de infraestructura de {{site.data.keyword.cloud_notm}}. El coste de los componentes que se solicitan en las instancias se factura a dicha cuenta de {{site.data.keyword.cloud_notm}}.
*  Configure las credenciales de la infraestructura {{site.data.keyword.cloud_notm}} en la página **Configuración**. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Valores** en el panel de navegación de la izquierda.

### Requisitos de nombre de instancia
{: #dr_backup_bundle_orderinginstance-inst-name-req}

Revise los requisitos del nombre de la instancia:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre de instancia debe empezar por un carácter alfabético y terminar por un carácter alfanumérico.
* La longitud máxima del nombre de instancia es de 10 caracteres.
* El nombre de instancia debe ser exclusivo dentro de su cuenta.

## Procedimiento para solicitar instancias de prueba de un solo nodo para instancias de Protección de datos y Recuperación tras desastre.
{: #dr_backup_bundle_orderinginstance-procedure}

1. En el catálogo de {{site.data.keyword.cloud_notm}}, pulse el icono **VMware** en el panel de navegación de la izquierda y, a continuación, pulse la tarjeta **Prueba de un solo nodo de Protección de datos y Recuperación tras desastre** en la sección **Centros de datos virtuales de VMware**.
2. En la página **Prueba de un solo nodo para Protección de datos y Recuperación tras desastre**, pulse **Continuar**.
3. Siga los pasos para solicitar una cuenta de la infraestructura {{site.data.keyword.cloud_notm}} o especifique su **Nombre de usuario** y **Clave de API** existentes y pulse **Recuperar**.

 Esta sección está oculta si la clave de API ya existe.
 {:note}
4. Escriba el nombre de la instancia.
5. Seleccione el {{site.data.keyword.CloudDataCent_notm}} que va a alojar la instancia.  

 De forma predeterminada, aparece preseleccionado el {{site.data.keyword.CloudDataCent_notm}} DAL09. Seleccione otra ubicación de {{site.data.keyword.CloudDataCent_notm}} si es necesario.
 {:note}
6. En el panel **Resumen del pedido**, verifique la configuración de la instancia antes de realizar el pedido.
   1. Revise los valores de la instancia.
   2. Revise el coste estimado de la instancia. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de solicitar la instancia.
   4. Pulse **Suministro**.

### Resultado tras solicitar instancias de prueba de un solo nodo para las instancias Protección de datos y Recuperación tras desastre
{: #dr_backup_bundle_orderinginstance-results}

* El despliegue de la instancia comienza automáticamente y solicita la clave de activación del servicio HCX on {{site.data.keyword.cloud_notm}} local.
* Puede comprobar el estado de despliegue, incluidos los problemas que puedan requerir su atención, mediante la visualización de la sección **Historial de despliegue** de los detalles de la instancia.
* Cuando la instancia se haya desplegado correctamente, se instalan los componentes que se describen en [Especificaciones técnicas para pruebas de un solo nodo para las instancias Protección de datos y Recuperación tras desastre](/docs/services/vmwaresolutions/services?topic=vmware-solutions-dr_backup_bundle_overview#dr_backup_bundle_overview-tech-specs).
* Cuando la instancia esté lista para ser utilizada, el estado de la instancia pasará a ser **Listo para su uso** y recibirá una notificación por correo electrónico.

#### Proceso de despliegue de HCX on IBM Cloud
{: #dr_backup_bundle_orderinginstance-hcx-deploy-process}

El despliegue de HCX on {{site.data.keyword.cloud_notm}} es automático. El proceso de automatización de {{site.data.keyword.vmwaresolutions_short}} lleva a cabo los siguientes pasos:
1. Se solicitan tres subredes para HCX desde la infraestructura de {{site.data.keyword.cloud_notm}}:
   * Dos subredes portátiles privadas para la gestión de HCX.
   * Una subred portátil pública para la activación y mantenimiento con VMware. Esta subred también se utiliza para las interconexiones HCX.

   Las direcciones IP de las subredes solicitadas para HCX están pensadas para que las gestione la automatización de VMware on {{site.data.keyword.cloud_notm}}. Estas direcciones IP no se pueden asignar a recursos de VMware, como VM y NSX Edges, creados por el cliente. Si necesita más direcciones IP para los artefactos de VMware, debe solicitar sus propias subredes de {{site.data.keyword.cloud_notm}}.
   {:important}
3. Se crean tres agrupaciones de recursos y carpetas de VM para HCX, que son necesarias para las interconexiones de HCX, los componentes locales de HCX y los componentes remotos de HCX.
4. Se despliega y se configura un par de VMware NSX Edge Services Gateways (ESG) para el tráfico de gestión de HCX:
   * Se configuran interfaces de enlaces ascendentes públicos y privados utilizando las subredes solicitadas.
   * Se configuran los ESG como un par de dispositivos de extremo extra grandes con alta disponibilidad (HA) habilitada.
   * Se configuran reglas de cortafuegos y reglas de conversión de direcciones de red (NAT) para permitir el tráfico HTTPS de entrada y de salida procedente y destinado a HCX Manager.
   * Se configuran las agrupaciones de recursos y las reglas del equilibrador de carga. Estas reglas y agrupaciones de recursos se utilizan para reenviar el tráfico de entrada relacionado con HCX a los dispositivos virtuales adecuados de HCX Manager y vCenter Server (con el controlador de servicios de plataforma integrado).
   * Se aplica el certificado SSL para cifrar el tráfico HTTPS de entrada relacionado con HCX que llega a través de los ESG.

   El extremo de gestión HCX se dedica al tráfico de gestión HCX entre los componentes locales de HCX y los componentes en la nube de HCX. No modifique el extremo de gestión de HCX ni lo utilice para extensiones de red de HCX. En su lugar, crear otros extremos para extensiones de red. Además, el uso de un cortafuegos o la inhabilitación de las comunicaciones del extremo de gestión de HCX con componentes de gestión privados de IBM o con internet pública pueden afectar negativamente a las funciones de HCX.
   {:important}

5. Se despliega, se activa y se configura HCX Manager on {{site.data.keyword.cloud_notm}}:
   * Se registra HCX Manager con vCenter Server.
   * Se configuran los componentes HCX Manager, vCenter Server (con el controlador de servicios de plataforma integrado) y NSX Manager.
   * Se configura la flota HCX.
   * Se configuran contenedores de despliegue de HCX locales y remotos.
6. Se registra el nombre de host y la dirección IP de HCX Manager con el servidor DNS de VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Visualización de detalles de una instancia
{: #dr_backup_bundle_orderinginstance-view-inst-details}

Puede comprobar el estado del despliegue visualizando los detalles de la instancia. Pulse **Recursos** en el panel de navegación de la izquierda y localice la tabla **Instancias de vCenter Server** o **Instancias de HCX locales** para
ver información sobre las instancias que ha solicitado.

Cuando la instancia se ha desplegado correctamente, los componentes que se describen en las secciones *Especificaciones técnicas* de este tema se instalan en la plataforma virtual de VMware y la clave de activación del servicio HCX on {{site.data.keyword.cloud_notm}} local aparece listado en la tabla **Instancias de HCX locales**.

El estado de la instancia pasa a ser **Listo para su uso** y el usuario recibe una notificación por correo electrónico.

### Qué hacer a continuación
{: #dr_backup_bundle_orderinginstance-next}

Instale HCX Enterprise Manager local y configure la conexión con la instancia de HCX on {{site.data.keyword.cloud_notm}}.

1. Localice la clave de activación local en la página **Recursos**.
  1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
  2. En la tabla **Instancias de vCenter Server**, revise la columna **Tipo** para localizar la instancia de la prueba de un solo nodo para migración y modernización de apps y anote el nombre de la instancia.
  3. Desplácese hasta la tabla **Instancias de HCX locales** y examine la columna **Nombre** para localizar la instancia que tiene el mismo nombre que la instancia de un solo nodo que ha solicitado con el prefijo *-OnPrem*.
  4. Anote la clave del campo **Clave de activación**.
2. Obtenga el HCX Enterprise Manager Open Virtual Appliance (OVA) local desde la consola de HCX Manager de HCX on {{site.data.keyword.cloud_notm}}.
  1. Conéctese a la consola de HCX Cloud.
    1. En la tabla **Instancias de vCenter Server**, pulse la instancia de la prueba de un solo nodo para migración y modernización de apps para ver los detalles de la instancia.
    2. En **Información de acceso**, localice y anote las credenciales de vCenter.
    3. Pulse **Servicios** en el panel de navegación izquierdo.
    4. En la página **Servicios**, pulse **HCX on IBM Cloud**.
    5. En la página de detalles de **HCX on IBM Cloud**, localice y anote la **IP de HCX Cloud**.
    6. Asegúrese de que está conectado a la VPN para acceder a la red privada de {{site.data.keyword.cloud_notm}}.
    7. Pulse **Ver consola de HCX Cloud**.
  2. En la **consola de HCX Cloud**, siga estos pasos:
      1. Pulse el separador **Administración**.
      2. En el separador **Actualizaciones del sistema**, pulse **SOLICITAR ENLACE DE DESCARGA**.
      3. Pulse **COPIAR ENLACE** y utilice este enlace para descargar el cliente de HCX Enterprise en un entorno local con acceso a su entorno local de vSphere.
3. En el cliente web de VMware vSphere, despliegue el cliente de HCX Enterprise como dispositivo virtual de HCX Manager (HCX Manager) en el entorno local. Siga las instrucciones de la
[Guía de usuario de VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

    Debe desplegar HCX Manager local en una red privada y debe otorgarle acceso a la red pública. Puede utilizar NSX Edge, Vyatta o pasarelas similares para permitir el acceso internet al HCX Manager local. Si las pasarelas utilizadas para el acceso a la red privada y a la red pública son distintas, se recomienda utilizar la pasarela predeterminada para permitir el acceso a la red pública y a la **consola de administración de HCX Manager** privada para crear una ruta estática para el acceso a la red privada.  
    {:note}
4. Utilice la clave de activación local que ha anotado en el paso 1 para activar la máquina virtual de HCX Enterprise Manager local.
  1. Inicie una sesión en la VM de HCX Enterprise Manager local utilizando las credenciales especificadas al desplegar OVA.
  2. Escriba la clave de activación cuando se le solicite.

  Siga las instrucciones de la
[Guía de usuario de VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

5. El servicio HCX on {{site.data.keyword.cloud_notm}} ha generado un certificado SSL autofirmado. Debe importar el certificado en el HCX Manager local siguiendo los siguientes pasos:
    1. En la **consola de administración de HCX Manager** local, pulse el separador **Administración**.
    2. En el panel de navegación de la izquierda, pulse **Certificado de CA de confianza** y luego pulse **IMPORTAR** a la derecha.
    3. Pulse **URL** y escriba el URL del certificado que desea aplicar. Esta es la **IP de HCX Cloud** (``https://<cloud-side public IP>``) que puede encontrar en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} en la consola de {{site.data.keyword.vmwaresolutions_short}}.
    4. Pulse **APLICAR**.
6. Continúe la configuración inicial y cree la interconexión. Siga las instrucciones de la
[Guía de usuario de VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.
7. Extienda las redes de VMware HCX del entorno local a {{site.data.keyword.cloud_notm}}. Siga las instrucciones de la
[Guía de usuario de VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.
8. Migre las VM del entorno local a {{site.data.keyword.cloud_notm}}. Siga las instrucciones de la
[Guía de usuario de VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

Solo debe gestionar los componentes de la infraestructura {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no a través del {{site.data.keyword.slportal}} ni por ningún otro medio fuera de la consola.
Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola y pueden hacer que el entorno sea inestable.
{:important}

## Procedimiento para suprimir instancias de prueba de un solo nodo de Protección de datos y Recuperación tras desastre.
{: #dr_backup_bundle_orderinginstance-deleting-procedure}

Cuando suprima una instancia de prueba de un solo nodo de Recuperación tras desastre, los siguientes componentes se liberarán en esta secuencia:

1. Todos los servicios desplegados
3. Licencias del producto VMware
4. Servidores ESXi
5. Subredes
6. VLAN

Debido a las dependencias entre recursos, los componentes de la instancia no se liberan inmediatamente cuando se suprime la instancia. Por ejemplo, las subredes y las VLAN no se pueden suprimir hasta que la infraestructura de {{site.data.keyword.cloud_notm}} haya reclamado por completo los servidores ESXi, lo cual sucede al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}. Al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días, se suprimen las subredes y las VLAN y se completa la supresión de la instancia.

Se le facturará por la instancia suprimida hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
{:note}

Siga los pasos siguientes para suprimir una instancia de prueba de un solo nodo para Protección de datos y Recuperación tras desastre:

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, busque la instancia que desea suprimir.
3. En la columna **Acciones**, pulse el icono Suprimir.
   El estado de la instancia pasa a ser **Suprimiendo**. Cuando la instancia se haya suprimido correctamente, los componentes de la instancia se liberarán y el estado de la instancia pasará a ser **Suprimido**.
4. Si desea eliminar el registro de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}, siga estos pasos:
   1. En la columna **Acciones**, pulse el icono Suprimir de nuevo.
   2. En la ventana **Suprimir instancia**, pulse **Aceptar**.

## Enlaces relacionados
{: #dr_backup_bundle_orderinginstance-related}

* [Guía de vCenter Server e IBM Cloud Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Apertura de una incidencia para IBM Cloud privado](https://www.ibm.com/mysupport/s/?language=en_US){:external}
* [Recursos de VMware HCX](https://hcx.vmware.com/#/docs){:external}
* [Guía de usuario de VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [Cancelación de servidores virtuales](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)
