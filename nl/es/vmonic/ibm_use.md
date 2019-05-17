---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# ID de usuario de IBM y mensajes de historial de despliegue para instancias de vCenter Server
{: #ibm_use}

{{site.data.keyword.cloud}} requiere acceso a su cuenta para fines de automatización y registro de operaciones.

## ID de usuario
{: #ibm_use-user-ids}

{{site.data.keyword.vmwaresolutions_short}} mantiene un conjunto de usuarios en la cuenta que utiliza la automatización de
{{site.data.keyword.cloud_notm}} cuando realiza operaciones como añadir hosts, clústeres o almacenamiento a la instancia de VMware. Revise las secciones siguientes para ver los ID de usuario de automatización de {{site.data.keyword.cloud_notm}}.

Las operaciones de la instancia de VMware fallarán si los ID de usuario de IBM se suprimen, se inhabilitan, o si se cambian sus contraseñas.
{:important}

### ID de usuario de vCenter y Platform Services Controller
{: #ibm_use-user-ids-vcenter-psc}

A partir de V2.5, {{site.data.keyword.vmwaresolutions_short}} utiliza los ID de usuario siguientes para añadir un origen de identidad, incorporado de forma predeterminada, en vCenter.

Tabla 1. ID de usuario de vCenter y Platform Services Controller

| Usuario     | ID de usuario      | Método | Descripción |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Utilizado para la configuración de VMware, por ejemplo, configurar la alta disponibilidad de VMware y crear conmutadores distribuidos. Se utiliza tras el despliegue para emparejar instancias primarias y secundarias de vCenter Server. |
| Cliente | customerroot | SSH    | Creado solo para uso del cliente. |
| IBM      | automation@``root_domain``<br/>(usuario de Active Directory) | HTTP | Utilizado tras el despliegue para añadir y eliminar hosts y clústeres, y para desplegar y configurar máquinas virtuales para servicios complementarios. |
| Cliente | Administrator@vsphere.local | HTTP | Creado solo para uso del cliente. |

HTTP se utiliza para la configuración de vCenter, así como para las operaciones de VMware como añadir hosts, clústeres o almacenamiento para la gestión de recursos de vCenter.
{:note}

### ID de usuario de NSX Manager
{: #ibm_use-user-ids-nsx-mgr}

Los ID de usuario de NSX Manager se utilizan para añadir reglas ESG para el servicio.

Tabla 2. ID de usuario de NSX Manager

| Usuario     | ID de usuario      | Descripción |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(usuario de Active Directory) | Se utiliza tras el despliegue para añadir direcciones IP de NSX VTEP, gestionar la configuración de host y clúster al añadir hosts y clústeres, y gestionar la configuración ESG para servicios complementarios que requieren acceso a la red pública para la notificación de licencias, activación o uso. |
| Cliente | arrendatario        | Creado solo para uso del cliente. |

### ID de usuario del host ESXi
{: #ibm_use-user-ids-esxi}

Los ID de usuario de host ESXi se utilizan para añadir almacenamiento, aplicar parches, configurar clústeres vSAN y ejecutar todo el código de validación del servidor.

Tabla 3. ID de usuario del host ESXi

| Usuario     | ID de usuario      | Descripción |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Se utiliza tras el despliegue para añadir almacenamiento NFS adicional y configurar rutas para dicho almacenamiento. |
| Cliente | root         | Creado solo para uso del cliente. |

### ID de usuario de Microsoft Active Directory
{: #ibm_use-user-ids-ad}

Los ID de usuario de Active Directory se utilizan para configurar entradas DNS.

Tabla 4. ID de usuario de Active Directory

| Usuario     | ID de usuario       | Descripción |
|:---------|:------------- |:------------|
| IBM      | automation    | Se utiliza para añadir un host, añadir una máquina virtual para el servicio y configurar entradas DNS y Active Directory. |
| Cliente | Administrador | Creado solo para uso del cliente. |

## Mensajes de historial de instancia
{: #ibm_use-msgs}

Todas las operaciones que realiza {{site.data.keyword.cloud_notm}} para la instancia de VMware se registran en el historial de instancia. Puede utilizar el historial de instancia como referencia para revisar estas operaciones. Para obtener más información sobre cómo revisar el historial de instancia, consulte
[Procedimiento para ver el historial de despliegue para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history).

En las secciones siguientes se proporcionan todos los mensajes posibles que se pueden emitir en el historial de instancia.

### Mensajes generales del historial de instancia
{: #ibm_use-msgs-general}

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
* ``La solicitud de SoftLayer ha fallado o se ha agotado el tiempo de espera.``

### Mensajes de historial de clúster
{: #ibm_use-msgs-cluster}

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

### Mensajes de historial de instancias de servidor virtual
{: #ibm_use-msgs-vsi}

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

### Mensajes de historial de IBM CloudDriver
{: #ibm_use-msgs-clouddriver}

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

### Mensajes de historial del servidor ESXi
{: #ibm_use-msgs-esxi}

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

### Mensajes de historial de IBM CloudBuilder
{: #ibm_use-msgs-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para IBM CloudBuilder:

* ``Verificando solicitud de instancia de servidor virtual de IBM CloudBuilder...``
* ``Iniciando solicitud de la instancia de servidor virtual de IBM CloudBuilder...``
* ``La instancia de servidor virtual de IBM CloudBuilder está lista.``
* ``IBM CloudBuilder está listo para el servicio.``
* ``Rechazando instancia de servidor virtual de IBM CloudBuilder...``

### Mensajes de historial de almacenamiento
{: #ibm_use-msgs-storage}

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

### Mensajes de historial de red
{: #ibm_use-msgs-network}

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

### Mensajes de historial de servicios
{: #ibm_use-msgs-services}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para los servicios:

* ``Iniciando la configuración de servicios de gestión...``
* ``Solicitando entradas de servicio...``
* ``Se ha completado la solicitud de entradas de servicio.``
* ``Los servicios de operación de IBM están en ejecución.``
* ``Habilitando servicios predeterminados...``
* ``Los servicios predeterminados se han habilitado correctamente.``
* ``Cancelación de entrada de servicio en curso...``
* ``La cancelación de entrada de servicio se ha completado.``

### Mensajes de historial de vCenter Server con el paquete híbrido (Hybridity)
{: #ibm_use-msgs-hybridity}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para instancias de vCenter Server con el paquete híbrido (Hybridity):

* ``Solicitando licencias de vCenter Server con el paquete híbrido...``
* ``Iniciando la conversión de vCenter Server con el paquete híbrido...``
* ``La conversión de vCenter Server con el paquete híbrido se ha completado.``
* ``Eliminando vCenter Server con el paquete híbrido...``
* ``vCenter Server con el paquete híbrido se ha eliminado correctamente.``
* ``Cancelando la conversión de vCenter Server con el paquete híbrido...``

### Mensajes de historial de Cloud Foundation
{: #ibm_use-msgs-cf}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes siguientes para instancias de Cloud Foundation:

* ``Iniciando solicitud de instancia de Cloud Foundation...``
* ``La solicitud de Cloud Foundation se ha recibido.``
* ``Procesando la solicitud de Cloud Foundation...``
* ``Solicitando un servidor virtual a utilizar para la configuración de Cloud Foundation...``
* ``Se ha completado la solicitud del servidor virtual a utilizar para la configuración de Cloud Foundation.``
* ``Se ha verificado la solicitud del servidor virtual a utilizar para la configuración de Cloud Foundation.``
* ``Solicitando servidores nativos a utilizar para la configuración de Cloud Foundation...``
* ``Se ha completado la solicitud de los servidores nativos a utilizar para la configuración de Cloud Foundation.``
* ``Configurando red de Cloud Foundation...``
* ``Se ha completado la configuración de red de Cloud Foundation.``
* ``Solicitando subredes de Cloud Foundation...``
* ``Se ha completado la solicitud de las subredes de Cloud Foundation``
* ``Configurando la instancia de Cloud Foundation...``
* ``Personalizando y optimizando los componentes de la instancia de Cloud Foundation...``
* ``Limpieza de Cloud Foundation en curso...``
* ``La limpieza de Cloud Foundation se ha completado.``
* ``La instancia de Cloud Foundation está lista para su uso.``
* ``Personalizando y optimizando la instancia de Cloud Foundation...``
* ``La configuración de la instancia de Cloud Foundation se ha completado.``
* ``La personalización y optimización de la instancia de Cloud Foundation se ha completado.``
* ``La solicitud de componentes de Cloud Foundation se ha completado.``
* ``La supresión de la instancia de Cloud Foundation se ha completado.``
* ``La supresión de la instancia de Cloud Foundation se ha completado.``

### Mensajes de error
{: #ibm_use-msgs-error}

{{site.data.keyword.vmwaresolutions_short}} emite los mensajes de error de historial de instancias siguientes:

* ``Error al solicitar un servidor virtual utilizado para la configuración de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error: SoftLayer no ha podido suministrar un servidor virtual para utilizarlo para la configuración de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar los servidores nativos utilizados para la configuración de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar VLAN a utilizar para la configuración de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al configurar la red de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar subredes de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al crear servicios de administración para crear la instancia de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar licencias de VMware. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar subredes. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al configurar la instancia de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al personalizar y optimizar la instancia de Cloud Foundation. Abra una incidencia de servicio para obtener ayuda.``
* ``Error: la clave de API de SoftLayer no es válida. Abra una incidencia de servicio para obtener ayuda.``
* ``Error: el centro de datos de SoftLayer no es válido. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al utilizar una imagen compartida en la cuenta de SoftLayer proporcionada. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar entradas de servicio. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar subredes. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar licencias. Abra una incidencia de servicio para obtener ayuda.``
* ``Error al solicitar servicios. Abra una incidencia de servicio para obtener ayuda.``


## Enlaces relacionados
{: #ibm_use-related}

* [Consideraciones sobre el cambio de artefactos de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Sucesos de Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
