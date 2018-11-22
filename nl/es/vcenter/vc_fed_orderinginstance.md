---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de instancias de VMware Federal

Para desplegar una plataforma virtualizada de VMware flexible y personalizable que se ajuste mejor a sus necesidades de carga de trabajo, solicite una instancia de VMware Federal. Las instancias de VMware Federal le ayudan a desconectar la conexión de gestión abierta y a proteger su instancia desplegada.

En la actualidad, solo las instancias de vCenter Server dan soporte a VMware Federal en {{site.data.keyword.cloud}}.
{:note}

## Requisitos para solicitar instancias de VMware Federal

Asegúrese de haber realizado las tareas siguientes:
* Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Gestión de cuentas y valores de usuario](../vmonic/useraccount.html).
* Ha revisado la información de [Requisitos y planificación de instancias de VMware Federal](vc_fed_planning.html).
* Ha revisado el formato del nombre de dominio e instancia. El nombre de dominio y la etiqueta de subdominio se utilizan para generar el nombre de usuario y los nombres de servidor de la instancia.

Tabla 1. Formato del valor de nombres de instancia y de dominio

| Nombre        | Formato del valor      |
  |:------------- |:------------- |
  | Nombre de dominio | `<root_domain>` |  
  | Nombre usuario inicio sesión vCenter Server | `<user_id>@<root_domain>` (usuario de Microsoft Active Directory) o `administrator@vsphere.local` |
  | FQDN de vCenter Server | `vcenter.<subdomain_label>.<root_domain>`. La longitud máxima es de 50 caracteres. |
  | Nombre sitio inicio sesión único (SSO) | `<subdomain_label>` |
  | Nombre completo de servidor ESXi | `<host_prefix><n>.<subdomain_label>.<root_domain>`, donde `<n>` es la secuencia del servidor ESXi. La longitud máxima es de 50 caracteres. |  
  | PSC FQDN | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. La longitud máxima es de 50 caracteres. |

No modifique ningún valor definido durante la solicitud o el despliegue de la instancia. Hacerlo puede hacer que la instancia se vuelva inutilizable. Por ejemplo, si se cierra la red pública, si los servidores y las Instancias de servidor virtual (VSI) se mueven detrás de una media disposición de Vyatta, o si el VSI de IBM CloudBuilder se detiene o se suprime.
{:important}

## Valores del sistema

Debe especificar los valores del sistema siguientes cuando solicite una instancia de VMware Federal.

### Nombre de instancia

El nombre de instancia debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre de instancia debe empezar y terminar por un carácter alfanumérico.
* La longitud máxima del nombre de instancia es de 10 caracteres.
* El nombre de instancia debe ser exclusivo dentro de su cuenta.

### Primaria o secundaria

Solicite una nueva instancia primaria. El despliegue de una instancia secundaria para alta disponibilidad no está soportado actualmente.

## Valores de licencia

Licencias proporcionadas por IBM para los siguientes componentes de VMware:

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5u1
* NSX Service Providers 6.4 (edición Base, Advanced o Enterprise)
* (Para clústeres vSAN) vSAN 6.6 (edición Advanced o Enterprise)

**Atención:**

* Las ediciones de licencia mínimas se indican en la interfaz de usuario. Si se da soporte a distintas ediciones de componentes, puede seleccionar la edición que desee. El usuario es el responsable de asegurar que la clave de licencia proporcionada es correcta para cada componente de VMware seleccionado.
* Para vSphere, se incurrirá en un cargo de licencia en el momento de realizar el pedido, pero posteriormente el cargo por licencia se abonará a su cuenta.

## Valores de Servidor nativo

Los valores del servidor nativo dependen del centro de datos seleccionado y de la configuración del servidor nativo.

### Ubicación del centro de datos

Seleccione el {{site.data.keyword.CloudDataCent_notm}} en el que se alojará la instancia.

### Skylake

