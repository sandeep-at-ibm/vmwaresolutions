---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-11"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de la prueba de un solo nodo para migración y modernización de apps
{: #cloud_modern_bundle_overview}

La prueba de un solo nodo para la migración y modernización de apps le permite realizar una prueba de IBM Cloud para migrar cargas de trabajo de VMware a IBM Cloud y, a continuación, modernizar cargas de trabajo simples utilizando contenedores.

La prueba de un solo nodo es una versión de prueba de IBM Cloud Private Hosted on VMware vCenter Server on IBM Cloud que proporciona la plataforma de gestión de Kubernetes para contenedores y la plataforma VMware de un solo arrendatario que se puede gestionar utilizando las mismas herramientas que en entornos locales. Puede aprovechar la velocidad y la capacidad de escalado de la nube mientras mantiene el mismo nivel de control y visibilidad que se proporciona en el entorno local.

La prueba está diseñada para la migración de un máximo de 20 cargas de trabajo sencillas de desarrollo o de prueba utilizando vCenter Server on IBM Cloud con el paquete híbrido (Hybridity) y la contenerización de dichas cargas de trabajo con la plataforma de desarrollo de aplicaciones de IBM Cloud Private Hosted basada en Kubernetes. La automatización instalará y configurará VMware HCX en IBM Cloud, proporcionará una clave de activación de HCX local e instalará y configurará una pequeña topología de desarrollo o prueba de IBM Cloud Private Hosted en cuestión de horas.

La prueba de un solo nodo para la migración y modernización de apps es solo para la prueba de concepto (POC). No ejecute cargas de trabajo de producción en este entorno. Las funciones de gestión, como la adición y eliminación de hosts y clústeres, la solicitud de servicios complementarios y la aplicación de actualizaciones, no reciben soporte.
{:important}

Para sacar el máximo provecho de la instancia de prueba de un solo nodo, puede utilizar [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf) de [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html), que le ayudarán con la migración de cargas de trabajo de VMware a IBM Cloud. Además, [IBM Cloud Garage Services](https://www.ibm.com/cloud/garage/) le puede ayudar a acelerar la modernización de aplicaciones con las prácticas nativas de la nube más avanzadas.

Esta versión de prueba está pensada para utilizarla durante un máximo de 90 días. Cuando finalice el periodo de prueba, puede suprimir este entorno y suministrar un nuevo entorno que se ajuste a sus necesidades de capacidad.
{:note}

## Especificaciones técnicas de instancias de prueba de un solo nodo para migración y modernización de apps
{: #cloud_modern_bundle_overview-tech-specs}

En la instancia de prueba de un solo nodo para la migración y modernización de apps se incluyen los siguientes componentes.

La disponibilidad y los precios de las configuraciones estandarizadas de hardware pueden variar en función del {{site.data.keyword.CloudDataCent_notm}} seleccionado para el despliegue.
{:note}

### Servidor nativo
{: #cloud_modern_bundle_overview-bare-metal}

Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz con 384 GB de RAM) para un máximo de unas 20 VM

#### Sobrecargas de CPU
{: #cloud_modern_bundle_overview-cpu}

* Sobrecarga de 16:1 de CPU para gestión de vCenter Server, HCX y 20 VM de carga de trabajo de cliente
* Sobrecarga de 11:1 de CPU para IBM Cloud Private

#### Sobrecargas de RAM
{: #cloud_modern_bundle_overview-ram}

* Sobrecarga de 1.22:1 de RAM para un despliegue de cliente de 20 VM de carga de trabajo con 8 GB cada una
* 1:1 (sin sobrecarga) para un despliegue de cliente de nueve VM de carga de trabajo con 8 GB cada una

### Almacenamiento NFS
{: #cloud_modern_bundle_overview-nfs-storage}

* 2 TB para gestión
* 1 TB para carga de trabajo de cliente (para 20 VM de cliente)
* 4 TB para IBM Cloud Private Hosted

### Especificaciones de red de las instancias de prueba de un solo nodo para migración y modernización de apps
{: #cloud_modern_bundle_overview-networking-specs}

Se solicitan los siguientes componentes del sistema de redes:
*  Enlaces ascendentes de red pública y privada de 10 Gbps
*  Tres VLAN (LAN virtuales): una VLAN pública y dos VLAN privadas
*  Se despliega una VXLAN (LAN extensible virtual) con DLR (direccionador lógico distribuido) para una potencial comunicación este-oeste entre cargas de trabajo locales conectadas a redes de la capa 2 (L2). La VXLAN se despliega como una topología de direccionamiento de ejemplo, que puede modificar o eliminar o a la que puede añadir componentes. También puede añadir zonas de seguridad adjuntando más VXLAN a las nuevas interfaces lógicas del DLR.
*  Dos VMware NSX Edge Services Gateways:
  * Una Edge Services Gateway (ESG) de NSX de VMware de servicios de gestión segura para el tráfico de gestión de HTTPS saliente, desplegado por IBM como parte de la topología del sistema de redes de gestión. Las VM de gestión de IBM utilizan esta ESG para comunicarse con componentes externos específicos de gestión de IBM que están relacionados con la automatización.

    El usuario no puede acceder ni utilizar esta ESG. Si la modifica, es posible que no pueda gestionar la instancia de prueba de un solo nodo para la migración y modernización de apps desde la consola de {{site.data.keyword.vmwaresolutions_short}}. Además, tenga en cuenta que el uso de un cortafuegos o la inhabilitación de las comunicaciones ESG con componentes externos de gestión de IBM harán que {{site.data.keyword.vmwaresolutions_short}} quede inutilizable.
    {:important}
  * Una Edge Services Gateway de NSX de VMware gestionada por el cliente para el tráfico de salida y de entrada de carga de trabajo HTTPS, que IBM despliega como plantilla que puede modificar para proporcionar acceso VPN o acceso público.

### Instancias de servidor virtual
{: #cloud_modern_bundle_overview-vsi}

Se solicitan las siguientes instancias de servidor virtual (VSI):

* Una VSI para IBM CloudBuilder, que se cancela una vez completado el despliegue de la instancia.
* Se despliega y se puede consultar una VSI de Microsoft Windows Server para Microsoft Active Directory (AD). La VSI funciona como el DNS para la instancia en la que se han registrado los hosts y las máquinas virtuales.

### Licencias proporcionadas por IBM y tarifas
{: #cloud_modern_bundle_overview-license-and-fee}

En el pedido de la instancia de prueba de un solo nodo para la migración y modernización de apps se incluyen las siguientes licencias.

* VMware vSphere Enterprise Plus 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4
* IBM Cloud Private Hosted V3.1

Las instancias de prueba de un solo nodo para la migración y modernización de apps no admiten la opción de traer su propia licencia (BYOL).
{:note}

## Especificaciones técnicas de VMware HCX on IBM Cloud
{: #cloud_modern_bundle_overview-hcx-tech-specs}

La prueba de un solo nodo para la migración y modernización de apps incluye HCX on {{site.data.keyword.cloud_notm}}. Los componentes siguientes se solicitan y se incluyen en el servicio HCX on {{site.data.keyword.cloud_notm}}.

Las instancias de HCX locales incluyen solo la licencia y la activación.
{:note}

### Un par activo/pasivo de pasarelas de servicio VMware NSX Edge para la gestión de HCX
{: #cloud_modern_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo de gestión HCX - máquina virtual
{: #cloud_modern_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: 60 GB VMDK

Los dispositivos HCX adicionales se despliegan durante la configuración, según sean necesarios para la conectividad de L2, la optimización de WAN y las conexiones de pasarela.

### Especificaciones de red para el servicio HCX on IBM Cloud
{: #cloud_modern_bundle_overview-hcx-networking-specs}

* Una subred portátil pública con 16 direcciones IP
* Dos subredes portátiles privadas con 64 direcciones IP
* Ocho direcciones IP desde una subred vMotion portátil privada

## Especificaciones técnicas de IBM Cloud Private Hosted
{: #cloud_modern_bundle_overview-icp-tech-specs}

IBM Cloud Private Hosted V3.1 se instala utilizando la topología de desarrollo o de prueba en todas las instancias de prueba de un solo nodo para la migración y modernización de apps. Para obtener más información acerca de IBM Cloud Private Hosted, consulte [Visión general de IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview).

## Enlaces relacionados
{: #cloud_modern_bundle_overview-related}

* [Guía de vCenter Server e IBM Cloud Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Apertura de una incidencia para IBM Cloud privado](https://www.ibm.com/mysupport/s/?language=en_US)
* [Documentación de VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Obtención de HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
