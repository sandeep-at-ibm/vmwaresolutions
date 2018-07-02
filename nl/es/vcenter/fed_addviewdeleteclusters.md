---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-12"

---

# Adición, visualización y supresión de clústeres para instancias de VMware Federal

Los servidores ESXi que ha configurado al solicitar una instancia se agrupan como **cluster1** de forma predeterminada.

Puede añadir clústeres a las instancias de VMware Federal para ampliar la capacidad de cálculo y de almacenamiento. Dentro de un clúster, puede gestionar los servidores ESXi para mejorar la asignación de recursos y la alta disponibilidad. Cuando ya no sea necesario, puede suprimir los clústeres añadidos de las instancias.

**Disponibilidad**: La característica de adición y de supresión de clústeres solo está disponible para las instancias que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos.

## Adición de clústeres a instancias de VMware Federal

Puede añadir hasta 10 clústeres a una instancia. Cuando añada un clúster a una instancia de VMware Federal, debe especificar los valores siguientes.

### Valores del sistema

Cuando añada un clúster a una instancia de VMware Federal, debe especificar los valores siguientes.

#### Nombre de clúster

El nombre del clúster debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre del clúster debe empezar y terminar por un carácter alfanumérico.
* La longitud máxima del nombre del clúster es de 30 caracteres.
* El nombre del clúster debe ser exclusivo dentro de la instancia de VMware Federal.

#### Ubicación del centro de datos

El centro de datos del clúster se establece de forma predeterminada en el centro de datos de la instancia de VMware Federal.

### Valores de Servidor nativo

#### Personalizado

Especifique el modelo de CPU y la RAM del servidor nativo. Las opciones disponibles pueden variar dependiendo de la versión en que se desplegó inicialmente la instancia.

Tabla 1. Opciones para {{site.data.keyword.baremetal_short}} personalizados

| Opciones de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Número de servidores nativos

Se necesita un mínimo de 2 {{site.data.keyword.baremetal_short}} para un clúster.

Para instancias de VMware Federal desplegadas en V2.3 o posterior, puede añadir un máximo de 59 {{site.data.keyword.baremetal_short}} para un clúster y puede añadir entre 1 y 59 servidores ESXi simultáneamente.

Después del despliegue, puede crear un máximo de cuatro clústeres más. Para los valores de almacenamiento vSAN, se necesitan 4 servidores para el clúster inicial y para los clústeres posteriores al despliegue.

<!--When there are more than 51 ESXi servers in the initial cluster of an instance, the HCX on {{site.data.keyword.cloud_notm}} service cannot be installed into the instance. Because the HCX service requires 8 IPs in the vMotion subnet from the initial cluster, if the number of ESXi servers exceeds 51, no IPs in the vMotion subnet can be available for HCX service.-->

### Valores de almacenamiento

Los valores de almacenamiento dependen de si ha seleccionado almacenamiento vSAN, NFS o personalizado.

#### Almacenamiento vSAN

Para vSAN, especifique las siguientes opciones de almacenamiento:

* **Tipo y tamaño de disco para discos de capacidad vSAN**: seleccione la capacidad que se ajuste a sus requisitos de almacenamiento compartido.
* **Número de discos de capacidad vSAN**: seleccione el número de discos para el almacenamiento compartido vSAN que desea añadir. Las cantidades de disco deben ser 2, 4, 6 u 8.
* Seleccione la edición de licencia de VMware vSAN 6.6 (Advanced o Enterprise).

Si el clúster inicial era vSAN, los clústeres vSAN adicionales utilizan la misma licencia de vSAN y tienen la misma configuración que el clúster vSAN inicial. Esto también se aplica si se ha elegido que se despliegue vSAN en cualquier clúster de la instancia (inicial o adicional). La primera vez se le solicitará la licencia de vSAN y la edición. La siguiente vez que seleccione vSAN para un clúster adicional, se reutiliza el valor que haya especificado inicialmente.

#### Almacenamiento NFS

Cuando seleccione **Almacenamiento de NFS**, puede añadir almacenamiento compartido a nivel de archivo para la instancia donde todas las comparticiones utilizan los mismos valores o pueden especificar distintos valores de configuración para cada compartición de archivos. Especifique las siguientes opciones de NFS:

**Nota:** El número de comparticiones de archivo debe estar comprendido entre 1 y 32.

