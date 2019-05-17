---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# IBM Cloud Private
{: #vcsnsxt-overview-icp}

{{site.data.keyword.icpfull_notm}} es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones contenerizadas. Constituye un entorno integrado que incluye el coordinador de contenedores Kubernetes, un repositorio de imágenes privadas, una consola de gestión, infraestructuras de supervisión y una interfaz gráfica de usuario, que proporciona una ubicación centralizada desde la que puede desplegar, gestionar, supervisar y escalar aplicaciones.

{{site.data.keyword.cloud_notm}} Private tiene las características siguientes:
-	**Instalador unificado**: el instalador configura rápidamente un clúster basado en Kubernetes con nodos maestro, trabajador y proxy utilizando un instalador basado en Ansible.
-	**Consola de gestión de {{site.data.keyword.cloud_notm}} Private**: permite gestionar, supervisar y resolver problemas de las aplicaciones y del clúster desde una consola de gestión única, centralizada y segura.
-	**Registro de imágenes privadas de Docker**: este registro local tiene las mismas características que Docker Hub, pero además le permite restringir los usuarios que pueden ver u obtener imágenes.
-	**Catálogo de servicios y software contenerizados**: el catálogo proporciona una ubicación centralizada desde la que se puede examinar e instalar paquetes en el clúster. Dispone de productos adicionales de IBM en los repositorios que se incluyen en la lista predeterminada de repositorios de {{site.data.keyword.cloud_notm}} Private.
-	**Redes de arrendatario aisladas**: Calico permite mejorar el rendimiento y el aislamiento de la red dentro del clúster. Con Calico, puede crear una subred aislada para cada proyecto dentro del clúster. Este aislamiento de red proporciona seguridad añadida durante las transmisiones de datos y reduce las posibilidades de comprometer las aplicaciones y sus datos. Calico también facilita la creación de nuevas políticas de red que pueden habilitar un control detallado sobre la compartición de objetos dentro de un espacio de nombres único.
-	**Potentes funciones de supervisión y registro con la pila ELK**: {{site.data.keyword.cloud_notm}} Private utiliza Elasticsearch, Logstash, Filebeat, y Heapster para la recopilación, el almacenamiento y la consulta de registros y métricas. Este proceso de supervisión y de registro proporciona un almacén centralizado para todos los registros y métricas, un mejor rendimiento y una estabilidad aumentada al acceder y consultar registros y métricas.

## Componentes de IBM Cloud Private
{: #vcsnsxt-overview-icp-comp}

Un clúster de {{site.data.keyword.cloud_notm}} Private tiene cuatro clases principales de nodos: arranque, maestro, trabajador y proxy. Si lo desea puede especificar nodos de gestión, Vulnerability Advisor (VA) y etcd en el clúster.
-	**Nodo de arranque**: se utiliza un nodo de arranque para ejecutar la instalación, la configuración, el escalado de nodos y las actualizaciones del clúster.
-	**Nodo maestro**: un nodo maestro proporciona servicios de gestión y controla los nodos trabajadores de un clúster. El nodo maestro contiene los procesos responsables de la asignación de recursos, el mantenimiento del estado, la planificación y la supervisión.
-	**Nodo trabajador**: un nodo trabajador es un nodo que proporciona un entorno contenerizado para ejecutar tareas. A medida que aumenta la demanda, se pueden añadir fácilmente más nodos trabajadores al clúster para mejorar el rendimiento y la eficacia.
-	**Nodo proxy**: un nodo proxy es un nodo que transmite la solicitud externa a los servicios creados dentro del clúster.
-	**Nodo de gestión**: un nodo de gestión es un nodo opcional que aloja únicamente servicios de gestión como, por ejemplo, supervisión, calibración y registro. Mediante la configuración de nodos de gestión dedicados, puede evitar que el nodo maestro se sobrecargue.
-	**Nodo de Vulnerability Advisor (VA)**: un nodo de Vulnerability Advisor (VA) es un nodo opcional que se utiliza para ejecutar los servicios de Vulnerability Advisor.
-	Nodo **etcd**: un nodo etcd es un nodo opcional que se utiliza para ejecutar el almacén de valores de claves distribuidas etcd.

## Red de IBM Cloud Private
{: #vcsnsxt-overview-icp-networking}

La gestión de la red de {{site.data.keyword.icpfull_notm}} se realiza mediante Calico.
Calico utiliza la capa 3 o la capa de red del modelo Open System Interconnection (OSI). Calico utiliza Border Gateway Protocol (BGP) para crear tablas de direccionamiento que facilitan la comunicación entre los nodos agente.

Para obtener más información sobre la red Calico, consulte [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-overview-iks).

## Enlaces relacionados
{: #vcsnsxt-overview-icp-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
