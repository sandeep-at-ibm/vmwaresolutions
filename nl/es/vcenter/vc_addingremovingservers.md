---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ampliación y reducción de la capacidad para instancias de vCenter Server
{: #vc_addingremovingservers}

Puede ampliar o reducir la capacidad de la instancia de VMware vCenter Server según sus necesidades empresariales añadiendo o eliminando servidores ESXi o almacenamiento del sistema de archivos de red (NFS).

A partir del release V2.9, puede añadir nuevos servidores ESXi a un clúster mientras los servidores estén en modalidad de mantenimiento. Además, puede añadir o eliminar simultáneamente servidores ESXi en varios clústeres. Están disponibles las siguientes operaciones simultáneas:

* Añadir hosts a un clúster y añadir hosts a clústeres adicionales.
* Eliminar hosts de un clúster y eliminar hosts de clústeres adicionales.
* Añadir hosts a un clúster y eliminar hosts de clústeres adicionales.
* Eliminar hosts de un clúster y añadir hosts a clústeres adicionales.

Puede añadir o eliminar comparticiones de almacenamiento NFS a o desde un clúster NFS o vSAN vCenter Server existente.
{:note}

Si el clúster inicial tiene vSAN como almacenamiento, el hecho de añadir uno o varios servidores ESXi después del despliegue puede aumentar la capacidad de almacenamiento del clúster.

## Adición de servidores ESXi a instancias de vCenter Server
{: #vc_addingremovingservers-adding}

### Antes de añadir servidores ESXi
{: #vc_addingremovingservers-adding-prereq}

* No añada servidores ESXi desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_full}}.
* Una instancia de vCenter Server con almacenamiento NFS debe tener como mínimo 2 servidores ESXi. Para las instancias desplegadas en la V2.1 o posterior, puede ampliar el clúster predeterminado para que tenga hasta un máximo de 51 servidores ESXi. Cada uno de los clústeres no predeterminados se puede ampliar hasta tener un máximo de 59 servidores ESXi.
* Una instancia de vCenter Server con almacenamiento vSAN debe tener como mínimo 4 servidores ESXi.
* Para instancias de vCenter Server desplegados en V2.0 o anterior, puede ampliar cada clúster para que tenga un máximo de 32 servidores ESXi.
* Puede añadir entre 1 y 20 servidores ESXi a la vez. Para obtener más información sobre el número mínimo de servidores ESXi, consulte [¿Está altamente disponible una instancia de vCenter Server de dos nodos?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)

### Procedimiento para añadir servidores ESXi
{: #vc_addingremovingservers-adding-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea ampliar la capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster al que desea añadir servidores ESXi.
5. En la sección **Servidores ESXi**, pulse **Añadir**.
6. En la ventana **Añadir servidor**, escriba el número de servidores que desea añadir.
7. Opcionalmente, marque el recuadro de selección para añadir servidores durante la modalidad de mantenimiento.
8. Revise el coste estimado y pulse **Añadir**.

### Resultados después de añadir servidores ESXi
{: #vc_addingremovingservers-adding-results}

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para añadir servidores ESXi se está procesando. En la consola, el estado del clúster asociado con los servidores ESXi se cambia a **Modificando**.
3. Si no ve que los nuevos servidores ESXi se han añadido a la lista del clúster, compruebe las notificaciones de correo electrónico o de la consola para ver más detalles sobre la anomalía.
4. Debe utilizar la consola de Zerto Virtual Manager (ZVM) y la dirección IP de Zerto Virtual Replication Appliance (VRA) llenada previamente para desplegar de forma manual la máquina virtual (VM) del VRA en las circunstancias siguientes:
   * Si añade servidores ESXi a un clúster predeterminado mientras los servidores están en modalidad de mantenimiento y está instalado Zerto para {{site.data.keyword.cloud_notm}}.
   * Si añade Zerto para {{site.data.keyword.cloud_notm}} a una instancia de vCenter Server que tiene un servidor ESXi que está en modalidad de mantenimiento.

Si va a añadir servidores ESXi durante la modalidad de mantenimiento, las máquinas virtuales no se migran a los nuevos servidores hasta que se elimina la modalidad de mantenimiento.   
{:important}

## Eliminación de servidores ESXi de instancias de vCenter Server
{: #vc_addingremovingservers-removing}

### Antes de eliminar los servidores ESXi
{: #vc_addingremovingservers-removing-prereq}

* No elimine servidores ESXi desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}.
* Una instancia de vCenter Server con almacenamiento NFS debe tener como mínimo 2 servidores ESXi y una instancia de vCenter Server con almacenamiento vSAN debe tener como mínimo 4 servidores ESXi.
* Antes de eliminar servidores ESXi con el servicio de F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalado, debe migrar las máquinas virtuales de F5 BIG-IP y FortiGate a un servidor ESXi distinto al que está alojando las máquinas virtuales.
* Antes de eliminar servidores ESXi con el servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} instalado, asegúrese de que no haya operaciones de copia de seguridad o restauración activas (anómalas o en curso), porque estas operaciones activas podrían impedir que se eliminaran los servidores ESXi.
* Si se eliminan servidores ESXi, los servidores se colocan en modalidad de mantenimiento, y, después de eso, todas las máquinas virtuales (VM) que se ejecutan en los servidores se migran antes de que se eliminen de vCenter Server. Para tener el máximo control sobre la reubicación de las VM, se recomienda colocar los servidores ESXi que se van a eliminar en modalidad de mantenimiento y migrar manualmente las VM que se ejecutan en los mismos mediante el cliente web de VMware vSphere. Después de eso, elimine los servidores ESXi utilizando la consola de {{site.data.keyword.vmwaresolutions_short}}.

### Procedimiento para eliminar servidores ESXi
{: #vc_addingremovingservers-removing-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea contratar capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster desde el que desea eliminar los servidores ESXi.
5. En la sección **Servidores ESXi**, seleccione los servidores que desea eliminar y pulse **Eliminar**.

### Resultados después de eliminar servidores ESXi
{: #vc_addingremovingservers-removing-results}

1. Puede experimentar un ligero retardo en la consola, mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para eliminar servidores ESXi se está procesando. En la consola, el estado del clúster asociado con los servidores ESXi se cambia a **Modificando**.
3. La infraestructura de {{site.data.keyword.cloud_notm}} reclama por completo los servidores ESXi al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días.

   Se le facturará por los servidores ESXi eliminados hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
   {:note}

## Adición de almacenamiento NFS a instancias de vCenter Server
{: #section-adding-nfs-storage-to-vcenter-server-instances}

### Antes de añadir almacenamiento NFS
{: #vc_addingremovingservers-adding-nfs-storage-prereq}

No añada almacenamiento NFS desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}. IBM no gestionará las comparticiones de archivos NFS que añada manualmente a una instancia.

### Procedimiento para añadir almacenamiento NFS
{: #vc_addingremovingservers-adding-nfs-storage-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea ampliar la capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster al que desea añadir almacenamiento NFS.
5. En la sección **Almacenamiento**, pulse **Añadir**.
6. En la ventana **Almacenamiento**, complete la configuración del almacenamiento.
   * Si desea añadir y configurar los mismos valores para todas las comparticiones de archivos, especifique el **Número de comparticiones**, el **Rendimiento** y el **Tamaño (GB)**.
   * Si añadir y configurar comparticiones de archivos individualmente, seleccione **Configurar comparticiones individualmente** y luego pulse el icono **+** junto a la etiqueta **Añadir almacenamiento compartido** y seleccione el **rendimiento** y el **Tamaño (GB)** para cada compartición de archivos individual. Debe seleccionar al menos una unidad compartida de archivo.
7. Pulse **Añadir almacenamiento NFS**.

### Resultados después de añadir almacenamiento NFS
{: #vc_addingremovingservers-adding-nfs-storage-results}

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para añadir almacenamiento NFS se está procesando. En la consola, el estado del clúster asociado con el almacenamiento NFS se cambia a **Modificando**.
3. Si no ve que el nuevo almacenamiento NFS se ha añadido a la lista del clúster, compruebe las notificaciones de correo electrónico o de la consola para ver más detalles sobre la anomalía.

## Eliminación de almacenamiento NFS de instancias de vCenter Server
{: #vc_addingremovingservers-removing-nfs-storage}

### Antes de eliminar almacenamiento NFS
{: #vc_addingremovingservers-removing-nfs-storage-prereq}

* No elimine almacenamiento NFS desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}.
* Antes de eliminar el almacenamiento NFS, asegúrese de haber eliminado todas las máquinas virtuales que residen en el almacenamiento.
* Asegúrese de que las comparticiones que va a eliminar estén asociadas a la instancia correcta de vCenter Server.
* El clúster debe estar en el estado **Listo para su uso**.

### Procedimiento para eliminar almacenamiento NFS
{: #vc_addingremovingservers-removing-nfs-storage-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea contratar capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster del que desea eliminar almacenamiento NFS.
5. En la sección **Almacenamiento**, seleccione el almacenamiento compartido que desea eliminar y pulse **Suprimir**.
6. Pulse **Eliminar** en la ventana **Eliminar almacenamiento**.

### Resultados después de eliminar almacenamiento NFS
{: #vc_addingremovingservers-removing-nfs-storage-results}

1. Puede experimentar un ligero retardo en la consola, mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para eliminar almacenamiento NFS se está procesando. En la consola, el estado del clúster asociado con el almacenamiento NFS se cambia a **Modificando**.
3. La infraestructura de {{site.data.keyword.cloud_notm}} reclama por completo el almacenamiento NFS al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días.

   Se le facturará por el almacenamiento NFS eliminado hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
   {:note}

## Enlaces relacionados
{: #vc_addingremovingservers-related}

* [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requisitos y planificación de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [Colocación de un host en modalidad de mantenimiento](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Soporte del procesador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
