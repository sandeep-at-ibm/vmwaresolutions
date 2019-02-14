---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visualización de instancias de vCenter Server con el paquete híbrido (Hybridity)

Visualice el resumen y la información detallada de las instancias de VMware vCenter Server con el paquete híbrido (Hybridity) que se suministran para cuentas de usuario diferentes.

## Procedimiento para visualizar instancias de vCenter Server con el paquete híbrido (Hybridity)

Para ver un resumen de todas las instancias de vCenter Server con el paquete híbrido (Hybridity) que se han suministrado para una cuenta de usuario, complete los pasos siguientes:
1. En la consola de {{site.data.keyword.vmwaresolutions_full}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En el banner de la consola, pulse el icono de la cuenta de usuario y, a continuación, pulse el campo **Cuenta** para seleccionar la cuenta de usuario para la que desea comprobar las instancias.
3. En la tabla **Instancias de vCenter Server**, visualice la lista de instancias que se han suministrado en la cuenta de usuario seleccionada.

Tabla 1. Elementos de las instancias de vCenter Server con el paquete híbrido (Hybridity)

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | El nombre de la instancia |
| Tipo | El tipo de instancia de vCenter Server |
| Versión | La versión del release en la que se ha desplegado la instancia o a la que se ha actualizado |  
| Ubicación | El {{site.data.keyword.CloudDataCent_notm}} en el que se aloja la instancia |  
| Hora de creación | La fecha y hora en que se ha creado la instancia |  
| Estado | El estado de la instancia |  

La instancia puede tener una serie de estados.

Tabla 2. Descripciones de estado de instancias de vCenter Server con el paquete híbrido (Hybridity)

| Estado        | Descripción       |
|:------------- |:------------- |
| Creando | La instancia se está creando. |
| Compilando | La instancia se está configurando. |
| Listo para su uso | La instancia está lista para ser utilizada. |
| Modificando | La instancia se está modificando. |
| Fallido | Se ha producido un error durante el proceso de creación, configuración o modificación. |
| Suprimiendo | La instancia se está suprimiendo. |
| Error de supresión | Se ha producido un error cuando se estaba suprimiendo la instancia. |
| Suprimido | La instancia se ha suprimido. |

## Procedimiento para visualizar propiedades de instancia de vCenter Server con el paquete híbrido (Hybridity)

Para ver los detalles de las propiedades de una instancia de vCenter Server con el paquete híbrido (Hybridity):
1. En la tabla **Instancias de vCenter Server**, pulse un nombre de instancia.
2. En **Propiedades**, consulte los detalles de la instancia.

Tabla 3. Propiedades de instancias de vCenter Server con el paquete híbrido (Hybridity)

| Propiedad        | Descripción       |
|:------------- |:------------- |
| Nombre | Nombre de la instancia. |
| ID | El ID de la instancia. |
| Ubicación | El {{site.data.keyword.CloudDataCent_notm}} en el que se aloja la instancia. |
| Versión actual | La versión actual de {{site.data.keyword.vmwaresolutions_short}}. |
| Versión de vCenter | La versión de VMware vCenter Server con el paquete híbrido (Hybridity).<br><br>**Nota:** hay una ligera variación entre la versión de vCenter Server que se muestra en la consola de {{site.data.keyword.vmwaresolutions_short}} y en el cliente web de VMware vSphere. Ambas son correctas. |
| NSX for vSphere | La versión del producto VMware NSX for vSphere. |
| Edición de licencia de NSX | La versión y la edición de la licencia de VMware NSX. |
| DNS, Root Domain | El nombre del dominio raíz es el nombre del dominio DNS (Sistema de nombres de dominio) y el nombre raíz del grupo Microsoft Active Directory (AD). |
| DNS, SSO Domain | El dominio SSO es el dominio de inicio de sesión único (Single Sign-On) de vSphere. El nombre de dominio SSO es fijo para todas las instancias de vCenter Server con el paquete híbrido (Hybridity) desplegadas con un valor de <samp class="ph codeph">vsphere.local</samp>. |
| DNS, Subdomain | El subdominio es el nombre del subdominio DNS del nombre del dominio raíz en el que residen los nombres de host de la instancia local de vCenter Server con el paquete híbrido (Hybridity). El nombre del subdominio está en el formato <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Hybridity Bundle | Indica si está instalado vCenter Server con el paquete híbrido (Hybridity). |
| Estado  | El estado de la instancia.<br><br>La información que se muestra proporciona una actualización sobre el progreso del despliegue o de la acción que se realiza sobre la instancia. Si hay algún problema, se muestra un mensaje para ayudarle a investigar y a resolver el problema. |

## Procedimiento para visualizar información de acceso para instancias de vCenter Server con el paquete híbrido (Hybridity)

En **Información de acceso**, consulte la información de acceso para los componentes relacionados con la instancia. Las contraseñas que se muestran son contraseñas iniciales que genera el sistema. Si las cambia fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, no se actualizarán en la página de resumen de la instancia.

Tabla 4. Información de acceso de vCenter Server con el paquete híbrido (Hybridity) para componentes relacionados con la instancia

| Componente        | Descripción       |
|:------------- |:------------- |
| AD/DNS IP | Las direcciones IP de los dos servidores AD. |
| AD/DNS FQDN | Los nombres de dominio completos del servidor AD/DNS.<br><br>**Nota:** se puede utilizar la misma contraseña del administrador para conectarse a todos los servidores AD/DNS mediante una conexión de escritorio remoto. |
| AD/DNS ADMIN (Remote Desktop)  | Para las instancias primarias, muestra el nombre de usuario y la contraseña para acceder al servidor AD mediante una conexión remota de escritorio.<br><br>Para instancias secundarias, pulse el enlace **Ver en la instancia primaria** para ir a la información sobre nombre de usuario y contraseña de la instancia primaria.<br><br>**Nota:** después de que la instancia secundaria se añada al dominio DNS primario y de que se produzca la réplica, la contraseña del administrador local de la instancia primaria puede sobrescribir la contraseña del administrador local en la instancia secundaria. Si pulsa el enlace **Ver en la instancia primaria**, accederá a la contraseña correcta del administrador.  
| NSX Manager IP  | La dirección IP de NSX Manager.  |
| NSX Manager FQDN  | El nombre de dominio completo de NSX Manager (FQDN).  |
| NSX Manager HTTP  | El nombre de usuario y la contraseña que se utilizan para acceder a la consola web de NSX Manager. |
| vCenter IP  | La dirección IP de vCenter Server.  |
| vCenter FQDN  | El nombre de dominio completo de vCenter Server (FQDN).  |
| vCenter ADMIN  | El nombre de usuario y la contraseña de inicio de sesión único de VMware vCenter que puede utilizar para iniciar una sesión en vCenter Server mediante el cliente web de vSphere.  |
| vCenter SSH  | El nombre de usuario y la contraseña que puede utilizar para acceder a vCenter Server VM mediante una conexión SSH.  |

## Procedimiento para visualizar el historial de despliegue para instancias de vCenter Server con el paquete híbrido (Hybridity)

Pulse **Historial de despliegue** en el panel de navegación izquierdo para ver el historial de despliegue de la instancia.

Tabla 5. Historial de despliegues de la instancia de vCenter Server con el paquete híbrido (Hybridity)

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Fecha | La fecha y hora en que se ha modificado el estado de la instancia |
| Resumen | Los detalles del cambio |

## Qué hacer si se producen errores

Si se producen errores durante el despliegue o durante la supresión de la instancia, se notifica automáticamente al equipo de soporte de {{site.data.keyword.cloud_notm}}. Para informarse sobre el estado de la incidencia, puede [ponerse en contacto con el servicio de soporte de IBM](../vmonic/trbl_support.html).

## Qué hacer a continuación

Gestione sus instancias desde la consola de {{site.data.keyword.vmwaresolutions_short}} o desde el cliente web de VMware vSphere.

Antes de pulsar la **Consola de vCenter** en la página de resumen de la instancia para ir al cliente web de vSphere y empezar a gestionar sus servidores ESXi, debe iniciar una sesión en el portal VPN del {{site.data.keyword.CloudDataCent_notm}}. Mueva el puntero del ratón sobre el botón de la **consola de vCenter** y siga las instrucciones para asegurarse de que cumple los requisitos y de que ha realizado los pasos necesarios antes de acceder al cliente web de vSphere.
{:important}

Revise los temas siguientes para obtener información que le ayudará a seguir las instrucciones de inicio de sesión:
*  Para ver los requisitos y pasos necesarios antes de acceder al cliente web de vSphere, consulte [Se ha alcanzado el tiempo de espera al conectar con el cliente web de vSphere](../vmonic/trbl_timeout_vc_console.html).
*  Para ver una lista de puntos de acceso para iniciar una sesión en la red privada de la infraestructura de {{site.data.keyword.cloud_notm}} utilizando VPN, consulte [Acceso VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Si tiene problemas al desplegar un archivo OVF (Open Virtualization Format) mediante el cliente web de vSphere, consulte [Despliegue de un archivo OVF mediante el cliente web de vSphere](../vmonic/trbl_deploy_ovf.html).

### Enlaces relacionados

* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_orderinginstance.html)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingviewingclusters.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservers.html)
* [Supresión de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_deletinginstance.html)
