---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: set credentials, user credentials, set notifications

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestión de cuentas y valores de usuario
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} se comunica con la infraestructura de {{site.data.keyword.cloud_notm}} mediante llamadas de {{site.data.keyword.slapi_short}}. Para acceder a la {{site.data.keyword.slapi_short}} de forma segura, debe enlazar las credenciales de su cuenta de infraestructura de {{site.data.keyword.cloud_notm}} a su cuenta de {{site.data.keyword.cloud_notm}}.

También puede especificar si desea recibir notificaciones por correo electrónico y por consola sobre diversos sucesos.

## Antes de empezar
{: #useraccount-reqs}

* Solo puede enlazar una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} a una cuenta de usuario de {{site.data.keyword.cloud_notm}}.
* La cuenta de infraestructura de {{site.data.keyword.cloud_notm}} que está utilizando debe cumplir determinados requisitos. Para obtener más información, consulte [Requisitos de cuenta de infraestructura de {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req). 
* Si la clave de API para su cuenta de infraestructura de {{site.data.keyword.cloud_notm}} cambia, debe actualizar la clave en la página **Valores** de la consola de {{site.data.keyword.vmwaresolutions_short}}.

   Es su responsabilidad asegurarse de que la clave de API que se guarda en la página **Configuración** es correcta y está actualizada. De lo contrario, las operaciones que requieren la validación de clave de API podrían fallar.
   {:important}

## Procedimiento para establecer notificaciones
{: #useraccount-set-notif}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Valores** en el panel de navegación de la izquierda.
2. Si desea recibir una notificación por correo electrónico cuando se produzcan sucesos, pulse **Habilitar notificaciones por correo electrónico**.
3. Si desea recibir una notificación en la consola cuando se produzcan sucesos, pulse **Habilitar notificaciones de consola**.

## Procedimiento para establecer credenciales de cuenta de usuario
{: #useraccount-set-cred}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Valores** en el panel de navegación de la izquierda.
2. En el área **IBM Cloud Infrastructure Credentials**, revise la información para los pasos que debe realizar. 
3. Si tiene una cuenta de infraestructura {{site.data.keyword.cloud_notm}} y una cuenta {{site.data.keyword.cloud_notm}} que están enlazadas, pulse **Recuperar** para completar las credenciales automáticamente. 
4. Si tiene un cuenta de infraestructura de {{site.data.keyword.cloud_notm}} y una cuenta de {{site.data.keyword.cloud_notm}} que no están enlazadas, debe enlazarlas. Siga las instrucciones de [Enlazar cuentas de IBMid](/docs/account?topic=account-unifyingaccounts#link_accounts) y, a continuación, pulse **Recuperar** para completar las credenciales automáticamente. 
5. Si no dispone de una cuenta de infraestructura de {{site.data.keyword.cloud_notm}}, y no tiene una cuenta de {{site.data.keyword.cloud_notm}} facturable, [actualice antes su cuenta](/docs/account?topic=account-upgrading-account) y luego [cree una clave de API de infraestructura clásica](/docs/iam?topic=iam-classic_keys). 
6. Si no tiene una cuenta de infraestructura de {{site.data.keyword.cloud_notm}}, y tiene una cuenta de {{site.data.keyword.cloud_notm}} facturable, debe [crear una clave de API de infraestructura clásica](/docs/iam?topic=iam-classic_keys). 
7. Pulse **Guardar credenciales**.

## Resultados
{: #useraccount-results}

Después de enlazar la cuenta de {{site.data.keyword.cloud_notm}} y la cuenta de infraestructura de {{site.data.keyword.cloud_notm}}, la consola recupera automáticamente las credenciales de la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} para comunicarse con el entorno de VMware en {{site.data.keyword.cloud_notm}}.

Las credenciales de la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} almacenadas se utilizan en operaciones futuras que requieren interacción con la infraestructura de {{site.data.keyword.cloud_notm}}.

Si las notificaciones por correo electrónico o en la consola están habilitadas para determinados sucesos de la instancia, se le notificará por correo electrónico o mediante mensajes en la consola cuando se produzcan dichos sucesos.

## Enlaces relacionados
{: #useraccount-related}

* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Notificaciones](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [API de SoftLayer](/docs/customer-portal?topic=customer-portal-customerportal_api)
