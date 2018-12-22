---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# Introducción a VMware y Skate Advisor Concept Car

La siguiente arquitectura de referencia es un “concept car”, es decir, un mecanismo para destacar y mostrar tecnologías que solucionan problemas del mundo real. El “concept car” no representa de ningún modo un servicio disponible actualmente.

La arquitectura de referencia también proporciona la información siguiente:

-   Proporciona lenguaje común para los distintos depositarios.
-   Proporciona coherencia en la implementación de la tecnología para resolver problemas.
-   Da soporte a la validación de soluciones en una arquitectura de referencia probada.
-   Facilita la conformidad con estándares, especificaciones y patrones comunes.

## Acerca de ACME Skate Advisor

El objetivo era demostrar una interacción entre la inteligencia artificial de Watson y machine learning con un ejemplo real y a partir de aquí explorar en profundidad la cultura del skateboarding. Mostramos los servicios disponibles y la infraestructura de nube a través de su capacidad técnica y los avances en esta área. La implementación del “concept car” constituye una extensión de la aplicación de Acme Skateboard de demostración llamada Skate Advisor. Skate Advisor es una herramienta que permite a los usuarios tener conversaciones sobre skateboarding con un motor controlado por Watson. Estos son algunos ejemplos de conversaciones:

-   “Watson, muéstrame combinaciones del truco Casper”
-   “Watson, muéstrame ubicaciones comunes donde realizar un truco”
-   “Watson, muéstrame un vídeo del truco Casper”

Acme Skate Advisor aprovecha Watson Discovery Service para ingerir artículos, vídeos,
blogs y otro contenido de Internet con el fin de crear una base de datos de trucos, que la aplicación puede consultar.

La aplicación Skate Advisor también se implementa en la plataforma de modernización de aplicaciones, que proporciona servicios basados en contenedor mediante {{site.data.keyword.cloud}} Private (ICP) alojado en la plataforma {{site.data.keyword.cloud_notm}} for VMware Services.

La aplicación Acme Skate Advisor aprovecha tanto la plataforma Watson como la plataforma de modernización de aplicaciones.

## Casos prácticos

### Demostración de la modernización de aplicaciones

Se muestra una aplicación que se ha desplegado en la plataforma de modernización de aplicaciones. La plataforma incluye los componentes ICP, CAM y NSX desplegados en la oferta {{site.data.keyword.cloud_notm}} para VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

### Reconocimiento de voz de Watson con Watson Assistant

Acme Skate Advisor se comunica con los usuarios a través de un servicio de conversión de voz en texto y de texto en voz que se proporciona con la plataforma Watson.

### Uso y entrenamiento de Watson Discovery Service

Acme Skate Advisor utiliza Watson Discovery Services para realizar el seguimiento de una base de datos de trucos para la que se aplica un lenguaje de clasificación y los trucos descubiertos en los servicios en línea.

### Uso de los servicios de Watson

Se utilizan los siguientes servicios de Watson para crear Acme Skate
Advisor:
-   Watson Text to Speech.
-   Watson Speech to Text.
-   Watson Advisor.
-   Watson Discovery Service.
-   Watson Knowledge Studio.

## Modernización de aplicaciones en IBM Cloud

Modernización de aplicaciones es un término que describe el proceso de transición de las aplicaciones existentes para que utilicen los nuevos enfoques de desarrollo y suministro de la nube. Actualmente los clientes buscan enfoques innovadores y eficientes que les ayuden a realizar esta transición en función de la complejidad empresarial y de las aplicaciones.

Las presiones de la industria exigen un plazo más rápido de salida de productos al mercado. El entorno existente no solo incluye aplicaciones, sino también datos, procesos, lógica empresarial e interfaces de usuario, y todos se deben adaptar para mantenerse al día con las nuevas necesidades de la empresa.

En esta lista se describen las ventajas de la modernización de aplicaciones:

- Mejora la productividad del desarrollador
- Aumenta la eficiencia operativa
- Reduce el coste de crear nuevas características
- Amplía la capacidad que se ofrece en un breve periodo de tiempo

IBM comprende que el 70 por ciento de la adopción de la nube privada está impulsada por la necesidad de modernizar los entornos de aplicaciones. Sin embargo, la mayoría de las organizaciones están abordando la modernización de las aplicaciones con un enfoque por etapas, que requiere un entorno híbrido y multinube, en el que:

- Las aplicaciones antiguas complejas y monolíticas que se suelen ejecutar en sistemas principales o sistemas UNIX permanecen como aplicaciones locales.
- Los entornos x86 utilizados para sistemas de registro (SoR), o las aplicaciones sensibles a la seguridad o las cargas de trabajo reguladas, se colocan en una infraestructura virtualizada o en una nube privada.
- Las aplicaciones como SAP o de cálculo de alto rendimiento utilizan recursos nativos.
- Las cargas de trabajo sensibles a la seguridad y algunas cargas de trabajo reguladas, que se pueden trasladar a la nube pública, se están moviendo a entornos dedicados.
- Los sistemas colaborativos (SoE), como web, móvil, IoT, IA o vídeo, se están trasladando a nubes públicas.

