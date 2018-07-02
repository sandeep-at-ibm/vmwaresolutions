---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-03"

---

# Gestión de cuentas y valores de usuario

{{site.data.keyword.vmwaresolutions_full}} se comunica con la infraestructura de {{site.data.keyword.cloud_notm}} mediante llamadas de {{site.data.keyword.slapi_short}}. Para acceder a la {{site.data.keyword.slapi_short}} de forma segura, debe asociar las credenciales de su cuenta de {{site.data.keyword.cloud_notm}} a su cuenta de usuario de {{site.data.keyword.vmwaresolutions_short}}.

**Nota**: la cuenta de {{site.data.keyword.cloud_notm}} se conocía anteriormente como cuenta de IBM SoftLayer.

En la consola de {{site.data.keyword.vmwaresolutions_short}}, también puede especificar si desea recibir notificaciones por correo electrónico sobre diversos sucesos.

## Antes de empezar

* Solo puede asociar una cuenta de {{site.data.keyword.cloud_notm}} a su cuenta de usuario de {{site.data.keyword.vmwaresolutions_short}}.
* La cuenta de {{site.data.keyword.cloud_notm}} que utilice debe cumplir ciertos requisitos. Para obtener más información, consulte [Requisitos de la cuenta de {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).
* Si la clave de API de su cuenta de {{site.data.keyword.cloud_notm}} se modifica, debe actualizar la clave en su cuenta de usuario de {{site.data.keyword.vmwaresolutions_short}}.

   **Importante**: es su responsabilidad asegurarse de que la clave de API que se guarda en la página **Configuración** es correcta y está actualizada.
   De lo contrario, las operaciones que requieren la validación de clave de API podrían fallar.

Para asociar la cuenta de {{site.data.keyword.vmwaresolutions_short}} con la cuenta de {{site.data.keyword.cloud_notm}}, especifique las credenciales de la cuenta de {{site.data.keyword.cloud_notm}} en la página **Configuración** de la consola de {{site.data.keyword.vmwaresolutions_short}}.

Después de asociar la cuenta de {{site.data.keyword.cloud_notm}}, la consola recupera automáticamente las credenciales de la cuenta de {{site.data.keyword.cloud_notm}} para comunicarse con el entorno de VMware en {{site.data.keyword.cloud_notm}}.

## Procedimiento

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Configuración** en el panel de navegación izquierdo.
2. Si desea recibir una notificación por correo electrónico cuando se produzcan nuevos sucesos, marque el recuadro de selección **Habilitar notificaciones por correo electrónico**.
3. Si desea recibir una notificación en la consola cuando se produzcan nuevos sucesos, marque el recuadro de selección **Habilitar notificaciones de consola**.
4. En el área **Credenciales de infraestructura de IBM Cloud**, escriba el nombre de usuario de la cuenta de {{site.data.keyword.cloud_notm}} y siga las instrucciones de la consola para especificar la clave de {{site.data.keyword.slapi_short}}.
5. Pulse **Guardar credenciales**.

## Resultados

Las credenciales almacenadas de la cuenta de {{site.data.keyword.cloud_notm}} se utilizan en futuras operaciones y requieren la interacción con la infraestructura de {{site.data.keyword.cloud_notm}}. Si las notificaciones por correo electrónico o en la consola están habilitadas para determinados sucesos de la instancia, se le notificará por correo electrónico o mediante mensajes en la consola cuando se produzcan dichos sucesos.

## Enlaces relacionados

* [Preguntas frecuentes](faq.html)
* [Pedido de instancias de Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedido de instancias de vCenter Server](../vcenter/vc_orderinginstance.html)
* [Notificaciones](notifications.html)
* [API de SoftLayer](../../../customer-portal/cpapi.html){:new_window}
