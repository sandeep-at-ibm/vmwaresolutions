---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Proceso de modernización
{: #vcscontent-modjourney}

Este es un caso de uso de referencia sobre cómo se moderniza una aplicación clásica de WebSphere Application Server mediante {{site.data.keyword.cloud}} Private, contenido de IBM Middleware, {{site.data.keyword.containerlong_notm}} y VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## La modernización es más que aplicaciones
{: #vcscontent-modjourney-modernization}

Todos estamos en un proceso de transición a la nube, y cada uno de nosotros está en un punto diferente del proceso. Este caso de uso se centra en cómo se moderniza una aplicación existente, Stock Trader, a través de pasos incrementales que el arquitecto de infraestructura de la aplicación, Jane, y el arquitecto de infraestructura de nube, Todd, han planificado. En este caso de uso se muestran ejemplos que pueden ayudar en cada paso del proceso y el valor que supone para la empresa, independientemente del tamaño de cada paso.

El proceso se centra principalmente en la modernización de la aplicación Stock Trader. Para modernizar por completo su negocio y transformarlo en un negocio nativo de la nube, se deben tener en cuenta temas relacionados con las aplicaciones, DevOps, la integración y la gestión. Cada tema trabaja en combinación con los demás para ayudarle a alcanzar sus objetivos. El hecho de modernizar un tema sin los otros podría dar lugar a problemas.

## Motivos para modernizar
{: #vcscontent-modjourney-reasons}

### Modernización de aplicaciones
{: #vcscontent-modjourney-app-mod}

El objetivo es conseguir aplicaciones nativas de la nube que se escalan y responden rápidamente a las demandas cambiantes.

* Es necesario modernizar las apps existentes y crear apps nativas de la nube para atraer la imaginación del cliente.
* Se necesitan apps que se puedan escalar, que sean accesibles en todo el mundo, que se ajusten a demandas, cambios y mejoras y que se puedan adaptar rápidamente.

### Modernización de DevOps
{: #vcscontent-modjourney-devops-mod}

Cuando se moderniza la aplicación, hay que modernizar la forma de distribuir dicha aplicación y el conducto de distribución entero para que la nueva cultura nativa de la nube que crean los desarrolladores se pueda escalar en cuanto a la forma en que se distribuye la app.

* Es necesario modernizar la cultura de desarrollo y de operaciones (y de seguridad) a la vez que se modernizan las aplicaciones.
* Se necesitan equipos de DevOps que se puedan escalar, que sean accesibles en todo el mundo, que se ajusten a demandas, cambios y mejoras y que se puedan adaptar rápidamente.

###  Modernización de la integración
{: #vcscontent-modjourney-integration-mod}

En este proceso de modernización, los equipos necesitan integrarse con los activos existentes, los nuevos servicios de nube, los datos y los nuevos conocimientos procedentes de los análisis que se realizan sobre dichos datos.

* Es necesario utilizar activos existentes en este proceso de forma que se puedan escalar, que sean accesibles en todo el mundo, que se ajusten a demandas, cambios y mejoras y que se puedan adaptar rápidamente.
* Es necesario optimizar con nuevos servicios de nube en cada paso de este proceso.
* Hay que integrar los datos y la información que se obtiene de aplicar análisis a los datos.

### Gestión
{: #vcscontent-modjourney-mgmt}

La modernización de las prácticas de gestión es otro proceso paralelo que hay que llevar a cabo mientras se modernizan las aplicaciones. Las herramientas, la cultura y los comportamientos principales en cuanto a la gestión y mantenimiento de una aplicación modernizada cambian sustancialmente.

* Necesita gestionar sus microservicios y el middleware contenerizado utilizando la coordinación, el registro y la supervisión integrados.
* Es necesario gestionar las plataformas híbridas multinube dispersas en ubicaciones de todo el globo de forma que se puedan escalar, que sean accesibles en todo el mundo, que se ajusten a demandas, cambios y mejoras y que se puedan adaptar rápidamente.
* Es necesario automatizar la forma de gestionar más de una nube y las aplicaciones y el middleware que se ejecutan en las mismas.

## Presentación de Todd y Jane
{: #vcscontent-modjourney-todd-jane}

En el proceso de modernización de Stock Trader, nos centraremos en dos personas: Todd y Jane. Todd es el director de operaciones de la empresa ACME y es el responsable de la infraestructura, la seguridad, los entornos de nube y las políticas que garantizan que las cargas de trabajo que se ejecutan en estos cumplen con diversas normativas.

Jane es la directora de desarrollo de la solución Stock Trader y es la responsable de modernizar Stock Trader, lo que significa trabajar con sus equipos de desarrollo para cambiar las herramientas de desarrollo, la cultura y las plataformas para que la solución Stock Trader monolítica se modernice y se convierta en una solución nativa de la nube de alto rendimiento.

## Presentación de Stock Trader
{: #vcscontent-modjourney-meet-stock-trader}

Todd y Jane han creado una aplicación que se ejecuta en WebSphere llamada Stock Trader. Aunque tiene una interfaz de usuario básica, es una aplicación fiable a la que acuden los gestores para gestionar portafolios, incluida la compra y venta de acciones, y para ver los niveles de fidelidad internos.

Stock Trader se ejecuta en WebSphere, se ha creado con unos cuantos archivos .war y utiliza una base de datos Db2 tradicional que se ejecuta en el centro de datos del que dependen desde hace años. Se tarda mucho en mejorar esta aplicación debido a las dependencias entre los equipos de infraestructura, los equipos de desarrollo y los equipos de datos.

Pero, aunque Stock Trader funciona correctamente, todos los empleados de la empresa quieren algo mejor. Los directores de producto quieren añadir redes sociales a sus programas de fidelidad. Esto complace a Jane, ya que puede refactorizar la app en microservicios, lo que les permite proporcionar de forma continuada funciones mejoradas con menos dependencias. Todd adora la eficacia de la nube, pero todavía necesita cierto control para mantener la conformidad con las políticas corporativas.

## Pasos del proceso
{: #vcscontent-modjourney-steps}

Todd y Jane saben por experiencia que un buen proceso para modernizar las soluciones comienza con una hoja de ruta. Aunque los planes pueden cambiar, siempre es bueno pensar a través de una visión prestablecida y definir una vía realista para alcanzarla. Cada paso debe aportar valor a la empresa y los pasos no deben ser tan significativos como para provocar costosas interrupciones a sus clientes.

Para Todd y Jane, los pasos a seguir en el proceso de Stock Trader son estos:
1. Convertir las VM de Stock Trader en {{site.data.keyword.cloud_notm}}. Este paso permite a Todd reducir la necesidad de gestionar su propio hardware y contenido de VMware en el centro de datos local.

2. Transformar Stock Trader en WebSphere Application Server en Stock Trader en contenedores. Este paso aumenta la resiliencia porque la ejecución de contenedores en Kubernetes incorporan coordinación y otros comportamientos de la nube. Esto requiere que Todd prepare una instancia de {{site.data.keyword.cloud_notm}} Private en su entorno de VMware vCenter Server on {{site.data.keyword.cloud_notm}} y que trabaje con Jane y con Transformation Advisor para contenerizar Stock Trader.

3. Refactorizar y añadir middleware a {{site.data.keyword.cloud_notm}} Private. Este paso incorpora el middleware existente en un entorno de nube y optimiza los comportamientos de la nube. También simplifica el proceso de licencias y prepara la solución para que sea totalmente portátil y se pueda utilizar en otros entornos de Kubernetes.

4. Perfeccionar la solución con Watson y otros servicios de la nube pública. Este paso puede añadir valor exponencialmente a la experiencia de Stock Trader al incorporar servicios de IA y la capacidad de comunicarse con centros de datos de nube de todo el mundo.

5. Hibridación real con {{site.data.keyword.cloud_notm}} Kubernetes Service. Este paso permite a Todd tener un servicio de Kubernetes gestionado que se siga conectando a la misma región de nube que su instancia de {{site.data.keyword.cloud_notm}} Private. También permite a los equipos de desarrollo de Jane tener un clúster de desarrollo y de prueba en el que pueden experimentar mientras siguen accediendo al mismo origen de datos que su clúster principal de {{site.data.keyword.cloud_notm}} Private.

6. Modernizar DevOps. Durante este proceso, Jane mejora la forma de distribuir Stock Trader.

7. Modernizar la gestión. Todd y Jane han trabajado para mejorar la forma de gestionar Stock Trader y la plataforma en la que se ejecuta, incluye a través de más de un clúster y entorno de nube.

## Enlaces relacionados
{: #vcscontent-modjourney-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
