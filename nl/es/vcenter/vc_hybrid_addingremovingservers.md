---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-07"

---

# Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)

Puede ampliar o reducir la capacidad de la instancia de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity) según sus necesidades empresariales añadiendo o eliminando servidores ESXi.

Puesto que el clúster inicial tiene vSAN como almacenamiento, el hecho de añadir uno o varios servidores ESXi después del despliegue puede aumentar la capacidad de almacenamiento del clúster.

## Adición de servidores ESXi a vCenter Server con instancias del paquete híbrido (Hybridity)

### Antes de añadir servidores ESXi

* No añada servidores ESXi desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}.
* El almacenamiento vSAN requiere al menos 4 servidores ESXi.

## Procedimiento para añadir servidores ESXi

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea ampliar la capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster al que desea añadir servidores ESXi.
5. En la tabla **Servidores ESXi**, pulse **Añadir**.
6. En la ventana **Añadir servidor**, escriba el número de servidores que desea añadir, pulse el enlace de precios para revisar el coste estimado y pulse **Añadir**.

### Resultados después de añadir servidores ESXi

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Deje que la operación finalice por completo antes de realizar otros cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para añadir servidores ESXi se está procesando. En la consola, el estado del clúster asociado con los servidores ESXi se cambia a **Modificando**.
3. Si no ve que los nuevos servidores ESXi se han añadido a la lista del clúster, compruebe las notificaciones de correo electrónico o de la consola para ver más detalles sobre la anomalía.

## Eliminación de servidores ESXi de vCenter Server con instancias del paquete híbrido (Hybridity)

### Antes de eliminar los servidores ESXi

* No elimine servidores ESXi desde el cliente web de VMware vSphere. Los cambios que realice en el cliente web de vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}.
* El almacenamiento vSAN requiere al menos 4 servidores ESXi.
* Antes de eliminar servidores ESXi con los servicios F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalados, debe migrar el F5 BIG-IP y las VM de FortiGate a un servidor ESXi distinto al que está alojando en este momento las VM.
* Antes de eliminar servidores ESXi con el servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} instalado, asegúrese de que no haya operaciones de copia de seguridad o restauración activas (anómalas o en curso), porque estas operaciones activas podrían impedir que se eliminaran los servidores ESXi.
* Si se eliminan servidores ESXi, los servidores se colocan en modalidad de mantenimiento, y, después de eso, todas las máquinas virtuales (VM) que se ejecutan en los servidores se migran antes de que se eliminen de vCenter Server. Para tener el máximo control sobre la reubicación de las VM, se recomienda colocar los servidores ESXi que se van a eliminar en modalidad de mantenimiento y migrar manualmente las VM que se ejecutan en los mismos mediante el cliente web de VMware vSphere. Después de eso, elimine los servidores ESXi mediante la consola de {{site.data.keyword.vmwaresolutions_short}}.

## Procedimiento para eliminar servidores ESXi

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea contratar capacidad.
3. Pulse **Infraestructura** en el panel de navegación izquierdo.
4. En la tabla **CLÚSTERES**, pulse el clúster desde el que desea eliminar los servidores ESXi.
5. En la tabla **Servidores ESXi**, seleccione los servidores que desee eliminar y pulse **Eliminar**.

### Resultados después de eliminar servidores ESXi

1. Puede experimentar un ligero retardo en la consola mientras el estado de instancia pasa de **Listo para su uso** a **Modificando**. Deje que la operación finalice por completo antes de realizar otros cambios en la instancia.
2. Se le notificará por correo electrónico de que su solicitud para eliminar servidores ESXi se está procesando. En la consola, el estado del clúster asociado con los servidores ESXi se cambia a **Modificando**.
3. La infraestructura de {{site.data.keyword.cloud_notm}} reclama por completo los servidores ESXi al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días.

   **Atención**: Se le facturará por lo servidores ESXi eliminados hasta el final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}.

### Enlaces relacionados

* [Lista de materiales de vCenter Server](vc_bom.html)
* [Requisitos y planificación de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_planning.html)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingviewingclusters.html)
* [Colocación de un host en modalidad de mantenimiento](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Soporte del procesador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
