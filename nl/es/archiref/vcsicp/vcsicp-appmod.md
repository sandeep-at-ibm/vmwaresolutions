---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

# Visión general de la modernización de aplicaciones

En el diagrama siguiente se muestra la arquitectura de referencia de la modernización de aplicaciones que se desplegará en Acme Skateboards y que se describe en profundidad en esta serie de documentos.

Figura 1. Diagrama de visión general de la arquitectura
![Diagrama de visión general de la arquitectura](vcsicp-arch-overview.svg)

Esta arquitectura híbrida permitirá a Acme Skateboards:
- Migrar máquinas virtuales VMware desde el entorno local a IBM Cloud muy poco o ningún tiempo de inactividad y sin tener que reconfigurar las aplicaciones.
- Iniciar el proceso de modernización de aplicaciones, permitiéndoles centrarse en contenerizar las interfaces web más simples y el middleware al tiempo que permite que bases de datos más complejas permanezcan como máquinas virtuales.
- Aprovechar Cloud Automation Manager (CAM) para disponer de una infraestructura como código (IaC) para componer y orquestar servicios en los que intervienen tanto de máquinas virtuales como contenedores para integrarlos en sus cadenas de herramientas de DevOps y en su solución ITSM.

La arquitectura de referencia comprende los siguientes componentes principales:
- **Virtualización local**: es un clúster VMware que actualmente aloja las VM de Acme Skateboards. Son estas máquinas virtuales las que actualmente alojan las aplicaciones que se modernizarán. Este clúster debe cumplir con los requisitos previos de la arquitectura de la [solución VMware HCX on IBM Cloud](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) para poder ejecutar HCX. HCX amplía las redes locales a IBM Cloud, permitiendo a los clientes migrar las VM a la instancia de VMware vCenter Server on IBM Cloud (VCS) que se ejecuta en IBM Cloud y viceversa si es necesario.

- **Soluciones IBM Cloud for VMware**: la instancia de VCS proporciona los bloques de creación de VMware fundamentales, como vSphere, vCenter Server, NSX-V y opciones de almacenamiento, incluido el almacenamiento de vSAN o IBM Cloud Endurance, necesario para desplegar automáticamente una solución de VMware Software Defined Data Center (SDDC). El clúster VMware es el destino de las máquinas virtuales migradas, así como de algunas de las aplicaciones modernizadas en los contenedores alojados en ICP. Los componentes principales de VCS son los siguientes:
    - **NSX-V**: NSX-V ofrece la capa de virtualización de red en VCS que proporciona una superposición de red para las VM de Acme Skateboards. NSX-V habilita BYOIP y aísla las redes de carga de trabajo de las redes de IBM Cloud. NSX-V está programado por HCX para crear las redes que Acme Skateboards extenderá desde el entorno local.

    - **NSX-T**: NSX-T proporciona un conjunto común de herramientas para la gestión de la red y de la seguridad tanto de contenedores como de máquinas virtuales. NSX-T es totalmente compatible con la interfaz de red de contenedor (CNI) de Kubernetes y se integra con la CNI para proporcionar redes de contenedores. NSX-T proporciona la red de superposición que utilizan las aplicaciones modernizadas y sustituye a Calico, que utilizan de forma nativa ICP e IKS.

- **IBM Cloud Private**: ICP es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas. ICP es un entorno integrado que incluye el orquestador de contenedores Kubernetes, un repositorio de imágenes privadas, una consola de gestión, infraestructuras de supervisión y una interfaz gráfica de usuario, que proporciona una ubicación centralizada desde la que Acme Skateboards puede desplegar, gestionar, supervisar y escalar aplicaciones. La instancia de VCS aloja los componentes de ICP, los nodos maestros, los nodos trabajadores, etc., que ejecutan como máquinas virtuales. ICP contiene:
    - **IBM Cloud Automation Manager**: CAM es una plataforma de código como infraestructura (IaC) preparada para la empresa que proporciona un único panel para suministrar cargas de trabajo de VM, locales o en VCS, junto con cargas de trabajo Kubernetes, en ICP o IKS, simplemente utilizando plantillas. CAM es una aplicación Docker que se ejecuta sobre ICP y que está estrechamente integrada para la autorización, el control de acceso basado en roles (RBAC) y otras funciones.
    - Las aplicaciones contenerizadas de Acme Skateboards que desean desplegar en este entorno.

- **Servicio IBM Kubernetes**: IKS permite a Acme Skateboards desplegar sus aplicaciones modernizadas en contenedores Docker que se ejecutan en clústeres de Kubernetes. IBM gestiona por completo los nodos maestros, mientras que los nodos trabajadores de la agrupación de nodos trabajadores se despliegan en la misma cuenta de IBM Cloud que su instancia de VCS. Los nodos trabajadores pueden ser: nativos, públicos o instancias de servidor virtual dedicado. Calico se instala y se configura automáticamente en IKS. Calico proporciona conectividad de red segura para contenedores y se configura en IKS para utilizar la encapsulación IP en IP para los paquetes que viajan a través de subredes y para utilizar NAT para las conexiones salientes de los contenedores.

- **Direct Link**: IBM Cloud Direct Link utiliza el proveedor de WAN de Acme Skateboard para conectar su centro de datos a IBM Cloud a fin de ofrecer una conexión de red fiable, segura y de baja latencia. Esta conexión proporciona:
    - Acceso a las aplicaciones alojadas en la nube desde los usuarios de la empresa.
    - Tráfico de VM interno entre las máquinas virtuales locales y las de la nube.
    - Tráfico entre sistemas antiguos del centro de datos local y las VM en la nube.

## Principales ventajas para Acme Skateboards

VMware vCenter Server on IBM Cloud (VCS) proporciona los bloques de creación fundamentales, que incluyen VMware vSphere, vCenter Server, NSX y las opciones de almacenamiento compartido que incluyen vSAN, necesarios para diseñar de forma flexible la solución de VMware Software Defined Data Center (SDDC) que mejor se adapte a las cargas de trabajo del cliente.

En resumen, las ofertas de IBM Cloud for VMware:

* Aceleran la entrega de proyectos de TI a desarrolladores y líneas de negocio, reduciendo el tiempo necesario para la adquisición, la arquitectura, la implementación y el despliegue de recursos de semanas, o incluso meses, a horas.
* Mejoran la seguridad con servidores nativos dedicados en una nube privada alojada, incluido el despliegue de puntos finales privados en servicios de IBM Cloud, que incluyen IKS y KMIP.
* Permiten llevar a cabo una gestión y gobierno coherentes de la nube híbrida desplegada, proporcionando acceso administrativo completo a la gestión de virtualización, conservando así las herramientas de VMware existentes, los scripts y las inversiones en formación.
* Aprovechan la experiencia de VMware a escala global con IBM Professional y Servicios gestionados que abarcan más de 30 centros de datos de IBM Cloud en todo el mundo.

Los clientes que realicen la transición hacia plataformas de aplicaciones nativas en la nube, como ICP e IKS, se centran en la velocidad y en la innovación y no siempre tienen en mente la seguridad y la red. El hecho de esperar a que los equipos de red o de seguridad suministren servicios como equilibradores de carga, cortafuegos, conmutadores y direccionadores degrada el tiempo de respuesta de las aplicaciones. Esta arquitectura de referencia muestra cómo VCS, ICP e IKS guían a Acme Skateboards en su proceso de modernización de aplicaciones.

## Enlaces relacionados

* [Visión general de VCS con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
