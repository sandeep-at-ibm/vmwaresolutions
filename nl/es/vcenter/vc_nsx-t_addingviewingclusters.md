---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Adición, visualización y supresión de clústeres para instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingviewingcluster}

Los servidores ESXi que ha configurado al solicitar una instancia se agrupan como **cluster1** de forma predeterminada.

Puede añadir sus propios clústeres a las instancias de VMware vCenter Server con NSX-T para ampliar la capacidad de cálculo y de almacenamiento. Dentro de un clúster, puede gestionar los servidores ESXi para mejorar la asignación de recursos y la alta disponibilidad. Cuando ya no sea necesario, suprima los clústeres añadidos de las instancias.

## Adición de clústeres a instancias de vCenter Server
{: #vc_nsx-t_addingviewingclusters-adding}

El número de clústeres, hosts y máquinas virtuales (VM) determina el límite máximo para el número de clústeres que puede añadir. Debe respetar las directrices de dimensionamiento de VMware y los límites para el despliegue.

Para obtener más información sobre los límites máximos, consulte [Máximos de configuración de VMware](https://configmax.vmware.com/home){:new_window}.

### Valores del sistema
{: #vc_nsx-t_addingviewingclusters-adding-sys-settings}

Cuando añada un clúster a una instancia de vCenter Server con NSX-T, debe especificar los valores siguientes.

#### Nombre de clúster
{: #vc_nsx-t_addingviewingclusters-adding-cluster-name}

El nombre del clúster debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre del clúster debe empezar y terminar por un carácter alfanumérico.
* El número máximo de caracteres es 30.
* El nombre del clúster debe ser exclusivo dentro de la instancia de vCenter Server.

#### Ubicación del centro de datos
{: #vc_nsx-t_addingviewingclusters-adding-dc-location}

La ubicación del {{site.data.keyword.CloudDataCent}} del clúster está definido en {{site.data.keyword.CloudDataCent_notm}} en la instancia de vCenter Server de forma predeterminada. Puede desplegar el clúster en un {{site.data.keyword.CloudDataCent_notm}} distinto del de la instancia desplegada, pero debe asegurarse de que la latencia de red entre los dos {{site.data.keyword.CloudDataCents_notm}} sea inferior a 150 ms. Para comprobar la latencia de red, puede utilizar una herramienta como [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/).

Si despliega el clúster en otro {{site.data.keyword.CloudDataCent_notm}} o en otro pod de la infraestructura de {{site.data.keyword.cloud_notm}}, se solicitan tres VLAN adicionales para su uso con el {{site.data.keyword.baremetal_short}} solicitado.

### Valores de Servidor nativo
{: #vc_nsx-t_addingviewingclusters-bare-metal-settings}

Puede elegir **Skylake**, **Certificado por SAP** o **Broadwell**.

#### Skylake
{: #vc_nsx-t_addingviewingclusters-adding-skylake}

Para el valor **Skylake**, dispone de varias opciones para **Modelo de CPU** y **RAM**. Las opciones disponibles pueden variar dependiendo de la versión en que se desplegó inicialmente la instancia.

Tabla 1. Opciones para {{site.data.keyword.baremetal_short}} Skylake

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Certificado por SAP
{: #vc_nsx-t_addingviewingclusters-adding-sap}

Si selecciona **Certificado por SAP**, no puede modificar los valores de CPU o RAM.

En función de sus requisitos, seleccione una configuración de servidor nativo:
* Procesador Dual Intel Xeon Gold 6140 / 36 núcleos en total, 2,3 GHz / 192 GB de RAM
* Procesador Dual Intel Xeon Gold 6140 / 36 núcleos en total, 2,3 GHz / 384 GB de RAM
* Procesador Dual Intel Xeon Gold 6140 / 36 núcleos en total, 2,3 GHz / 768 GB de RAM
* Procesador Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz / 512 GB de RAM
* Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,2 GHz / 1024 GB de RAM
* Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,2 GHz / 2048 GB de RAM
* Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,2 GHz / 4096 GB de RAM

#### Broadwell
{: #vc_nsx-t_addingviewingclusters-adding-broadwell}

Para el valor **Broadwell**, dispone de varias opciones para **Modelo de CPU** y **RAM**. Las opciones disponibles pueden variar dependiendo de la versión en que se desplegó inicialmente la instancia.

Tabla 2. Opciones para {{site.data.keyword.baremetal_short}} Broadwell

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 núcleos en total, 1,9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 núcleos en total, 2,2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

#### Número de servidores nativos
{: #vc_nsx-t_addingviewingclusters-adding-bare-metal-number}

Los clústeres necesitan al menos tres {{site.data.keyword.baremetal_short}}.

Puede añadir un máximo de 59 {{site.data.keyword.baremetal_short}} para un clúster. Puede añadir entre 1 y 59 servidores ESXi a la vez.

Después del despliegue, puede crear un máximo de cuatro clústeres más. Si selecciona la configuración de servidor nativo **Skylake** o **Broadwell** con el almacenamiento VMware vSAN, se necesitan cuatro servidores para el clúster inicial y los clústeres posteriores al despliegue.

### Valores de almacenamiento
{: #vc_nsx-t_addingviewingclusters-adding-storage-settings}

Los valores de almacenamiento dependen de la opción que seleccione de configuración de Servidor nativo y de tipo de almacenamiento.

#### Almacenamiento vSAN
{: #vc_nsx-t_addingviewingclusters-adding-vsan-storage}

Especifique las siguientes opciones de vSAN:
* **Tipo y tamaño de disco para discos de capacidad vSAN**: Seleccione una opción para los discos de capacidad que necesite.
* **Número de discos de capacidad de vSAN**: Especifique el número de discos de capacidad que desea añadir.
* Si desea añadir discos de capacidad por encima del límite de ocho, marque el recuadro **Intel Optane de alto rendimiento**. Esta opción proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad y es útil para cargas de trabajo que requieren menos latencia y un rendimiento de IOPS más alto.

  La opción **Intel Optane de alto rendimiento** solo está disponible para los modelos de CPU de Skylake Dual Intel Xeon Gold 5120 y Dual Intel Xeon Gold 6140.
  {:note}

* Revise los valores **Tipo de disco para discos de memoria caché vSAN** y **Número de discos de memoria caché de vSAN**. Estos valores dependen de si ha marcado el recuadro **Intel Optane de alto rendimiento**.
* **Licencia de vSAN**: Utilice la licencia de VMware que proporciona IBM para el componente vSAN seleccionando **Incluir con la compra**, o traiga su propia licencia (BYOL) seleccionando **Proporcionaré** e indicando su propia clave de licencia.

Si el clúster inicial era un clúster vSAN, los clústeres vSAN adicionales utilizan la misma licencia de vSAN y tienen la misma configuración que el inicial. Esto también se aplica si se ha elegido que se despliegue vSAN en cualquier clúster de la instancia (inicial o adicional). La primera vez se le solicitará la licencia de vSAN (BYOL o adquirida) y la edición. La próxima vez que seleccione vSAN para un nuevo clúster, la licencia que se seleccione inicialmente se reutilizará.

#### Almacenamiento NFS
{: #vc_nsx-t_addingviewingclusters-adding-nfs-storage}

Cuando seleccione **Almacenamiento de NFS**, puede añadir almacenamiento compartido a nivel de archivo para la instancia donde todas las comparticiones utilizan los mismos valores o pueden especificar distintos valores de configuración para cada compartición de archivos. Especifique las siguientes opciones de NFS:

El número de comparticiones de archivo debe estar comprendido entre 1 y 32.
{:note}

* **Configurar las comparticiones individualmente**: Seleccione para especificar distintos valores de configuración para cada compartición de archivos.
* **Número de comparticiones**: Cuando desee utilizar el mismo valor de configuración para cada compartición de archivos, especifique el número de comparticiones de archivos para el almacenamiento compartido de NFS que desee añadir.
* **Almacenamiento**: seleccione la capacidad que se ajuste a sus requisitos de almacenamiento compartido.
* **Rendimiento**: Seleccione el valor de IOPS (operaciones de entrada/salida por segundo) por GB en función de sus requisitos de carga de trabajo.
* **AÑADIR NFS**: Seleccione esta opción para añadir comparticiones de archivos individuales con distintos valores de configuración.

Tabla 3. Opciones de nivel de rendimiento de NFS

| Opción        | Detalles       |
  |:------------- |:------------- |
  | 0,25 IOPS/GB | Esta opción está diseñada para cargas de trabajo que no se utilizan a menudo. Estas son algunas aplicaciones de ejemplo: datos en caja fuerte, alojamiento de bases de datos grandes con datos antiguos o imágenes de disco virtual del sistema de memoria virtual como copia de seguridad. |
  | 2 IOPS/GB | Esta opción está diseñada para la mayoría de cargas de trabajo generales. Entre las aplicaciones de ejemplo se encuentran alojamiento de bases de datos pequeñas, copia de seguridad de aplicaciones web o imágenes de disco de máquina virtual (VM) para un hipervisor. |
  | 4 IOPS/GB | Esta opción está diseñada para cargas de trabajo de mayor intensidad que tienen un alto porcentaje de datos activos en un momento determinado. Las aplicaciones de ejemplo incluyen bases de datos transaccionales. |
  | 10 IOPS/GB | Esta opción está diseñada para los tipos de carga de trabajo más exigentes, como las analíticas. Las aplicaciones de ejemplo incluyen bases de datos con un gran número de transacciones y otras bases de datos sensibles al rendimiento. Este nivel de rendimiento está limitado a una capacidad máxima de 4 TB por compartición de archivo. |

### Discos locales
{: #vc_nsx-t_addingviewingclusters-adding-local-disks}

La opción de discos locales solo está disponible para la configuración de tipo procesador nativo Quad Intel Xeon E7-8890 v4 **certificado por SAP**. Especifique las siguientes opciones:
* **Recuento de discos**: seleccione el número de discos que desea añadir.
* **Tipo de disco**: seleccione una opción para el tipo de disco que necesita.

### Valores de licencia
{: #vc_nsx-t_addingviewingclusters-adding-licensing-settings}

Especifique la opción de licencia para el componente VMware vSphere en el clúster:
* Para los usuarios de Business Partners, se incluye y se adquiere en su nombre la licencia de vSphere (edición Enterprise Plus).
* Para usuarios que no son Business Partners, puede utilizar las licencias de VMware que proporciona IBM para este componente seleccionando **Incluir con la compra** o puede traer su propia licencia (BYOL) seleccionando **Proporcionaré** e indicando su propia clave de licencia.

### Valores de interfaz de red
{: #vc_nsx-t_addingviewingclusters-adding-network-interface-settings}

Los valores de habilitación de la tarjeta de interfaz de red (NIC) se basan en la selección de **Red pública y privada** o de **Solo red privada**.rd.cloud_notm}}

### Resumen del pedido
{: #vc_nsx-t_addingviewingclusters-adding-order-summary}

En función de la configuración seleccionada para el clúster, el coste estimado se genera y se muestra al instante en el panel derecho **Resumen de pedido**.

## Procedimiento para añadir clústeres a instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingviewingclusters-adding-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia a la que desea añadir clústeres.

   Asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede añadir clústeres a la instancia.
   {:note}
3. Pulse **Infraestructura** en el panel de navegación izquierdo y pulse **Añadir** en la esquina superior derecha de la tabla **CLÚSTERES**.
4. En la página **Añadir clúster**, escriba el nombre de clúster.
5. Si desea alojar el clúster en un {{site.data.keyword.CloudDataCent_notm}} diferente al que se aloja la instancia, en **Servidor nativo**, marque el recuadro de selección **Seleccione otra ubicación** y elija el {{site.data.keyword.CloudDataCent_notm}} para alojar la instancia.
6. Complete la configuración del servidor nativo.
   * Si ha seleccionado **Skylake** o **Broadwell**, especifique el valor de **Modelo de CPU**, la cantidad de **RAM** y el valor de **Número de {{site.data.keyword.baremetal_short}}**.
   * Si ha seleccionado **Certificado por SAP**, especifique el modelo de CPU.
7. Complete la configuración del almacenamiento.
  * Si selecciona **Almacenamiento vSAN**, especifique los tipos de disco para la capacidad y los discos de memoria caché, el número de discos y la edición de licencia vSAN. Si desea más almacenamiento, marque el recuadro **Intel Optane de alto rendimiento**.
  * Si selecciona **Almacenamiento NFS** y desea añadir y configurar los mismos valores para todas las comparticiones de archivos, especifique el **Número de comparticiones**, el **Rendimiento** y el **Tamaño (GB)**.
  * Si selecciona **Almacenamiento NFS** y desea añadir y configurar comparticiones de archivos individualmente, seleccione **Configurar comparticiones individualmente**. A continuación, pulse el icono **+** situado junto a la etiqueta **Añadir almacenamiento compartido** y seleccione el **Rendimiento** y el **Tamaño (GB)** de cada compartición de archivos. Debe seleccionar al menos una unidad compartida de archivo.
  * Si selecciona **Discos locales**, especifique el recuento de discos y el tipo de disco.
8. Complete los valores de interfaz de red.
8. Especifique cómo se proporciona la clave de licencia de vSphere:
  * Para los usuarios de Business Partners, se incluye y se adquiere en su nombre la licencia de vSphere (edición Enterprise Plus).
  * Para los usuarios que no son Business Partners, puede seleccionar una de las opciones siguientes:
      * Si desea que se adquieran nuevas licencias en su nombre, seleccione **Incluir con la compra** para el componente.
      * Si desea utilizar su propia licencia de VMware para el componente, seleccione **Proporcionaré** y especifique la clave de licencia.
9. Seleccione el valor de red de **Red pública y privada** o **Solo red privada**.
10. En el panel **Resumen del pedido**, verifique la configuración del clúster antes de añadir el clúster.
   1. Revise los valores para el clúster.
   2. Revise el coste estimado del clúster. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de añadir el clúster.
   4. Pulse **Suministro**.

### Resultados después de añadir clústeres a instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingviewingclusters-adding-results}

1. El despliegue del clúster se inicia automáticamente y el estado del clúster pasa a ser **Inicializando**. Puede comprobar el estado del despliegue viendo el historial de despliegue desde la página **Resumen** de la instancia.
2. Cuando el clúster esté listo para ser utilizado, su estado pasará a ser **Listo para su uso**. El clúster recién añadido está habilitado con alta disponibilidad (HA) de vSphere y con el planificador de recursos distribuidos (DRS) de vSphere.

No puede cambiar el nombre de clúster. Si se cambia el nombre del clúster, es posible que las operaciones de adición o eliminación de servidores ESXi en el clúster fallen.
{:important}

## Procedimiento para visualizar clústeres a instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingviewingclusters-viewing-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse una instancia para ver los clústeres que contiene.
3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, vea el resumen sobre los clústeres:
  * **Nombre**: el nombre del clúster.
  * **Servidores ESXi**: el número de servidores ESXi del clúster.
  * **CPU**: la especificación de CPU de los servidores ESXi del clúster.
  * **Discos vSAN personalizados**: el número de discos vSAN del clúster, incluido el tipo y la capacidad del disco.
  * **Memoria**: el tamaño total de la memoria de los servidores ESXi del clúster.
  * **Ubicación del centro de datos**: el {{site.data.keyword.CloudDataCent_notm}} en el que está alojado el clúster.
  * **Pod**: el pod en el que se ha desplegado el clúster.
  * **Estado**: el estado del clúster. El estado puede tener uno de los valores siguientes:
    <dl class="dl">
        <dt class="dt dlterm">Inicializando</dt>
        <dd class="dd">El clúster se está creando y configurando.</dd>
        <dt class="dt dlterm">Modificando</dt>
        <dd class="dd">El clúster se está modificando.</dd>
        <dt class="dt dlterm">Listo para su uso</dt>
        <dd class="dd">El clúster está listo para ser utilizado.</dd>
        <dt class="dt dlterm">Suprimiendo</dt>
        <dd class="dd">El clúster se está suprimiendo.</dd>
        <dt class="dt dlterm">Suprimido</dt>
        <dd class="dd">El clúster se ha suprimido.</dd>
    </dl>
  * **Acciones**: Pulse el icono **Suprimir** para suprimir el clúster.
4. Pulse un nombre de clúster para ver los detalles del servidor ESXi, almacenamiento e interfaz de red:

Tabla 4. Detalles del servidor ESXi

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | El nombre del servidor ESXi está en el formato siguiente:<br> `<host_prefix><n>.<subdomain_label>.<root_domain>` <br> donde:<br> `host_prefix` es el prefijo del nombre de host<br> `n` es la secuencia del servidor<br> `subdomain_label` es la etiqueta de subdominio<br> `root_domain` es el nombre de dominio raíz |
| Versión | La versión del servidor ESXi. |
| Credenciales | El nombre de usuario y la contraseña para acceder al servidor ESXi. |
| IP privada | La dirección IP privada del servidor ESXi. |
| Estado | El estado del servidor ESXi, que puede tener uno de estos valores:<br> **Añadido** El servidor ESXi se ha añadido y está listo para ser utilizado.<br> **Añadiendo** El servidor ESXi se está añadiendo.<br> **Suprimiendo** El servidor ESXi se está suprimiendo. |

Tabla 5. Detalles de almacenamiento

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | El nombre de almacén de datos. |
| Tamaño | La capacidad de almacenamiento. |
| IOPS/GB | El nivel de rendimiento del almacenamiento. |
| Protocolo NFS | La versión NFS del almacenamiento. |

## Supresión de clústeres de instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingviewingclusters-deleting}

Puede que desee suprimir un clúster de una instancia cuando ya no sea necesario.

### Antes de suprimir
{: #vc_nsx-t_addingviewingclusters-deleting-prereq}

* Puede suprimir un único clúster al mismo tiempo. Para suprimir más de un clúster, debe hacerlo en secuencia. Espere a que el clúster anterior se suprima antes de suprimir el clúster siguiente.
* Asegúrese de que todos los nodos de un clúster estén encendidos y operativos antes de suprimir el clúster.
* Cuando se suprime un clúster, todas las VM del clúster también se suprimen y no se pueden recuperar. Si desea mantener las VM, mígrelas a otros clústeres.
* El clúster predeterminado no se puede suprimir.

### Procedimiento para suprimir clústeres de instancias de vCenter Server con NSX-T
{: #vc_nsx-t_addingviewingclusters-deleting-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia de la que desea suprimir clústeres.

   Asegúrese de que la instancia está en el estado **Listo para su uso**. De lo contrario, no puede suprimir clústeres de la instancia.
   {:note}

3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, localice el clúster que desea suprimir y pulse el icono **Suprimir** en la columna **Acciones**.
4. Confirme que ha completado la migración de las VM a otros clústeres, si es necesario, y que desea suprimir el clúster.

## Enlaces relacionados
{: #vc_nsx-t_addingviewingclusters-related}

* [Visualización de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
