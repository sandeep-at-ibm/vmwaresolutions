---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Visualización de instancias de VMware Federal

Siga este procedimiento para ver las instancias de VMware Federal que ha solicitado e información detallada sobre las mismas.

## Visualización de resumen de instancias de VMware Federal

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **vCenter Server**, visualice la lista de las instancias.

Tabla 1. Elementos de una instancia de VMware Federal

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | Nombre de la instancia. |
| Versión | La versión del release en la que se ha desplegado la instancia o a la que se ha actualizado. |  
| Ubicación | El {{site.data.keyword.CloudDataCent}} en el que se aloja la instancia. |  
| Hora de creación | La fecha y hora en que se ha creado la instancia. |  

La instancia puede tener una serie de estados.

Tabla 2. Descripciones de los estados de una instancia de centro de datos de VMware Federal

| Estado        | Descripción       |
|:------------- |:------------- |
| Creando | La instancia se está creando. |
| Compilando | La instancia se está configurando. |
| Listo para su uso | La instancia está lista para ser utilizada. |
| Modificando | La instancia se está modificando. |
| Protegido | La instancia desplegada se ha desconectado de la conexión de gestión abierta y de la automatización.
| Fallido | Se ha producido un error durante el proceso de creación, configuración o modificación. |
| Suprimiendo | La instancia se está suprimiendo. |
| Error de supresión | Se ha producido un error cuando se estaba suprimiendo la instancia. |
| Suprimido | La instancia se ha suprimido. |

## Visualización de detalles de las propiedades de una instancia de VMware Federal

Para ver los detalles de las propiedades de una instancia:

1. En la tabla **Instancias de vCenter Server**, pulse un nombre de instancia.
2. En **Propiedades**, consulte los detalles de la instancia.

Tabla 3. Propiedades de instancias de VMware Federal

| Propiedad        | Descripción       |
|:------------- |:------------- |
| Nombre | Nombre de la instancia. |
| ID | El ID de la instancia. |
| Ubicación | El {{site.data.keyword.CloudDataCent_notm}} en el que se aloja la instancia. |
| Versión actual |  La versión actual de {{site.data.keyword.vmwaresolutions_short}}. |
| Versión de vCenter | La versión de VMware vCenter Server.<br><br>**Nota:** hay una ligera variación entre la versión de vCenter Server que se muestra en la consola de {{site.data.keyword.vmwaresolutions_short}} y en el cliente web de VMware vSphere. Ambas son correctas. |
| NSX for vSphere | La versión del producto VMware NSX for vSphere. |
| Edición de licencia de NSX | La versión y la edición de la licencia de VMware NSX. |
| DNS Root Domain | El nombre del dominio raíz es el nombre del dominio DNS (Sistema de nombres de dominio) y el nombre raíz del grupo Microsoft Active Directory (AD). |
| DNC SSO Domain | El dominio SSO es el dominio de inicio de sesión único (Single Sign-On) de vSphere. El nombre de dominio SSO es fijo para todas las instancias de vCenter Server desplegadas y tiene el valor <samp class="ph codeph">vsphere.local</samp>. |
| DNS Subdomain | El subdominio es el nombre del subdominio DNS del nombre del dominio raíz en el que residen los nombres de host de la instancia local de vCenter Server. El nombre del subdominio está en el formato <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Estado | El estado de la instancia. |

## Visualización de información de acceso para instancias de VMware Federal

En **Información de acceso**, consulte la información de acceso para los componentes relacionados con la instancia. Las contraseñas que se muestran son contraseñas iniciales que genera el sistema. Si las cambia fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, no se actualizarán en la página de resumen de la instancia.

Tabla 4. Información de acceso correspondiente a los componentes relacionados con la instancia