Por ejemplo, un patrón común consiste en desplegar las aplicaciones SoE frontales como contenedores con bases de datos y middleware antiguo que se despliegan en máquinas virtuales en una nube privada.

Puesto que la infraestructura de TI y las necesidades empresariales son exclusivas, un enfoque de modernización debe proporcionar las siguientes prioridades:

* Acelerar el valor empresarial
* Minimizar el tiempo de entrega
* Reducir los riesgos
* Aprovechar las inversiones existentes.

IBM proporciona el enfoque que necesita para modernizar las aplicaciones, que se puede personalizar para satisfacer sus necesidades particulares empresariales y de tecnología.

En los siguientes documentos se proporcionan distintas vistas sobre las tecnologías utilizadas en el proceso de modernización de aplicaciones a {{site.data.keyword.cloud_notm}}:

* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html). una arquitectura de referencia para desplegar las siguientes plataformas.
   - ** VMware vCenter Server on IBM Cloud**: vCenter Server es una oferta de {{site.data.keyword.vmwaresolutions_short}} que es una plataforma basada en VMware que se suministra automáticamente en {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Private**: ICP es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas. ICP es un entorno integrado que incluye el coordinador de contenedores Kubernetes,
un repositorio de imágenes privadas, una consola de gestión e infraestructuras de supervisión. La interfaz de usuario proporciona una ubicación centralizada desde la que puede desplegar, gestionar, supervisar y escalar las aplicaciones.
   - **IBM Cloud Automation Manager**: CAM es una plataforma de infraestructura como código preparada para la empresa que proporciona un único panel para suministrar cargas de trabajo basadas en VM junto con cargas de trabajo basadas en Kubernetes utilizando plantillas que se almacenan en un repositorio y de las que se crean versiones.
* [vCenter Server y servicio IBM Kubernetes](../vcsiks/vcsiks-intro.html). una arquitectura de referencia para desplegar las siguientes plataformas.
   - ** VMware vCenter Server on IBM Cloud**: vCenter Server es una oferta de {{site.data.keyword.vmwaresolutions_short}} que es una plataforma basada en VMware que se suministra automáticamente en {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Kubernetes Service**: IKS un servicio gestionado en {{site.data.keyword.cloud_notm}} que utiliza Kubernetes como motor de coordinación para automatizar el despliegue, el escalado y las operaciones de los contenedores de aplicaciones en un clúster de un solo arrendatario.
* [Red de vCenter Server](../vcsnsxt/vcsnsxt-intro.html): se centra en las tecnologías de red utilizadas para la integración entre vCenter, ICP e IKS, como NSX-V y Calico, junto con una presentación técnica de NSX-T.
* _Guía de VMware y Skate Advisor Concept Car_: una arquitectura de referencia que constituye un “concept car”, es decir, un mecanismo para destacar y mostrar tecnologías que solucionan problemas del mundo real. El objetivo era demostrar una interacción entre Watson AI y Machine Learning con un ejemplo real. A través de la cultura del skateboarding, demostramos de forma global los servicios de la nube de una forma única. La implementación del “concept car” constituye una extensión de la aplicación de Acme Skateboard llamada Skate Advisor. Skate Advisor es una herramienta que permite a los usuarios tener conversaciones sobre skateboarding con un motor controlado por Watson.
* [VMware: el proceso de modernización de Stock Trader](../vcscontent/vcscontent-modjourney.html): un caso de uso de referencia describe una aplicación de WebSphere Application Server clásica que se moderniza con {{site.data.keyword.cloud_notm}} Private, contenido de IBM Middleware, el servicio Kubernetes de {{site.data.keyword.cloud_notm}} y vCenter Server on {{site.data.keyword.cloud_notm}}. Todos estamos en un proceso de transición a la nube, y cada uno de nosotros está en un punto diferente del proceso. Siguiendo los pasos indicados por la arquitecta de la aplicación, Jane, y por el arquitecto de la infraestructura de nube, Todd, modernizamos una aplicación existente denominada Stock Trader. Revise los ejemplos que le pueden ayudar en cada paso del proceso y el valor que supone para la empresa, independientemente del tamaño de cada paso. Nos centramos en cuatro temas: aplicaciones, DevOps, integración y gestión. Cada uno de ellos trabaja combinación con los demás para ayudarle a alcanzar sus objetivos y, de hecho, a modernizar cada uno sin que los otros tengan problemas.

### Enlaces relacionados

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
