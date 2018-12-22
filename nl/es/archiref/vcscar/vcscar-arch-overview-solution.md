---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# Componentes de la solución

## Componentes de VMware vCenter Server on IBM Cloud

Figura 1. Diagrama del entorno de vCenter Server
![Entorno vCenter Server](vcscar-vcs.svg)

### Controlador de servicios de la plataforma

El despliegue de vCenter Server utiliza un único controlador externo de servicios de la plataforma, instalado en una subred portátil en la VLAN privada asociada a las máquinas virtuales (VM) de gestión. Su pasarela predeterminada se establece en el direccionador del cliente de fondo (BCR).

### vCenter Server

Al igual que el controlador de servicios de la plataforma, vCenter Server se despliega como un dispositivo. Además, vCenter Server se instala en una subred portátil en la VLAN privada asociada a las máquinas virtuales de gestión. Su pasarela predeterminada se establece en la dirección IP asignada en el BCR para dicha subred determinada.

### NSX Manager

NSX Manager se despliega en el clúster inicial. Se asigna a NSX Manager una dirección IP respaldada por VLAN desde el bloque de direcciones portátiles privado, que está destinado a los componentes de gestión y configurado con los servidores DNS y NTP.

### Controladores NSX

La automatización de {{site.data.keyword.cloud}} despliega tres controladores NSX dentro del clúster inicial. Se asigna a los controladores una dirección IP respaldada por VLAN desde la subred portátil privada que está destinada a los componentes de gestión.

### NSX Edge y direccionador lógico distribuido

Se despliegan pares NSX Edge Services Gateway (ESG). En todos los casos, se utiliza un par de pasarela para el tráfico de salida de los componentes de automatización que residen en la red privada. Para vCenter Server e {{site.data.keyword.cloud_notm}} Private (ICP), una segunda pasarela, conocida como el borde gestionado por el cliente, se despliega y se configura con un enlace ascendente a la red pública y una interfaz asignada a la red privada. El administrador puede configurar cualquier componente NSX necesario, como por ejemplo DLR (Distributed Logical Router), conmutadores lógicos y cortafuegos.

Para obtener más información sobre el diseño de red, consulte [Arquitectura de referencia de red de vCenter Server](../vcsnsxt/vcsnsxt-intro.html).

En la tabla siguiente se resumen las especificaciones de ICP ESG y DLR.

Tabla 1. Especificaciones de ICP ESG

Atributo | Especificación
--|--
Edge Service Gateway | Dispositivo virtual
Tamaño de Edge    Grande | Número de vCPU	2
Memoria    | 1 GB
Disco    | 1000 GB en almacén de datos local

Tabla 2. Especificaciones de DLR de ICP

Atributo | Especificación
--|--|
Direccionador lógico distribuido |     Dispositivo virtual
Tamaño de Edge    Compacto | Número de vCPU	1
Memoria    | 512 MB
Disco    | 1000 GB en almacén de datos local

## Componentes de ICP

ICP es una plataforma de aplicaciones para desarrollar y gestionar aplicaciones de contenedor locales. ICP es un entorno integrado para gestionar contenedores que incluye el coordinador de contenedores Kubernetes,
un repositorio de imágenes privadas, una consola de gestión e infraestructuras de supervisión.

Figura 2. Despliegue de ICP virtual con vCenter Server
![Despliegue de ICP virtual con vCenter Server](vcscar-icp.svg)

### Nodo de arranque

Se utiliza un nodo de arranque o de rutina de carga (opcional) para ejecutar la instalación, la configuración, el escalado de nodos y actualizaciones de clústeres. Solo se necesita un nodo de arranque por clúster. Utilice un solo nodo como nodo maestro y de arranque.

### Nodo maestro

Un nodo maestro proporciona servicios de gestión y controla los nodos trabajadores de un clúster. El nodo maestro contiene los procesos responsables de la asignación de recursos, el mantenimiento del estado, la planificación y la supervisión.
Dado que un entorno de alta disponibilidad (HA) tiene más de un nodo maestro, si el nodo maestro inicial falla, la lógica de la migración tras error promociona automáticamente otro nodo y le asigna el rol de maestro. Los hosts que pueden actuar como nodo maestro se denominan candidatos a maestro.

### Nodo trabajador

