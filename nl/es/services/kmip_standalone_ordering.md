---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-11"

---

# Solicitud de instancias de KMIP for VMware on IBM Cloud

Puede solicitar una instancia de KMIP for VMware on {{site.data.keyword.cloud}} sin asociarla a ninguna instancia de VMware para poder gestionar de forma flexible el servicio y las instancias.

## Antes de empezar

Asegúrese de haber realizado las tareas siguientes:
*  Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Cuentas de usuario y valores](../vmonic/useraccount.html).
*  Ha revisado todas las consideraciones del apartado [Consideraciones sobre la instalación de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_standalone_considerations.html).

## Solicitud de instancias de KMIP for VMware on IBM Cloud

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Iniciación** en el panel de navegación de la izquierda.
2. En el área **Solicitar servicios adicionales**, pulse **KMIP for VMware on IBM Cloud**.
3. En la página **KMIP for VMware on IBM Cloud**, configure los valores necesarios del servicio.
4. Pulse **Suministro**.

## Configuración de servicio de KMIP for VMware on IBM Cloud

Al solicitar este servicio, proporcione los valores siguientes:

### Nombre de instancia

Especifique un nombre para la instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}}.

### Región de servicio

Seleccione la región de {{site.data.keyword.cloud_notm}} en la que se va a alojar su instancia de KMIP for VMware {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} mantiene un punto final altamente disponible del servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} en cada región en la que está disponible el servicio.

Tabla 1. Regiones de puntos finales del servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Región         | Puntos finales               |
|:---------------|:-----------------------|
| Alemania        |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Tokio          | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| EE.UU. sur       |  <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### Clave de API para ID de servicio

Especifique la clave de API para el ID de servicio de {{site.data.keyword.cloud_notm}} que se utiliza para acceder a la instancia de IBM Key Protect Service.

### Instancia de Key Protect

Pulse **Recuperar** para obtener la lista de instancias disponibles de IBM Key Protect Service y seleccione la que se utilizará para la gestión de claves.

### Clave raíz de cliente

Pulse **Recuperar** para obtener la clave raíz del cliente que se almacena en la instancia de IBM Key Protect seleccionada.

### Reconozco que mi cuenta de infraestructura de IBM Cloud está habilitada para VRF y puntos finales de servicio

Si marca este recuadro de selección, reconoce que su cuenta de infraestructura de {{site.data.keyword.cloud_notm}} está habilitada para Virtual Routing and Forwarding (VRF) y para la conectividad con los puntos finales de servicio.

Para obtener más información, consulte:
* [Visión general de Virtual Routing and Forwarding (VRF) en IBM Cloud](../../../infrastructure/direct-link/vrf-on-ibm-cloud.html)
* [Habilitación de la cuenta para que utilice puntos finales de servicio mediante la CLI de IBM Cloud](../../../services/service-endpoint/enable-servicepoint.html#getting-started)

## Resultados

La solicitud de la instancia comienza automáticamente. Recibirá una confirmación de que el pedido se está procesando y puede comprobar el estado del pedido consultando los detalles de la instancia.

Cuando la instancia esté lista para ser utilizada, el estado de la instancia pasará a ser **Instalado** y recibirá una notificación por correo electrónico.

## Qué hacer a continuación

Añada certificados de cliente para la instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}} que ha solicitado. Para obtener más información, consulte [Adición, visualización y supresión de certificados para instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_standalone_addingdeletingcert.html).

### Enlaces relacionados

* [Visualización de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_standalone_viewing.html)
* [Supresión de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_standalone_deleting.html)
* [Sucesos de Activity Tracker](../vmonic/at-events.html)
