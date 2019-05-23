---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-08"

subcollection: vmware-solutions


---

# Visión general de la modernización de aplicaciones
{: #vcsicp-appmod}

En el diagrama siguiente se muestra la arquitectura de referencia de la modernización de aplicaciones que se despliega en Acme Skateboards. La arquitectura se describe en profundidad en esta serie de documentos.

![Diagrama de visión general de arquitectura](../../images/vcsicp-arch-overview.svg "Diagrama de visión general de arquitectura")

Esta arquitectura híbrida permite a Acme Skateboards alcanzar los siguientes objetivos:
- Migrar máquinas virtuales (VM) VMware desde el entorno local a {{site.data.keyword.cloud}} con muy poco o ningún tiempo de inactividad y sin tener que reconfigurar las aplicaciones.
- Iniciar el proceso de modernización de aplicaciones, permitiéndoles centrarse en contenerizar las interfaces web más simples y el middleware al tiempo que permite que bases de datos más complejas permanezcan como máquinas virtuales.
- Utilizar {{site.data.keyword.cloud_notm}} Automation Manager (CAM) para disponer de una infraestructura como código (IaC) para componer y coordinar servicios en los que intervienen tanto de máquinas virtuales como contenedores para integrarlos en sus cadenas de herramientas de DevOps y en su solución ITSM.

La arquitectura de referencia comprende los siguientes componentes principales:
- **Virtualización local**: un clúster VMware que actualmente aloja las VM de Acme Skateboards. Estas máquinas virtuales alojan actualmente las aplicaciones que se van a modernizar. Este clúster debe cumplir los requisitos previos de la
[Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro) para que pueda ejecutar HCX. HCX amplía las redes locales a {{site.data.keyword.cloud_notm}}, permitiendo a los clientes migrar las VM a la instancia de VMware vCenter Server on {{site.data.keyword.cloud_notm}} que se ejecuta en {{site.data.keyword.cloud_notm}} y viceversa si es necesario.

- **{{site.data.keyword.vmwaresolutions_short}}**: la instancia de vCenter Server proporciona los componentes fundamentales de VMware, como vSphere, vCenter Server, NSX-V y opciones de almacenamiento que incluyen vSAN o almacenamiento {{site.data.keyword.cloud_notm}} Endurance, necesarios para desplegar automáticamente una solución VMware Software Defined Data Center (SDDC). El clúster VMware es el destino de las máquinas virtuales migradas y de algunas de las aplicaciones modernizadas en los contenedores alojados en {{site.data.keyword.icpfull_notm}}. Estos son los componentes clave de vCenter Server:
    - **NSX-V**: NSX-V ofrece la capa de virtualización de red en vCenter Server que proporciona una superposición de red para las VM de Acme Skateboards. NSX-V habilita BYOIP y aísla las redes de carga de trabajo de las redes de IBM Cloud. NSX-V está programado por HCX para crear las redes que Acme Skateboards extiende desde el entorno local.

    - **NSX-T**: NSX-T proporciona un conjunto común de herramientas para la gestión de la red y de la seguridad tanto de contenedores como de máquinas virtuales. NSX-T es totalmente compatible con la interfaz de red de contenedor (CNI) de Kubernetes y se integra con la CNI para proporcionar redes de contenedores. NSX-T proporciona la red de superposición que utilizan las aplicaciones modernizadas y sustituye a Calico, que utilizan de forma nativa {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}.

- **{{site.data.keyword.icpfull_notm}}**: {{site.data.keyword.icpfull_notm}} es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas. {{site.data.keyword.icpfull_notm}} es un entorno integrado que incluye el coordinador de contenedores Kubernetes, un repositorio de imágenes privadas, una consola de gestión, infraestructuras de supervisión y una interfaz gráfica de usuario, que proporciona una ubicación centralizada desde la que Acme Skateboards puede desplegar, gestionar, supervisar y escalar aplicaciones. La instancia de vCenter Server aloja los componentes de {{site.data.keyword.icpfull_notm}}, los nodos maestros, los nodos trabajadores, y los ejecuta como máquinas virtuales. {{site.data.keyword.icpfull_notm}} contiene lo siguiente:
    - **{{site.data.keyword.cloud_notm}} Automation Manager**: CAM es una plataforma de código como infraestructura (IaC) preparada para la empresa que proporciona un único panel para suministrar cargas de trabajo de VM, locales o en vCenter Server, junto con cargas de trabajo Kubernetes, en {{site.data.keyword.icpfull_notm}} o {{site.data.keyword.containerlong_notm}}, utilizando plantillas. CAM es una aplicación Docker que se ejecuta en una instalación {{site.data.keyword.icpfull_notm}} y que está estrechamente integrada para la autorización, el control de acceso basado en roles (RBAC) y otras funciones.
    - Las aplicaciones de Acme Skateboards contenerizadas que los clientes desean desplegar en este entorno.

- **{{site.data.keyword.containerlong_notm}}**: {{site.data.keyword.containerlong_notm}} permite a Acme Skateboards desplegar sus aplicaciones modernizadas en contenedores Docker que se ejecutan en clústeres Kubernetes. IBM gestiona por completo los nodos maestros, mientras que los nodos trabajadores de la agrupación de nodos trabajadores se despliegan en la misma cuenta de {{site.data.keyword.cloud_notm}} que su instancia de vCenter Server. Los nodos trabajadores pueden ser nativos, públicos o instancias de servidor virtual dedicado. Calico se instala y se configura automáticamente en {{site.data.keyword.containerlong_notm}}. Calico proporciona conectividad de red segura para contenedores y se configura en {{site.data.keyword.containerlong_notm}} para utilizar la encapsulación IP en IP para los paquetes que viajan a través de subredes y para utilizar NAT para las conexiones salientes de los contenedores.

- **Direct Link**: {{site.data.keyword.cloud_notm}} Direct Link utiliza el proveedor de WAN de Acme Skateboard para conectar su centro de datos a {{site.data.keyword.cloud_notm}} para ofrecer una conexión de red fiable, segura y de baja latencia. Esta conexión proporciona lo siguiente:
    - Acceso a las aplicaciones alojadas en la nube desde los usuarios de la empresa.
    - Tráfico de VM interno entre las máquinas virtuales locales y las de la nube.
    - Tráfico entre sistemas antiguos del centro de datos local y las VM en la nube.

## Principales ventajas para Acme Skateboards
{: #vcsicp-appmod-benefits}

vCenter Server ofrece los bloques básicos fundamentales que incluyen VMware vSphere, vCenter Server, NSX y opciones de almacenamiento compartido que incluyen vSAN, necesario para diseñar una solución de VMware Software Defined Data Center (SDDC) flexible que se adapte a sus cargas de trabajo.

En resumen, las ofertas de {{site.data.keyword.vmwaresolutions_short}} proporcionan las ventajas siguientes:

* Aceleran la entrega de proyectos de TI a desarrolladores y líneas de negocio, reduciendo el tiempo necesario para la adquisición, la arquitectura, la implementación y el despliegue de recursos de semanas o meses a horas.
* Mejoran la seguridad con servidores nativos dedicados en una nube privada alojada, incluido el despliegue de puntos finales de red privados en servicios de {{site.data.keyword.cloud_notm}}, como {{site.data.keyword.containerlong_notm}} y KMIP.
* Permiten llevar a cabo una gestión y gobierno coherentes de la nube híbrida desplegada, proporcionando acceso administrativo completo a la gestión de virtualización, conservando así las herramientas de VMware existentes, los scripts y las inversiones en formación.
* Aprovechan la experiencia de VMware a escala global con IBM Professional y Servicios gestionados que abarcan más de 30 {{site.data.keyword.CloudDataCents_notm}} en todo el mundo.

Los clientes que realicen la transición hacia plataformas de aplicaciones nativas en la nube, como {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}, se centran en la velocidad y en la innovación y no siempre tienen en mente la seguridad y la red. El tiempo de rentabilización de la aplicación desciende si tienen que esperar hasta que los equipos de red o de seguridad puedan solicitar servicios como equilibradores de carga, cortafuegos, conmutadores y direccionadores.

Esta arquitectura de referencia muestra cómo vCenter Server, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}} guían a Acme Skateboards de forma segura en su proceso de modernización de aplicaciones.

## Enlaces relacionados
{: #vcsicp-appmod-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
