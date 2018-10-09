---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Visión general de vCenter Server con el paquete híbrido (Hybridity)

VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity) es una instancia disponible en V2.3 y releases posteriores. A partir de V2.6, la instancia de vCenter Server con el paquete híbrido (Hybridity) está disponible para Business Partners.

vCenter Server con el paquete híbrido (Hybridity) es una red privada alojada que ofrece la pila de VMware vSphere como un servicio. El entorno VMware se crea sobre cuatro {{site.data.keyword.baremetal_short}} de {{site.data.keyword.cloud_notm}}, incluye VMware vSAN como almacenamiento dedicado, proporciona funciones automáticas de despliegue y configuración de un cortafuegos lógico fácil de gestionar respaldado por VMware NSX y cuenta con el servicio VMware HCX on {{site.data.keyword.cloud_notm}}.

En muchos casos, todo el entorno se puede suministrar en menos de un día, y la capacidad de cálculo de la infraestructura de servidores nativos se puede aumentar y reducir de forma rápida y elástica según las necesidades.

Para aumentar la capacidad de almacenamiento basado en vSAN de un clúster vSAN, puede añadir más servidores ESXi después del despliegue.

Puede actualizar la edición VMware NSX Advanced a la edición Enterprise, y puede adquirir más componentes de VMware, como por ejemplo VMware vRealize Operations.

Puede añadir servicios gestionados por IBM si desea descargar las operaciones cotidianas y el mantenimiento de la virtualización, el sistema operativo invitado o las capas de aplicaciones. El equipo de {{site.data.keyword.cloud_notm}} Professional Services también está disponible para ayudarle a acelerar la implantación en la nube con servicios de migración, implementación, planificación e incorporación.

## Arquitectura de vCenter Server con el paquete híbrido (Hybridity)

En el gráfico siguiente se muestra la arquitectura general y los componentes del despliegue de tres nodos de vCenter Server con el paquete híbrido (Hybridity).

Figura 1. Arquitectura general de vCenter Server con el paquete híbrido (Hybridity)

![Arquitectura de vCenter Server con el paquete híbrido (Hybridity)](hybrid_architecture.svg "Arquitectura general de vCenter Server con el paquete híbrido (Hybridity)")

### Infraestructura física

Esta capa proporciona la infraestructura física (recursos de cálculo, de almacenamiento y de red) que utilizará la infraestructura virtual.

### Infraestructura de virtualización (cálculo, almacenamiento y red)

Esta capa virtualiza la infraestructura física mediante diversos productos de VMware:
* VMware vSphere virtualiza los recursos físicos de cálculo.
* VMware Virtual SAN (vSAN) proporciona almacenamiento compartido definido por software, basado en el almacenamiento de los servidores físicos.
* VMware NSX es la plataforma de virtualización de red que proporciona los componentes lógicos de red y las redes virtuales.

### Gestión de la virtualización

Esta capa consta de vCenter Server Appliance (vCSA), NSX Manager, dos NSX ESG, tres controladores NSX, el dispositivo virtual Platform Services Controller (PSC) y la Instancia de servidor virtual (VSI) de IBM CloudDriver. La VSI de CloudDriver se despliega a petición según sea necesario para determinadas operaciones, como por ejemplo, añadir hosts al entorno.

La oferta básica se despliega con un dispositivo vCenter Server cuyo tamaño se ajusta para dar soporte a un entorno con un máximo de 400 hosts y hasta 4000 máquinas virtuales. Se pueden utilizar las mismas herramientas y scripts compatibles con la API de vSphere para gestionar el entorno VMware alojado por IBM.

En total, la oferta básica necesita 38 vCPU y 67 GB de vRAM que se reservan para la capa de gestión de virtualización. El resto de la capacidad de host para sus VM depende de varios factores, como la tasa de sobresuscripción, el dimensionamiento de VM y los requisitos de rendimiento de la carga de trabajo.

