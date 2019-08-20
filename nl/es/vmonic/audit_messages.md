---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-24"

keywords: history message, audit history, error messages

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Mensajes de historial de instancia
{: #audit_messages}

Todas las operaciones que realiza {{site.data.keyword.cloud}} para la instancia de VMware se registran en el historial de instancia. Puede utilizar el historial de instancia como referencia para revisar estas operaciones. Para obtener más información sobre cómo revisar el historial de instancia, consulte
[Procedimiento para ver el historial de despliegue para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history).

En las secciones siguientes se proporcionan todos los mensajes posibles que se pueden emitir en el historial de instancia.

## Mensajes generales del historial de instancia
{: #audit_messages-general}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para acciones generales:

* ``Iniciando la creación del usuario de instancia y los servicios necesarios...``
* ``La creación del usuario de instancia y los servicios necesarios se ha completado.``
* ``Solicitando la licencia de vCenter Server...``
* ``Solicitando licencias de VMware...``
* ``Se ha completado la solicitud de las licencias de VMware.``
* ``Solicitando <quantity> recargos...``
* ``Iniciando la instalación y configuración de <environment>...``
* ``La instalación y configuración de <environment> se ha completado.``
* ``Iniciando componentes de VMware...``
* ``Iniciando el despliegue de la instancia...``
* ``La instancia <instance_name> está lista para su uso.``
* ``Iniciando actualización a <version>...``
* ``La actualización a <version> se ha completado.``
* ``La actualización del componente de VMware se ha completado.``
* ``Iniciando la supresión de la instancia <instance_name>...``
* ``La instancia <instance_name> se ha suprimido correctamente.``
* ``El borrado seguro de la instancia se ha completado.``
* ``Cancelando la licencia de vCenter...``
* ``Cancelando el usuario de instancia y los servicios necesarios...``
* ``Cancelando recargos de <environment>...``
* ``Cancelación de licencia de VMware en curso...``
* ``La cancelación de la licencia de VMware se ha completado.``
* ``La orden de infraestructura {{site.data.keyword.cloud_notm}} ha fallado o se ha agotado el tiempo de espera.``

## Mensajes de error de instancia
{: #audit_messages-error}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes de error de historial de instancias siguientes:

* ``Error al solicitar licencias de VMware. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar subredes. Abra una incidencia de servicio para obtener ayuda.``
* ``Error: la clave de API de la infraestructura de {{site.data.keyword.cloud_notm}} no es válida. Abra una incidencia de servicio para obtener ayuda.``
* ``Error: el centro de datos API de la infraestructura de {{site.data.keyword.cloud_notm}} no es válida. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al utilizar una imagen compartida en la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} proporcionada. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar entradas de servicio. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar subredes. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar licencias. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar servicios. Abra una incidencia de servicio para obtener ayuda.``

## Mensajes de historial de clúster
{: #audit_messages-cluster}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para clústeres de vCenter Server:

* ``Iniciando la configuración del clúster...``
* ``Iniciando la configuración de clúster para <cluster_name>...``
* ``La configuración del clúster se ha completado.``
* ``El clúster <cluster_name> está listo para su uso.``
* ``Añadiendo el nuevo clúster a vCenter...``
* ``El nuevo clúster se ha añadido a vCenter.``
* ``Iniciando la supresión del clúster <cluster_name>...``
* ``Suprimiendo el clúster <cluster_name> de vCenter...``
* ``El clúster <cluster_name> se ha suprimido de vCenter.``
* ``El clúster <cluster_name> se ha suprimido.``

## Mensajes de historial del servidor ESXi
{: #audit_messages-esxi}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para servidores ESXi:

* ``Iniciando la solicitud de <quantity> servidores ESXi...``
* ``Verificando la solicitud del servidor ESXi...``
* ``Los servidores ESXi con la dirección IP privada <ip_addresses> están listos.``
* ``Se han reclamado todos los servidores ESXi.``
* ``Añadiendo servidores ESXi a la instancia de vCenter Server...``
* ``Los servidores ESXi se han actualizado correctamente.``
* ``Iniciando solicitud de servidores ESXi para el clúster...``
* ``Iniciando solicitud de <quantity> servidores ESXi para el clúster <Cluster Name>...``
* ``Los servidores ESXi para el clúster están listos.``
* ``Los servidores ESXi con la dirección IP privada <ip_addresses> están listos para el clúster.``
* ``El servidor ESXi está listo.``
* ``La configuración del servidor ESXi se ha completado.``
* ``El servidor ESXi se ha añadido correctamente con la propiedad.``
* ``Todas las solicitudes para añadir servidores ESXi se han completado correctamente.``
* ``Añadiendo el servidor ESXi...``
* ``Solicitando un servidor nativo para el servidor ESXi...``
* ``Se han añadido nuevos servidores ESXi a vCenter.``
* ``Iniciando adición de servicios a los nuevos servidores ESXi...``
* ``Los servidores ESXi seleccionados se han cancelado correctamente.``
* ``Se han suministrado nuevos servidores ESXi.``
* ``Los nuevos servidores ESXi se han verificado y están listos.``
* ``Iniciando solicitud de <quantity> nuevos servidores ESXi para el clúster <cluster_name>...``
* ``Los servidores ESXi seleccionados se han eliminado de vCenter Server.``
* ``Iniciando eliminación de servicios para eliminar servidores ESXi...``
* ``Verificando servidores ESXi para el clúster <cluster_name>...``
* ``Los nuevos servidores ESXi del clúster han superado con éxito la verificación.``
* ``Verificando solicitud de nuevo servidor ESXi...``
* ``La verificación de la solicitud de servidores ESXi ha fallado.``
* ``Dividiendo lote de solicitud de adición de servidores ESXi.``
* ``Se han completado correctamente todas las solicitudes para eliminar servidores ESXi.``
* ``El host se ha añadido correctamente.``
* ``Los hosts se han eliminado correctamente.``
* ``Cancelación de servidor nativo en curso...``
* ``La cancelación del servidor nativo se ha completado.``
* ``Eliminando servidores ESXi de la instancia de vCenter Server...``
* ``Eliminando el servidor ESXi.``
* ``Eliminando el servidor ESXi <server_id>.``
* ``Eliminando los servidores ESXi seleccionados de vCenter Server...``
* ``Cancelando los servidores ESXi...``
* ``Cancelando los servidores ESXi seleccionados...``

## Mensajes de historial de red
{: #audit_messages-network}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para valores de red:

* ``Iniciando solicitud de VLAN pública...``
* ``La configuración de la VLAN se ha completado correctamente.``
* ``Solicitando VLAN privada adicional...``
* ``Se ha suministrado la VLAN privada adicional.``
* ``Se ha suministrado una instancia de servidor virtual de VLAN privada adicional.``
* ``Trucando VLAN privada adicional para servidores nativos...``
* ``La VLAN privada adicional se ha truncado correctamente para servidores nativos.``
* ``Cancelando la instancia de servidor virtual de VLAN privada adicional...``
* ``Cancelando VLAN...``
* ``Cancelación de VLAN en curso...``
* ``La cancelación de VLAN se ha completado.``
* ``Solicitando una licencia NSX de <type> de dos sockets...``
* ``La configuración de NSX para el nuevo clúster se ha completado.``
* ``Cancelando la licencia NSX de dos sockets...``
* ``La licencia NSX se ha cancelado correctamente.``
* ``Iniciando solicitud de subredes...``
* ``La subred está lista.``
* ``La subred privada portátil está lista.``
* ``Otorgando a la nueva subred acceso al almacenamiento NFS...``
* ``Cancelando subredes...``
* ``Cancelación de subred en curso...``
* ``Cancelando subred privada portátil de cliente...``
* ``Cancelando subred pública portátil de cliente...``
* ``Cancelando subred privada de almacenamiento resistente...``
* ``Cancelando la subred pública portátil...``
* ``La subred pública portátil está lista.``
* ``Iniciando solicitud de subred pública portátil...``
* ``La cancelación de la subred se ha completado.``
* ``Cancelando almacenamiento en red...``

## Mensajes de historial de instancias de servidor virtual
{: #audit_messages-vsi}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para instancias de servidor virtual (VSI):

* ``Solicitando una nueva instancia de servidor virtual para IBM CloudDriver...``
* ``Se ha suministrado la instancia de servidor virtual IBM CloudDriver <ip_address>.``
* ``Cancelando la instancia de servidor virtual de IBM CloudDriver <ip_address>...``
* ``Iniciando la solicitud de la instancia de servidor virtual de Microsoft Windows para Microsoft Active Directory/DNS...``
* ``Verificando la solicitud de la instancia de servidor virtual de Microsoft Windows para Active Directory/DNS...``
* ``La instancia de servidor virtual de Microsoft Windows para Active Directory/DNS está lista.``
* ``Cancelación de instancia de servidor virtual en curso...``
* ``Cancelando instancias de servidor virtual asociadas...``
* ``La cancelación de la instancia de servidor virtual se ha completado.``

## Mensajes de historial de IBM CloudBuilder
{: #audit_messages-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para IBM CloudBuilder:

* ``Verificando solicitud de instancia de servidor virtual de IBM CloudBuilder...``
* ``Iniciando solicitud de la instancia de servidor virtual de IBM CloudBuilder...``
* ``La instancia de servidor virtual de IBM CloudBuilder está lista.``
* ``IBM CloudBuilder está listo para el servicio.``
* ``Rechazando instancia de servidor virtual de IBM CloudBuilder...``

## Mensajes de historial de IBM CloudDriver
{: #audit_messages-clouddriver}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para IBM CloudDriver:

* ``Preparando IBM CloudDriver...``
* ``IBM CloudDriver está listo.``
* ``IBM CloudDriver <ip_address> está listo para su uso.``
* ``Comprobando estado de IBM CloudDriver...``
* ``Reutilizando el IBM CloudDriver <ip_address> existente...``
* ``Reutilizando el IBM CloudDriver existente (en suministro)...``
* ``Liberando IBM CloudDriver...``
* ``Liberando IBM CloudDriver <ip_address>...``
* ``Iniciando supresión de IBM CloudDriver...``
* ``Se ha completado la supresión de IBM CloudDriver.``

## Mensajes de historial de almacenamiento
{: #audit_messages-storage}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para valores de almacenamiento:

* ``Solicitando la licencia de vSAN...``
* ``Cancelando la licencia de vSAN...``
* ``La cancelación de la licencia de vSAN se ha completado.``
* ``Solicitando <quantity> almacenamiento(s) NFS para el clúster <cluster_name>.``
* ``El nuevo almacenamiento NFS se ha añadido y está listo para su uso.``
* ``Cancelando almacenamiento compartido NFS de gestión...``
* ``El almacenamiento NFS seleccionado se ha suprimido.``
* ``Iniciando solicitud de almacenamiento resistente...``
* ``Cancelando almacenamiento resistente...``

## Mensajes de historial de servicios
{: #audit_messages-services}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para los servicios:

* ``Iniciando la configuración de servicios de gestión...``
* ``Solicitando entradas de servicio...``
* ``Se ha completado la solicitud de entradas de servicio.``
* ``Los servicios de operación de IBM están en ejecución.``
* ``Habilitando servicios predeterminados...``
* ``Los servicios predeterminados se han habilitado correctamente.``
* ``Cancelación de entrada de servicio en curso...``
* ``La cancelación de entrada de servicio se ha completado.``

## Enlaces relacionados
{: #audit_messages-related}

* [Consideraciones sobre el cambio de artefactos de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Sucesos de Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