Especifique el modelo de CPU y la RAM del servidor nativo.

Tabla 2. Opciones para {{site.data.keyword.baremetal_short}} Skylake

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Broadwell

Especifique el modelo de CPU y la RAM del servidor nativo.

Tabla 3. Opciones para {{site.data.keyword.baremetal_short}} Broadwell

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB |

### Número de servidores nativos

Puede configurar un número de servidores ESXi comprendido entre 2 y 20.

Todos los servidores ESXi comparten la misma configuración. Después del despliegue, puede añadir cuatro clústeres más. Para los valores de almacenamiento vSAN, se necesitan 4 servidores ESXi para el clúster inicial y para los posteriores al despliegue. Para obtener más información sobre el número mínimo de servidores ESXi, consulte [¿Está altamente disponible una instancia de vCenter Server de dos nodos?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Valores de almacenamiento

Los valores de almacenamiento dependen de la opción que seleccione de configuración de Servidor nativo y de tipo de almacenamiento.

### Almacenamiento vSAN

Especifique las siguientes opciones de vSAN:
* **Tipo y tamaño de disco para discos de capacidad vSAN**: Seleccione una opción para los discos de capacidad que necesite.
* **Número de discos de capacidad de vSAN**: Especifique el número de discos de capacidad que desea añadir.
* Si desea añadir discos de capacidad por encima del límite de ocho, marque el recuadro **Intel Optane de alto rendimiento**. Esta opción proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad y es útil para cargas de trabajo que requieren menos latencia y un rendimiento de IOPS más alto. La opción **Intel Optane de alto rendimiento** solo está disponible para los procesadores Dual Intel Xeon Gold 5120 y 6140.
* Revise los valores **Tipo de disco para discos de memoria caché vSAN** y **Número de discos de memoria caché de vSAN**. Estos valores dependen de si ha marcado el recuadro **Intel Optane de alto rendimiento**.
* **Licencia de vSAN**: Seleccione la edición de licencia de vSAN 6.6 (Advanced o Enterprise).

### Almacenamiento NFS

Cuando seleccione **Almacenamiento de NFS**, puede añadir almacenamiento compartido a nivel de archivo para la instancia donde todas las comparticiones utilizan los mismos valores o pueden especificar distintos valores de configuración para cada compartición de archivos. Especifique las siguientes opciones de NFS:

El número de comparticiones de archivo debe estar comprendido entre 1 y 32.
{:note}

* **Configurar las comparticiones individualmente**: Seleccione para especificar distintos valores de configuración para cada compartición de archivos.
* **Número de unidades compartidas**: Al utilizar el mismo valor de configuración para cada compartición de archivos, especifique el número de comparticiones de archivos para el almacenamiento compartido de NFS que desee añadir.
* **Almacenamiento**: seleccione la capacidad que se ajuste a sus requisitos de almacenamiento compartido.
* **Rendimiento**: seleccione el valor de IOPS (operaciones de entrada/salida por segundo) por GB en función de sus requisitos de carga de trabajo.
* **AÑADIR NFS**: Seleccione para añadir comparticiones de archivos individuales que utilicen distintos valores de configuración.

Tabla 3. Opciones de nivel de rendimiento de NFS

| Opción        | Detalles       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Esta opción está diseñada para la mayoría de cargas de trabajo generales. Entre las aplicaciones de ejemplo se encuentran alojamiento de bases de datos pequeñas, copia de seguridad de aplicaciones web o imágenes de disco de máquina virtual para un hipervisor. |
  | 4 IOPS/GB | Esta opción está diseñada para cargas de trabajo de mayor intensidad que tienen un alto porcentaje de datos activos en un momento determinado. Las aplicaciones de ejemplo incluyen bases de datos transaccionales. |
  | 10 IOPS/GB | Esta opción está diseñada para los tipos de carga de trabajo más exigentes, como las analíticas. Las aplicaciones de ejemplo incluyen bases de datos con un gran número de transacciones y otras bases de datos sensibles al rendimiento. Este nivel de rendimiento está limitado a una capacidad máxima de 4 TB por compartición de archivo. |

## Valores de interfaz de red

### Prefijo de nombre de host

El prefijo del nombre de host debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  El prefijo de nombre de host debe empezar y terminar por un carácter alfanumérico.
*  La longitud máxima del prefijo de nombre de host es de 10 caracteres.

### Etiqueta de subdominio

La etiqueta de subdominio debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  La etiqueta de subdominio debe empezar y terminar por un carácter alfanumérico.
*  La longitud máxima de la etiqueta de subdominio es de 10 caracteres.
*  La etiqueta de subdominio debe ser exclusiva dentro de su cuenta.

### Nombre de dominio

El nombre del dominio raíz debe cumplir los siguientes requisitos:
* El nombre de dominio debe constar de dos o más series de caracteres separadas por un punto (.)
* La primera serie debe comenzar por un carácter alfabético y terminar por un carácter alfanumérico.
* Todas las series, excepto la última, solo pueden contener caracteres alfanuméricos y caracteres de guión (-).
* La última serie solo puede contener caracteres alfabéticos.
* La longitud de la última serie debe estar comprendida entre 2 y 24 caracteres.

La longitud máxima del nombre de dominio completo (FQDN) para hosts y VM es de 50 caracteres. Los nombres de dominio deben cumplir con esta longitud máxima.
{:note}

### Configuración DNS

Seleccione la configuración de DNS (sistema de nombres de dominio) para la instancia:

* **Una sola VSI pública de Windows para Active Directory/DNS**: se despliega y se puede consultar una sola VSI de Microsoft Windows Server para Microsoft Active Directory (AD), que funciona como DNS para la instancia en la que se han registrado los hosts y máquinas virtuales.
* **Dos VM dedicadas y altamente disponibles de Windows Server en el clúster de gestión**: Para V2.3 y futuros releases, se despliegan dos máquinas virtuales Microsoft Windows, lo que ayuda a mejorar la seguridad y la solidez.

Debe proporcionar dos licencias de Microsoft Windows Server 2012 R2 si configura la instancia de modo que utilice las dos máquinas virtuales Microsoft Windows. Utilice la licencia de edición Microsoft Windows Server 2012 R2 Standard o la licencia de edición Microsoft Windows Server 2012 R2 Datacenter, o ambas.
{:important}

Actualmente, cada licencia se puede asignar a un solo servidor físico y cubre hasta dos procesadores físicos. Al utilizar una licencia de edición Standard, puede ejecutar dos máquinas virtuales Microsoft Windows virtualizadas por servidor de 2 procesadores. Por lo tanto, se necesitan dos licencias, ya que se despliegan dos máquinas virtuales Microsoft Windows en dos hosts distintos.

Tiene 30 días para activar las máquinas virtuales.

Para obtener más información sobre cómo solicitar licencias de Windows, consulte [Documentación de Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Resumen del pedido

En función de la configuración seleccionada para la instancia, el coste estimado se genera y se muestra al instante en la sección **Resumen de pedido** en el panel derecho. Pulse **Detalles sobre precios** en la parte inferior del panel derecho para generar un documento PDF que proporcione la información estimada.

## Procedimiento para solicitar instancias de VMware Federal

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** desde el panel de navegación de la izquierda y, a continuación, pulse **vCenter Server** en la sección **Centros de datos virtuales**.
2. En la página **VMware vCenter Server on IBM Cloud**, pulse la tarjeta **vCenter Server** y pulse **Crear**.
3. En la página **vCenter Server**, escriba el nombre de la instancia.
4. Pulse **Instancia primaria** para desplegar una sola instancia en el entorno.
5. Especifique la edición de licencia de VMware NSX.
6. Complete la configuración del servidor nativo:
   1. Seleccione el {{site.data.keyword.CloudDataCent_notm}} que va a alojar la instancia.
   2. Seleccione el modelo de CPU y la cantidad de **RAM** de **Skylake** o **Broadwell**.
7. Complete la configuración del almacenamiento.
   * Si selecciona **Almacenamiento vSAN**, especifique los tipos de disco para la capacidad y los discos de memoria caché, el número de discos y la edición de licencia vSAN. Si desea más almacenamiento, marque el recuadro **Intel Optane de alto rendimiento**.
   * Si selecciona **Almacenamiento NFS** y desea añadir y configurar los mismos valores para todas las comparticiones de archivos, especifique el **Número de comparticiones**, **Tamaño** y **Rendimiento**.
   * Si selecciona **Almacenamiento NFS** y desea añadir y configurar comparticiones de archivos individualmente, seleccione **Configurar comparticiones individualmente** y, a continuación, pulse el icono **+** junto a la etiqueta **Añadir NFS** y seleccione el **Tamaño** y el **Rendimiento** para cada compartición de archivos individual. Debe seleccionar al menos una unidad compartida de archivo.
8. Complete la configuración de interfaz de red.
   1. Especifique el prefijo de nombre de host, la etiqueta de subdominio y el nombre de dominio raíz.
   2. Seleccione la configuración de DNS.
9. En el panel **Resumen del pedido**, verifique la configuración de la instancia antes de realizar el pedido.
   1. Revise los valores de la instancia.
   2. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de solicitar la instancia.
   3. Para revisar el coste estimado de los servicios, pulse el enlace de coste que hay bajo **Calcular coste**. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   4. Pulse **Suministro**.

## Resultados

El despliegue de la instancia comienza automáticamente. Recibirá una confirmación de que el pedido se está procesando y puede comprobar el estado del despliegue consultando los detalles de la instancia.

Cuando la instancia se haya desplegado correctamente, los componentes que se describen en [Especificaciones técnicas para las instancias de VMware Federal en {{site.data.keyword.cloud_notm}}](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances) se instalan en la plataforma virtual de VMware. Los servidores ESXi que ha solicitado se agrupan de forma predeterminada como **cluster1**.

Cuando la instancia esté lista para ser utilizada, el estado de la instancia pasará a ser **Listo para su uso** y recibirá una notificación por correo electrónico.

## Qué hacer a continuación

Vea, gestione o proteja la instancia de VMware Federal que ha solicitado.

Solo debe gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no a través del {{site.data.keyword.slportal}} ni por ningún otro medio fuera de la consola.
Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola.
{:important}

**ATENCIÓN:** el hecho de gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} (que se instalaron en la cuenta de {{site.data.keyword.cloud_notm}} al solicitar la instancia) desde fuera de la consola de {{site.data.keyword.vmwaresolutions_short}} podría hacer que el entorno quedara inestable. Estas actividades de gestión incluyen:
*  Añadir, modificar, devolver o eliminar componentes
*  Ampliar o reducir la capacidad de la instancia mediante la adición o eliminación de servidores ESXi
*  Apagar componentes

   Las excepciones a estas actividades incluyen la gestión de comparticiones del archivo de almacenamiento compartido desde el {{site.data.keyword.slportal}}. Estas actividades incluyen: solicitar, suprimir (lo que puede afectar los almacenes de datos si están montados), autorizar y montar comparticiones del archivo de almacenamiento compartido.

### Enlaces relacionados

* [Registro de una cuenta de {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Visualización de instancias de VMware Federal](vc_fed_viewinginstance.html)
* [Ampliación y reducción de la capacidad para instancias de VMware Federal](vc_fed_addingremovingservers.html)
* [Adición, visualización y supresión de clústeres para instancias de VMware Federal](fed_addviewdeleteclusters.html)
* [Protección de instancias de VMware Federal](vc_fed_securinginstance.html)
* [Supresión de instancias de VMware Federal](vc_fed_deletinginstance.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
