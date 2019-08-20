---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestión de los recursos de Shared
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} Shared se proporciona como una oferta experimental.
{:note}

Los clientes gestionan el ciclo de vida de los centros de datos virtuales mediante utilizando la oferta de {{site.data.keyword.vmwaresolutions_short}}.

Se da soporte a las funciones siguientes, ya sea utilizando la interfaz de usuario web o la API pública::
- Ver instancias de Centro de datos virtual
- Acceder a la consola de gestión de vCloud
- Redimensionar instancias de Centro de datos virtual
- Suprimir instancias de Centro de datos virtual
- Añadir y eliminar servicios de VMware Services a instancias de Centro de datos virtual (**Futuro**)

## Visualizar instancias de Centro de datos virtual
{: #shared_managing-viewing}

Para ver un resumen de todas las instancias de Centro de datos virtual que se han suministrado para una cuenta de usuario, complete los pasos siguientes:

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En el banner de la consola, pulse el icono de la cuenta de usuario y, a continuación, pulse el campo **Cuenta** para seleccionar la cuenta de usuario para la que desea comprobar las instancias.  
3. En la tabla **IBM Cloud VMware Solutions Shared**, visualice la lista de instancias que se han suministrado en la cuenta de usuario seleccionada.

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | El nombre de la instancia |
| Tipo | El tipo de Centro de datos virtual |
| Ubicación | El {{site.data.keyword.CloudDataCent_notm}} en el que se aloja la instancia |  
| Hora de creación | La fecha y hora en que se ha creado la instancia |
| Estado | El estado de la instancia |

{: caption="Tabla 1. Elementos de una instancia de Centro de datos virtual" caption-side="top"}

La instancia puede tener una serie de estados.

| Estado        | Descripción       |
|:------------- |:------------- |
| Creando | La instancia se está creando. |
| Listo para su uso | La instancia está lista para ser utilizada. |
| Modificando | La instancia se está modificando. |
| Suprimiendo | La instancia se está suprimiendo. |
| Suprimido | La instancia se ha suprimido. |

{: caption="Tabla 2. Descripciones de estado de las instancias de Centro de datos virtual" caption-side="top"}

## Procedimiento para visualizar los detalles de un Centro de datos virtual
{: #vc_viewinginstances-procedure-view-vdc-details}

Para ver los detalles de las propiedades de una instancia:

1. En la tabla **IBM Cloud VMware Solutions Shared**, pulse en un nombre de instancia.
2. En **Propiedades**, consulte los detalles de la instancia.

| Propiedad        | Descripción       |
|:------------- |:------------- |
| Nombre | Nombre de la instancia. |
| Tipo | El tipo de Centro de datos virtual. |
| Ubicación | El {{site.data.keyword.CloudDataCent_notm}} en el que se aloja la instancia. |
| ID | El ID de la instancia. |
| Hora de creación | La fecha y hora en que se ha creado la instancia, que es también cuando se inicia la facturación. |
| vCPU | El límite o la cantidad reservada de CPU que puede ser utilizada en cualquier momento por el Centro de datos virtual.  |
| RAM | El límite o la cantidad reservada de memoria que puede ser utilizada en cualquier momento por el Centro de datos virtual.  |
| IP pública | Cada centro de datos virtual se proporciona con cinco direcciones IP públicas que se pueden utilizar para conectar vApps y VM a Internet. |

{: caption="Tabla 3. Propiedades del Centro de datos virtual" caption-side="top"}

## Acceso a la consola de gestión de vCloud Director
{: #shared_managing-accessing}

Puede gestionar el centro de datos virtual a través de la consola de gestión de vCloud Director.

El primer acceso a la consola de gestión de vCloud Director se realiza utilizando la credencial **admin**. Genere una contraseña en la página de detalles del Centro de datos virtual con el enlace **Restablecer contraseña de ubicación**. Esta acción genera una contraseña aleatoria compleja inicial, que se puede restablecer en cualquier momento.

La oferta {{site.data.keyword.vmwaresolutions_short}} no almacena la contraseña de **admin**. Cuando se genera una contraseña, debe capturarla. Si se perdiera la contraseña, sería necesario generar una nueva.

Todos los centros de datos virtuales de la misma ubicación tienen la misma contraseña de **admin**. Si se restablece la contraseña en una instancia de Centro de datos virtual, se restablece la contraseña de **admin** para acceder a la consola de gestión de vCloud Director para todas las instancias de Centro de datos virtual de una misma ubicación.

Una vez que se ha generado la primera contraseña de **admin**, el botón **Portal de vCloud Director** está disponible en la esquina superior derecha de la página de detalles. Pulse en **Portal de vCloud Director** para acceder a la consola de gestión de vCloud Director. Para iniciar la sesión, utilice el nombre de usuario **admin** y la contraseña que ha obtenido con el enlace **Restablecer contraseña de ubicación**.

## Redimensionar instancias de Centro de datos virtual
{: #shared_managing-resizing}

En cualquier momento en que una instancia de Centro de datos virtual esté en el estado **Listo para su uso**, puede cambiar la cantidad de recursos asignados a un centro de datos virtual. 

Redimensionar los recursos de vCPU o RAM para una instancia de Centro de datos virtual en la página de detalles del Centro de datos virtual. Pulse en el icono de lápiz situado junto a **Recursos** en la página de detalles y cambie los valores de las propiedades de vCPU o RAM.

Finalmente, verifique la configuración y el coste estimado antes de realizar el pedido.

  El cambio de configuración falla si los recursos de vCPU y RAM se están utilizando mientras se reducen, porque los recursos del Centro de datos virtual no se pueden reducir a un nivel inferior al del uso de recursos actualmente activo.
  {:note}

La instancia de Virtual Data Center está en el estado **Modificando** mientras se realiza el cambio. Cuando los recursos están listos para su uso, el estado se cambia a **Listo para su uso**.

## Suprimir instancias de Centro de datos virtual
{: #shared_managing-deleting}

Una instancia de Centro de datos virtual se puede suprimir cuando está en el estado **Listo para su uso**. Puede llevar a cabo la operación de supresión desde la página de detalles del Centro de datos virtual la tabla IBM Cloud VMware Solutions Shared Resource.

En la página de detalles, pulse el icono **Suprimir** en la opción de menú de desbordamiento en la parte superior derecha de la página de detalles. A continuación, confirme que desea suprimir la instancia.

En la tabla IBM Cloud VMware Solutions Shared Resource, localice la instancia que desea suprimir y pulse el icono **Suprimir** en la columna **Acciones**. A continuación, confirme que desea suprimir la instancia.

## Enlaces relacionados
{: #shared_managing-related}

* [Visión general de {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Solicitud de Shared bajo demanda](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Solicitud de Shared reservado](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
