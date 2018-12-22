---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---

# Visión general de la arquitectura

Las ofertas de {{site.data.keyword.vmwaresolutions_full}} proporcionan la automatización para desplegar componentes de tecnología VMware en {{site.data.keyword.CloudDataCents_notm}} en todo el mundo.
La arquitectura consta de una sola región de nube y permite la ampliación a más regiones de nube ubicadas en otra geografía y/o en otro pod de {{site.data.keyword.cloud_notm}} dentro del mismo centro de datos.

Puede desplegar manualmente los productos {{site.data.keyword.cloud_notm}} Private (ICP) y Cloud Automation Manager (CAM) en la plataforma de virtualización local, lo que permite gestionar la nube desde ubicaciones locales. Como alternativa, ICP y CAM se ofrecen como extensiones de servicio de un despliegue de vCenter Server on {{site.data.keyword.cloud_notm}} nuevo o existente, mediante automatización, lo que permite gestionar la nube desde {{site.data.keyword.cloud_notm}}.

ICP es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones de contenedor locales. ICP es un entorno integrado para gestionar contenedores que incluye el coordinador de contenedores Kubernetes,
un repositorio de imágenes privadas, una consola de gestión e infraestructuras de supervisión.

IBM Multi-Cluster Cloud Manager MCM proporciona visibilidad de usuario, gestión centrada en aplicaciones (política, despliegues, estado, operaciones) y conformidad basada en políticas entre nubes y clústeres. Con MCM, tiene el control sobre los clústeres de Kubernetes. Se asegura de que sus clústeres sean seguros, que funcionen de forma eficiente y que ofrezcan una plataforma de gestión de servicios que se ejecute en ICP que permita a los desarrolladores y a los administradores satisfacer las necesidades empresariales.
Utilice Cloud Automation Manager Service Composer para visualizar los servicios de nube híbrida en el catálogo de ICP.

## Plataforma de gestión de nube desde IBM Cloud

El siguiente diagrama es un ejemplo de un despliegue de ICP y CAM con la infraestructura de {{site.data.keyword.cloud_notm}, con conexiones a vCenter local y al servicio IBM Kubernetes Service (IKS) desplegado en {{site.data.keyword.cloud_notm}. Los usuarios pueden desplegar máquinas virtuales (VM) locales y VM en una instancia de vCenter Server, y contenedores en el clúster ICP e IKS.

Figura 1. Gestión de la nube desde la nube

![Gestión de la nube en la nube](vcsicp-oncloud-cloudmgt.svg)

En el diagrama, CAM crea de forma lógica conexiones en la nube con los entornos de vCenters, proveedores de nube, ICP e IKS. Los clústeres de ICP deben desplegarse en cada entorno de nube del centro de datos, y MCM proporciona el mecanismo para conectar los clústeres de ICP en una única vista de gestión.

Puede desplegar ICP con componentes NSX-V o NSX-T. ICP con NSX-V permite ejecutar VM ICP en la red VXLAN y utilizar el sistema de red interno de Calico de Kubernetes.

ICP con NSX-T permite a los usuarios controlar y configurar el sistema de red, de subred y las políticas desde la interfaz de usuario central (NSX-T Manager). Consulte la [guía de redes de vCenter Server](../vcsnsxt/vcsnsxt-intro.html) para ver las diferencias entre NSX-V y NSX-T.

## Plataforma de gestión de nube local

El siguiente diagrama es un ejemplo de un despliegue de ICP y CAM en la infraestructura local, con conexiones con vCenter y con IKS desplegado en {{site.data.keyword.cloud_notm}. Los usuarios pueden desplegar las VM y los contenedores locales, las VM en las instancias de vCenter Server y los contenedores en el clúster IKS.

Figura 2. Gestión de nube desde el entorno local
![Gestión de nube desde el entorno local](vcsicp-onprem-cloudmgt.svg)

Se utiliza strongSwan VPN para establecer la conectividad con los contenedores IKS desplegados. strongSwan VPM se puede sustituir por una conectividad Direct Link.

En el diagrama, CAM crea de forma lógica conexiones en la nube con los entornos de vCenters, proveedores de nube, ICP e IKS. Los clústeres de ICP deben desplegarse en cada entorno de nube del centro de datos, y MCM proporciona el mecanismo para conectar los clústeres de ICP en una única vista de gestión.

### Enlaces relacionados

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
