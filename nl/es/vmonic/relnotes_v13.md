---

copyright:

  years:  2016, 2017

lastupdated: "2017-01-23"

subcollection: vmware-solutions


---

# Notas del release para V1.3
{: #relnotes_v13}

Este release incluye nuevas características, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Almacenamiento a nivel de archivos compartidos para instancias de vCenter Server
{: #relnotes_v13-storage}

Ahora puede añadir NAS (almacenamiento conectado a red) compartido a instancias de vCenter Server. La adición de esta característica le permite ejecutar cargas de trabajo de producción en vCenter Server y evitar la pérdida de datos si se producen errores en un nodo. El almacenamiento de archivos NFS (sistema de archivos de red) se proporciona como una opción en el proceso de pedido de instancias de vCenter Server. Para obtener más información, consulte [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Eliminación de la recuperación tras error de Zerto
{: #relnotes_v13-zerto}

Tanto si ha solicitado la recuperación tras desastre de Zerto como parte de la instancia como si la ha añadido a una instancia existente, ahora puede eliminar este servicio cuando ya no lo necesite. Después de solicitar la eliminación del servicio desde la consola, el equipo de soporte de IBM le guiará por el proceso de eliminación.

## Instancias de VMware NSX Edge para Cloud Foundation
{: #relnotes_v13-nsx}

Ahora NSX Edge se incluye como parte de las nuevas instancias de Cloud Foundation que se solicitan. NSX Edge ofrece seguridad de extremo a extremo de la red y servicios de pasarela para aislar una red virtualizada.

Durante el despliegue de la instancia, IBM® despliega Management NSX Edge Services Gateway (ESG). Las máquinas virtuales de gestión de IBM utilizan esta ESG para comunicarse con componentes externos específicos de gestión de IBM que están relacionados con la automatización. Esta ESG se despliega para incluir dos interfaces: una interfaz está conectada a la VLAN privada de {{site.data.keyword.cloud_notm}}, y la otra está conectada a la VLAN pública de {{site.data.keyword.cloud_notm}}.

Para garantizar la seguridad, se imponen reglas de cortafuegos que solo permiten las comunicaciones HTTPS de salida iniciadas por las máquinas virtuales de gestión. Esta ESG se despliega en una configuración de tipo Grande y solo el equipo de soporte de IBM puede modificar la configuración.

Para obtener más información, consulte los temas siguientes:
* [¿Representa NSX Edge de servicios de gestión un riesgo para la seguridad?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#faq-mgmt-nsx)
* [Documentación de VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Proceso de pedido de una instancia
{: #relnotes_v13-inst-order}

El proceso de pedido de instancias se ha mejorado para las instancias de Cloud Foundation y para las instancias de vCenter Server:

* La página de resumen muestra todos los términos y condiciones aplicables para todos los componentes y servicios solicitados, para que pueda revisar y aceptar fácilmente estos términos antes de realizar el pedido.
* Puede guardar e imprimir el resumen del pedido de la instancia antes de realizar el pedido. Con esta nueva función, puede revisar los valores y el coste de la instancia, modificar los componentes solicitados si es necesario, obtener la aprobación y luego volver a su pedido.

Para obtener más información, consulte [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Gestión de instancias
{: #relnotes_v13-inst-mgmt}

Se han realizado mejoras y se han incorporado nuevas características al proceso de gestión de instancias:

* Tanto para instancias de Cloud Foundation como para instancias de vCenter Server, puede ver y revisar el coste estimado de los servidores ESXi antes de decidir si los quiere añadir a la instancia. Después de especificar el número de servidores que desea añadir, se muestra en la consola el coste estimado por servidor al mes. Para obtener más información, consulte [Ampliación y reducción de capacidad para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).
* Tanto para instancias de Cloud Foundation como para instancias de vCenter Server, el número total de instancias se muestra en la parte superior de la página de resumen. También puede solicitar una instancia con una pulsación desde las páginas de resumen de la instancia. Además, en la página de resumen puede ver el estado detallado del pedido durante el suministro. Si mueve el puntero del ratón sobre el estado que se muestra, verá más detalles sobre el paso actual o el error, si hay alguno.
* Para instancias de Cloud Foundation, la página de detalles de la instancia muestra el historial de despliegues de la instancia, con información sobre el estado del despliegue paso a paso.
* Para instancias de Cloud Foundation, el manejo del proceso de aplicación de actualizaciones y de parches se ha mejorado al proporcionar más detalles sobre la actualización en la página **Actualización y parche**, como por ejemplo: el tiempo de inactividad que se necesita para un parche, la hora a la que se ha planificado la actualización y una indicación visual cuando se tiene que aplicar un parche necesario antes que el actual.

## Notificaciones por correo electrónico
{: #relnotes_v13-email-notif}

Ahora recibirá una notificación por correo electrónico cuando se haya realizado un nuevo pedido de despliegue de instancia y cuando se haya añadido, desplegado o eliminado un servicio de la instancia. Los valores de notificación están habilitados de forma predeterminada. Según sus preferencias, puede establecer qué notificaciones desea recibir en la página **Configuración**. Para obtener más información, consulte [Cuentas de usuario y valores](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
