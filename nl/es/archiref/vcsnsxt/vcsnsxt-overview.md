---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Visión general de la arquitectura

En esta sección se proporcionan más detalles sobre la arquitectura de red que se utiliza en esta arquitectura de referencia. Consta de las secciones siguientes:
* **Visión general de VCS**: en esta sección se describen los aspectos destacados de la plataforma VCS.
* **Visión general de la red**: estas secciones proporcionan información sobre los componentes de red que se utilizan en esta arquitectura de referencia:
  - **Red de IBM Cloud**: {{site.data.keyword.cloud}} proporciona la red física y se gestiona por completo mediante {{site.data.keyword.cloud_notm}}. Esta red tiene algunas características clave que deben entenderse para comprender los flujos de red entre el entorno local y externo y entre las cargas de trabajo alojadas en distintos servicios.
  - **NSX-V**: la red VCS se basa en la red de {{site.data.keyword.cloud_notm}} con una superposición proporcionada por VMware NSX-V. Esta superposición segmenta el tráfico procedente de la red subyacente de {{site.data.keyword.cloud_notm}}, lo que permite un mayor control y capacidad de configuración, que incluye BYOIP.
  - **IBM Kubernetes Service**: IKS utiliza Calico como plugin de interfaz de red de contenedor.
  - **IBM Cloud Private**: ICP utiliza Calico como plugin de interfaz de red de contenedor.

* **Integración**: en esta sección se describe la arquitectura de los componentes de red que permiten el flujo y el direccionamiento necesarios del tráfico de red:
  - Asignación de direcciones IP
  - Flujos de tráfico de red

## Visión general de VCS

VMware vCenter Server (VCS) on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity) (VCS) es una nube privada alojada que le ayuda a extender de forma rápida y sencilla su infraestructura local a la nube para disponer de una infraestructura híbrida segura y movilidad real de las aplicaciones.

El paquete híbrido de VCS se despliega sobre un mínimo de cuatro {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, ofrece almacenamiento dedicado mediante una red de área de almacenamiento virtual (VSAN) e incluye configuración y despliegue automáticos de una infraestructura de red definida por software (NSX-V) fácil de gestionar. El paquete híbrido de VCS constituye una arquitectura de referencia que se despliega mediante automatización y que garantiza la coherencia, el rendimiento y la conformidad. En muchos casos, todo el entorno se puede suministrar en menos de un día, y la capacidad de cálculo y de almacenamiento de la infraestructura de servidores nativos se puede aumentar y reducir de forma rápida y elástica según las necesidades.

Existen muchas opciones para mejorar y ampliar VCS Server con el paquete híbrido de VCS. Las ofertas del servicio {{site.data.keyword.cloud_notm}} no solo incluyen opciones de incremento del almacenamiento y varias opciones de conectividad de WAN públicas y privadas, sino que también cubren áreas que van desde la seguridad de la plataforma, la seguridad de la red y el equilibrio de la carga de tráfico hasta la copia de seguridad y la recuperación en caso de error.

Los servicios de seguridad de la plataforma incluyen HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, que proporciona soporte de seguridad y conformidad automatizado, lo que permite una mejor visibilidad y control sobre el entorno de nube y los administradores. HyTrust DataControl on {{site.data.keyword.cloud_notm}} proporciona protección de datos con un potente cifrado y gestión de claves escalables para proteger las cargas de trabajo durante todo su ciclo de vida. {{site.data.keyword.cloud_notm}} Secure Virtualization simplifica la conformidad y protege sus datos con cifrado, políticas de "geofencing" y controles de accesos basados en roles, mientras que KMIP for VMware on {{site.data.keyword.cloud_notm}}, una oferta de gestión del ciclo de vida de las claves de cifrado, gestiona las claves de cifrado que utilizan los servicios de {{site.data.keyword.cloud_notm}} o las aplicaciones incorporadas del cliente.

Las opciones de seguridad de red son FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, que ofrece un par de alta disponibilidad de dispositivos FortiGate Security Appliance para analizar el tráfico de la red y proteger la infraestructura virtual, y FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, que despliega un par de alta disponibilidad de VM FortiGate en {{site.data.keyword.cloud_notm}} para reducir el riesgo mediante la implementación de potentes controles de seguridad en la infraestructura virtual. Se están desarrollando más ofertas de seguridad de red.

El servicio de equilibrador de carga de red F5 on {{site.data.keyword.cloud_notm}} optimiza el rendimiento y garantiza la seguridad y la disponibilidad de las aplicaciones importantes con la suite de productos F5 BIG-IP.

Las ofertas de copia de seguridad y recuperación tras desastre de IBM, Veeam y Zerto le ofrecen la tranquilidad de disponer de continuidad operativa en el caso de que se produzca un desastre. IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} es una solución de disponibilidad y protección de datos para entornos virtuales. Veeam on {{site.data.keyword.cloud_notm}} ofrece disponibilidad para Always-On Enterprise™ con copia de seguridad, recuperación y réplica integradas en {{site.data.keyword.cloud_notm}}. Zerto on {{site.data.keyword.cloud_notm}} ofrece a los clientes de entornos locales y de {{site.data.keyword.cloud_notm}} una solución de recuperación tras desastre segura, flexible y escalable.

{{site.data.keyword.cloud_notm}} VCS con el paquete híbrido (Hybridity) no es un servicio gestionado, aunque puede añadir servicios gestionados por IBM para descargar las operaciones diarias y el mantenimiento de las capas de virtualización, de sistema operativo invitado o de aplicaciones. El equipo de {{site.data.keyword.cloud_notm}} Professional Services también está disponible para ayudarle a acelerar la implantación en la nube con servicios de migración, implementación, planificación e incorporación.

Las opciones de integración del paquete híbrido de VCS no se limitan a las opciones disponibles en VMware, como vRealize Suite o vSphere con gestión de operaciones, sino que abarcan varias ofertas de servicios de {{site.data.keyword.cloud_notm}}, como [vCenter Server de IBM Kubernetes](../vcsiks/vcsiks-intro.html) y [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html), que utilizan Terraform de código abierto para gestionar y suministrar la infraestructura como código.

La amplia gama de servicios y opciones de integración de varias ofertas disponibles para el paquete híbrido de VCS ofrecen una verdadera plataforma híbrida, que facilita la hibridación como servicio.

### Enlaces relacionados

* [Visión general de VCS con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
