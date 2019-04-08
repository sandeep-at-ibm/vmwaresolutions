---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations}

El servicio KMIP for VMware on {{site.data.keyword.cloud}} ofrece un servicio altamente disponible de tipo 24x7 para gestionar las claves de cifrado que utiliza VMware en {{site.data.keyword.cloud_notm}}. Este servicio ofrece capacidad de tiempo de ejecución que permite a los clientes crear, recuperar, activar, revocar y destruir las claves de cifrado. También proporciona capacidad de gestión para mantener las asociaciones entre las credenciales del cliente y las claves de cifrado.

El servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} está disponible como un servicio autónomo sin estar asociado a una instancia de VMware. Cada instancia del servicio puede dar servicio a una o varias instancias de Cloud Foundation, instancias de vCenter Server o clústeres de vSphere.

## Especificaciones técnicas para KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

Las siguientes especificaciones se incluyen con el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* Un protocolo Key Management Interoperability (KMIP) compatible con VMware
* Un servicio gestionado
* Disponible en múltiples regiones geográficas de todo el mundo
* Se proporcionan dos puntos finales de servicio de red KMIP en cada región para alta disponibilidad

## Consideraciones sobre la instalación de instancias de KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations-install}

Revise las siguientes consideraciones antes de instalar una instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* KMIP for VMware on {{site.data.keyword.cloud_notm}} utiliza el servicio IBM Key Protect para {{site.data.keyword.cloud_notm}} para crear, cifrar y descifrar claves de cifrado. Por lo tanto, antes de instalar KMIP para VMware en {{site.data.keyword.cloud_notm}}, asegúrese de que:
   * Ha solicitado un servicio de protección de claves utilizable en la región de {{site.data.keyword.cloud_notm}} en la que se va a alojar la instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Suministro del servicio](/docs/services/key-protect?topic=key-protect-provision).
   * Se ha creado un ID de servicio de {{site.data.keyword.cloud_notm}} siguiendo los pasos indicados en [Creación de un ID de servicio](/docs/iam?topic=iam-serviceids). Este ID de servicio se utiliza para acceder a la instancia del servicio Key Protect que ha creado.
   * Ha otorgado los siguientes niveles de acceso al ID de servicio:
      * A nivel de acceso a la plataforma: autorización de visualización a la instancia de IBM Key Protect
      * A nivel de acceso al servicio: autorización de gestor a la de IBM Key Protect
   * Tiene una clave de API para el ID de servicio creado. La clave es necesaria al solicitar el servicio.
   * Ha creado al menos una clave raíz de cliente (CRK) desde la interfaz de usuario de Key Protect siguiendo los pasos del apartado [Creación de claves raíz](/docs/services/keymgmt/keyprotect_create_root.html) o utilizando la API REST de [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect).

     **Importante:** No puede solicitar el servicio sin CRK. Se recomienda utilizar el método para crear una CRK utilizando el material de claves existente y hacer una copia de seguridad del material de claves que se crea. De este modo se asegura de que puede recuperar sus claves en el caso de que se produzca un fallo del centro de datos en el que se aplica IBM Key Protect para almacenar los CRK.
* Asegúrese de que la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} esté habilitada para Virtual Routing and Forwarding (VRF) y para la conectividad con los puntos finales de servicio. Para obtener más información, consulte:
   * [Visión general de Virtual Routing and Forwarding (VRF) en IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Habilitación de la cuenta para que utilice puntos finales de servicio mediante la CLI de IBM Cloud](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started)
* Puesto que solo se da soporte a la conexión privada, no es necesario configurar ningún cortafuegos ni regla de SNAT en vCenter Server para la conectividad de red entre el vCenter Server y el punto final de la instancia de KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Para obtener más información, consulte [Arquitectura de la solución KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview).

## Consideraciones sobre la supresión de instancias de KMIP for VMware on IBM Cloud
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

Los datos protegidos por el servicio KMIP for VMware on IBM Cloud, incluidas las copias de seguridad cifradas, no se pueden descifrar después de eliminar el servicio.

## Enlaces relacionados
{: #kmip_standalone_considerations-related}

* [Solicitud de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [Adición, visualización y supresión de certificados para instancias de KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [Visualización de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Supresión de instancias de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Sucesos de Activity Tracker](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
