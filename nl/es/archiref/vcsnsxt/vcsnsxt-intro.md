---

copyright:

  years:  2016, 2019

lastupdated: "2018-01-14"

---

# Introducción a la red de vCenter Server

En este documento se proporciona una introducción al proceso de modernización de aplicaciones a {{site.data.keyword.cloud}}, que se centra en los aspectos de la red de las siguientes plataformas para permitir que se utilice un entorno multinube integrado para la modernización de las aplicaciones:

- **VMware vCenter Server on IBM Cloud**: una oferta de {{site.data.keyword.vmwaresolutions_short}}, que es una plataforma basada en VMware que se suministra automáticamente en {{site.data.keyword.cloud_notm}}.
- **IBM Cloud Private**: una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas, que se despliegan en la plataforma de la infraestructura virtualizada, como vCenter Server o un entorno vSphere local.
- **{{site.data.keyword.containerlong_notm}}**: servicio gestionado en {{site.data.keyword.cloud_notm}} que utiliza Kubernetes como motor de coordinación para automatizar el despliegue, el escalado y las operaciones de los contenedores de aplicaciones en un clúster de un solo arrendatario.

Los principales retos a los que se enfrenta el proceso de modernización de aplicaciones son la migración, la red y la seguridad. vCenter Server, VMware Hybrid Cloud Extension (HCX), VMware NSX, {{site.data.keyword.containerlong_notm}} e {{site.data.keyword.icpfull_notm}} ayudan a resolver estos retos. En la siguiente arquitectura de red se describe el enfoque que utiliza Acme Skateboards como ejemplo para conectar componentes que se distribuyen entre entornos de nube y local.

La [presentación técnica NSX-T](vcsnsxt-techpreview.html) es una presentación que describe el uso de VMware NSX Transformers (NSX-T) en una futura arquitectura de referencia. NSX-T está diseñado para ofrecer entornos de aplicaciones y arquitecturas que tienen puntos finales y pilas de tecnologías heterogéneos. Además de vSphere, estos entornos pueden incluir otros hipervisores, KVM, contenedores y servidores nativos. NSX-T permite a los equipos de TI y de desarrollo elegir las tecnologías que mejor se adaptan a sus aplicaciones. NSX-T también está diseñado para la gestión, la operación y el consumo por parte de las organizaciones de desarrollo, además de los equipos de red.

## Modernización de aplicaciones en IBM Cloud

Modernización de aplicaciones es un término que describe el proceso de transición de las aplicaciones existentes para que utilicen los nuevos enfoques de desarrollo y suministro de la nube. Actualmente los clientes buscan enfoques innovadores y eficientes que les ayuden a realizar esta transición en función de la complejidad empresarial y de las aplicaciones.

Las presiones de la industria exigen un plazo más rápido de salida de productos al mercado. El entorno existente no solo incluye aplicaciones, sino también datos, procesos, lógica empresarial e interfaces de usuario, y todos se deben adaptar para mantenerse al día con las nuevas necesidades de la empresa.

Entre las ventajas de la modernización de aplicaciones se incluyen las siguientes:

- Mejora la productividad del desarrollador
- Aumenta la eficiencia operativa
- Reduce el coste de crear nuevas funciones
- Amplía la capacidad que se ofrece en un breve periodo de tiempo

IBM comprende que el 70% de la adopción de la nube privada está impulsada por la necesidad de modernizar los entornos de aplicaciones; sin embargo, la mayoría de las organizaciones están abordando la modernización de las aplicaciones con un enfoque por etapas, lo que requiere un entorno híbrido y multinube, en el que:

- Las aplicaciones antiguas complejas y monolíticas que se suelen ejecutar en sistemas principales o sistemas UNIX permanecen como aplicaciones locales.
- Los entornos x86 utilizados para sistemas de registro (SoR), o las aplicaciones sensibles a la seguridad o las cargas de trabajo reguladas, se colocan en una infraestructura virtualizada o en una nube privada.
- Las aplicaciones como SAP o de cálculo de alto rendimiento consumen recursos nativos.
- Las cargas de trabajo sensibles a la seguridad y algunas cargas de trabajo reguladas, que se pueden trasladar a la nube pública, se están moviendo a entornos dedicados.
- Los sistemas colaborativos (SoE), como web, móvil, IoT, IA o vídeo, se están trasladando a nubes públicas.

