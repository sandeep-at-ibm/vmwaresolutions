---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: single-node trial, data protection DR, tech specs data protection DR

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de Prueba de un solo nodo de Protección de datos y Recuperación tras desastre.
{: #dr_backup_bundle_overview}

La Prueba de un solo nodo de Protección de datos y Recuperación tras desastre le permite probar {{site.data.keyword.cloud}} para migrar y recuperar cargas de trabajo de VMware a {{site.data.keyword.cloud_notm}}. Además, la prueba de un solo nodo de Protección de datos y Recuperación tras desastre incluye los servicios Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX on {{site.data.keyword.cloud_notm}} y Zerto on {{site.data.keyword.cloud_notm}}.

La Prueba de un solo nodo es una versión de prueba de VMware vCenter Server on {{site.data.keyword.cloud_notm}} que proporciona la plataforma VMware de un solo arrendatario que se puede gestionar utilizando las mismas herramientas que en los entornos de instalaciones locales. Puede aprovechar la velocidad y la capacidad de escalado de la nube mientras mantiene el mismo nivel de control y visibilidad que se proporciona en el entorno local.

La Prueba está diseñada para la migración de un máximo de 20 cargas de trabajo sencillas de desarrollo o de prueba utilizando vCenter Server. La automatización instalará y configurará VMware HCX on {{site.data.keyword.cloud_notm}}, proporciona una clave de activación de HCX para instalaciones locales e instala Veeam on {{site.data.keyword.cloud_notm}} y Zerto on {{site.data.keyword.cloud_notm}} en cuestión de horas. Puede hacer copia de seguridad y replicar 20 máquinas virtuales (VM) con Veeam on {{site.data.keyword.cloud_notm}} y Zerto on {{site.data.keyword.cloud_notm}}. 

La Prueba de un solo nodo para protección de datos y recuperación tras desastre es solo como muestra de viabilidad(POC). No ejecute cargas de trabajo de producción en este entorno. Las funciones de gestión, como la adición y eliminación de hosts y clústeres, la solicitud de servicios complementarios adicionales y la aplicación de actualizaciones, no reciben soporte.
{:important}

Tras desplegar su instancia de Prueba de un solo nodo, puede utilizar [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:external} desde [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:external} como ayuda para su instancia. Además, [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:external} le puede ayudar a acelerar la modernización de aplicaciones con las prácticas nativas de la nube más avanzadas.

Esta versión de prueba está pensada para utilizarla durante un máximo de 90 días. Los cargos recurrentes mensuales se facturan en función de su planificación de facturación, y no cuando se solicita la instancia. Si la instancia no se cancela el último día (o antes) del ciclo de facturación, se le carga el mes siguiente. Es posible que una prueba de 90 días corresponda a cuatro meses de cargos, a menos que se realice la cancelación antes de que empiece el cuarto mes.
{:note}

Cuando finalice el periodo de prueba, puede suprimir este entorno y suministrar un nuevo entorno que se ajuste a sus necesidades de capacidad.

## Especificaciones técnicas para instancias de prueba de un solo nodo de Protección de datos y Recuperación tras desastre.
{: #dr_backup_bundle_overview-tech-specs}

En la instancia de prueba de un solo nodo para la protección de datos y recuperación tras desastre se incluyen los siguientes componentes.

La disponibilidad y los precios de las configuraciones estandarizadas de hardware pueden variar en función del {{site.data.keyword.CloudDataCent_notm}} seleccionado para el despliegue.
{:note}

### Servidor nativo
{: #dr_backup_bundle_overview-bare-metal}

Procesador Skylake Dual Intel Xeon Gold 5120 / 28 cores en total, 2,2 GHz con 384 GB RAM para hasta 20 VM.

#### Sobrecargas de CPU
{: #dr_backup_bundle_overview-cpu}

Sobrecarga de 16:1 de CPU para gestión de vCenter Server, HCX y 20 VM de carga de trabajo de cliente

#### Sobrecargas de RAM
{: #dr_backup_bundle_overview-ram}

* Sobrecarga de 1.22:1 de RAM para un despliegue de cliente de 20 VM de carga de trabajo con 8 GB cada una
* 1:1 (sin sobrecarga) para un despliegue de cliente de nueve VM de carga de trabajo con 8 GB cada una

### Almacenamiento NFS
{: #dr_backup_bundle_overview-nfs-storage}

* 2 TB para gestión
* 1 TB para carga de trabajo de cliente (para 20 VM de cliente)

### Especificaciones de red para instancias de prueba de un solo nodo de Protección de datos y Recuperación tras desastre.
{: #dr_backup_bundle_overview-networking-specs}

Se solicitan los siguientes componentes del sistema de redes:
*  Enlaces ascendentes de red pública y privada de 10 Gbps
*  Tres VLAN (LAN virtuales): una VLAN pública y dos VLAN privadas
*  Se despliega una VXLAN (LAN extensible virtual) con DLR (direccionador lógico distribuido) para una potencial comunicación este-oeste entre cargas de trabajo locales conectadas a redes de la capa 2 (L2). La VXLAN se despliega como una topología de direccionamiento de ejemplo, que puede modificar o eliminar o a la que puede añadir componentes. También puede añadir zonas de seguridad adjuntando más VXLAN a las nuevas interfaces lógicas del DLR.
*  Dos VMware NSX Edge Services Gateways:
  * Una Edge Services Gateway (ESG) de NSX de VMware de servicios de gestión segura para el tráfico de gestión de HTTPS saliente, desplegado por IBM como parte de la topología del sistema de redes de gestión. Las VM de gestión de IBM utilizan esta ESG para comunicarse con componentes externos específicos de gestión de IBM que están relacionados con la automatización.

    El usuario no puede acceder ni utilizar esta ESG. Si lo modifica, es posible que no pueda gestionar la prueba de un solo nodo para la instancia de protección de datos y recuperación tras desastre desde la consola de {{site.data.keyword.vmwaresolutions_short}}. Además, tenga en cuenta que el uso de un cortafuegos o la inhabilitación de las comunicaciones ESG con componentes externos de gestión de IBM harán que {{site.data.keyword.vmwaresolutions_short}} quede inutilizable.
    {:important}
  * Una Edge Services Gateway de NSX de VMware gestionada por el cliente para el tráfico de salida y de entrada de carga de trabajo HTTPS, que IBM despliega como plantilla que puede modificar para proporcionar acceso VPN o acceso público.

### Instancias de servidor virtual
{: #dr_backup_bundle_overview-vsi}

Se solicitan las siguientes instancias de servidor virtual (VSI):

* Una VSI para IBM CloudBuilder, que se cancela una vez completado el despliegue de la instancia.
* Se despliega y se puede consultar una VSI de Microsoft Windows Server para Microsoft Active Directory (AD). La VSI funciona como el DNS para la instancia en la que se han registrado los hosts y las máquinas virtuales.
* Una VSI para Zerto on {{site.data.keyword.cloud_notm}} - Zerto Virtual Manager.
* Una VSI con Veeam Backup and Replication 9.5 OS Add-on y Veeam Availability Suite 9.5.

### Licencias proporcionadas por IBM y tarifas
{: #dr_backup_bundle_overview-license-and-fee}

En el pedido de la instancia de prueba de un solo nodo para la protección de datos y recuperación tras desastre se incluyen las licencias siguientes.

* Las licencias de vCenter Server:
  * VMware vSphere Enterprise Plus 6.7u2
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Las instancias de prueba de un solo nodo para la protección de datos y la recuperación tras desastre no admiten la opción de traer su propia licencia (BYOL).
{:note}

## Especificaciones técnicas de VMware HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-tech-specs}

La Prueba de un solo nodo para la protección de datos y la recuperación tras desastre incluye HCX on {{site.data.keyword.cloud_notm}}. Los componentes siguientes se solicitan y se incluyen en el servicio HCX on {{site.data.keyword.cloud_notm}}.

Las instancias de HCX locales incluyen solo la licencia y la activación.
{:note}

### Un par activo/pasivo de pasarelas de servicio VMware NSX Edge para la gestión de HCX
{: #dr_backup_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo de gestión HCX - Máquina virtual
{: #dr_backup_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: 60 GB VMDK

Los dispositivos HCX adicionales se despliegan durante la configuración, según sean necesarios para la conectividad de L2, la optimización de WAN y las conexiones de pasarela.

### Especificaciones de red para HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-networking-specs}

* Una subred portátil pública con 16 direcciones IP
* Dos subredes portátiles privadas con 64 direcciones IP
* Ocho direcciones IP desde una subred vMotion portátil privada

## Especificaciones técnicas para Veeam on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-veeam-tech-specs}

La Prueba de un solo nodo para la protección de datos y la recuperación tras desastre incluye Veeam on {{site.data.keyword.cloud_notm}}. Los siguientes componentes se solicitan y se incluyen en el servicio Veeam on {{site.data.keyword.cloud_notm}}.

* Licencia de 25 paquetes de la Veeam Availability Suite
* 4000 GB de almacenamiento
* Rendimiento del almacenamiento de 0,25 IOPS/GB
* Windows Server 2016 Standard Edition (64 bits)
* 4 núcleos x 2,0 GHz
* 8 GB RAM
* Enlace ascendente de red privada de 1 Gbps
* Disco de 100 GB (SAN)

## Especificaciones técnicas para Zerto on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-zerto-tech-specs}

La Prueba de un solo nodo para la protección de datos y la recuperación tras desastre incluye Zerto on {{site.data.keyword.cloud_notm}}. Los siguientes componentes se solicitan y se incluyen en el servicio Zerto on {{site.data.keyword.cloud_notm}}.

* Licencia de Zerto Virtual Replication V6.5u3
* Una VSI (instancia de servicio virtual) - Zerto Virtual Manager
* 2 núcleos x 2.0 GHz
* 4 GB de RAM
* Windows Server 2016 Standard Edition (64 bits)
* Disco de 100 GB (SAN)

## Especificaciones técnicas de IBM Cloud Automation Manager
{: #dr_backup_bundle_overview-cam-tech-specs}

{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 se instala utilizando la topología de desarrollo o de prueba en todas las instancias de prueba de un solo nodo para la protección de datos y la recuperación tras desastre. Para obtener más información sobre {{site.data.keyword.cloud_notm}} Automation Manager, consulte [Documentación de {{site.data.keyword.cloud_notm}} Automation Manager](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: external}.

## Enlaces relacionados
{: #dr_backup_bundle_overview-related}

* [Recursos de VMware HCX](https://hcx.vmware.com/#/docs){:external}
* [Guía de usuario de VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)
