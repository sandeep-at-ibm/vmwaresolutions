---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Consideraciones operativas

## Copia de seguridad

### Copia de seguridad VCS

Como parte de {{site.data.keyword.vmwaresolutions_full}}, el software de copia de seguridad de Veeam se puede desplegar de forma opcional en una instancia de servidor virtual de {{site.data.keyword.cloud_notm}} (VSI) mediante el uso del almacenamiento de resistencia (Endurance) de {{site.data.keyword.cloud_notm}} fuera del clúster VMware. El objetivo de este software es hacer copia de seguridad de los componentes de gestión de la solución. En el apartado sobre [visión general de Veeam on {{site.data.keyword.cloud_notm}}](../../services/veeam_considerations.html) encontrará detalles sobre la oferta.

La copia de seguridad de todos los componentes de NSX es crucial para restaurar el sistema a su estado de trabajo si se produce una anomalía. No es suficiente realizar una copia de seguridad de los dispositivos virtuales NSX; se debe utilizar la función de copia de seguridad NSX del gestor de NSX para realizar copia de seguridad efectiva. Esta operación requiere que se especifique un servidor FTP o SFTP para el repositorio de datos de copia de seguridad NSX.

La copia de seguridad de NSX Manager contiene toda la configuración de NSX, incluidos controladores, entidades de conmutación y de direccionamiento lógicos, seguridad, reglas de cortafuegos y todo lo demás que configure dentro de la interfaz de usuario o API de NSX Manager. Se debe hacer copia de seguridad por separado de la base de datos de vCenter y de los elementos relacionados, como los conmutadores virtuales. Consulte [Copia de seguridad basada en archivo NSX](../solution/solution_backingup.html#nsx-file-based-backup) para obtener más información. Se debe realizar una copia de seguridad de la configuración de NSX junto con una [copia de seguridad basada en archivos de vCenter](../solution/solution_backingup.html#vcenter-file-based-backup).

### Copia de seguridad y recuperación en caso de error para IBM Cloud Private

Las copias de seguridad de un despliegue de ICP resultan cruciales para restaurar el sistema a su estado de trabajo si se produce una anomalía. Sobre una copia de seguridad de VM tradicional, hay un punto conflictivo: cada nodo maestro de ICP ejecuta un servicio *etcd* y en la documentación de *etcd* se indica claramente que no se utilice la copia de seguridad de VM tradicional para restaurarlo.

En {{site.data.keyword.cloud_notm}} Private a nivel de plataforma, deberá realizar una copia de seguridad de estos componentes.
- **etcd** - etcd se utiliza para almacenar recursos de Kubernetes y la información de estado de Calico.
- **Registro de Docker** - Este registro de imágenes privadas que se utiliza para almacenar archivos de imágenes de contenedor.
- **MongoDB** - Utilizan esta base de datos el servicio de medición, el servidor de repositorio de Helm, el servidor de API de Helm, la configuración de LDAP, el arrendatario (espacio de nombres) y las configuraciones de rol team/user/usergroup.
- **MariaDB** - OIDC utiliza esta base de datos.
-	**Elasticsearch** - Almacena los registros del sistema y de las aplicaciones.
-	**Prometheus** - Almacena datos para la supervisión.
-	**Almacenamiento persistente** - Se utiliza para los servicios de gestión que utilizan {{site.data.keyword.cloud_notm}} Private o el volumen persistente de Kubernetes y el proveedor de almacenamiento.

Puede utilizar la tecnología de copia de seguridad o restauración que proporciona el proveedor de almacenamiento. También se puede extender un proceso similar a la aplicación del usuario. Para obtener más información, consulte el [blog sobre cómo hacer copia de seguridad y restaurar {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8) o [icp-backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/).

### Copia de seguridad y recuperación en caso de error para CAM

Las copias de seguridad de un despliegue de CAM resultan cruciales para restaurar el sistema a su estado de trabajo si se produce una anomalía. La copia de seguridad de CAM requiere que el cliente realice una copia de seguridad de los componentes siguientes:
-	**Base de datos Mongo**: base de datos principal de CAM.
-	**Base de datos de Maria**: utilizada por CAM Blueprint Designer.
-	**Sistemas de archivos NFS/Gluster**: los datos de CAM residen en cuatro volúmenes persistentes.

### Copia de seguridad y DR para IKS

La copia de seguridad de la base de datos etcd se proporciona al cliente como parte del servicio gestionado; sin embargo, el cliente es el responsable de realizar la copia de seguridad de los datos de las aplicaciones.

## Escalabilidad

### Escalabilidad de VCS

Después del despliegue de los hosts iniciales, los usuarios pueden escalar la capacidad de cálculo desde dentro del portal de {{site.data.keyword.cloud_notm}} for VMware.

El proceso de escalada del entorno sigue uno de estos tres métodos:
-	Adición de nuevos sitios gestionados por distintos vCenter Servers.
-	Adición de nuevos clústeres.
-	Adición de nuevos hosts a un clúster existente.

#### Despliegues en varios sitios

VMware on {{site.data.keyword.cloud_notm}} puede utilizar la presencia del centro de datos a nivel mundial de {{site.data.keyword.cloud_notm}} y la red troncal integrada para permitir que varios casos de uso entre geografía se desplieguen y funcionen en una fracción del tiempo que se necesitaría para crear dicha infraestructura desde cero. Encontrará más información en el apartado sobre [Configuración de varios sitios para instancias de vCenter Server on {{site.data.keyword.cloud_notm}}](../../vcenter/vc_multisite.html).

#### Escalada con nuevo clúster

Los usuarios pueden escalar la capacidad de cálculo creando un nuevo clúster desde dentro de la consola, solicitando los hosts, y los nuevos hosts se añaden automáticamente al nuevo clúster. Esta opción crea otro clúster en el entorno y proporciona a los usuarios la posibilidad de segregar de forma física y lógica la gestión de cargas de trabajo desde las cargas de trabajo de la aplicación, la posibilidad de segregar las cargas de trabajo en función de otras características (por ejemplo, clúster de base de datos de Microsoft SQL) y la posibilidad de desplegar aplicaciones en topologías de alta disponibilidad. Para obtener más información, consulte [Pedido de instancias de vCenter Server](../../vcenter/vc_orderinginstance.html).

#### Escalada de un clúster existente

El usuario puede escalar un clúster existente solicitando hosts desde dentro de la consola y los nuevos hosts se añaden automáticamente al clúster. Para obtener más información, consulte [Ampliación y reducción de capacidad para instancias de vCenter Server](../../vcenter/vc_addingremovingservers.html). Es posible que tenga que ajustar la política de reserva de HA para el clúster en función de sus requisitos de reserva.

### Escalabilidad de ICP e IKS

En función de la capacidad de cálculo disponible en las ubicaciones locales o en la nube, los usuarios pueden escalar la arquitectura de nodos desde el nodo de arranque desplegado inicialmente. Para escalar el entorno puede:
-	Ampliar los nodos trabajadores de ICP.
-	Ampliar y utilizar la oferta IKS.

#### Expansión de ICP

Los nodos de máquina virtual de nodos trabajadores de ICP se escalan para ampliar el cálculo y la aplicación:
- El cliente suministra una nueva máquina virtual en la misma VXLAN que la que está desplegado ICP.
- Los clientes pueden escalar los nodos trabajadores, suministrando nuevas máquinas virtuales y luego iniciando una sesión en el nodo de arranque y ejecutando un mandato para incorporar los nuevos nodos al clúster. Consulte [Adición y eliminación de nodos del clúster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html) para obtener más información.
- Utilice CAM para automatizar el suministro de la VM y la ejecución de mandatos para añadirla al clúster ICP.

#### Expansión de IKS

Los usuarios pueden suministrar un entorno IKS mediante el portal de {{site.data.keyword.cloud_notm}} para ampliar y utilizar un entorno de contenedor. Para obtener más información, consulte [Mejoras en la hibridación en {{site.data.keyword.cloud_notm}} e {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us).

Los despliegues de aplicaciones en IKS son posibles con los métodos siguientes:
-	La conexión y los servicios de IKS que se desarrollan en CAM y se publican en el catálogo ICP.
-	Multi Cloud Manager, una futura mejora para gestionar instancias de IKS.
-	Línea de mandatos de Helm.

### Enlaces relacionados

* [Visión general de VCS con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
