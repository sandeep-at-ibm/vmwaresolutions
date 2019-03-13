---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Transformación de Stock Trader de WebSphere Application Server a Stock Trader en contenedores
{: #vcscontent-stocktrmod}

El siguiente paso en el proceso de modernización de Stock Trader es transformar la carga de trabajo que se ejecuta en máquinas virtuales (VM) en carga de trabajo que se ejecuta en contenedores.

Para continuar, Todd y Jane ejecutan Transformation Advisor para analizar la carga de trabajo de Stock Trader, identificar cualquier complejidad de la migración y recomendar cambios. Cuando están preparados, utilizan Transformation Advisor para desplegar Stock Trader en los contenedores Liberty que se ejecutan en {{site.data.keyword.icpfull_notm}}.

## Preparar IBM Cloud Private
{: #vcscontent-stocktrmod-prep-icp}

En primer lugar Todd tiene que instalar {{site.data.keyword.icpfull_notm}}. Puesto que Todd tiene su VMware en el entorno {{site.data.keyword.cloud_notm}}, decide utilizar la oferta {{site.data.keyword.cloud_notm}} Private Hosted, que le proporciona una instancia de {{site.data.keyword.icpfull_notm}} completa que se ejecuta en las máquinas virtuales VMware en {{site.data.keyword.cloud_notm}}.

El panel de control predeterminado proporciona una interfaz de usuario completa para gestionar el clúster de Kubernetes, la seguridad, el almacenamiento y el despliegue desde el catálogo.

### Preparar el almacenamiento
{: #vcscontent-stocktrmod-prep-storage}

{{site.data.keyword.cloud_notm}} Private Hosted se configura rápidamente con GlusterFS y ofrece almacenamiento de archivos en las VM como nodos GlusterFS dedicados. La ventaja de GlusterFS es que habilita el suministro dinámico. Si Todd quiere, puede configurar máquinas virtuales adicionales como servidores NFS.

Puesto que Todd desea que haya un servidor NFS esté disponible para él, ha identificado una VM llamada 'toddnfs' y ha ejecutado estos [pasos](https://help.ubuntu.com/community/SettingUpNFSHowTo).

Todd ejecuta los siguientes mandatos para crear un nuevo servidor NFS:

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

A continuación, Todd añade la siguiente línea:

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

A continuación, Todd ejecuta el siguiente mandato en cada VM para instalar NFS en cada VM de nodo trabajador de {{site.data.keyword.icpfull_notm}}:

`sudo apt-get update`

`sudo apt-get install nfs-common`

Todd ejecuta el siguiente mandato para confirmar la versión instalada:

`apt-cache policy nfs-common`

Siempre que se necesite un nuevo volumen NFS, Todd ejecuta el siguiente mandato para crear un nuevo volumen NFS, cuando sea necesario:

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### Preparar la seguridad de imágenes
{: #vcscontent-stocktrmod-prep-img-sec}

En {{site.data.keyword.icpfull_notm}} V3.1, la seguridad se ha mejorado al requerir una política de imágenes para que se pueda incorporar una imagen en una instancia de {{site.data.keyword.icpfull_notm}}. La mejora requiere que añada una política de imagen para el lugar en que residen las imágenes de IBM, *dockerhub/ibmcom*, y en el almacén de docker.

Se proporciona la política ibmcloud-default-cluster-image-policy de forma predeterminada, que cubre cualquier imagen de IBM de docker.io/ibmcom/\*, pero, como Db2 y otro contenido de IBM se encuentra en el almacén de Docker, se necesita otra política de imágenes para el almacén de docker, *docker.io/store/ibmcorp/*.

Además, algún contenido requiere un conjunto de políticas de seguridad de pod para permitir el acceso específico para el pod. Por ejemplo, Db2 requiere una política para los clientes que deseen ejecutar Db2 en un espacio de nombres que no sea 'default'.

Encontrará más información en [IBM Knowledge
Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html).

## Desplegar Transformation Advisor y Microclimate
{: #vcscontent-stocktrmod-deploy-tam}

Cuando Todd tiene {{site.data.keyword.icpfull_notm}} en ejecución, instala Transformation Advisor, junto con Microclimate. Todd abre el [catálogo](https://www.ibm.com/cloud/private/developer) y ve todo el contenido disponible.

Todd busca Transformation Advisor y Microclimate y los instala mediante las instrucciones del archivo readme que se proporciona cuando pulsa el diagrama de helm.

### Ejecutar Transformation Advisor
{: #vcscontent-stocktrmod-run-trans-advisor}

Para ejecutar Transformation Advisor, Jane ha añadido el recopilador de datos en la VM que ejecuta Stock Trader en WebSphere y abre la interfaz de usuario de [Transformation
Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/) para ver los resultados.

Jane pulsa Stock Trader y ve la recomendación de ejecutar cada archivo war en Liberty y descubre que la mayor parte de la migración resultaría más sencilla con una migración moderada. Jane pulsa los detalles de la migración y ve que Transformation Advisor proporciona los archivos de despliegue que puede utilizar para completar la migración. Después de que Jane cargue los archivos binarios en Transformation Advisor, este utiliza las API que proporciona Microclimate para desplegar los contenedores liberty.

Al final, las opciones de diseño resultantes de Stock Trader son las siguientes:
* Un solo contenedor Liberty: si Jane despliega un tiempo de ejecución de Liberty y añade su app Stock Trader en dicho contenedor único.
* Varios contenedores Liberty: uno para cada archivo .war, tal como recomienda Transformation Advisor para Stock Trader.

Todd no ha modificado el origen de los datos durante el paso de transformación. Transformation Advisor toma la configuración de origen de datos de WebSphere Application Server Network Deployment y los añade al archivo server.xml del contenedor Liberty.
{:important}

## Enlaces relacionados
{: #vcscontent-stocktrmod-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
