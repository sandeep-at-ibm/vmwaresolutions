---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

keywords: KMIP for VMware, order KMIP stand-alone, KMIP for VMware configuration

subcollection: vmware-solutions


---

# Solicitud de instancias de KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering}

Puede solicitar una instancia de KMIP for VMware on {{site.data.keyword.cloud}} sin asociarla a ninguna instancia de VMware para poder gestionar de forma flexible el servicio y las instancias.

## Antes de empezar
{: #kmip_standalone_ordering-req}

Asegúrese de haber realizado las tareas siguientes:
* Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Cuentas de usuario y valores](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Ha revisado todas las consideraciones del apartado [Consideraciones sobre la instalación de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations-install).

## Procedimiento para solicitar instancias de KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Iniciación** en el panel de navegación de la izquierda.
2. En la sección **Servicios de VMware**, pulse la tarjeta **KMIP for VMware on IBM Cloud**.
3. En la página **KMIP for VMware on IBM Cloud**, configure los valores necesarios del servicio.
4. Pulse **Suministro**.

## Configuración de servicio de KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering-config}

Al solicitar este servicio, proporcione los valores siguientes:

### Nombre de instancia
{: #kmip_standalone_ordering-config-instance-name}

Especifique un nombre para la instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}}.

### Ubicación del servicio
{: #kmip_standalone_ordering-config-service-region}

Seleccione la ubicación de {{site.data.keyword.cloud_notm}} en la que se va a alojar su instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} mantiene un punto final altamente disponible del servicio de red KMIP for VMware on {{site.data.keyword.cloud_notm}} en cada ubicación en la que está disponible el servicio.

| Ubicación         | Puntos finales               |
|:---------------|:-----------------------|
| Dallas | <<code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code><br>y<br><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Frankfurt | <code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code><br>y<br><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code> |
| Londres | <code>kmip-1.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code><br>y<br><code>kmip-2.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Sídney | <code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code><br>y<br><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Tokio | <code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code><br>y<br><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code> |
| Washington DC | <code>kmip-1.private.us-east.vmware-solutions.cloud.ibm.com:5696</code><br>y<br><code>kmip-2.private.us-east.vmware-solutions.cloud.ibm.com:5696</code> |
{: caption="Tabla 1. Ubicaciones de puntos finales del servicio de red KMIP for VMware on {{site.data.keyword.cloud_notm}}" caption-side="top"}

### Clave de API para ID de servicio
{: #kmip_standalone_ordering-config-api-key}

Especifique la clave de API para el ID de servicio de {{site.data.keyword.cloud_notm}} que se utiliza para acceder a la instancia de servicio de Key Protect o Hyper Protect Crypto Services.

### Instancia de gestor de claves
{: #kmip_standalone_ordering-config-key-protect}

Pulse **Recuperar** para obtener la lista de instancias disponibles de gestor de claves y seleccione la que se utilizará para la gestión de claves.

### Clave raíz de cliente
{: #kmip_standalone_ordering-config-root-key}

Pulse **Recuperar** para obtener la clave raíz del cliente que se almacena en la instancia del gestor de claves seleccionada.

## Resultados
{: #kmip_standalone_ordering-results}

La solicitud de la instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}} comienza automáticamente. Recibirá una confirmación de que el pedido se está procesando y puede comprobar el estado del pedido consultando los detalles de la instancia.

Cuando la instancia esté lista para ser utilizada, el estado de la instancia pasará a ser **Instalado** y recibirá una notificación por correo electrónico.

## Qué hacer a continuación
{: #kmip_standalone_ordering-next}

Añada certificados de cliente para la instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}} que ha solicitado. Para obtener más información, consulte [Adición, visualización y supresión de certificados para instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert).

## Enlaces relacionados
{: #kmip_standalone_ordering-related}

* [Visualización de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Supresión de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Sucesos de Activity Tracker](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
