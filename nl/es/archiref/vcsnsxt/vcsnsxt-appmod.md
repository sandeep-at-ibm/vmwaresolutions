---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Visión general de la modernización de aplicaciones

En el diagrama siguiente se muestra la arquitectura de referencia de la modernización de aplicaciones que se desplegará en Acme Skateboards y que se describe en profundidad en esta serie de documentos.

Figura 1. Visión general de la arquitectura
![Diagrama de visión general de la arquitectura](vcsnsxt-aod.svg)

Esta arquitectura híbrida permite a Acme Skateboards:
- Migrar máquinas virtuales (VM) VMware desde el entorno local a {{site.data.keyword.cloud}} con muy poco o ningún tiempo de inactividad y sin tener que reconfigurar las aplicaciones.
-	Iniciar el proceso de modernización de aplicaciones, permitiéndoles centrarse en contenerizar las interfaces web más simples y el middleware al tiempo que permite que bases de datos más complejas permanezcan como máquinas virtuales.
-	Aprovechar Cloud Automation Manager (CAM) para disponer de una infraestructura como código (IaC) para componer y coordinar servicios en los que intervienen tanto de máquinas virtuales como contenedores para integrarlos en sus cadenas de herramientas de DevOps y en su solución ITSM.

En lo que respecta a la arquitectura de red, la arquitectura de referencia comprende los siguientes componentes principales:
- **Virtualización local**: es un clúster VMware que actualmente aloja las VM de Acme Skateboards. Son estas máquinas virtuales las que actualmente alojan las aplicaciones que se modernizarán. Este clúster debe cumplir con los requisitos previos descritos en la documentación de la arquitectura de la [solución VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) para poder ejecutar HCX. HCX amplía las redes locales a {{site.data.keyword.cloud_notm}}, permitiendo a los clientes migrar las VM a la instancia de VCS que se ejecuta en {{site.data.keyword.cloud_notm}} y viceversa si es necesario.
- **VMware vCenter Server on IBM Cloud**: VCS proporciona los componentes fundamentales de VMware: vSphere, vCenter Server, NSX-V y opciones de almacenamiento que incluyen vSAN o almacenamiento {{site.data.keyword.cloud_notm}} Endurance, necesarios para desplegar automáticamente una solución VMware Software Defined Data Center (SDDC). Este clúster VMware es el destino de las máquinas virtuales migradas, así como de algunas de las aplicaciones modernizadas en los contenedores alojados en ICP.

  Los componentes clave de la arquitectura son:
 - **NSX-V**: NSX-V ofrece la capa de virtualización de red en VCS que proporciona una superposición de red para las VM de Acme Skateboards. NSX-V habilita BYOIP y aísla las redes de carga de trabajo de las redes de {{site.data.keyword.cloud_notm}}. NSX-V está programado por HCX para crear las redes que Acme Skateboards extenderá desde el entorno local.
 - **IBM Cloud Private**: ICP es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas. Es un entorno integrado que incluye el coordinador de contenedores Kubernetes, un repositorio de imágenes privadas, una consola de gestión, infraestructuras de supervisión y una interfaz gráfica de usuario, que proporciona una ubicación centralizada desde la que Acme Skateboards puede desplegar, gestionar, supervisar y escalar aplicaciones. La instancia de VCS aloja los componentes de ICP, los nodos maestros, los nodos trabajadores, etc., que ejecuta como máquinas virtuales.
  -	**IBM Cloud Automation Manager**: CAM es una plataforma de infraestructura como código (IaC) preparada para la empresa que ofrece un único panel para suministrar cargas de trabajo basadas en máquina virtual junto con cargas de trabajo basadas en Kubernetes simplemente utilizando plantillas. CAM es una aplicación Docker que se ejecuta sobre ICP y que está estrechamente integrada para la autorización, RBAC y otras funciones.
  - **Servicio IBM Kubernetes**: IKS permite a Acme Skateboards desplegar sus aplicaciones modernizadas en contenedores Docker que se ejecutan en clústeres de Kubernetes. IBM gestiona por completo los nodos maestros, mientras que los nodos trabajadores de la agrupación de nodos trabajadores se despliegan en la misma cuenta de {{site.data.keyword.cloud_notm}} que su instancia de VCS. Los nodos trabajadores pueden ser nativos, públicos o instancias de servidor virtual dedicado. Calico se instala y se configura automáticamente en IKS. Calico proporciona conectividad de red segura para contenedores y se configura en IKS para utilizar la encapsulación IP en IP para encapsular los paquetes que viajan a través de subredes y utiliza NAT para las conexiones salientes de los contenedores.
  - **Direct Link**: {{site.data.keyword.cloud_notm}} Direct Link utiliza el proveedor de WAN de Acme Skateboard para conectar su centro de datos a {{site.data.keyword.cloud_notm}} a fin de ofrecer una conexión de red fiable, segura y de baja latencia. Esta conexión proporciona:
      - Acceso a las aplicaciones alojadas en la nube desde los usuarios de la empresa.
      - Tráfico de VM interno entre las máquinas virtuales locales y las de la nube.
      - Tráfico entre sistemas antiguos del centro de datos local y las VM en la nube.

## Principales ventajas para Acme Skateboards

-	Aceleración en la entrega de proyectos de TI a desarrolladores y líneas de negocio, reduciendo el tiempo necesario para la adquisición, la arquitectura, la implementación y el despliegue de recursos de semanas, o incluso meses, a horas. El hecho de esperar a que los equipos de red o de seguridad suministren servicios como equilibradores de carga, cortafuegos, conmutadores y direccionadores degrada el tiempo de respuesta de las aplicaciones.
-	Mejora en la seguridad con servidores nativos dedicados en una nube privada alojada, incluido el despliegue de puntos finales privados en servicios de {{site.data.keyword.cloud_notm}}, como IKS y KMIP.
-	Gestión y gobierno coherentes de la nube híbrida desplegada, proporcionando acceso administrativo completo a la gestión de virtualización, conservando así las herramientas de VMware existentes, los scripts y las inversiones en formación.
-	Experiencia de VMware a escala global con IBM Professional y Servicios gestionados que abarcan más de 30 {{site.data.keyword.CloudDataCents_notm}} en todo el mundo.

Los clientes que realicen la transición hacia plataformas de aplicaciones nativas en la nube, como ICP e IKS, se centran en la velocidad y en la innovación y no siempre tienen en mente la seguridad y la red. Esta arquitectura de referencia muestra cómo VCS, ICP e IKS guían a Acme Skateboards en su proceso de modernización de aplicaciones.

## Enlaces relacionados

* [Visión general de VCS con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
