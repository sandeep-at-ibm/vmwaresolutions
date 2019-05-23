---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-08"

subcollection: vmware-solutions


---

# Visión general de la arquitectura
{: #vcsiks-arch-overview}

Las ofertas de {{site.data.keyword.vmwaresolutions_full}} proporcionan la automatización para desplegar componentes de tecnología VMware en {{site.data.keyword.CloudDataCents_notm}} en todo el mundo. La arquitectura consta de una sola región de nube y permite la ampliación a más regiones de nube ubicadas en otra geografía o en otro pod de {{site.data.keyword.cloud_notm}} dentro del mismo centro de datos.

Puede desplegar manualmente los productos {{site.data.keyword.icpfull_notm}} y Cloud Automation Manager (CAM) en la plataforma de virtualización local, lo que permite gestionar la nube desde ubicaciones locales. Como alternativa, {{site.data.keyword.icpfull_notm}} y CAM se ofrecen como extensiones de servicio de un despliegue de vCenter Server on {{site.data.keyword.cloud_notm}} nuevo o existente, mediante automatización, lo que permite gestionar la nube desde {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.icpfull_notm}} es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones locales contenerizadas. {{site.data.keyword.icpfull_notm}} es un entorno integrado para gestionar contenedores que incluye el coordinador de contenedores Kubernetes,
un repositorio de imágenes privadas, una consola de gestión e infraestructuras de supervisión.

IBM Multi-Cluster Manager proporciona visibilidad de usuario, gestión centrada en aplicaciones (política, despliegues, estado, operaciones) y conformidad basada en políticas entre nubes y clústeres. Con IBM Multi-Cluster Manager, tiene el control sobre los clústeres de Kubernetes. Se asegura de que sus clústeres sean seguros, que funcionen de forma eficiente y que proporcionen los niveles de servicio que esperan las aplicaciones.

{{site.data.keyword.cloud_notm}} Automation Manager es una plataforma de gestión de autoservicio multinube que se ejecuta en {{site.data.keyword.cloud_notm}} Private que ayuda a los desarrolladores y a los administradores a satisfacer las necesidades de la empresa. Cloud Automation Manager Service Composer le permite exponer los servicios de nube híbrida en el catálogo de IBM Cloud Private.

## Plataforma de gestión de nube desde IBM Cloud
{: #vcsiks-arch-overview-ibm-cloud-side}

El diagrama siguiente muestra {{site.data.keyword.icpfull_notm}} y CAM desplegados con la infraestructura de {{site.data.keyword.cloud_notm}}, con conexiones con el vCenter local y el servicio de {{site.data.keyword.containerlong_notm}} desplegado en {{site.data.keyword.cloud_notm}}. Los usuarios pueden desplegar máquinas virtuales (VM) locales y VM en instancias de vCenter Server y contenedores en el clúster {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}.

![En la nube - Gestión de la nube](../../images/vcsiks-oncloud-cloudmgt.svg "En la nube - Gestión de la nube")

En el diagrama, CAM crea de forma lógica conexiones en la nube con los entornos de vCenters, proveedores de nube, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}. Los clústeres de {{site.data.keyword.icpfull_notm}} deben desplegarse en cada centro de datos o entorno de nube, y MCM proporciona el mecanismo para conectar los clústeres de {{site.data.keyword.icpfull_notm}} en una única vista de gestión.

{{site.data.keyword.icpfull_notm}} se puede desplegar con los componentes NSX-V o NSX-T. {{site.data.keyword.icpfull_notm}} con NSX-V permite ejecutar VM {{site.data.keyword.icpfull_notm}} en la red VXLAN y utilizar el sistema de red interno de Calico de Kubernetes.

{{site.data.keyword.icpfull_notm}} con NSX-T permite a los usuarios controlar y configurar el sistema de red, de subred y las políticas desde la interfaz de usuario central (NSX-T Manager). Para obtener información sobre las diferencias entre NSX-V y NSX-T, consulte la
[Arquitectura de referencia de red VCS de {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-vcsnsxt-intro#vcsnsxt-intro).

## Plataforma de gestión de nube local
{: #vcsiks-arch-overview-on-premises}

En el diagrama siguiente se muestra {{site.data.keyword.icpfull_notm}} y CAM desplegados en la infraestructura local, con conexiones con vCenter e {{site.data.keyword.containerlong_notm}} desplegado en {{site.data.keyword.cloud_notm}}. Los usuarios pueden desplegar las VM y los contenedores locales, las VM en las instancias de vCenter Server y los contenedores en el clúster {{site.data.keyword.containerlong_notm}}.

![Local - Gestión de la nube](../../images/vcsiks-onprem-cloudmgt.svg "Local - Gestión de la nube")

Se utiliza strongSwan VPN para establecer la conectividad con los contenedores {{site.data.keyword.containerlong_notm}} desplegados. strongSwan se podría sustituir por la conectividad Direct-link.

En el diagrama, CAM crea de forma lógica conexiones en la nube con los entornos de vCenters, proveedores de nube, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}. Los clústeres de {{site.data.keyword.icpfull_notm}} deben desplegarse en cada centro de datos o entorno de nube, y MCM proporciona el mecanismo para conectar los clústeres de {{site.data.keyword.icpfull_notm}} en una única vista de gestión.

## Enlaces relacionados
{: #vcsiks-arch-overview-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-hybridity-intro#vcs-hybridity-intro)
