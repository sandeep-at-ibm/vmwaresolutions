---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-20"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de instancias de vCenter Server con NSX-T
{: #vc_nsx-t_orderinginstance}

Para desplegar una plataforma virtualizada VMware flexible y personalizable que se adapte perfectamente a sus necesidades de carga de trabajo, solicite una instancia de VMware vCenter con NSX-T.

## Requisitos
{: #vc_nsx-t_orderinginstance-req}

Asegúrese de haber realizado las tareas siguientes:
* Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Gestión de cuentas y valores de usuario](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Ha revisado la información de [Requisitos y planificación de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).
* Ha revisado el formato del nombre de dominio e instancia. El nombre de dominio y la etiqueta de subdominio se utilizan para generar el nombre de usuario y los nombres de servidor de la instancia.

Tabla 1. Formato del valor de nombres de instancia y de dominio

| Nombre        | Formato del valor      |
  |:------------|:------------ |
  | Nombre de dominio | `<root_domain>` |  
  | Nombre usuario inicio sesión vCenter Server | `<user_id>@<root_domain>` (usuario de Microsoft Active Directory) o `administrator@vsphere.local` |
  | vCenter Server (con PSC incorporado) FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. La longitud máxima es de 50 caracteres. |
  | Nombre sitio inicio sesión único (SSO) | `<subdomain_label>` |
  | Nombre completo de servidor ESXi | `<host_prefix><n>.<subdomain_label>.<root_domain>`, donde `<n>` es la secuencia del servidor ESXi. La longitud máxima es de 50 caracteres. |

No modifique ningún valor definido durante la solicitud o el despliegue de la instancia. Hacerlo puede hacer que la instancia se vuelva inutilizable. Por ejemplo, si se cierra la red pública, si los servidores y las Instancias de servidor virtual (VSI) se mueven detrás de una media disposición de Vyatta, o si el VSI de IBM CloudBuilder se detiene o se suprime.
{:important}

## Valores del sistema
{: #vc_nsx-t_orderinginstance-sys-settings}

Debe especificar los valores del sistema siguientes cuando solicite una instancia de vCenter Server.

### Nombre de instancia
{: #vc_nsx-t_orderinginstance-inst-name}

El nombre de instancia debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre de instancia debe empezar por un carácter alfabético y terminar por un carácter alfanumérico.
* La longitud máxima del nombre de instancia es de 10 caracteres.
* El nombre de instancia debe ser exclusivo dentro de su cuenta.

### Licencias de VMware vSphere
{: ##vc_nsx-t_orderinginstance-vsphere-license}

La licencia de vSphere Enterprise Plus 6.7u1 está seleccionada de forma predeterminada.

### Primaria o secundaria
{: #vc_nsx-t_orderinginstance-primary-secondary}

Seleccione si desea solicitar una nueva instancia primaria o una instancia secundaria para una instancia primaria existente.

## Valores de licencia
{: #vc_nsx-t_orderinginstance-licensing-settings}

Especifique las opciones de licencia para los siguientes componentes de VMware de la instancia:
* vCenter Server 6.5
* vSphere Enterprise Plus 6.7
* NSX-T 2.4 (edición Base, Advanced o Enterprise)

Para los usuarios de Business Partners, se incluyen y se adquieren en su nombre la licencia de vCenter Server (edición Standard), la licencia de vSphere (edición Enterprise Plus) y la licencia de NSX. Sin embargo, debe especificar la edición para la licencia de NSX.

Para usuarios que no son Business Partner, puede utilizar las licencias de VMware que proporciona IBM para estos componentes seleccionando **Incluir con la compra** o puede traer su propia licencia (BYOL) seleccionando **Proporcionaré** e indicando sus propias claves de licencia.

### Notas de licencia
{: #vc_nsx-t_orderinginstance-licensing-notes}

* Se necesita una licencia con un mínimo de ocho CPU, lo que equivale a cuatro servidores con dos CPU por servidor. La opción de licencia de cada componente de VMware se aplica a la instancia básica y a cualquier servidor ESXi que añada a la instancia posteriormente. Asegúrese de que su licencia da soporte a la expansión de capacidad futura en su infraestructura.
* Las ediciones de licencia mínimas se indican en la interfaz de usuario. Si se da soporte a distintas ediciones de componentes, puede seleccionar la edición que desee. El usuario es el responsable de asegurar que la clave de licencia proporcionada es correcta para cada componente de VMware seleccionado.
* Para vSphere, se incurre en un cargo de licencia en el momento de realizar el pedido, pero el cargo por licencia se abonará entonces a su cuenta.
* Puede cambiar cualquier licencia que haya suministrado mediante el cliente web de VMware vSphere una vez finalizado el despliegue de la instancia.
* El soporte para los componentes de VMware para los que suministre licencias lo ofrece VMware, no el equipo de soporte de IBM.

## Valores de Servidor nativo
{: #vc_nsx-t_orderinginstance-bare-metal-settings}

Los valores del servidor nativo dependen del centro de datos seleccionado y de la configuración del servidor nativo.

### Ubicación del centro de datos
{: #vc_nsx-t_orderinginstance-dc-location}

Seleccione el {{site.data.keyword.CloudDataCent_notm}} en el que se alojará la instancia.

### Skylake
{: #vc_nsx-t_orderinginstance-skylake}

Si selecciona **Skylake**, puede elegir la combinación de CPU y RAM del servidor nativo que se ajuste a sus necesidades.

Tabla 2. Opciones para {{site.data.keyword.baremetal_short}} Skylake

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Broadwell
{: #vc_nsx-t_orderinginstance-broadwell}

Si selecciona **Broadwell**, puede elegir la combinación de CPU y RAM del servidor nativo que se ajuste a sus necesidades.

Tabla 3. Opciones para {{site.data.keyword.baremetal_short}} Broadwell

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 núcleos en total, 2,0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 núcleos en total, 2,1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Número de servidores nativos
{: #vc_nsx-t_orderinginstance-bare-metal-number}

Para el clúster inicial de la instancia, puede configurar un número de servidores ESXi comprendido entre 3 y 20. Todos los servidores ESXi comparten la configuración del conjunto.

Después del despliegue inicial, puede añadir cuatro clústeres más. Si ha seleccionado la configuración **Skylake** o **Broadwell** para VMware vSAN, se necesitan 4 servidores ESXi para el clúster inicial y para los posteriores al despliegue. Para obtener más información sobre el número mínimo de servidores ESXi, consulte [¿Está altamente disponible una instancia de vCenter Server de dos nodos?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)

## Valores de almacenamiento
{: #vc_nsx-t_orderinginstance-storage-settings}

Los valores de almacenamiento dependen de la opción que seleccione de configuración de Servidor nativo y de tipo de almacenamiento.

Para instancias desplegadas, puede añadir comparticiones de almacenamiento NFS a un clúster NFS o vSAN existente. Para obtener más información, consulte la sección *Adición de almacenamiento NFS a instancias de vCenter Server* en [Expansión y contracción de la capacidad de las instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).
{:note}

### Almacenamiento vSAN
{: #vc_nsx-t_orderinginstance-vsan-storage}

vSAN está disponible solo para la configuración de servidor nativo **Skylake** o **Broadwell**. Especifique las siguientes opciones de vSAN:
* **Tipo y tamaño de disco para discos de capacidad vSAN**: Seleccione una opción para los discos de capacidad que necesite.
* **Número de discos de capacidad de vSAN**: Especifique el número de discos de capacidad que desea añadir.
* Si desea añadir discos de capacidad por encima del límite de ocho, marque el recuadro **Intel Optane de alto rendimiento**. Esta opción proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad y es útil para cargas de trabajo que requieren menos latencia y un rendimiento de IOPS más alto.

  La opción **Intel Optane de alto rendimiento** solo está disponible para los modelos de CPU de Skylake Dual Intel Xeon Gold 5120 y Dual Intel Xeon Gold 6140.
  {:note}

* Revise los valores **Tipo de disco para discos de memoria caché vSAN** y **Número de discos de memoria caché de vSAN**. Estos valores dependen de si ha marcado el recuadro **Intel Optane de alto rendimiento**.
* **Licencia de vSAN**: Utilice la licencia de VMware que proporciona IBM para el componente vSAN seleccionando **Incluir con la compra**, o traiga su propia licencia (BYOL) seleccionando **Proporcionaré** e indicando su propia clave de licencia.

### Almacenamiento NFS
{: #vc_nsx-t_orderinginstance-nfs-storage}

Cuando seleccione **Almacenamiento de NFS**, puede añadir almacenamiento compartido a nivel de archivo para la instancia donde todas las comparticiones utilizan los mismos valores o pueden especificar distintos valores de configuración para cada compartición de archivos. Especifique las siguientes opciones de NFS:

El número de comparticiones de archivo debe estar comprendido entre 1 y 32.
{:note}

* **Configurar las comparticiones individualmente**: Seleccione para especificar distintos valores de configuración para cada compartición de archivos.
* **Número de comparticiones**: Cuando se utiliza el mismo valor de configuración para cada compartición de archivos, especifique el número de comparticiones de archivos para el almacenamiento compartido de NFS que desee añadir.
* **Rendimiento**: Seleccione el valor de IOPS (operaciones de entrada/salida por segundo) por GB en función de sus requisitos de carga de trabajo.
* **Tamaño (GB)**: seleccione la capacidad que se ajuste a sus requisitos de almacenamiento compartido.
* **Añadir almacenamiento compartido**: seleccione esta opción para añadir comparticiones de archivos individuales que utilicen distintos valores de configuración.

Tabla 4. Opciones de nivel de rendimiento de NFS

| Opción        | Detalles       |
  |:------------- |:------------- |
  | 0,25 IOPS/GB | Esta opción está diseñada para cargas de trabajo que no se utilizan a menudo. Estas son algunas aplicaciones de ejemplo: datos en caja fuerte, alojamiento de bases de datos grandes con datos antiguos o imágenes de disco virtual del sistema de memoria virtual como copia de seguridad. |
  | 2 IOPS/GB | Esta opción está diseñada para la mayoría de cargas de trabajo generales. Entre las aplicaciones de ejemplo se encuentran alojamiento de bases de datos pequeñas, copia de seguridad de aplicaciones web o imágenes de disco de máquina virtual para un hipervisor. |
  | 4 IOPS/GB | Esta opción está diseñada para cargas de trabajo de mayor intensidad que tienen un alto porcentaje de datos activos en un momento determinado. Las aplicaciones de ejemplo incluyen bases de datos transaccionales. |
  | 10 IOPS/GB | Esta opción está diseñada para los tipos de carga de trabajo más exigentes, como las analíticas. Las aplicaciones de ejemplo incluyen bases de datos con un gran número de transacciones y otras bases de datos sensibles al rendimiento. Este nivel de rendimiento está limitado a una capacidad máxima de 4 TB por compartición de archivo. |

## Valores de interfaz de red
{: #vc_nsx-t_orderinginstance-network-interface-settings}

Debe especificar los siguientes valores de interfaz de red cuando solicite una instancia de vCenter Server.

### Prefijo de nombre de host
{: #vc_nsx-t_orderinginstance-host-name-prefix}

El prefijo del nombre de host debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  El prefijo de nombre de host debe empezar y terminar por un carácter alfanumérico.
*  La longitud máxima del prefijo de nombre de host es de 10 caracteres.

### Etiqueta de subdominio
{: #vc_nsx-t_orderinginstance-subdomain-label}

La etiqueta de subdominio debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  La etiqueta de subdominio debe empezar por un carácter alfabético y terminar por un carácter alfanumérico.
*  La longitud máxima de la etiqueta de subdominio es de 10 caracteres.
*  La etiqueta de subdominio debe ser exclusiva dentro de su cuenta.

### Nombre de dominio
{: #vc_nsx-t_orderinginstance-domain-name}

El nombre del dominio raíz debe cumplir los siguientes requisitos:
* El nombre de dominio debe constar de dos o más series de caracteres separadas por un punto (.)
* La primera serie debe empezar por un carácter alfabético y terminar por un carácter alfanumérico.
* Todas las series, excepto la última, solo pueden contener caracteres alfanuméricos y caracteres de guión (-).
* La última serie solo puede contener caracteres alfabéticos.
* La longitud de la última serie debe estar comprendida entre 2 y 24 caracteres.

La longitud máxima del nombre de dominio completo (FQDN) para hosts y VM es de 50 caracteres. Los nombres de dominio deben cumplir con esta longitud máxima.
{:note}

### Red pública o privada
{: #vc_nsx-t_orderinginstance-public-private-network}

Los valores de habilitación de la tarjeta de interfaz de red (NIC) se basan en la selección de **Red pública y privada** o de **Solo red privada**.

### VLAN
{: #vc_nsx-t_orderinginstance-vlans}

Los valores del sistema de redes dependen de si ha seleccionado **Realizar pedido de nuevas VLAN** o **Seleccionar las VLAN existentes**.

Se necesita una VLAN pública y dos VLAN privadas para el pedido de la instancia. Las dos VLAN privadas se conectan en modalidad troncal en cada servidor nativo.

#### Realizar pedido de nuevas VLAN
{: #vc_nsx-t_orderinginstance-new-vlans}

Seleccione esta opción para solicitar una VLAN pública nueva y dos VLAN privadas nuevas.

#### Seleccionar las VLAN existentes
{: #vc_nsx-t_orderinginstance-existing-vlans}

En función del {{site.data.keyword.CloudDataCent_notm}} que haya seleccionado, puede que haya VLAN públicas y privadas existentes disponibles.

Cuando seleccione reutilizar las VLAN públicas y privadas existentes, especifique las VLAN y las subredes:
* **VLAN pública** es para acceder a la red pública.
* **VLAN privada** es para la conectividad entre los centros de datos y los servicios de {{site.data.keyword.cloud_notm}}.
* **VLAN privada secundaria** es para las características de VMware, como vSAN.
* **Subred primaria** se asigna a hosts físicos para acceder a la red pública.
* **Subred primaria privada** se asigna a hosts físicos para el tráfico de gestión.

Asegúrese de que la configuración del cortafuegos en las VLAN seleccionadas no bloquee el tráfico de datos de gestión. También asegúrese de que todas las VLAN que seleccione estén en el mismo pod. Los servidores ESXi no se pueden suministrar en VLAN en pods mixtos.
{:important}

### Configuración DNS
{: #vc_nsx-t_orderinginstance-dns-config}

Seleccione la configuración de DNS (sistema de nombres de dominio) para la instancia:

* **Una sola VSI pública de Windows para Active Directory/DNS**: Se despliega y se puede consultar una sola VSI de Microsoft Windows Server para Microsoft Active Directory (AD), que funciona como DNS para la instancia en la que se han registrado los hosts y VM. Esta opción se despliega de forma predeterminada para V1.9 e instancias posteriores.
* **Dos VM dedicadas y altamente disponibles de Windows Server en el clúster de gestión**: Se despliegan dos VM Microsoft Windows, que ayudan a mejorar la seguridad y la solidez.

Debe proporcionar dos licencias de Microsoft Windows Server 2012 R2 si configura la instancia de modo que utilice las dos VM Microsoft Windows. Utilice la licencia de Microsoft Windows Server 2012 R2 Standard Edition, o la licencia de Microsoft Windows Server 2012 R2 Datacenter Edition, o ambas.
{:important}

Cada licencia solo se puede asignar a un solo servidor físico y cubre un máximo de dos procesadores físicos. Una licencia de edición Standard puede ejecutar dos máquinas virtuales virtualizadas de Microsoft Windows por servidor de 2 procesadores. Por lo tanto, se necesitan dos licencias, ya que se despliegan dos VM Microsoft Windows en dos hosts distintos.

Tiene 30 días para activar las VM.

Para obtener más información sobre las licencias de Windows, consulte [Documentación de Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Resumen del pedido
{: #vc_nsx-t_orderinginstance-order-summary}

En función de la configuración seleccionada para la instancia, el coste estimado se genera y se muestra al instante en la sección **Resumen de pedido** en el panel derecho. Pulse **Detalles sobre precios** en la parte inferior del panel derecho para generar un documento PDF que proporcione la información estimada.

## Procedimiento para solicitar instancias de vCenter Server
{: #vc_nsx-t_orderinginstance-procedure}

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** desde el panel de navegación de la izquierda y, a continuación, pulse **vCenter Server** en la sección **Centros de datos virtuales**.
2. En la página **VMware vCenter Server on IBM Cloud**, pulse la tarjeta **vCenter Server** y pulse **Crear**.
3. En la página **vCenter Server**, escriba el nombre de la instancia.
4. Seleccione el tipo de instancia:
   * Pulse **Instancia primaria** para desplegar una sola instancia en el entorno o para desplegar la primera instancia en una topología de varios sitios.
   * Pulse **Instancia secundaria** para conectar la instancia con una instancia existente (primaria) en el entorno para conseguir alta disponibilidad y siga estos pasos:
     1. Seleccione la instancia primaria a la que desea conectar la instancia secundaria.
     2. Para las instancias primarias V2.8 o posteriores, especifique la contraseña del administrador de vCenter Server para la instancia primaria.
     3. Para las instancias primarias V2.5, 2.6 o 2.7, especifique la contraseña del administrador de PSC para la instancia primaria.
     4. Para las instancias primarias V2.4 o anteriores, verifique que el valor especificado correspondiente a la contraseña del administrador de PSC para la instancia primaria sea correcto.
6. Complete los valores de licencia de los componentes de la instancia.
   *  Para utilizar licencias proporcionadas por IBM, seleccione **Incluir con la compra** y seleccione la edición de licencia, si es necesario.
   *  Para utilizar su propia licencia, seleccione **Proporcionaré** y escriba la clave de la licencia.
7. Complete los valores del servidor nativo.
    1. Seleccione el {{site.data.keyword.CloudDataCent_notm}} que va a alojar la instancia.
    2. Seleccione la configuración de servidor nativo y especifique el modelo de CPU y el tamaño de RAM.
    3. Especifique el número de {{site.data.keyword.baremetal_short}}. Si tiene previsto utilizar vSAN como solución de almacenamiento, se necesitan un mínimo de 4 {{site.data.keyword.baremetal_short}}.  
8. Complete la configuración del almacenamiento.
  * Si selecciona **Almacenamiento vSAN**, especifique los tipos de disco para la capacidad y los discos de memoria caché, el número de discos y la edición de licencia vSAN. Si desea más almacenamiento, marque el recuadro **Intel Optane de alto rendimiento**.
  * Si selecciona **Almacenamiento NFS** y desea añadir y configurar los mismos valores para todas las comparticiones de archivos, especifique el **Número de comparticiones**, el **Rendimiento** y el **Tamaño (GB)**.
  * Si selecciona **Almacenamiento NFS** y desea añadir y configurar comparticiones de archivos individualmente, seleccione **Configurar comparticiones individualmente**. A continuación, pulse el icono **+** situado junto a la etiqueta **Añadir almacenamiento compartido** y seleccione el **Rendimiento** y el **Tamaño (GB)** de cada compartición de archivos. Debe seleccionar al menos una unidad compartida de archivo.
9. Complete los valores de interfaz de red.
   1. Especifique el prefijo de nombre de host, la etiqueta de subdominio y el nombre de dominio raíz. Para una instancia secundaria, el nombre de dominio se rellena automáticamente.
   2. Seleccione el valor de red de **Red pública y privada** o **Solo red privada**.
   3. Seleccione los valores de VLAN:
      * Si desea solicitar nuevas VLAN públicas y privadas, pulse **Realizar pedido de nuevas VLAN**.
      * Si desea reutilizar las VLAN públicas y privadas existentes cuando estén disponibles, pulse **Seleccionar las VLAN existentes** y especifique las VLAN y las subredes.
   4. Especifique la configuración de DNS.

11. En el panel **Resumen del pedido**, verifique la configuración de la instancia antes de realizar el pedido.
   1. Revise los valores de la instancia.
   2. Revise el coste estimado de la instancia. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de solicitar la instancia.
   4. Pulse **Suministro**.

## Resultados después de solicitar instancias de vCenter Server con NSX-T
{: #vc_nsx-t_orderinginstance-results}

El despliegue de la instancia comienza automáticamente. Recibirá una confirmación de que el pedido se está procesando y puede comprobar el estado del despliegue consultando los detalles de la instancia.

Cuando la instancia se haya desplegado correctamente, los componentes que se describen en [Especificaciones técnicas para las instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview-specs) se instalan en la plataforma virtual de VMware. Los servidores ESXi que ha solicitado se agrupan de forma predeterminada como **cluster1**.

Cuando la instancia esté lista para ser utilizada, el estado de la instancia pasará a ser **Listo para su uso** y recibirá una notificación por correo electrónico.

Cuando se solicita una instancia secundaria, es posible que el cliente web de VMware vSphere para la instancia primaria (enlazada a la secundaria) se rearranque cuando finalice el pedido de la instancia secundaria.

## Qué hacer a continuación
{: #vc_nsx-t_orderinginstance-next}

Puede ver y gestionar la instancia de vCenter Server con NSX-T que ha solicitado. Para obtener más información sobre la visualización de la instancia, consulte [Visualización de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances).

Solo debe gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no a través del {{site.data.keyword.slportal}} ni por ningún otro medio fuera de la consola.
Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola.
{:important}

**ATENCIÓN:** el hecho de gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} (que se instalaron en la cuenta de {{site.data.keyword.cloud_notm}} al solicitar la instancia) desde fuera de la consola de {{site.data.keyword.vmwaresolutions_short}} podría hacer que el entorno quedara inestable. Estas actividades de gestión incluyen:
*  Añadir, modificar, devolver o eliminar componentes
*  Ampliar o reducir la capacidad de la instancia mediante la adición o eliminación de servidores ESXi
*  Apagar componentes
*  Rearrancar servicios

   Las excepciones a estas actividades incluyen la gestión de comparticiones del archivo de almacenamiento compartido desde el {{site.data.keyword.slportal}}. Estas actividades incluyen: solicitar, suprimir (lo que puede afectar los almacenes de datos si están montados), autorizar y montar comparticiones del archivo de almacenamiento compartido.

## Enlaces relacionados
{: #vc_nsx-t_orderinginstance-related}

* [Registro de una cuenta de {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [Visualización de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Configuración de varios sitios de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)
* [Adición, visualización y supresión de clústeres para instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vc_nsx-t_deletinginstance)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
* [Supresión de instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
