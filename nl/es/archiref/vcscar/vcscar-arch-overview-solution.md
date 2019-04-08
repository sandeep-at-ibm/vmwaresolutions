---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

# Componentes de la solución
{: #vcscar-arch-overview-solution}

## Componentes de VMware vCenter Server on IBM Cloud
{: #vcscar-arch-overview-solution-vcs-comp}

Figura 1. Diagrama del entorno de vCenter Server
![Entorno vCenter Server](vcscar-vcs.svg)

### Controlador de servicios de la plataforma
{: #vcscar-arch-overview-solution-psc}

El despliegue de vCenter Server utiliza un único controlador externo de servicios de la plataforma, instalado en una subred portátil en la VLAN privada asociada a las máquinas virtuales (VM) de gestión. Su pasarela predeterminada se establece en el direccionador del cliente de fondo (BCR).

### vCenter Server
{: #vcscar-arch-overview-solution-vcs}

Al igual que el controlador de servicios de la plataforma, vCenter Server se despliega como un dispositivo. Además, vCenter Server se instala en una subred portátil en la VLAN privada asociada a las máquinas virtuales de gestión. Su pasarela predeterminada se establece en la dirección IP asignada en el BCR para dicha subred determinada.

### NSX Manager
{: #vcscar-arch-overview-solution-nsx-manager}

NSX Manager se despliega en el clúster inicial. Se asigna a NSX Manager una dirección IP respaldada por VLAN desde el bloque de direcciones portátiles privado, que está destinado a los componentes de gestión y configurado con los servidores DNS y NTP.

### Controladores NSX
{: #vcscar-arch-overview-solution-nsx-controllers}

La automatización de {{site.data.keyword.cloud}} despliega tres controladores NSX dentro del clúster inicial. Se asigna a los controladores una dirección IP respaldada por VLAN desde la subred portátil privada que está destinada a los componentes de gestión.

### NSX Edge y direccionador lógico distribuido
{: #vcscar-arch-overview-solution-nsx-edge}

Se despliegan pares NSX Edge Services Gateway (ESG). En todos los casos, se utiliza un par de pasarela para el tráfico de salida de los componentes de automatización que residen en la red privada. Para vCenter Server e {{site.data.keyword.icpfull_notm}}, una segunda pasarela, conocida como el borde gestionado por el cliente, se despliega y se configura con un enlace ascendente a la red pública y una interfaz asignada a la red privada. El administrador puede configurar cualquier componente NSX necesario, como por ejemplo DLR (Distributed Logical Router), conmutadores lógicos y cortafuegos.

Para obtener más información sobre el diseño de red, consulte [Arquitectura de referencia de red de vCenter Server](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro).

En la tabla siguiente se resumen las especificaciones de {{site.data.keyword.icpfull_notm}} ESG y DLR.

Tabla 1. Especificaciones de {{site.data.keyword.icpfull_notm}} ESG

Atributo | Especificación
--|--
Edge Service Gateway | Dispositivo virtual
Tamaño de Edge    Grande | Número de vCPU	2
Memoria    | 1 GB
Disco    | 1000 GB en almacén de datos local

Tabla 2. Especificaciones de DLR de {{site.data.keyword.icpfull_notm}}

Atributo | Especificación
--|--|
Direccionador lógico distribuido |     Dispositivo virtual
Tamaño de Edge    Compacto | Número de vCPU	1
Memoria    | 512 MB
Disco    | 1000 GB en almacén de datos local

## Componentes de IBM Cloud Private
{: #vcscar-arch-overview-solution-icp-comp}

{{site.data.keyword.icpfull_notm}} es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones locales contenerizadas. {{site.data.keyword.icpfull_notm}} es un entorno integrado para gestionar contenedores que incluye el coordinador de contenedores Kubernetes,
un repositorio de imágenes privadas, una consola de gestión e infraestructuras de supervisión.

Figura 2. Despliegue de {{site.data.keyword.icpfull_notm}} virtual con vCenter Server
![Desarrollo de {{site.data.keyword.icpfull_notm}} virtual con vCenter Server](vcscar-icp.svg)

### Nodo de arranque
{: #vcscar-arch-overview-solution-boot-node}

Se utiliza un nodo de arranque o de rutina de carga (opcional) para ejecutar la instalación, la configuración, el escalado de nodos y actualizaciones de clústeres. Solo se necesita un nodo de arranque por clúster. Utilice un solo nodo como nodo maestro y de arranque.

### Nodo maestro
{: #vcscar-arch-overview-solution-master-node}

Un nodo maestro proporciona servicios de gestión y controla los nodos trabajadores de un clúster. El nodo maestro contiene los procesos responsables de la asignación de recursos, el mantenimiento del estado, la planificación y la supervisión.

Dado que un entorno de alta disponibilidad (HA) tiene más de un nodo maestro, si el nodo maestro inicial falla, la lógica de la migración tras error promociona automáticamente otro nodo y le asigna el rol de maestro. Los hosts que pueden actuar como nodo maestro se denominan candidatos a maestro.

### Nodo trabajador
{: #vcscar-arch-overview-solution-worker-node}

Un nodo trabajador es un nodo que proporciona un entorno contenerizado para ejecutar tareas. A medida que aumenta la demanda, se pueden añadir fácilmente más nodos trabajadores al clúster para mejorar el rendimiento y la eficacia. Un clúster puede tener tantos nodos trabajadores como desee, pero se necesita al menos un nodo trabajador.

### Nodo proxy
{: #vcscar-arch-overview-solution-proxy-node}

Un nodo proxy es un nodo que transmite la solicitud externa a los servicios creados dentro del clúster. Dado que un entorno de alta disponibilidad (HA) tiene más de un nodo proxy, si el nodo proxy inicial falla, la lógica de la migración tras error promociona automáticamente otro nodo y le asigna el rol de proxy.

Aunque puede utilizar un nodo único como maestro y proxy, es mejor utilizar nodos proxy dedicados para reducir la carga en el nodo maestro. Un clúster debe tener al menos un nodo proxy si se necesita equilibrio de carga dentro del clúster.

### Nodo de gestión
{: #vcscar-arch-overview-solution-mgmt-node}

Un nodo de gestión es un nodo opcional que aloja servicios de gestión como, por ejemplo, supervisión, calibración y registro. Mediante la configuración de nodos de gestión dedicados, puede evitar que el nodo maestro se sobrecargue. Solo puede habilitar el nodo de gestión durante la instalación de {{site.data.keyword.icpfull_notm}}.

### Nodo de Vulnerability Advisor
{: #vcscar-arch-overview-solution-va-node}

Un nodo de Vulnerability Advisor (VA) es un nodo opcional que se utiliza para ejecutar los servicios de Vulnerability Advisor. Los servicios de Vulnerability Advisor consumen muchos recursos. Si utiliza el servicio Vulnerability Advisor, especifique un nodo VA dedicado.

En la tabla siguiente encontrará las especificaciones de VM necesarias para una instancia {{site.data.keyword.icpfull_notm}} de alta disponibilidad.

Tabla 3. Especificaciones de {{site.data.keyword.icpfull_notm}} VM

Nodo |     Instancias    | IP    | CPU    | RAM (GB)    | DISCO (GB)
:-----|------------:|:----|----:|----------:|----------:|
Maestro|    3    | IP (x3) VIP (x1)    | 4    | 64    | 200
Gestión    |3    | IP (x3)    |8    |64    |500
Proxy    | 3    | IP (x3)VIP (x1)    |2    |4    |150
Vulnerability Advisor    |3    | IP (x3)    | 4    | 16    |500
GlusterFS    | 3    | IP (x3)    |8    |16    |150
Trabajador    | 3-6    | IP (x3)    |4-8    |4    |150

CAM requiere que los nodos trabajadores tengan una configuración de vCPU y de memoria superior.

Tabla 4. Especificaciones de {{site.data.keyword.icpfull_notm}} VM

Nodo |     Instancias    | IP    | CPU    | RAM (GB)    | DISCO (GB)
:-----|------------:|:----|----:|----------:|----------:|
Trabajador  |  3 | IP (x3)  |  4-8 |16-20   |  150

## Componentes de IBM Cloud Automation Manager
{: #vcscar-arch-overview-solution-icam-comp}

{{site.data.keyword.cloud_notm}} Automation Manager (CAM) es una plataforma de gestión de autoservicio multinube de autoservicio que se ejecuta en {{site.data.keyword.icpfull_notm}} que ayuda a los desarrolladores y a los administradores a satisfacer las necesidades de la empresa.

Figura 3. Referencia de componentes de CAM
![Referencia de componentes de CAM](vcscar-cam-components.svg)

### Proxy de CAM
{: #vcscar-arch-overview-solution-cam-proxy}

Proporciona un acceso de proxy nginx a CAM.

### Interfaz de usuario de CAM
{: #vcscar-arch-overview-solution-cam-ui}

Los componentes de la interfaz de usuario de CAM se dividen en más de un contenedor: interfaz de usuario de conexiones de nube, interfaz de usuario de biblioteca de plantillas e interfaz de usuario de instancias desplegadas.

### API de CAM
{: #vcscar-arch-overview-solution-cam-api}

Las API de CAM se dividen en más de un contenedor.

### Helm
{: #vcscar-arch-overview-solution-helm}

Un contenedor con los archivos binarios necesarios para desplegar diagramas de helm en clústeres de Kubernetes.

### Terraform
{: #vcscar-arch-overview-solution-terra}

Un contenedor con los archivos binarios necesarios para desplegar recursos de Terraform en varias nubes.

### Registros
{: #vcscar-arch-overview-solution-logs}

La ubicación de los registros de contenedor.

### Base de datos Mongo
{: #vcscar-arch-overview-solution-mongo-db}

La base de datos principal de la aplicación CAM.

### Redis
{: #vcscar-arch-overview-solution-redis}

La base de datos Redis se utiliza para almacenar la memoria caché de sesiones y los bloqueos dentro de CAM.

### Diseñador de plantillas
{: #vcscar-arch-overview-solution-templ-designer}

Una interfaz gráfica de usuario para crear plantillas de Terraform, con una característica para arrastrar módulos de Terraform.

### Base de datos Maria
{: #vcscar-arch-overview-solution-maria-db}

La base de datos para la aplicación del diseñador de plantillas.

## Enlaces relacionados
{: #vcscar-arch-overview-solution-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