Por ejemplo, un patrón común consiste en desplegar las aplicaciones SoE frontales como contenedores con bases de datos y middleware antiguo que se despliegan en máquinas virtuales en una nube privada.

Debido a que su infraestructura de TI y sus necesidades empresariales son únicas, necesita un enfoque de modernización que acelere la obtención de valor empresarial, minimice el tiempo de distribución, reduzca los riesgos y aproveche las inversiones realizadas. IBM proporciona el enfoque que necesita para modernizar las aplicaciones, que se puede personalizar para satisfacer sus necesidades particulares empresariales y de tecnología.

En este documento se proporcionan distintas vistas sobre las tecnologías utilizadas en el proceso de modernización de aplicaciones a {{site.data.keyword.cloud_notm}}:

* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html): una arquitectura de referencia para desplegar las siguientes plataformas:
   - **VMware vCenter Server on IBM Cloud**: una oferta de {{site.data.keyword.vmwaresolutions_short}}, que es una plataforma basada en VMware que se suministra automáticamente en {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.icpfull_notm}}**: {{site.data.keyword.icpfull_notm}} es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas. Constituye un entorno integrado que incluye el coordinador de contenedores Kubernetes, un repositorio de imágenes privadas, una consola de gestión, infraestructuras de supervisión y una interfaz gráfica de usuario, que proporciona una ubicación centralizada desde la que puede desplegar, gestionar, supervisar y escalar aplicaciones.
   - **IBM Cloud Automation Manager**: CAM es una plataforma de infraestructura como código preparada para la empresa que proporciona un único panel para suministrar cargas de trabajo basadas en VM junto con cargas de trabajo basadas en Kubernetes utilizando plantillas que se almacenan en un repositorio y de las que se crean versiones.
* [vCenter Server y e {{site.data.keyword.containerlong_notm}}](../vcsiks/vcsiks-intro.html): una arquitectura de referencia para desplegar las siguientes plataformas:
   - **VMware vCenter Server on IBM Cloud**: una oferta de {{site.data.keyword.vmwaresolutions_short}}, que es una plataforma basada en VMware que se suministra automáticamente en {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.containerlong_notm}}**: servicio gestionado en {{site.data.keyword.cloud_notm}} que utiliza Kubernetes como motor de coordinación para automatizar el despliegue, el escalado y las operaciones de los contenedores de aplicaciones en un clúster de un solo arrendatario.
* _Red de vCenter Server_: la guía actual se centra en las tecnologías de red utilizadas para la integración entre vCenter, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}, como NSX-V y Calico, junto con una presentación técnica de NSX-T.
* [VMware y Skate Advisor Concept Car](../vcscar/vcscar-intro.html): esta arquitectura de referencia es un "concept car" (prototipo), es decir, un mecanismo para resaltar y mostrar tecnologías que solucionan problemas del mundo real. El objetivo era demostrar una interacción entre Watson AI y Machine Learning con un ejemplo real. A través de la cultura del skateboarding, demostramos de forma global los servicios de la nube de una forma única. La implementación del “concept car” constituye una extensión de la aplicación de Acme Skateboard llamada Skate Advisor. Skate Advisor es una herramienta que permite a los usuarios tener conversaciones sobre skateboarding con un motor controlado por Watson.
* [VMware: el proceso de modernización de Stock Trader](../vcscontent/vcscontent-modjourney.html): nuestro caso de uso de referencia describe una aplicación de WebSphere Application Server clásica que se moderniza con {{site.data.keyword.cloud_notm}} Private, contenido de IBM Middleware, {{site.data.keyword.containerlong_notm}} y vCenter Server on {{site.data.keyword.cloud_notm}}. Todos estamos en un proceso de transición a la nube, y cada uno de nosotros está en un punto diferente del proceso. Siguiendo los pasos indicados por la arquitecta de la aplicación, Jane, y por el arquitecto de la infraestructura de nube, Todd, modernizamos una aplicación existente denominada Stock Trader. Muestra ejemplos que pueden ayudar en cada paso del proceso y el valor que supone para la empresa, independientemente del tamaño de cada paso. Nos centramos en cuatro temas: aplicaciones, DevOps, integración y gestión. Cada tema trabaja en combinación con los demás para ayudarle a alcanzar sus objetivos. El hecho de modernizar un tema sin los otros podría dar lugar a problemas.

### Enlaces relacionados

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
