---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-30"

---

# Introducción a los procedimientos operativos
{: #opsprocs-intro}

Muchas organizaciones de TI documentan sus procedimientos operativos en un runbook. Un runbook es un conjunto de documentos estandarizados, referencias y procedimientos que explican tareas de TI comunes y recurrentes. El personal de TI consulta el runbook para realizar su trabajo de forma óptima. Los runbooks mejoran la eficiencia organizativa mediante la estandarización y ayudan a incorporar nuevos empleados de forma más eficaz. Generalmente hay dos tipos de runbooks:

1. Documentación general utilizada para describir procedimientos, guías y tareas. Suelen ser de carácter general, y se refieren a la documentación existente proporcionada por los proveedores.
2. Documentación especializada escrita para la empresa. Esta documentación es específica de un sistema, una aplicación o una suite de aplicaciones y no está cubierta por la documentación de los proveedores. Para crear su documentación especializada, recomendamos la siguiente estructura: 

 * Visión general: Una visión general del servicio con secciones que describan:
    * ¿Qué es el servicio y por qué lo necesita la empresa?
    * ¿Quiénes son los contactos principales del servicio?
    * Cómo notificar los problemas con el servicio.
 * Construcción: Esta sección se centra en los equipos de desarrollo, en los principales componentes de software del servicio y en cómo se construye el servicio. Información sobre productos de software, ubicaciones de los OVA, medios de distribución o ubicación del código fuente. Los pasos necesarios para empaquetar o distribuir el release. Incluye todas las instrucciones necesarias para que un nuevo desarrollador pueda empezar a trabajar.
 * Despliegue: Esta sección se centra en el equipo de operaciones y en cómo desplegar el software. Incluye detalles del hardware y de la infraestructura virtualizada y de cómo construir las máquinas virtuales (VM), incluyendo: vCPU, RAM y requisitos de disco; versión y configuración del sistema operativo, información sobre el middleware o los paquetes que hay que instalar. 
 * Procedimientos: Instrucciones paso a paso para tareas comunes como añadir, cambiar y suprimir, problemas comunes y sus soluciones o recomendaciones para la resolución de problemas. 
 * Resolución de problemas: Una lista de alertas comunes del sistema de supervisión, incluyendo tareas paso a paso para estas alertas, así como la guía genérica para la resolución de problemas del servicio.
 * Planes y procedimientos de recuperación tras desastre: Detalles sobre cómo recuperar el servicio en otra ubicación debido a un siniestro en la ubicación principal.
 * Acuerdo de nivel de servicio: los parámetros de servicio acordados, como por ejemplo los acuerdos de nivel operativo, los indicadores de puntos clave, los objetivos de disponibilidad, los objetivos de punto de recuperación, el objetivo de tiempo de recuperación.

La mayoría de las organizaciones de TI tienen varios runbooks que les sirven de manuales de referencia. Esta serie de documentación está diseñada para ser utilizada como un runbook general para su organización, para utilizar las instancias de vCenter Server. Aunque el contenido de cada runbook es específico de las necesidades de la organización, la metodología de creación de runbooks es bastante estándar y sigue dos fases:

1. La primera fase consiste en decidir qué procedimientos se deben documentar y, una vez enumerados, documentar cada procedimiento con suficiente detalle.
2. La segunda fase es continuada y consiste en mantener, actualizar y corregir estos procedimientos, añadiendo nuevos procedimientos y retirando los que ya no son necesarios. 

{{site.data.keyword.vmwaresolutions_full}} le permite utilizar las habilidades, los conjuntos de herramientas y los runbooks existentes del equipo para gestionar las instancias en {{site.data.keyword.cloud_notm}}. Como recomendación, la documentación general siguiente captura los procedimientos, las guías y las tareas comunes: 

* Tareas de configuración: Estas tareas son actividades comunes que los administradores de sistemas deben realizar para ajustar el entorno a fin de adaptarlo a las necesidades de la empresa y responder a las solicitudes de servicio como, por ejemplo, añadir nuevas máquinas virtuales y aumentar la capacidad. Estas tareas se agrupan en la estructura siguiente:
 * Instrucciones genéricas
 * Procedimientos de VM
 * Procedimientos de vCenter
 * Procedimientos de host de vSphere ESXi
 * Procedimientos de almacenamiento
 * Procedimientos de red
* Alarmas: vSphere incluye un subsistema de sucesos y alarmas que realiza el seguimiento de sucesos que se producen en el entorno de vSphere y publica esta información en vCenter. En esta sección se describe este subsistema y cómo habilitar y utilizar las alarmas de la empresa.
* Comprobaciones diarias proactivas: Estas comprobaciones permiten a los administradores del sistema mantener el entorno en buen estado. Si se llevan a cabo a diariamente, deberían impedir que muchos problemas comunes relacionados con la capacidad y el rendimiento, tengan impacto en sus cargas de trabajo. 
* Resolución de problemas: Aunque se realicen comprobaciones diarias proactivas, a veces se producen problemas que afectan a las cargas de trabajo. Por lo tanto, es necesario arreglar el problema subyacente lo antes posible. Estas guías de resolución de problemas y otros escenarios comunes de resolución de problemas ayudan a los administradores del sistema a identificar y arreglar estos problemas rápidamente.
* Conformidad: la guía de conformidad proporciona información sobre cómo conservar la conformidad del entorno con a un régimen de cumplimiento normativo o con las mejores prácticas del sector. El foco de esta guía se encuentra en la guía de refuerzo de VMware, que es un número de listas documentadas de las mejores prácticas para un entorno VMware.

Muchas de las tareas anteriores se automatizan en Operations Management on {{site.data.keyword.cloud_notm}} y, para las tareas que no se automatizan, estas herramientas facilitan los procesos manuales para los administradores de sistemas. Es fundamental tener los componentes principales del entorno de VMware supervisados, en Operations Management on {{site.data.keyword.cloud_notm}}, esto se consigue de la forma siguiente:

## Operations Management on IBM Cloud
{: #opsprocs-intro-ops-mgmt}

Puede tener herramientas de empresa en su lugar que puede utilizar para supervisar y gestionar la instancia del servidor vCenter. En la Tabla 1 se describen los componentes principales del entorno de vCenter Server y se explica por qué es necesario supervisarlos y cómo se supervisan con Operations Management on {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte la documentación de la arquitectura de referencia.

Tabla 1. Componentes principales del entorno de vCenter Server

| Componente | Por qué | Supervisado por  |
|---|---|---|
| vCenter | vCenter es el componente de gestión de infraestructuras que gestiona los hosts de vSphere y gestiona las construcciones virtualizadas, como por ejemplo los clústeres. vSAN se supervisa mediante vCenter. Las redes de vSphere como por ejemplo conmutadores distribuidos y los grupos de puertos, se supervisan mediante vCenter. | vRealize Operations Manager (vROps) y VMware SDDC Health Management Pack. vRealize Log Insights (vRLI) recopila los datos de registro de vCenter, y el paquete de contenido de vSphere añade un conocimiento específico a los registros y, a su vez, envía alertas a los vROP. |
| Hosts de vSphere | Los hosts de vSphere proporcionan la CPU virtualizada, la RAM y la red a las máquinas virtuales de cálculo. | vROps a través de vCenter. vRLI recopila los datos de registro |
| vSAN | vSAN proporciona un almacén de datos consolidando el almacenamiento de los hosts para que lo utilicen las máquinas virtuales. Los problemas que afectan a la capacidad y el rendimiento afectan a las aplicaciones que se ejecutan en estas VM. |vROps y el Paquete de gestión para vSAN proporciona paneles de control adicionales para ayudar en la supervisión de vSAN. Las comprobaciones de estado de vCenter vSAN se recopilan mediante vROps. vRLI recopila los datos de registro de vCenter. |
| NSX | NSX proporciona los componentes de red virtualizados utilizados por las VM de cálculo, cualquier anomalía de la red puede tener un impacto en las aplicaciones que se ejecutan en estas máquinas virtuales. | vROps y el Paquete de gestión de vROps para VMware NSX proporciona visibilidad en la topología de red. vRLI recopila los datos de registro de los componentes NSX como, por ejemplo, Controladores, ESG y conmutadores lógicos. vRealize Network Insight (vRNI) proporciona una resolución detallada de problemas de red. |

Además de ayuda para la supervisión, Operations Management on {{site.data.keyword.cloud_notm}}, proporciona ayuda para la configuración, la conformidad y muchas de las tareas proactivas que se detallan en esta documentación. 


## Enlaces relacionados
{: #opsprocs-intro-links}

* [Supervisión de vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [Guía para reforzar la seguridad en VMware](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [Consideraciones sobre el cambio de artefactos de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