* **Configurar las comparticiones de archivos individualmente**: Seleccione para especificar distintos valores de configuración para cada compartición de archivos.
* **Número de unidades compartidas**: Al utilizar el mismo valor de configuración para cada compartición de archivos, especifique el número de comparticiones de archivos para el almacenamiento compartido de NFS que desee añadir.
* **Almacenamiento**: seleccione la capacidad que se ajuste a sus requisitos de almacenamiento compartido.
* **Rendimiento**: seleccione el valor de IOPS (operaciones de entrada/salida por segundo) por GB en función de sus requisitos de carga de trabajo.
* **AÑADIR NFS**: Seleccione para añadir comparticiones de archivos individuales que utilizarán distintos valores de configuración.

Tabla 2. Opciones de nivel de rendimiento de NFS

| Opción        | Detalles       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Esta opción está diseñada para la mayoría de cargas de trabajo generales. Entre las aplicaciones de ejemplo se encuentran alojamiento de bases de datos pequeñas, copia de seguridad de aplicaciones web o imágenes de disco de máquina virtual para un hipervisor. |
  | 4 IOPS/GB | Esta opción está diseñada para cargas de trabajo de mayor intensidad que tienen un alto porcentaje de datos activos en un momento determinado. Las aplicaciones de ejemplo incluyen bases de datos transaccionales. |
  | 10 IOPS/GB | Esta opción está diseñada para los tipos de carga de trabajo más exigentes, como las analíticas. Las aplicaciones de ejemplo incluyen bases de datos con un gran número de transacciones y otras bases de datos sensibles al rendimiento. Este nivel de rendimiento está limitado a una capacidad máxima de 4 TB por compartición de archivo.|

### Valores de licencia

Licencias de VMware proporcionadas por IBM para:
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Base, Advanced o Enterprise) 6.3
  * (Para clústeres vSAN) VMware vSAN Advanced o Enterprise 6.6

### Resumen del pedido

En función de la configuración seleccionada para el clúster, el coste estimado se genera y se muestra al instante en el panel derecho **Resumen de pedido**.

## Procedimiento para añadir clústeres a instancias de VMware Federal

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia a la que desea añadir clústeres.

   **Nota**: asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede añadir clústeres a la instancia.

3. Pulse **Infraestructura** en el panel de navegación izquierdo y pulse **Añadir** en la esquina superior derecha de la tabla **CLÚSTERES**.
4. En la página **Añadir clúster**, escriba el nombre de clúster.
5. Seleccione el **Modelo de CPU**, la cantidad de **RAM** y el **Número de servidores nativos** de la configuración del servidor nativo.
6. Complete la configuración del almacenamiento.
  * Si selecciona **Almacenamiento vSAN**, seleccione el **Tipo y tamaño de disco para discos de capacidad vSAN**, el **Número de discos de capacidad vSAN** y la edición de licencia de VMware vSAN.
  * Si selecciona **Almacenamiento NFS**, seleccione el **Número de unidades compartidas**, el **Tamaño** y el **Rendimiento**.
  * Para añadir y configurar las unidades compartidas de archivos individualmente, seleccione el separador **Almacenamiento NFS personalizado**, pulse el icono **+** situado junto a la etiqueta **Añadir NFS** y seleccione el **Tamaño** y el **Rendimiento** para cada compartición de archivo. Debe seleccionar al menos una unidad compartida de archivo.
7. Seleccione la edición de licencia para vSAN VMware para la configuración de licencia.
8. En el panel **Resumen del pedido**, verifique la configuración del clúster antes de añadir el clúster.
   1. Revise los valores para el clúster.
   2. Revise el coste estimado del clúster. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen de pedido, pulse el icono **Imprimir** o **Descargar** en la esquina superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de añadir el clúster.
   4. Pulse **Suministro**.

## Resultados después de añadir clústeres a instancias de VMware Federal

1. El despliegue del clúster se inicia automáticamente y el estado del clúster pasa a ser **Inicializando**. Puede comprobar el estado del despliegue consultando el historial de despliegue desde la página de resumen de la instancia.
2. Cuando el clúster esté listo para ser utilizado, su estado pasará a ser **Listo para su uso**. El clúster recién añadido está habilitado con alta disponibilidad (HA) de vSphere y con el planificador de recursos distribuidos (DRS) de vSphere.

**Importante**: no puede cambiar el nombre del clúster. Si se cambia el nombre del clúster, es posible que las operaciones de adición o eliminación de servidores ESXi en el clúster fallen.

