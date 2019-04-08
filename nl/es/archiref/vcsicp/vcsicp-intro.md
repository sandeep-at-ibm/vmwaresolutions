---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Introducción a VMware vCenter Server on IBM Cloud y a IBM Cloud Private
{: #vcsicp-intro}

En este documento se proporciona una vista del proceso de modernización de aplicaciones a {{site.data.keyword.cloud}}, que se centra en los componentes de gestión de la nube para permitir que se utilice un entorno multinube integrado para la modernización de las aplicaciones:

- **vCenter Server on {{site.data.keyword.cloud_notm}}**: vCenter Server constituye una oferta de {{site.data.keyword.vmwaresolutions_short}} y es una plataforma basada en VMware que se suministra automáticamente en {{site.data.keyword.cloud_notm}}.
- **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas, que se despliegan en plataformas de infraestructura virtualizada como VMware.
- **{{site.data.keyword.containerlong_notm}}**: {{site.data.keyword.containerlong_notm}} es un servicio gestionado en {{site.data.keyword.cloud_notm}} que utiliza Kubernetes como motor de coordinación para automatizar el despliegue, el escalado y las operaciones de los contenedores de aplicaciones en un clúster de un solo arrendatario
- **IBM Multi-Cluster Cloud Manager**: MCM proporciona visibilidad de usuario, gestión centrada en aplicaciones (política, despliegues, estado, operaciones) y conformidad basada en políticas entre nubes y clústeres. Con MCM, tiene el control sobre los clústeres de Kubernetes.
- **{{site.data.keyword.cloud_notm}} Automation Manager**: CAM es una plataforma de gestión de autoservicio multinube que se ejecuta en {{site.data.keyword.icpfull_notm}} que permite a los desarrolladores y a los administradores satisfacer las necesidades de la empresa.

## Modernización de aplicaciones en IBM Cloud
{: #vcsicp-intro-app-mod}

Modernización de aplicaciones es un término que describe el proceso de transición de las aplicaciones existentes para que utilicen los nuevos enfoques de la nube. Actualmente los clientes buscan enfoques innovadores y eficientes que les ayuden a realizar esta transición en función de la complejidad empresarial y de las aplicaciones.

Las presiones de la industria exigen un plazo más rápido de salida de productos al mercado. El entorno existente no solo incluye aplicaciones, sino también datos, procesos, lógica empresarial e interfaces de usuario, y todos se deben adaptar para mantenerse al día con las nuevas necesidades de la empresa.

Entre las ventajas de la modernización de aplicaciones se incluyen las siguientes:

- Mejora de la productividad del desarrollador.
- Mayor eficiencia operativa.
- Reducción del coste de crear nuevas prestaciones.
- Capacidad ampliada que se ofrece en un breve periodo de tiempo.

IBM comprende que el 70% de la adopción de la nube privada está impulsada por la necesidad de modernizar los entornos de aplicaciones. Sin embargo, la mayoría de las organizaciones están abordando la modernización de las aplicaciones con un enfoque por etapas, lo que requiere un entorno híbrido y multinube, en el que:

- Las aplicaciones antiguas complejas y monolíticas que se suelen ejecutar en sistemas principales o sistemas UNIX permanecen como aplicaciones locales.
- Los entornos x86 utilizados para sistemas de registro (SoR), o las aplicaciones sensibles a la seguridad o las cargas de trabajo reguladas, se colocan en una infraestructura virtualizada o en una nube privada.
- Las aplicaciones como SAP o de cálculo de alto rendimiento consumen recursos nativos.
- Las cargas de trabajo sensibles a la seguridad y algunas cargas de trabajo reguladas, que se pueden trasladar a la nube pública, se están moviendo a entornos dedicados.
- Los sistemas colaborativos (SoE), como web, móvil, IoT, IA o vídeo, se están trasladando a nubes públicas.

Por ejemplo, un patrón común consiste en desplegar las aplicaciones SOE frontales como contenedores con bases de datos y middleware antiguo que se despliegan en máquinas virtuales en una nube privada.

Debido a que su infraestructura de TI y sus necesidades empresariales son únicas, necesita un enfoque de modernización que ayude a acelerar la obtención de valor empresarial, reduzca los riesgos y aproveche las inversiones realizadas. IBM proporciona un enfoque de este tipo, que se puede personalizar para satisfacer sus necesidades empresariales y tecnológicas exclusivas relacionadas con la modernización de aplicaciones.

Este documento es uno de los cinco documentos que proporcionan distintas vistas sobre las tecnologías utilizadas en el proceso de modernización de aplicaciones a {{site.data.keyword.cloud_notm}}:

* _vCenter Server e {{site.data.keyword.icpfull_notm}}_: la guía actual, que constituye una arquitectura de referencia para desplegar las siguientes plataformas:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**: es una oferta de {{site.data.keyword.vmwaresolutions_short}} y constituye una plataforma basada en VMware que se suministra automáticamente en {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.icpfull_notm}}**: una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas. {{site.data.keyword.icpfull_notm}} es un entorno integrado que incluye el coordinador de contenedores Kubernetes, un repositorio de imágenes privadas, una consola de gestión, infraestructuras de supervisión y una interfaz gráfica de usuario, que proporciona una ubicación centralizada desde la que puede desplegar, gestionar, supervisar y escalar aplicaciones.
  - **{{site.data.keyword.cloud_notm}} Automation Manager**: una plataforma de infraestructura como código (IaC) preparada para la empresa que proporciona un único panel para suministrar cargas de trabajo basadas en VM junto con cargas de trabajo basadas en Kubernetes utilizando plantillas que se almacenan en un repositorio y de las que se crean versiones.
* [vCenter Server e {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro): una arquitectura de referencia para desplegar las siguientes plataformas:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**: es una oferta de {{site.data.keyword.vmwaresolutions_short}} y constituye una plataforma basada en VMware que se suministra automáticamente en {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.containerlong_notm}}**: servicio gestionado en {{site.data.keyword.cloud_notm}} que utiliza Kubernetes como motor de coordinación para automatizar el despliegue, el escalado y las operaciones de los contenedores de aplicaciones en un clúster de un solo arrendatario.
* [Redes de vCenter Server](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro): esta guía se centra en las tecnologías de red que se utilizan en vCenter Server, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}, como NSX-V, NSX-T y Calico.
* [VMware y Skate Advisor Concept Car](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro): esta arquitectura de referencia es un "concept car" (prototipo), es decir, un mecanismo para resaltar y mostrar tecnologías que solucionan problemas del mundo real. El objetivo era demostrar una interacción entre Watson AI y Machine Learning con un ejemplo real. A través de la cultura del skateboarding, demostramos de forma global los servicios de la nube de una forma única. La implementación del “concept car” constituye una extensión de la aplicación de Acme Skateboard llamada Skate Advisor. Skate Advisor es una herramienta que permite a los usuarios tener conversaciones sobre skateboarding con un motor controlado por Watson.
* [VMware: el proceso de modernización de Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney): nuestro caso de uso de referencia describe una aplicación de WebSphere Application Server clásica que se moderniza con {{site.data.keyword.icpfull_notm}}, contenido de IBM Middleware, {{site.data.keyword.containerlong_notm}} y vCenter Server. Todos estamos en un proceso de transición a la nube, y cada uno de nosotros está en un punto diferente del proceso. Siguiendo los pasos indicados por la arquitecta de la aplicación, Jane, y por el arquitecto de la infraestructura de nube, Todd, modernizamos una app existente denominada Stock Trader. Muestra ejemplos que pueden ayudar en cada paso del proceso y el valor que supone para la empresa, independientemente del tamaño de cada paso. Nos centramos en cuatro temas: aplicaciones, DevOps, integración y gestión. Cada tema trabaja en combinación con los demás para ayudarle a alcanzar sus objetivos. El hecho de modernizar un tema sin los otros podría dar lugar a problemas.

## Enlaces relacionados
{: #vcsicp-intro-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
