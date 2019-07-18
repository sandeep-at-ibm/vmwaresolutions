---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: IBM Cloud Private Hosted, ICP configuration, order Cloud Private

subcollection: vmware-solutions


---

# Solicitud de IBM Cloud Private Hosted
{: #icp_ordering}

Puede solicitar el servicio {{site.data.keyword.cloud}} Private Hosted cuando solicite una nueva instancia con el servicio incluido o añadiendo el servicio a una instancia existente.

## Solicitud de IBM Cloud Private Hosted para una instancia nueva
{: #icp_ordering-new}

Puede solicitar una nueva instancia con el servicio {{site.data.keyword.cloud_notm}} Private Hosted incluido utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, cuando solicite una nueva instancia, seleccione **IBM Cloud Private Hosted** en la sección **Servicios opcionales**.
* En el catálogo de {{site.data.keyword.cloud_notm}}, pulse el icono **VMware** en el panel de navegación de la izquierda y, a continuación, pulse la tarjeta **IBM Cloud Private Hosted** en la sección **Servicios de VMware**. Especifique los valores del servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de IBM Cloud Private Hosted para una instancia existente
{: #icp_ordering-existing}

Puede añadir el servicio {{site.data.keyword.cloud_notm}} Private Hosted a una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia a la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* En el catálogo de {{site.data.keyword.cloud_notm}}, pulse el icono **VMware** en el panel de navegación de la izquierda y, a continuación, pulse la tarjeta **IBM Cloud Private Hosted** en la sección **Servicios de VMware**. Especifique los valores del servicio y seleccione **Añadir a instancia existente**.

## Configuración del servicio IBM Cloud Private Hosted
{: #icp_ordering-config}

Cuando solicite el servicio, especifique los valores siguientes:
* Seleccione **Preparado para producción** o **Desarrollo/Prueba** según necesite.
* Marque el recuadro de selección adecuado para certificar que ya ha obtenido la licencia necesaria para desplegar el servicio {{site.data.keyword.cloud_notm}} Private Hosted.

## Despliegue de nodos adicionales
{: #icp_ordering-deploy-nodes}

Si desea desplegar nodos adicionales, revise la información siguiente:
* Utilice la plantilla de Ubuntu de
{{site.data.keyword.cloud_notm}} Private (Ubuntu1604) que se despliega con su instalación inicial de
{{site.data.keyword.cloud_notm}} Private Hosted.
* Para encontrar la plantilla de Ubuntu, en el cliente web de VMware vSphere, vaya al separador
**Máquinas virtuales y plantillas**, en la carpeta `cam`.
* La contraseña predeterminada para la plantilla de Ubuntu es `icponcloud`. Se recomienda que cambie esta contraseña antes de utilizar la plantilla.
* {{site.data.keyword.vmwaresolutions_short}} no ofrece soporte para aplicar actualizaciones y parches para la plantilla de Ubuntu. Debe supervisar y aplicar estas actualizaciones usted mismo.

## Enlaces relacionados
{: #icp_ordering-related}

* [Visión general de IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
