---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Copia de seguridad, recuperación tras desastre y escalabilidad
{: #vcsicp-detail-design-resiliency}

## Copia de seguridad y DR
{: #vcsicp-detail-design-resiliency-backup-dr}

### Copia de seguridad de VMware vCenter Server on IBM Cloud
{: #vcsicp-detail-design-resiliency-vcs-backup}

Como parte de {{site.data.keyword.vmwaresolutions_full}}, el software de copia de seguridad de Veeam se puede desplegar de forma opcional en una instancia de servidor virtual de {{site.data.keyword.cloud_notm}} (VSI) que utiliza almacenamiento de resistencia (Endurance) de {{site.data.keyword.cloud_notm}} fuera del clúster VMware. El objetivo de este software es hacer copia de seguridad de los componentes de gestión de la solución.

### Copia de seguridad NSX
{: #vcsicp-detail-design-resiliency-nsx-backup}

La copia de seguridad adecuada de todos los componentes de NSX es crucial para restaurar el sistema a su estado de funcionamiento si se produce una anomalía. No es suficiente hacer una copia de seguridad de las máquinas virtuales (VM) NSX. Se debe utilizar la función de copia de seguridad NSX dentro del NSX Manager para realizar copia de seguridad adecuada. Se debe especificar un servidor FTP o SFTP para el repositorio de datos de copia de seguridad NSX.
La copia de seguridad de NSX Manager contiene toda la configuración de NSX, incluidos controladores, entidades de conmutación y de direccionamiento lógicos, seguridad, reglas de cortafuegos y todo lo demás que configure dentro de la interfaz de usuario o API de NSX Manager. Se debe hacer copia de seguridad por separado de la base de datos de vCenter y de los elementos relacionados, como los conmutadores virtuales. Se debe hacer una copia de seguridad de la configuración de NSX junto con una copia de seguridad de vCenter.

### Copia de seguridad y DR para IBM Cloud Private
{: #vcsicp-detail-design-resiliency-backup-dr-icp}

Las copias de seguridad de un despliegue de {{site.data.keyword.icpfull_notm}} resultan cruciales para restaurar el sistema a su estado de funcionamiento si se produce una anomalía. Además de una copia de seguridad de máquina virtual tradicional, cada nodo maestro de {{site.data.keyword.icpfull_notm}} ejecuta etcd. En la documentación de etcd se indica claramente que no se utilice la copia de seguridad de VM tradicional para restaurarla.

Para {{site.data.keyword.icpfull_notm}} a nivel de plataforma, necesita realizar una copia de seguridad de estos componentes:
- **Etcd** se utiliza para almacenar recursos de Kubernetes y la información de estado de Calico.
- **Registro de Docker** registro de imágenes privadas que se utiliza para almacenar archivos de imágenes de contenedor en un repositorio de imágenes.
- **MongoDB** base de datos que utiliza el servicio de medición, el servidor de repositorio de Helm, el servidor de API de Helm, la configuración de LDAP, el arrendatario (espacio de nombres) y las configuraciones de rol de team/user/usergroup.
- **MariaDB** base de datos que utiliza OIDC.
- **Elasticsearch** almacena los registros del sistema y de las aplicaciones.
- **Prometheus** almacena datos para la supervisión.
- **Almacenamiento persistente** se utiliza para los servicios de gestión que utilizan {{site.data.keyword.icpfull_notm}} o el volumen persistente de Kubernetes y para el proveedor de almacenamiento. Puede utilizar la tecnología de copia de seguridad o restauración que proporciona el proveedor de almacenamiento. También se puede extender un proceso similar a la aplicación del usuario.

### Copia de seguridad y DR para CAM
{: #vcsicp-detail-design-resiliency-backup-dr-cam}

La copia de seguridad para un despliegue de CAM resulta crucial para restaurar el sistema a su estado de funcionamiento si se produce una anomalía. La copia de seguridad de CAM requiere que el cliente realice una copia de seguridad de los componentes siguientes:
- La **base de datos Mongo** es base de datos principal de CAM.
- La **base de datos de Maria** es la base de datos que utiliza CAM Blueprint Designer.
- **NFS/GlusterFS** es donde residen los datos de CAM en cuatro volúmenes persistentes.

### Copia de seguridad y DR para el servicio IBM Cloud Kubernetes
{: #vcsicp-detail-design-resiliency-backup-dr-iks}

Las copias de seguridad de la base de datos etcd se proporcionan al cliente como parte del servicio gestionado; el cliente es el responsable de realizar la copia de seguridad de los datos de las aplicaciones.

## Escalabilidad
{: #vcsicp-detail-design-resiliency-scalability}

### Escalabilidad de VCS
{: #vcsicp-detail-design-resiliency-vcs-scalability}

Después del despliegue de los hosts iniciales, el usuario puede escalar la capacidad de cálculo desde dentro del portal de {{site.data.keyword.cloud_notm}} for VMware.

Este proceso de escalada del entorno sigue uno de estos tres métodos:
- Adición de nuevos sitios gestionados por distintos vCenter Servers.
- Adición de nuevos clústeres.
- Adición de nuevos hosts a un clúster existente.

#### Despliegues de varios sitios
{: #vcsicp-detail-design-resiliency-multi-site}

VMware on {{site.data.keyword.cloud_notm}} puede utilizar la presencia del centro de datos a nivel mundial de IBM Cloud y la red troncal integrada para permitir que varios casos de uso entre geografía se desplieguen y funcionen en una fracción del tiempo que se necesitaría para crear dicha infraestructura desde cero.

#### Escalada con nuevo clúster
{: #vcsicp-detail-design-resiliency-scale-out-new}

El usuario puede escalar la capacidad de cálculo creando un nuevo clúster desde dentro de la consola, solicitando los hosts, y los nuevos hosts se añaden automáticamente al nuevo clúster. Esta opción crea otro clúster en el entorno y proporciona a los usuarios la posibilidad de segregar de forma física y lógica la gestión de cargas de trabajo desde las cargas de trabajo de la aplicación, la posibilidad de segregar las cargas de trabajo en función de otras características (por ejemplo, clúster de base de datos de Microsoft SQL) y la posibilidad de desplegar aplicaciones en topologías de alta disponibilidad.

#### Escalada de un clúster existente
{: #vcsicp-detail-design-resiliency-scale-out-existing}

El usuario puede escalar un clúster existente solicitando hosts desde dentro de la consola y los nuevos hosts se añaden automáticamente al clúster. Es posible que los usuarios tengan que ajustar la política de reserva de HA para el clúster en función de sus requisitos de reserva.

### Escalabilidad de IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-scalability}

En función de la capacidad de cálculo disponible en las ubicaciones locales o en la nube, el usuario puede escalar la arquitectura de nodos desde el nodo de arranque desplegado inicialmente.

Este proceso de escalada del entorno sigue uno de los siguientes métodos:
- Ampliar los nodos trabajadores de {{site.data.keyword.icpfull_notm}}.
- Ampliar y utilizar la oferta {{site.data.keyword.containerlong_notm}}.

#### Expansión de IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-expansion}

Los nodos VM de nodos trabajadores de {{site.data.keyword.icpfull_notm}} se escalan para ampliar el cálculo o la aplicación:
- El cliente suministra una nueva VM, en la misma VXLAN que la que está desplegado {{site.data.keyword.icpfull_notm}}.
- Los clientes pueden escalar los nodos trabajadores, suministrando nuevas VM y luego iniciando una sesión en el nodo de arranque y ejecutando un mandato para incorporar los nuevos nodos al clúster.
- Utilice CAM para automatizar el suministro de la VM y la ejecución de mandatos para añadirla al clúster {{site.data.keyword.icpfull_notm}}.

###  Expansión del servicio IBM Cloud Kubernetes
{: #vcsicp-detail-design-resiliency-iks-expansion}

Los usuarios pueden suministrar un entorno {{site.data.keyword.containerlong_notm}} a través de {{site.data.keyword.cloud_notm}} Portal para ampliar o utilizar un entorno de contenedor.

Utilice lo siguiente para despliegues de aplicaciones en {{site.data.keyword.containerlong_notm}}:
- La conexión o los servicios de {{site.data.keyword.containerlong_notm}} se desarrollan en CAM y se publican en el catálogo de {{site.data.keyword.icpfull_notm}}.
- Futura mejora de Multi-Cloud Manager para gestionar instancias de {{site.data.keyword.containerlong_notm}}
- Interfaz de línea de mandatos de Helm.
- Uso de clústeres multizona para aumentar la alta disponibilidad.

## Enlaces relacionados
{: #vcsicp-detail-design-resiliency-related}

* [Adición o eliminación de nodos de clúster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Adición de nodos trabajadores cambiando el tamaño de una agrupación de nodos trabajadores existente](/docs/containers?topic=containers-clusters)
* [Cómo hacer copia de seguridad y restaurar {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [GitHub de copia de seguridad de {{site.data.keyword.icpfull_notm}}](https://github.com/ibm-cloud-architecture/icp-backup/)
* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
