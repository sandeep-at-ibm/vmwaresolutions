---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ampliación y reducción de la capacidad para instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingremovingservers}

Puede ampliar o reducir la capacidad de la instancia de VMware vCenter Server con NSX-T según sus necesidades empresariales añadiendo o eliminando servidores ESXi o almacenamiento del sistema de archivos de red (NFS).

* A partir del release V3.0, puede añadir o eliminar de forma simultánea almacenamiento NFS y servidores ESXi en los clústeres que tengan el estado
**Listo para su uso**. Por ejemplo, puede añadir o eliminar un servidor ESXi en un clúster y añadir o eliminar almacenamiento NFS en otro clúster.
* A partir del release V2.9, puede añadir nuevos servidores ESXi a un clúster mientras los servidores estén en modalidad de mantenimiento. Además, puede añadir o eliminar simultáneamente servidores ESXi en varios clústeres.

**Notas**:
* Si el clúster inicial tiene vSAN como almacenamiento, el hecho de añadir uno o varios servidores ESXi después del despliegue puede aumentar la capacidad de almacenamiento del clúster.
* Puede añadir o eliminar comparticiones de almacenamiento NFS a o desde un clúster de vCenter Server NFS o vSAN con NSX-T existente.

## Adición de servidores ESXi a instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingremovingservers-adding}

### Antes de añadir servidores ESXi
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* Siempre que sea posible, añada servidores ESXi utilizando la consola de {{site.data.keyword.vmwaresolutions_full}}, ya que los cambios que realice en el cliente web de VMware vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}. Por lo tanto, añada servidores ESXi a vCenter Server solo para servidores ESXi locales o servidores ESXi que no pueda o no vaya a gestionar en la consola de
{{site.data.keyword.vmwaresolutions_short}}.
* Una instancia de vCenter Server con NSX-T con almacenamiento NFS debe tener como mínimo 3 servidores ESXi. Puede ampliar el clúster predeterminado para que tenga hasta un máximo de 51 servidores ESXi. Cada uno de los clústeres no predeterminados se puede ampliar hasta tener un máximo de 59 servidores ESXi.
* Una instancia de vCenter Server con NSX-T con almacenamiento vSAN debe tener como mínimo 4 servidores ESXi.

### Procedimiento para añadir servidores ESXi
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea ampliar la capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster al que desea añadir servidores ESXi.
5. En la sección **Servidores ESXi**, pulse **Añadir**.
6. En la ventana **Añadir servidor**, escriba el número de servidores que desea añadir.
7. Opcionalmente, marque el recuadro de selección para añadir servidores durante la modalidad de mantenimiento.
8. Revise el coste estimado y pulse **Añadir**.

### Resultados después de añadir servidores ESXi
{: #vc_nsx-t_addingremovingservers-adding-results}

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para añadir servidores ESXi se está procesando. En la consola, el estado del clúster asociado con los servidores ESXi se cambia a **Modificando**.
3. Si no ve que los nuevos servidores ESXi se han añadido a la lista del clúster, compruebe las notificaciones de correo electrónico o de la consola para ver más detalles sobre la anomalía.

Si va a añadir servidores ESXi durante la modalidad de mantenimiento, las máquinas virtuales (VM) no se migran a los nuevos servidores hasta que se elimina el clúster de la modalidad de mantenimiento.   
{:important}

## Eliminación de servidores ESXi de instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingremovingservers-removing}

### Antes de eliminar los servidores ESXi
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* Siempre que sea posible, elimine servidores ESXi utilizando la consola de {{site.data.keyword.vmwaresolutions_full}}, ya que los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}. Por lo tanto, elimine servidores ESXi de vCenter Server solo para servidores ESXi locales o servidores ESXi que no pueda o no vaya a gestionar en la consola de
{{site.data.keyword.vmwaresolutions_short}}.
* Una instancia de vCenter Server con NSX-T con almacenamiento NFS debe tener como mínimo 3 servidores ESXi y una instancia de vCenter Server con NSX-T con almacenamiento vSAN debe tener como mínimo 4 servidores ESXi.
* Si se eliminan servidores ESXi, los servidores se colocan en modalidad de mantenimiento, y, después de eso, todas las VM que se ejecutan en los servidores se migran antes de que se eliminen de vCenter Server. Para tener el máximo control sobre la reubicación de las VM, se recomienda colocar los servidores ESXi que se van a eliminar en modalidad de mantenimiento y migrar manualmente las VM que se ejecutan en los mismos mediante el cliente web de VMware vSphere. Después de eso, elimine los servidores ESXi utilizando la consola de {{site.data.keyword.vmwaresolutions_short}}.

### Procedimiento para eliminar servidores ESXi
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea contratar capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster desde el que desea eliminar los servidores ESXi.
5. En la sección **Servidores ESXi**, seleccione los servidores que desea eliminar y pulse **Eliminar**.

### Resultados después de eliminar servidores ESXi
{: #vc_nsx-t_addingremovingservers-removing-results}

1. Puede experimentar un ligero retardo en la consola, mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para eliminar servidores ESXi se está procesando. En la consola, el estado del clúster asociado con los servidores ESXi se cambia a **Modificando**.
3. La infraestructura de {{site.data.keyword.cloud_notm}} reclama por completo los servidores ESXi al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días.

   Se le facturará por los servidores ESXi eliminados hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
   {:note}

## Adición de almacenamiento NFS a instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### Antes de añadir almacenamiento NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

No añada almacenamiento NFS desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}. IBM no gestionará las comparticiones de archivos NFS que añada manualmente a una instancia.

### Procedimiento para añadir almacenamiento NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

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
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para añadir almacenamiento NFS se está procesando. En la consola, el estado del clúster asociado con el almacenamiento NFS se cambia a **Modificando**.
3. Si no ve que el nuevo almacenamiento NFS se ha añadido a la lista del clúster, compruebe las notificaciones de correo electrónico o de la consola para ver más detalles sobre la anomalía.

## Eliminación de almacenamiento NFS de instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### Antes de eliminar almacenamiento NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* No elimine almacenamiento NFS desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}.
* Antes de eliminar el almacenamiento NFS, asegúrese de haber eliminado todas las máquinas virtuales que residen en el almacenamiento.
* Asegúrese de que las comparticiones que va a eliminar estén asociadas a la instancia correcta de vCenter Server.
* El clúster debe estar en el estado **Listo para su uso**.

### Procedimiento para eliminar almacenamiento NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea contratar capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster del que desea eliminar almacenamiento NFS.
5. En la sección **Almacenamiento**, seleccione el almacenamiento compartido que desea eliminar y pulse **Suprimir**.
6. Pulse **Eliminar** en la ventana **Eliminar almacenamiento**.

### Resultados después de eliminar almacenamiento NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. Puede experimentar un ligero retardo en la consola, mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Permita que la operación finalice por completo antes de realizar más cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para eliminar almacenamiento NFS se está procesando. En la consola, el estado del clúster asociado con el almacenamiento NFS se cambia a **Modificando**.
3. La infraestructura de {{site.data.keyword.cloud_notm}} reclama por completo el almacenamiento NFS al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días.

   Se le facturará por el almacenamiento NFS eliminado hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
   {:note}

## Enlaces relacionados
{: #vc_nsx-t_addingremovingservers-related}

* [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requisitos y planificación de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Solicitud de instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [Colocación de un host en modalidad de mantenimiento](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Soporte del procesador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/s/article/1003212){:new_window}