## Visualización de clústeres en instancias de VMware Federal

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse una instancia para ver los clústeres que contiene.
3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, vea el resumen sobre los clústeres:
   * **Nombre**: el nombre del clúster.
   * **Servidores ESXi**: el número de servidores ESXi del clúster.
   * **CPU**: la especificación de CPU de los servidores ESXi del clúster.
   * **Discos vSAN personalizados**: el número de discos vSAN del clúster, incluido el tipo y la capacidad del disco.
   * **Memoria**: el tamaño total de la memoria de los servidores ESXi del clúster.
   * **Ubicación del centro de datos**: el centro de datos en el que está alojado el clúster.
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
4. Pulse un nombre de clúster para ver los detalles del servidor, almacenamiento y licencia de ESXi.

### Servidores ESXi

   * **Nombre**: el nombre del servidor ESXi está en el formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, donde:

      `host_prefix` es el prefijo del nombre de host,
       `n` es la secuencia del servidor ESXi,
       `subdomain_label` es la etiqueta del subdominio y
       `root_domain` es el nombre del dominio raíz.

   * **Versión**: la versión del servidor ESXi.
   * **Credenciales**: el nombre de usuario y la contraseña para acceder al servidor ESXi.
   * **IP privada**: la dirección IP privada del servidor ESXi.
   * **Estado**: el estado del servidor ESXi, que puede tener uno de estos valores:
        <dl class="dl">
        <dt class="dt dlterm">Añadido</dt>
        <dd class="dd">El servidor ESXi se ha añadido y está listo para ser utilizado. </dd>
        <dt class="dt dlterm">Añadiendo</dt>
        <dd class="dd">El servidor ESXi se está añadiendo. </dd>
        <dt class="dt dlterm">Suprimiendo</dt>
        <dd class="dd">El servidor ESXi se está suprimiendo.</dd>
        </dl>

### Almacenamiento

   * **Nombre**: el nombre del almacén de datos.
   * **Tamaño**: la capacidad del almacenamiento.
   * **IOPS/GB**: el nivel de rendimiento del almacenamiento.
   * **NFS/Portal**: la versión de NFS del almacenamiento.
   * **Estado**: el estado del almacenamiento, que puede tener uno de estos valores:
        <dl class="dl">
        <dt class="dt dlterm">Añadido</dt>
        <dd class="dd">El servidor ESXi se ha añadido y está listo para ser utilizado. </dd>
        <dt class="dt dlterm">Añadiendo</dt>
        <dd class="dd">El servidor ESXi se está añadiendo. </dd>
        <dt class="dt dlterm">Suprimiendo</dt>
        <dd class="dd">El servidor ESXi se está suprimiendo.</dd>
        </dl>

### Licencias

   * **Licencia**: el tipo de licencia.
   * **Tipo de pedido**: la licencia la ha proporcionado IBM o el usuario.
   * **Edición de licencia**: la versión y la edición de la licencia.
   * **Clave de licencia**: la clave de licencia.
   * **Capacidad total (CPU)**: la cantidad total de capacidad de CPU de la licencia.
   * **Capacidad libre (CPU)**: la cantidad de capacidad de CPU libre de la licencia.

## Supresión de clústeres de instancias de VMware Federal

Puede que desee suprimir un clúster de una instancia cuando ya no sea necesario.

**Nota**: utilice este procedimiento para eliminar clústeres de instancias que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos.

### Antes de suprimir

* Utilice este procedimiento para suprimir clústeres de instancias que se han desplegado en V2.3 o releases posteriores.
* Para los clústeres desplegados en V2.2 o instancias anteriores, debe actualizar la instancia a V2.3 para poder suprimir los clústeres que ha añadido a la instancia.
* Puede suprimir un único clúster al mismo tiempo. Para suprimir varios clústeres, debe hacerlo de forma secuencial: esperando a que el clúster anterior se suprima antes de intentar suprimir el clúster siguiente.
* Asegúrese de que todos los nodos de un clúster están encendidos y en funcionamiento antes de suprimir el clúster.
* Cuando suprime un clúster, todas las máquinas virtuales (VM) del clúster también se suprimen y no pueden recuperarse. Si desea mantener las VM, mígrelas a otros clústeres.
* El clúster predeterminado no se puede suprimir.

## Procedimiento para suprimir clústeres de instancias de VMware Federal

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia de la que desea suprimir clústeres.

   **Nota**: asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede suprimir clústeres de la instancia.

3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, localice el clúster que desea suprimir y pulse el icono **Suprimir** en la columna **Acciones**.

## Enlaces relacionados

* [Visualización de instancias de VMware Federal](vc_fed_viewinginstance.html)
* [Ampliación y reducción de la capacidad para instancias de VMware Federal](vc_fed_addingremovingservers.html)
