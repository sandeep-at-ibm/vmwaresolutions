---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Visión general de la arquitectura
{: #vcsicp-arch-overview}

Las ofertas de {{site.data.keyword.vmwaresolutions_full}} proporcionan la automatización para desplegar componentes de tecnología VMware en {{site.data.keyword.CloudDataCents_notm}} en todo el mundo.
La arquitectura consta de una sola región de nube y permite la ampliación a más regiones de nube ubicadas en otra geografía o en otro pod de {{site.data.keyword.cloud_notm}} dentro del mismo centro de datos.

Puede desplegar manualmente los productos {{site.data.keyword.cloud_notm}} Private y Cloud Automation Manager (CAM) en la plataforma de virtualización local, lo que permite gestionar la nube desde ubicaciones locales. Como alternativa, {{site.data.keyword.icpfull_notm}} y CAM se ofrecen como extensiones de servicio de un despliegue de vCenter Server on {{site.data.keyword.cloud_notm}} nuevo o existente, mediante automatización, lo que permite gestionar la nube desde {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} Private es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones locales contenerizadas. {{site.data.keyword.cloud_notm}} Private es un entorno integrado para gestionar contenedores que incluye el coordinador de contenedores Kubernetes,
un repositorio de imágenes privadas, una consola de gestión e infraestructuras de supervisión.

IBM Multi-Cluster Cloud Manager MCM proporciona visibilidad de usuario, gestión centrada en aplicaciones (política, despliegues, estado, operaciones) y conformidad basada en políticas entre nubes y clústeres. Con MCM, tiene el control sobre los clústeres de Kubernetes. MCM le ayuda a asegurarse de que sus clústeres son seguros, funcionan de forma eficiente y ofrecen una plataforma de gestión de servicios que se ejecuta en {{site.data.keyword.cloud_notm}} Private, lo que permite a los desarrolladores y a los administradores satisfacer las demandas de la empresa.

Utilice Cloud Automation Manager Service Composer para visualizar los servicios de nube híbrida en el catálogo de {{site.data.keyword.cloud_notm}} Private.

## Plataforma de gestión de nube desde IBM Cloud
{: #vcsicp-arch-overview-ibm-cloud-side-platform}

El diagrama siguiente es un ejemplo de un despliegue de {{site.data.keyword.icpfull_notm}} y CAM con la infraestructura de {{site.data.keyword.cloud_notm}}, con conexiones con el vCenter local e {{site.data.keyword.containerlong_notm}} desplegado en {{site.data.keyword.cloud_notm}}. Los usuarios pueden desplegar máquinas virtuales (VM) de forma local y VM en una instancia de vCenter Server, y contenedores en el clúster de {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}.

Figura 1. Gestión de la nube desde la nube

![Gestión de la nube en la nube](vcsicp-oncloud-cloudmgt.svg)

En el diagrama, CAM crea de forma lógica conexiones en la nube con los entornos de vCenters, proveedores de nube, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}. Los clústeres de {{site.data.keyword.icpfull_notm}} deben desplegarse en cada entorno de nube del centro de datos, y MCM proporciona el mecanismo para conectar los clústeres de {{site.data.keyword.icpfull_notm}} en una única vista de gestión.

Puede desplegar {{site.data.keyword.icpfull_notm}} con los componentes NSX-V o NSX-T. {{site.data.keyword.icpfull_notm}} con NSX-V permite ejecutar VM {{site.data.keyword.icpfull_notm}} en la red VXLAN y utilizar el sistema de red interno de Calico de Kubernetes.

{{site.data.keyword.icpfull_notm}} con NSX-T permite a los usuarios controlar y configurar el sistema de red, de subred y las políticas desde la interfaz de usuario central (NSX-T Manager). Consulte la [guía de redes de vCenter Server](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) para ver las diferencias entre NSX-V y NSX-T.

## Plataforma de gestión de nube local
{: #vcsicp-arch-overview-on-premises-platform}

En el diagrama siguiente se muestra un ejemplo de despliegue de {{site.data.keyword.icpfull_notm}} y CAM en la infraestructura local, con conexiones con el vCenter e {{site.data.keyword.containerlong_notm}} desplegado en {{site.data.keyword.cloud_notm}}. Los usuarios pueden desplegar las VM y los contenedores locales, las VM en las instancias de vCenter Server y los contenedores en el clúster {{site.data.keyword.containerlong_notm}}.

Figura 2. Gestión de nube desde el entorno local
![Gestión de nube desde el entorno local](vcsicp-onprem-cloudmgt.svg)

Se utiliza strongSwan VPN para establecer la conectividad con los contenedores {{site.data.keyword.containerlong_notm}} desplegados. strongSwan VPM se puede sustituir por una conectividad Direct Link.

En el diagrama, CAM crea de forma lógica conexiones en la nube con los entornos de vCenters, proveedores de nube, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}. Los clústeres de {{site.data.keyword.icpfull_notm}} deben desplegarse en cada entorno de nube del centro de datos, y MCM proporciona el mecanismo para conectar los clústeres de {{site.data.keyword.icpfull_notm}} en una única vista de gestión.

## Enlaces relacionados
{: #vcsicp-arch-overview-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