Un nodo trabajador es un nodo que proporciona un entorno contenerizado para ejecutar tareas. A medida que aumenta la demanda, se pueden añadir fácilmente más nodos trabajadores al clúster para mejorar el rendimiento y la eficacia. Un clúster puede tener tantos nodos trabajadores como desee, pero se necesita al menos un nodo trabajador.

### Nodo proxy

Un nodo proxy es un nodo que transmite la solicitud externa a los servicios creados dentro del clúster. Dado que un entorno de alta disponibilidad (HA) tiene más de un nodo proxy, si el nodo proxy inicial falla, la lógica de la migración tras error promociona automáticamente otro nodo y le asigna el rol de proxy. Aunque puede utilizar un nodo único como maestro y proxy, es mejor utilizar nodos proxy dedicados para reducir la carga en el nodo maestro. Un clúster debe tener al menos un nodo proxy si se necesita equilibrio de carga dentro del clúster.

### Nodo de gestión

Un nodo de gestión es un nodo opcional que aloja servicios de gestión como, por ejemplo, supervisión, calibración y registro. Mediante la configuración de nodos de gestión dedicados, puede evitar que el nodo maestro se sobrecargue. Solo puede habilitar el nodo de gestión durante la instalación de ICP.

### Nodo de Vulnerability Advisor

Un nodo de Vulnerability Advisor (VA) es un nodo opcional que se utiliza para ejecutar los servicios de Vulnerability Advisor. Los servicios de Vulnerability Advisor consumen muchos recursos. Si utiliza el servicio Vulnerability Advisor, especifique un nodo VA dedicado.

En la tabla siguiente encontrará las especificaciones de VM necesarias para una instancia ICP de alta disponibilidad.

Tabla 3. Especificaciones de ICP VM

Nodo |     Instancias    | IP    | CPU    | RAM (GB)    | DISCO (GB)
:-----|------------:|:----|----:|----------:|----------:|
Maestro|    3    | IP (x3) VIP (x1)    | 4    | 64    | 200
Gestión    |3    | IP (x3)    |8    |64    |500
Proxy    | 3    | IP (x3)VIP (x1)    |2    |4    |150
Vulnerability Advisor    |3    | IP (x3)    | 4    | 16    |500
GlusterFS    | 3    | IP (x3)    |8    |16    |150
Trabajador    | 3-6    | IP (x3)    |4-8    |4    |150

CAM requiere que los nodos trabajadores tengan una configuración de vCPU y de memoria superior.

Tabla 4. Especificaciones de ICP VM

Nodo |     Instancias    | IP    | CPU    | RAM (GB)    | DISCO (GB)
:-----|------------:|:----|----:|----------:|----------:|
Trabajador  |  3 | IP (x3)  |  4-8 |16-20   |  150

## Componentes de IBM Cloud Automation Manager

{{site.data.keyword.cloud_notm}} Automation Manager (CAM) es una plataforma de gestión de autoservicio multinube de autoservicio que se ejecuta en ICP que ayuda a los desarrolladores y a los administradores a satisfacer las necesidades de la empresa.

Figura 3. Referencia de componentes de CAM
![Referencia de componentes de CAM](vcscar-cam-components.svg)

### Proxy de CAM

Proporciona un acceso de proxy nginx a CAM.

### Interfaz de usuario de CAM

Los componentes de la interfaz de usuario de CAM se dividen en más de un contenedor: interfaz de usuario de conexiones de nube, interfaz de usuario de biblioteca de plantillas e interfaz de usuario de instancias desplegadas.

### API de CAM

Las API de CAM se dividen en más de un contenedor.

### Helm

Un contenedor con los archivos binarios necesarios para desplegar diagramas de helm en clústeres de Kubernetes.

### Terraform

Un contenedor con los archivos binarios necesarios para desplegar recursos de Terraform en varias nubes.

### Registros

La ubicación de los registros de contenedor.

### Base de datos Mongo

La base de datos principal de la aplicación CAM.

### Redis

La base de datos Redis se utiliza para almacenar la memoria caché de sesiones y los bloqueos dentro de CAM.

### Diseñador de plantillas

Una interfaz gráfica de usuario para crear plantillas de Terraform, con una característica para arrastrar módulos de Terraform.

### Base de datos Maria

La base de datos para la aplicación del diseñador de plantillas.

## Enlaces relacionados

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