| Componente        | Descripción       |
|:------------- |:------------- |
| AD/DNS IP | Las direcciones IP de los dos servidores AD. |
| AD/DNS FQDN | Los nombres de dominio completos del servidor AD/DNS.<br><br>**Nota:** se puede utilizar la misma contraseña del administrador para conectarse a todos los servidores AD/DNS mediante una conexión de escritorio remoto. |
| AD/DNS ADMIN (Remote Desktop)  | Para las instancias primarias, muestra el nombre de usuario y la contraseña para acceder al servidor AD mediante una conexión remota de escritorio.
| NSX Manager IP  | La dirección IP de NSX Manager.  |
| NSX Manager FQDN  | El nombre de dominio completo de NSX Manager (FQDN).  |
| NSX Manager HTTP  | El nombre de usuario y la contraseña que se utilizan para acceder a la consola web de NSX Manager. |
| PSC IP  | La dirección IP de Platform Services Controller (PSC).  |
| PSC FQDN  | El nombre de dominio completo de PSC (FQDN).  |    
| PSC ADMIN  | El nombre de usuario y la contraseña de inicio de sesión único de VMware vCenter que puede utilizar para acceder a la consola web de PSC.  |
| PSC SSH  | El nombre de usuario y la contraseña que puede utilizar para acceder a PSC VM mediante una conexión SSH.  |
| vCenter IP  | La dirección IP de vCenter Server.  |
| vCenter FQDN  | El nombre de dominio completo de vCenter Server (FQDN).  |
| vCenter ADMIN  | El nombre de usuario y la contraseña de inicio de sesión único de VMware vCenter que puede utilizar para iniciar una sesión en vCenter Server mediante el cliente web de vSphere.  |
| vCenter SSH  | El nombre de usuario y la contraseña que puede utilizar para acceder a vCenter Server VM mediante una conexión SSH.  |

## Visualización del historial de despliegues de instancias de VMware Federal

En **Historial de despliegue**, consulte el historial de despliegue de la instancia.

Tabla 5. Historial de despliegues de la instancia de VMware Federal

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Fecha | La fecha y hora en que se ha modificado el estado de la instancia. |
| Resumen | Los detalles del cambio. |

## Qué hacer si se producen errores

Si se producen errores durante el despliegue o durante la supresión de la instancia, se notifica automáticamente al equipo de soporte de {{site.data.keyword.cloud_notm}}. Para informarse sobre el estado de la incidencia, puede [ponerse en contacto con el servicio de soporte de IBM](../vmonic/trbl_support.html).

## Qué hacer a continuación

Gestione sus instancias desde la consola de {{site.data.keyword.vmwaresolutions_short}} o desde el cliente web de VMware vSphere.

**Importante**: Antes de pulsar la **Consola de vCenter** en la página de resumen de la instancia para ir al cliente web de vSphere y empezar a gestionar sus servidores ESXi, debe iniciar una sesión en el portal VPN del {{site.data.keyword.CloudDataCent_notm}}. Mueva el puntero del ratón sobre el botón de la **consola de vCenter** y siga las instrucciones para asegurarse de que cumple los requisitos y de que ha realizado los pasos necesarios antes de acceder al cliente web de vSphere.

Revise los temas siguientes para obtener información que le ayudará a seguir las instrucciones de inicio de sesión:
*  Para ver los requisitos y pasos necesarios antes de acceder al cliente web de vSphere, consulte [Se ha alcanzado el tiempo de espera al conectar con el cliente web de vSphere](../vmonic/trbl_timeout_vc_console.html).
*  Para ver una lista de puntos de acceso para iniciar una sesión en la red privada de la infraestructura de {{site.data.keyword.cloud_notm}} utilizando VPN, consulte [Acceso VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Si tiene problemas al desplegar un archivo OVF (Open Virtualization Format) mediante el cliente web de vSphere, consulte [Despliegue de un archivo OVF mediante el cliente web de vSphere](../vmonic/trbl_deploy_ovf.html).

## Enlaces relacionados

* [Visión general de VMware Federal on IBM Cloud](vc_fed_overview.html)
* [Solicitud de instancias de VMware Federal](vc_fed_orderinginstance.html)
* [Supresión de instancias de VMware Federal](vc_fed_deletinginstance.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
