---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server Hybridity add host, add server vCenter Server Hybridity, remove host vCenter Server Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_addingremovingservers}

Puede ampliar o reducir la capacidad de la instancia de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity) según sus necesidades empresariales añadiendo o eliminando servidores ESXi.

A partir del release de v3.1, puede añadir nuevos servidores ESXi a un clúster existente seleccionando una configuración existente o una configuración alternativa a la de los hosts existentes en el clúster. Las configuraciones existentes están disponibles para la selección instantánea cuando se hace el pedido del nuevo servidor. Para evitar problemas de rendimiento o estabilidad, se recomienda que los clústeres utilicen la misma configuración o una configuración similar con respecto a la CPU, la RAM y el almacenamiento. Esta funcionalidad es útil para actualizaciones de hardware dentro del mismo clúster. Un clúster sólo puede tener un tipo de almacenamiento.

A partir del release V2.9, puede añadir nuevos servidores ESXi a un clúster mientras el clúster esté en modalidad de mantenimiento. Además, puede añadir o eliminar simultáneamente servidores ESXi en varios clústeres. Están disponibles las siguientes operaciones simultáneas:

* Añadir hosts a un clúster y añadir hosts a clústeres adicionales.
* Eliminar hosts de un clúster y eliminar hosts de clústeres adicionales.
* Añadir hosts a un clúster y eliminar hosts de clústeres adicionales.
* Eliminar hosts de un clúster y añadir hosts a clústeres adicionales.

Puesto que el clúster inicial tiene vSAN como almacenamiento, el hecho de añadir uno o varios servidores ESXi después del despliegue puede aumentar la capacidad de almacenamiento del clúster.

## Adición de servidores ESXi a vCenter Server con instancias del paquete híbrido (Hybridity)
{: #vc_hybrid_addingremovingservers-adding}

### Antes de añadir servidores ESXi
{: #vc_hybrid_addingremovingservers-adding-prereq}

* Siempre que sea posible, añada servidores ESXi utilizando la consola de {{site.data.keyword.vmwaresolutions_full}}, ya que los cambios que realice en el cliente web de VMware vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}. Por lo tanto, añada servidores ESXi a vCenter Server solo para servidores ESXi locales o servidores ESXi que no pueda o no vaya a gestionar en la consola de
{{site.data.keyword.vmwaresolutions_short}}.
* El almacenamiento vSAN requiere al menos 4 servidores ESXi.

## Procedimiento para añadir servidores ESXi
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea ampliar la capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster al que desea añadir servidores ESXi.
5. En la tabla **Servidores ESXi**, pulse **Añadir**.
6. En la ventana **Añadir servidor**, escriba el número de servidores que desea añadir.
7. Opcionalmente, marque el recuadro de selección para añadir servidores durante la modalidad de mantenimiento. El recuadro de selección está seleccionado de forma predeterminada.

   Cuando se suministre el nuevo servidor ESXi, las máquinas virtuales (VM) se migran inmediatamente a los nuevos servidores si no selecciona la casilla de verificación **Modalidad de mantenimiento**. No se recibe un mensaje de confirmación antes de que empiece la migración.
   {:important}

8. Complete la configuración del servidor nativo.
   * Seleccione una configuración a partir de los hosts existentes en el clúster.
   * Seleccione una configuración nueva de {{site.data.keyword.baremetal_short_sing}} y especifique el modelo de CPU y el tamaño de RAM.
9. Complete la configuración del almacenamiento. Especifique los tipos de disco para la capacidad y los
discos de memoria caché, el número de discos y la edición de licencia vSAN. Si desea más almacenamiento, marque el recuadro **Intel Optane de alto rendimiento**.
10. Revise el coste estimado y pulse **Añadir**.

  También puede añadir los recursos suministrados a la herramienta de estimación {{site.data.keyword.cloud_notm}}, pulsando **Añadir a estimación**. Esto es útil si desea estimar el coste de los recursos estimare {{site.data.keyword.vmwaresolutions_short}} seleccionados junto con otros recursos de {{site.data.keyword.cloud_notm}} que le podría interesar adquirir.

### Resultados después de añadir servidores ESXi
{: #vc_hybrid_addingremovingservers-adding-results}

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para añadir servidores ESXi se está procesando. En la consola, el estado del clúster asociado con los servidores ESXi se cambia a **Modificando**.
3. Si no ve que los nuevos servidores ESXi se han añadido a la lista del clúster, compruebe las notificaciones de correo electrónico o de la consola para ver más detalles sobre la anomalía.

Si va a añadir servidores ESXi durante la modalidad de mantenimiento, las máquinas virtuales (VM) no se migran a los nuevos servidores hasta que se elimina el clúster de la modalidad de mantenimiento.   
{:important}

## Eliminación de servidores ESXi de vCenter Server con instancias del paquete híbrido (Hybridity)
{: #vc_hybrid_addingremovingservers-removing}

### Antes de eliminar los servidores ESXi
{: #vc_hybrid_addingremovingservers-removing-prereq}

* Siempre que sea posible, elimine servidores ESXi utilizando la consola de {{site.data.keyword.vmwaresolutions_full}}, ya que los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}. Por lo tanto, elimine servidores ESXi de vCenter Server solo para servidores ESXi locales o servidores ESXi que no pueda o no vaya a gestionar en la consola de
{{site.data.keyword.vmwaresolutions_short}}.
* El almacenamiento vSAN requiere al menos 4 servidores ESXi.
* Antes de eliminar servidores ESXi con el servicio de F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalado, debe migrar las máquinas virtuales de F5 BIG-IP y FortiGate a un servidor ESXi distinto al que está alojando las máquinas virtuales.
* Antes de eliminar los servidores ESXi con el servicio de IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} instalado, asegúrese de que no haya operaciones de copia de seguridad o restauración activas (anómalas o en curso), porque estas operaciones activas podrían impedir que se eliminen los servidores ESXi.
* Si se eliminan servidores ESXi, los servidores se colocan en modalidad de mantenimiento, y, después de eso, todas las máquinas virtuales (VM) que se ejecutan en los servidores se migran antes de que se eliminen de vCenter Server. Para tener el máximo control sobre la reubicación de las VM, se recomienda colocar los servidores ESXi que se van a eliminar en modalidad de mantenimiento y migrar manualmente las VM que se ejecutan en los mismos mediante el cliente web de VMware vSphere. Después de eso, elimine los servidores ESXi mediante la consola de {{site.data.keyword.vmwaresolutions_short}}.

## Procedimiento para eliminar servidores ESXi
{: #vc_hybrid_addingremovingservers-removing-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea contratar capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster desde el que desea eliminar los servidores ESXi.
5. En la tabla **Servidores ESXi**, seleccione los servidores que desee eliminar y pulse **Eliminar**.

### Resultados después de eliminar servidores ESXi
{: #vc_hybrid_addingremovingservers-removing-results}

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Deje que la operación finalice por completo antes de realizar otros cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para eliminar servidores ESXi se está procesando. En la consola, el estado del clúster asociado con los servidores ESXi se cambia a **Modificando**.
3. La infraestructura de {{site.data.keyword.cloud_notm}} reclama por completo los servidores ESXi al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días.

   Se le facturará por los servidores ESXi eliminados hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
   {:note}

## Enlaces relacionados
{: #vc_hybrid_addingremovingservers-related}

* [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requisitos y planificación de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Colocación de un host en modalidad de mantenimiento](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Soporte del procesador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/s/article/1003212){:external}
