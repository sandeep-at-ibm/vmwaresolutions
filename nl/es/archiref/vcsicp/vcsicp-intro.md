---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Introducción a vCenter Server e IBM Cloud Private

En este documento se proporciona una vista del proceso de modernización de aplicaciones a IBM Cloud, que se centra en los componentes de gestión de la nube para permitir que se aproveche un entorno multinube integrado para la modernización de las aplicaciones:

- **VMware vCenter Server on IBM Cloud**: VCS es una oferta de IBM Cloud for VMware Solutions y constituye una plataforma basada en VMware que se suministra automáticamente en IBM Cloud.
- **IBM Cloud Private**: ICP es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas, diseñadas para que se desplieguen en plataformas de infraestructura virtualizada, como VMware.
- **Servicios IBM Kubernetes**: IKS es un servicio gestionado en IBM Cloud que aprovecha Kubernetes como motor de orquestación para automatizar el despliegue, el escalado y el funcionamiento de los contenedores de aplicaciones de un clúster de un solo arrendatario
- **IBM Multi-Cluster Cloud Manager**: MCM proporciona visibilidad de usuario, gestión centrada en aplicaciones (política, despliegues, estado, operaciones) y conformidad basada en políticas entre nubes y clústeres. Con MCM, tiene el control sobre los clústeres de Kubernetes.
- **IBM Cloud Automation Manager**: CAM es una plataforma de gestión de autoservicio multinube que se ejecuta en ICP que permite a los desarrolladores y a los administradores satisfacer las necesidades de la empresa.

## Modernización de aplicaciones en IBM Cloud

Modernización de aplicaciones es un término que describe el proceso de transición de las aplicaciones existentes para aprovechar los nuevos enfoques de la nube. Actualmente los clientes buscan enfoques innovadores y eficientes que les ayuden a realizar esta transición en función de la complejidad empresarial y de las aplicaciones.

Las presiones de la industria exigen un plazo más rápido de salida de productos al mercado. El entorno existente no solo incluye aplicaciones, sino también datos, procesos, lógica empresarial e interfaces de usuario, y todos se deben adaptar para mantenerse al día con las nuevas necesidades de la empresa.

Entre las ventajas de la modernización de aplicaciones se incluyen las siguientes:
- Mejora de la productividad del desarrollador.
- Mayor eficiencia operativa.
- Reducción del coste de crear nuevas prestaciones.
- Capacidad ampliada que se ofrece en un breve periodo de tiempo.

IBM comprende que el 70% de la adopción de la nube privada está impulsada por la necesidad de modernizar los entornos de aplicaciones; sin embargo, la mayoría de las organizaciones están abordando la modernización de las aplicaciones con un enfoque por etapas, lo que requiere un entorno híbrido y multinube, en el que:
- Las aplicaciones antiguas complejas y monolíticas que se suelen ejecutar en sistemas principales o sistemas UNIX permanecen como aplicaciones locales.
- Los entornos x86 utilizados para sistemas de registro (SoR), o las aplicaciones sensibles a la seguridad o las cargas de trabajo reguladas, se colocan en una infraestructura virtualizada o en una nube privada.
- Las aplicaciones como SAP o de cálculo de alto rendimiento consumen recursos nativos.
- Las cargas de trabajo sensibles a la seguridad y algunas cargas de trabajo reguladas, que se pueden trasladar a la nube pública, se están moviendo a entornos dedicados.
- Los sistemas colaborativos (SoE), como web, móvil, IoT, IA o vídeo, se están trasladando a nubes públicas.

Por ejemplo, un patrón común consiste en desplegar las aplicaciones SOE frontales como contenedores con bases de datos y middleware antiguo desplegados en máquinas virtuales en una nube privada.

Debido a que su infraestructura de TI y sus necesidades empresariales son únicas, necesita un enfoque de modernización que ayude a acelerar la obtención de valor empresarial, reduzca los riesgos y aproveche las inversiones realizadas. IBM proporciona un enfoque de este tipo, que se puede personalizar para satisfacer sus necesidades empresariales y tecnológicas exclusivas relacionadas con la modernización de aplicaciones.

