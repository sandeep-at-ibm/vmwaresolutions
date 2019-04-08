---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Visión general de VMware Update Manager
{: #vum-overview}

VMware Update Manager (VUM) utiliza un proceso de varias etapas para actualizar objetos de vSphere y para aplicar parches o extensiones. Este proceso permite un procedimiento de actualización sin problemas con un mínimo de tiempo de inactividad del sistema. Antes de examinar este proceso, tenemos que comprender los términos siguientes:
* **Objeto de inventario**: un objeto dentro de vCenter, como por ejemplo máquina virtual, dispositivos virtuales o host ESXi de vSphere.
* **Línea base**: La línea base contiene una recopilación de uno o más parches, extensiones, service packs, correcciones de errores o actualizaciones que se pueden clasificar como líneas base de parche, extensión o actualización. Hay dos clasificaciones de líneas base: el host y el VM/VA; ambos tienen dos líneas base predefinidas por VMware y las personalizadas se pueden añadir según sea necesario:
  - Líneas base de hosts predefinidos:
    - Parches de host críticos
    - Parches de host no críticos

  - Línea base predefinida de VM/VA:
    - Actualización de VA a más reciente
    - Actualización de VM Hardware para que coincida con el host
    - Actualización de VMware Tools para que coincida con el host

* **Grupo de línea base**: un conjunto de líneas base no conflictivas, que combina diferentes tipos de líneas base y explora y corrige un objeto de inventario frente a todos ellos al completo. Si un grupo de línea base contiene las líneas base de actualización y de parche o de extensión, primero se ejecuta la actualización.
* **Exploración**: La exploración es el proceso en el que el objeto u objetos de inventario se evalúan en relación con la línea base o el grupo de línea base.
* **Transferencia**: la transferencia garantiza que los parches y las extensiones se descarguen en los hosts de vSphere ESXi antes de la corrección y es un paso opcional para minimizar los hosts de tiempo que están en modalidad de mantenimiento.
* **Corrección**: La corrección es el proceso en el que VUM aplica parches, extensiones y actualizaciones al objeto u objetos de inventario.

Por lo tanto, el proceso VUM es el siguiente:
* Se exploran un objeto de inventario o un grupo de objetos para la conformidad con una línea base o un grupo de líneas base.
* Después de una revisión, los parches y las extensiones se pueden realizar de forma opcional, antes de la corrección.

La descarga de las actualizaciones, los parches de host, las extensiones y los metadatos relacionados es un proceso automático predefinido que se puede modificar. De forma predeterminada, a intervalos configurables regulares, VUM se pone en contacto con VMware o con orígenes de terceros para recopilar las siguientes actualizaciones, parches o extensiones disponibles:

* Los metadatos acerca de todos los parches ESXi 5.5 y ESXi 6.x independientemente de si tiene hosts de dichas versiones en su entorno.
* Los metadatos sobre los parches de ESXi 5.5 y ESXi 6.x y sobre las extensiones de direcciones URL de proveedores de terceros.
* Notificaciones, alertas y recuperaciones de parches para hosts ESXi 5.5 y ESXi 6.x.
* Metadatos sobre actualizaciones para dispositivos virtuales.

VUM admite la recuperación de parches para hosts que ejecutan ESXi 5.0 o posterior. Se recupera un parche si el parche liberado tiene problemas o problemas potenciales. Después de explorar los hosts en la instancia de VMware vCenter Server on {{site.data.keyword.cloud}}, VUM le avisa si el parche recuperado se instala en un host determinado. Los parches recuperados no se pueden instalar en hosts con VUM. VUM también suprime todos los parches recuperados del repositorio de parches. Después de que se publique un parche que solucione el problema, VUM descarga el nuevo parche en su repositorio de parches. Si ha instalado el parche problemático, VUM le notifica que se ha publicado una solución y le solicita que aplique el parche nuevo.

La interfaz de cliente VUM proporciona dos vistas principales:
*	Vista de administración
*	Vista de conformidad

##	Vista de administración
{: #vum-overview-admin-view}

Se accede a la vista de administración navegando a **Inicio** > **Gestor de actualizaciones** y seleccionando las direcciones IP de la instancia de Update Manager. En la vista Administración, puede realizar las tareas siguientes:
*	Configurar los valores del gestor de actualizaciones
*	Crear y gestionar las líneas base y los grupos de línea base
*	Ver sucesos de Update Manager
*	Revisar el repositorio de parches y las actualizaciones de dispositivos virtuales disponibles
*	Revisar y comprobar notificaciones
*	Importar imágenes ESXi

##	Vista de conformidad
{: #vum-overview-compliance-view}

Se accede a la vista de conformidad de un objeto de inventario seleccionado desde **Hosts y clústeres** o **Máquinas y plantillas** y pulsando el **separador Update Manager**. En la vista Conformidad de Update Manager, puede realizar las tareas siguientes:
*	Ver la conformidad y los resultados de la exploración de cada objeto de inventario seleccionado
*	Adjuntar y desconectar las líneas base y los grupos de línea base de un objeto de inventario seleccionado
*	Explorar un objeto de inventario seleccionado
*	Parches de transferencia o extensiones a hosts
*	Corregir un objeto de inventario seleccionado

## Enlaces relacionados
{: #vum-overview-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demostraciones)
