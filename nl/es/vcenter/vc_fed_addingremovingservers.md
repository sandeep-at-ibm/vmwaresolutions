---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Ampliación y reducción de la capacidad para instancias de VMware Federal

Puede ampliar o reducir la capacidad de la instancia de VMware Federal según sus necesidades empresariales añadiendo o eliminando servidores ESXi.

Si el clúster primario tiene vSAN como almacenamiento, el hecho de añadir uno o varios servidores ESXi después del despliegue puede aumentar la capacidad de almacenamiento del clúster.

**Nota:** esta característica solo está disponible para las instancias de VMware Federal que no se han protegido.

## Antes de empezar

* No añada ni elimine servidores ESXi desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_full}}.
* Una instancia de VMware Federal con almacenamiento NFS debe tener como mínimo 2 servidores ESXi. Puede ampliar el clúster predeterminado para que tenga hasta un máximo de 51 servidores ESXi. Cada uno de los clústeres no predeterminados se puede ampliar hasta tener un máximo de 59 servidores ESXi.
* Una instancia de VMware Federal con almacenamiento vSAN debe tener como mínimo 4 servidores ESXi.
*  Si se eliminan servidores ESXi, los servidores se colocan en modalidad de mantenimiento, y, después de eso, todas las máquinas virtuales (VM) que se ejecutan en los servidores se migran antes de que se eliminen de vCenter Server. Para tener el máximo control sobre la reubicación de las VM, se recomienda colocar los servidores ESXi que se van a eliminar en modalidad de mantenimiento y migrar manualmente las VM que se ejecutan en los mismos mediante el cliente web de VMware vSphere. Después de eso, elimine los servidores ESXi mediante la consola de {{site.data.keyword.vmwaresolutions_short}}.

## Procedimiento

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia cuya capacidad desea ampliar o reducir.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster al que desea añadir servidores ESXi, o desde el que desea eliminar servidores ESXi.
5. Para añadir servidores ESXi, siga estos pasos:
   1. En la tabla **Servidores ESXi**, pulse **Añadir**.
   2. En la ventana **Añadir servidor**, escriba el número de servidores que desea añadir, pulse el enlace de precios para revisar el coste estimado y pulse **Añadir**.
6. Para eliminar servidores ESXi, seleccione los servidores que desea eliminar en la tabla **Servidores ESXi** y pulse **Eliminar**.

## Resultados

Después de iniciar la operación de adición o eliminación, puede experimentar un ligero retardo en el estado de instancia mientras pasa de **Listo para su uso** a **Modificando**. Deje que la operación finalice por completo antes de realizar otros cambios en la instancia.

Se le notificará por correo electrónico de que su solicitud para añadir o eliminar servidores ESXi se está procesando. El estado del clúster asociado con los servidores ESXi pasa a ser **Modificando**. Cuando elimine servidores, tenga en cuenta que la infraestructura de {{site.data.keyword.cloud_notm}} reclama por completo los servidores ESXi al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días.

**Atención**: se le facturará por los servidores ESXi eliminados hasta el final del ciclo de facturación de {{site.data.keyword.cloud_notm}}.

Si no ve que los nuevos servidores ESXi se han añadido a la lista del clúster, compruebe las notificaciones de correo electrónico o de la consola para ver más detalles sobre la anomalía.

### Enlaces relacionados

* [Requisitos y planificación de instancias de VMware Federal](vc_fed_planning.html)
* [Adición, visualización y supresión de clústeres para instancias de VMware Federal](fed_addviewdeleteclusters.html)
* [Colocación de un host en modalidad de mantenimiento](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Soporte del procesador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
