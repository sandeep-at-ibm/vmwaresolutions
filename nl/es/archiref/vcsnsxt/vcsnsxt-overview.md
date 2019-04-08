---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Visión general de la arquitectura
{: #vcsnsxt-overview}

En la siguiente información se proporcionan más detalles sobre la arquitectura de red que se utiliza en esta arquitectura de referencia. Consta de las secciones siguientes:
* **Visión general de VMware vCenter Server on {{site.data.keyword.cloud}}**: se describen las principales características de la plataforma vCenter Server.
* **Visión general de la red**: contiene información sobre los componentes de red que se utilizan en esta arquitectura de referencia:
  - **Red de {{site.data.keyword.cloud_notm}}**: {{site.data.keyword.cloud_notm}} proporciona la red física y se gestiona por completo mediante {{site.data.keyword.cloud_notm}}. Revise las principales características de la red de {{site.data.keyword.cloud_notm}} para comprender los flujos de red entre el entorno local y externo y entre las cargas de trabajo alojadas en distintos servicios.
  - **NSX-V**: la red de vCenter Server se basa en la red de {{site.data.keyword.cloud_notm}} con una superposición proporcionada por VMware NSX-V. Esta superposición segmenta el tráfico procedente de la red subyacente de {{site.data.keyword.cloud_notm}}, lo que permite un mayor control y capacidad de configuración, que incluye BYOIP.
  - **{{site.data.keyword.containerlong_notm}}**: {{site.data.keyword.containerlong_notm}} utiliza Calico como plugin de interfaz de red de contenedor.
  - **{{site.data.keyword.icpfull_notm}}**: {{site.data.keyword.icpfull_notm}} utiliza Calico como plugin de interfaz de red de contenedor.

* **Integración**: se describe la arquitectura de los componentes de red que permiten el flujo y el direccionamiento necesarios del tráfico de red:
  - Asignación de direcciones IP
  - Flujos de tráfico de red

## Visión general de vCenter Server
{: #vcsnsxt-overview-vcs-ovw}

VMware vCenter Server (VCS) on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity) es una nube privada alojada que le ayuda a extender de forma rápida y sencilla su infraestructura local a la nube para disponer de una infraestructura híbrida segura y movilidad real de las aplicaciones.

vCenter Server con el paquete híbrido (Hybridity) se despliega en un mínimo de cuatro {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, ofrece almacenamiento dedicado mediante una red de área de almacenamiento virtual (VSAN) e incluye configuración y despliegue automáticos de una infraestructura de red definida por software (NSX-V) fácil de gestionar. vCenter Server con el paquete híbrido (Hybridity) constituye una arquitectura de referencia que se despliega mediante automatización y que garantiza la coherencia, el rendimiento y la conformidad. En muchos casos, puede suministrar todo el entorno en menos de un día, y la capacidad de cálculo y de almacenamiento de la infraestructura de servidores nativos se puede aumentar y reducir de forma rápida y elástica según las necesidades.

Existen muchas opciones para mejorar y ampliar vCenter Server con el paquete híbrido (Hybridity). Las ofertas del servicio {{site.data.keyword.cloud_notm}} no solo incluyen opciones de incremento del almacenamiento y varias opciones de conectividad de WAN públicas y privadas, sino que también cubren áreas que van desde la seguridad de la plataforma, la seguridad de la red y el equilibrio de la carga de tráfico hasta la copia de seguridad y la recuperación en caso de error.

Los servicios de seguridad de la plataforma incluyen HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, que proporciona soporte de seguridad y conformidad automatizado, lo que permite una mejor visibilidad y control sobre el entorno de nube y los administradores. HyTrust DataControl on {{site.data.keyword.cloud_notm}} proporciona protección de datos con un potente cifrado y gestión de claves escalables para proteger las cargas de trabajo durante todo su ciclo de vida. {{site.data.keyword.cloud_notm}} Secure Virtualization simplifica la conformidad y protege sus datos con cifrado, políticas de "geofencing" y controles de accesos basados en roles, mientras que KMIP for VMware on {{site.data.keyword.cloud_notm}}, una oferta de gestión del ciclo de vida de las claves de cifrado, gestiona las claves de cifrado que utilizan los servicios de {{site.data.keyword.cloud_notm}} o las aplicaciones incorporadas del cliente.

Las opciones de seguridad de red son FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, que ofrece un par de alta disponibilidad de dispositivos FortiGate Security Appliance para analizar el tráfico de la red y proteger la infraestructura virtual, y FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, que despliega un par de alta disponibilidad de VM FortiGate en {{site.data.keyword.cloud_notm}} para reducir el riesgo mediante la implementación de potentes controles de seguridad en la infraestructura virtual. Se están desarrollando más ofertas de seguridad de red.

El servicio de equilibrador de carga de red F5 on {{site.data.keyword.cloud_notm}} optimiza el rendimiento y garantiza la seguridad y la disponibilidad de las aplicaciones importantes con la suite de productos F5 BIG-IP.

Las ofertas de copia de seguridad y recuperación tras desastre de IBM, Veeam y Zerto le ofrecen la tranquilidad de disponer de continuidad operativa en el caso de que se produzca un desastre. IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} es una solución de disponibilidad y protección de datos para entornos virtuales. Veeam on {{site.data.keyword.cloud_notm}} ofrece disponibilidad para Always-On Enterprise™ con copia de seguridad, recuperación y réplica integradas en {{site.data.keyword.cloud_notm}}. Zerto on {{site.data.keyword.cloud_notm}} ofrece a los clientes de entornos locales y de {{site.data.keyword.cloud_notm}} una solución de recuperación tras desastre segura, flexible y escalable.

vCenter Server con el paquete híbrido (Hybridity) no es un servicio gestionado, aunque puede añadir servicios gestionados por IBM para descargar las operaciones diarias y el mantenimiento de las capas de virtualización, de sistema operativo invitado o de aplicaciones. El equipo de {{site.data.keyword.cloud_notm}} Professional Services también está disponible para ayudarle a acelerar la implantación en la nube con servicios de migración, implementación, planificación e incorporación.

Las opciones de integración de plataforma de vCenter Server con el paquete híbrido (Hybridity) no se limitan a las opciones disponibles en VMware, como vRealize Suite o vSphere con gestión de operaciones, sino que abarcan varias ofertas de servicio de {{site.data.keyword.cloud_notm}}, como [vCenter Server e {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) y [vCenter Server e {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro), que utilizan Terraform de código abierto para gestionar y suministrar la infraestructura como código.

La amplia gama de servicios y opciones de integración de varias ofertas disponibles para vCenter Server con el paquete híbrido (Hybridity) ofrecen una verdadera plataforma híbrida, que facilita la hibridación como servicio.

## Enlaces relacionados
{: #vcsnsxt-overview-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