Para ver los requisitos de recurso de gestión adicionales al desplegar el servicio de HCX on {{site.data.keyword.cloud_notm}}, consulte [Visión general de VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### Infraestructura híbrida

Esta capa proporciona una abstracción de recursos entre los sitios locales y los sitios de {{site.data.keyword.cloud_notm}} para que pueda mover hacia atrás y hacia adelante cargas de trabajo de forma segura y sencilla sin necesidad de cambiar características de las VM como por ejemplo sus direcciones IP.

En función de la VMware Hybrid Cloud Extension (HCX), puede crear interconexiones débilmente acopladas entre los sitios locales y de {{site.data.keyword.cloud_notm}} para habilitar la migración masiva de VM o de vMotion activos de VM sin tiempo de inactividad.

## Especificaciones técnicas para las instancias de vCenter Server con el paquete híbrido (Hybridity)

Se incluyen los siguientes componentes en la instancia de vCenter Server con el paquete híbrido (Hybridity):

**Nota:** La disponibilidad y los precios de las configuraciones estandarizadas de hardware pueden variar en función del {{site.data.keyword.CloudDataCent_notm}} seleccionado para el despliegue.

### Servidor nativo

El pedido de la instancia de vCenter Server con el paquete híbrido (Hybridity) incluye cuatro {{site.data.keyword.baremetal_short}} personalizados. Están disponibles los siguientes modelos de CPU:
  * 2-CPU Intel Broadwell generation (Intel Xeon E5-2600 v4 series)
  * 2-CPU Intel Skylake generation (Intel Xeon 4100/5100/6100 series)

### Redes

Se solicitan los siguientes componentes del sistema de redes:
*  Enlaces ascendentes de red pública y privada de 10 Gbps
*  Tres VLAN (LAN virtuales): una VLAN pública y dos VLAN privadas
*  Se despliega una VXLAN (LAN extensible virtual) con DLR (direccionador lógico distribuido) para una potencial comunicación este-oeste entre cargas de trabajo locales conectadas a redes de la capa 2 (L2). La VXLAN se despliega como una topología de direccionamiento de ejemplo, que puede modificar o eliminar o a la que puede añadir componentes. También puede añadir zonas de seguridad por conectar VXLAN adicionales a las nuevas interfaces lógicas del DLR.
*  Dos VMware NSX Edge Services Gateways:
  * Una Edge Services Gateway (ESG) de NSX de VMware de servicios de gestión segura para el tráfico de gestión de HTTPS saliente, desplegado por IBM como parte de la topología del sistema de redes de gestión. Las VM de gestión de IBM utilizan esta ESG para comunicarse con componentes externos específicos de gestión de IBM que están relacionados con la automatización. Para obtener más información, consulte [Configuración de la red para que utilice la ESG gestionada por el cliente](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    **Importante**: el usuario no puede acceder ni utilizar esta ESG. Si lo modifica, es posible que no pueda gestionar la instancia de vCenter Server con el paquete híbrido (Hybridity) desde la consola de {{site.data.keyword.vmwaresolutions_short}}. Además, tenga en cuenta que el uso de un cortafuegos o la inhabilitación de las comunicaciones ESG con componentes externos de gestión de IBM harán que {{site.data.keyword.vmwaresolutions_short}} quede inutilizable.
  * Una Edge Services Gateway de NSX de VMware gestionada por el cliente para el tráfico de salida y de entrada de carga de trabajo HTTPS, que IBM despliega como plantilla que puede modificar para proporcionar acceso VPN o acceso público. Para obtener más información, consulte [¿Representa NSX Edge gestionado por el cliente un riesgo para la seguridad?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

Para obtener más información sobre los componentes de red ordenados al desplegar el servicio de HCX on {{site.data.keyword.cloud_notm}}, consulte [Visión general de HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### Instancias de servidor virtual

Se solicitan las siguientes instancias de servidor virtual (VSI):
* Una VSI para IBM CloudBuilder, que se cierra una vez completado el despliegue de la instancia.
* Puede elegir desplegar un único Microsoft Windows Server VSI for Microsoft Active Directory (AD) o dos VM Microsoft Windows de alta disponibilidad en el clúster de gestión para ayudar a mejorar la seguridad y la solidez.

### Almacenamiento vSAN

El almacenamiento de vSAN ofrece configuraciones personalizadas, con diversas opciones para el tipo y la cantidad de disco:
* Cantidad de disco: 2, 4, 6 u 8.
* Disco de almacenamiento: SSD SED de 960 GB, SSD SED de 1,9 TB o SSD SED de 3,8 TB.

  Además, se solicitan dos discos de memoria caché de 960 GB por host.
* Opción de Intel Optane de alto rendimiento, que proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad. Esta opción depende del modelo de CPU.

### Licencias proporcionadas por IBM y tarifas

Las licencias siguientes se incluyen con el pedido de instancia de vCenter Server con el paquete híbrido (Hybridity).

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Advanced o Enterprise) 6.4
* VMware vSAN (Advanced o Enterprise) 6.6

Puede que se apliquen tarifas de servicio y soporte adicionales.

## Especificaciones técnicas para los nodos de expansión de vCenter Server con el paquete híbrido (Hybridity)

Cada nodo de expansión de vCenter Server con el paquete híbrido (Hybridity) desplegará e incurrirá en cargos para los siguientes componentes de la cuenta de {{site.data.keyword.cloud_notm}}.

### Hardware para nodos de expansión

Un servidor nativo con la configuración personalizada.

### Licencias y tarifas correspondientes a nodos de expansión

* Un VMware vSphere Enterprise Plus 6.5u1
* Un VMware NSX Service Providers Edition (Advanced o Enterprise) 6.4
* Una cuota de soporte y servicios
* VMware vSAN (Advanced o Enterprise) 6.6

**Importante**: Solo debe gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no desde el {{site.data.keyword.slportal}} ni mediante ningún otro método fuera de la consola. Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola.

**ATENCIÓN:**: el hecho de gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}}, que se instalaron en la cuenta de {{site.data.keyword.cloud_notm}} al solicitar la instancia, desde fuera de la consola de {{site.data.keyword.vmwaresolutions_short}} podría hacer que el entorno quedara inestable. Estas actividades de gestión incluyen:
*  Añadir, modificar, devolver o eliminar componentes
*  Ampliar o reducir la capacidad de la instancia mediante la adición o eliminación de servidores ESXi
*  Apagar componentes
*  Rearrancar servicios

   Las excepciones a estas actividades incluyen la gestión de comparticiones del archivo de almacenamiento compartido desde el {{site.data.keyword.slportal}}. Estas actividades incluyen: solicitar, suprimir (lo que puede afectar los almacenes de datos si están montados), autorizar y montar comparticiones del archivo de almacenamiento compartido.

### Enlaces relacionados

* [Lista de materiales de software de vCenter Server](vc_bom.html)
* [Requisitos y planificación de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_planning.html)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_orderinginstance.html)
* [Visión general de HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