Este documento es uno de los cinco documentos que proporcionan distintas vistas sobre las tecnologías utilizadas en el proceso de modernización de aplicaciones a IBM Cloud:

* _vCenter Server e IBM Cloud Private_: la guía actual, que constituye una arquitectura de referencia para desplegar las siguientes plataformas:
  - **VMware vCenter Server on IBM Cloud**: una oferta de IBM Cloud for VMware Solutions que constituye una plataforma basada en VMware que se suministra automáticamente en IBM Cloud.
  - **IBM Cloud Private**: una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas. Se trata de un entorno integrado que incluye el orquestador de contenedores Kubernetes, un repositorio de imágenes privadas, una consola de gestión, infraestructuras de supervisión y una interfaz gráfica de usuario, que proporciona una ubicación centralizada desde la que puede desplegar, gestionar, supervisar y escalar aplicaciones.
  - **IBM Cloud Automation Manager**: una plataforma de infraestructura como código (IaC) preparada para la empresa que proporciona un único panel para suministrar cargas de trabajo basadas en VM junto con cargas de trabajo basadas en Kubernetes utilizando simplemente plantillas que se almacenan en un repositorio y de las que se crean versiones.
* [vCenter Server y servicio IBM Kubernetes](../vcsiks/vcsiks-intro.html): esta guía es una arquitectura de referencia para desplegar las siguientes plataformas:
  - **VMware vCenter Server on IBM Cloud**: una oferta de IBM Cloud for VMware Solutions que constituye una plataforma basada en VMware que se suministra automáticamente en IBM Cloud.
  - **Servicio IBM Kubernetes**: servicio gestionado en IBM Cloud que aprovecha Kubernetes como motor de orquestación para automatizar el despliegue, el escalado y el funcionamiento de los contenedores de aplicaciones de un clúster de un solo arrendatario.
* [Redes de vCenter Server](../vcsnsxt/vcsnsxt-intro.html): esta guía se centra en las tecnologías de red utilizadas en VCS, ICP e IKS, como NSX-V, NSX-T y Calico.
* [VMware y Skate Advisor Concept Car](../vcscar/vcscar-intro.html): esta arquitectura de referencia es un "concept car" (prototipo), es decir, un mecanismo para resaltar y mostrar tecnologías que solucionan problemas del mundo real. El objetivo era demostrar una interacción entre Watson AI y Machine Learning con un ejemplo real. Mediante la cultura del skateboarding demostramos de forma global los servicios de la nube de una forma única. La implementación del “concept car” constituye una extensión de la aplicación de Acme Skateboard llamada Skate Advisor. Skate Advisor es una herramienta que permite a los usuarios tener conversaciones sobre skateboarding con un motor controlado por Watson.
* [VMware: el proceso de modernización de Stock Trader](../vcscontent/vcscontent-modjourney.html): nuestro caso de uso de referencia describe una aplicación de WebSphere Application Server clásica que se moderniza con IBM Cloud Private, contenido de IBM Middleware, el servicio Kubernetes de IBM Cloud y vCenter Server on IBM Cloud. Todos estamos en un proceso de transición a la nube, y cada uno de nosotros está en un punto diferente del proceso. Siguiendo los pasos incrementales indicados por la arquitecta de la aplicación, Jane, y el por el arquitecto de la infraestructura de nube, Todd, modernizamos una app existente denominada Stock Trader. Muestra ejemplos que pueden ayudar en cada paso del proceso y el valor que supone para la empresa, independientemente del tamaño de cada paso. Nos centramos en cuatro temas: aplicaciones, DevOps, integración y gestión. Cada uno de ellos trabaja combinación con los demás para ayudarle a alcanzar sus objetivos y, de hecho, a modernizar cada uno sin que los otros tengan problemas.

### Enlaces relacionados

* [Visión general de VCS con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
