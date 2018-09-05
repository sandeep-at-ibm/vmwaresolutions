---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-02"

---

# Adición, visualización y supresión de clústeres para instancias de vCenter Server

Los servidores ESXi que ha configurado al solicitar una instancia se agrupan como **cluster1** de forma predeterminada.

Puede añadir sus propios clústeres a las instancias de VMware vCenter Server para ampliar la capacidad de cálculo y de almacenamiento. Dentro de un clúster, puede gestionar los servidores ESXi para mejorar la asignación de recursos y la alta disponibilidad. Cuando ya no sea necesario, puede suprimir los clústeres añadidos de las instancias.

**Disponibilidad**: la característica de supresión de clúster solo está disponible para las instancias que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos.

## Adición de clústeres a instancias de vCenter Server

El número de clústeres que pueden añadirse a una instancia depende de la versión de la instancia:
* Para instancias que se han desplegado en (o se han actualizado a) V2.2 y releases posteriores, puede añadir hasta 10 clústeres.
* Para instancias que se han desplegado en V2.2 o releases anteriores, puede añadir hasta 5 clústeres.

### Valores del sistema

Cuando añada un clúster a una instancia de vCenter Server, debe especificar los valores siguientes.

#### Nombre de clúster

El nombre del clúster debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre del clúster debe empezar y terminar por un carácter alfanumérico.
* La longitud máxima del nombre del clúster es de 30 caracteres.
* El nombre del clúster debe ser exclusivo dentro de la instancia de vCenter Server.

#### Ubicación del centro de datos

La ubicación del {{site.data.keyword.CloudDataCent}} del clúster está definido en {{site.data.keyword.CloudDataCent_notm}} en la instancia de vCenter Server de forma predeterminada. Puede desplegar el clúster en un {{site.data.keyword.CloudDataCent_notm}} distinto del de la instancia desplegada, pero debe asegurarse de que la latencia de red entre los dos {{site.data.keyword.CloudDataCents_notm}} sea inferior a 150 ms. Para comprobar la latencia de red, puede utilizar una herramienta como [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Si despliega el clúster en otro {{site.data.keyword.CloudDataCent_notm}} o en otro pod de la infraestructura de {{site.data.keyword.cloud_notm}}, se solicitan tres VLAN adicionales para que las utilice con el {{site.data.keyword.baremetal_short}} solicitado.

### Valores de Servidor nativo

Puede elegir **Preconfigurado** o **Personalizado**.

#### Preconfigurado

Para el valor **Preconfigurado**, puede seleccionar una **configuración de servidor nativo** en función de sus requisitos:
* Pequeño (Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz / 128 GB de RAM / 2 discos)
* Medio (Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz / 256 GB de RAM / 2 discos)
* Grande (Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz / 512 GB de RAM / 2 discos)

#### Personalizado

Para el valor **Personalizado**, dispone de varias opciones para **Modelo de CPU** y **RAM**. Las opciones disponibles pueden variar dependiendo de la versión en que se desplegó inicialmente la instancia.

Tabla 1. Opciones para {{site.data.keyword.baremetal_short}} personalizados

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Número de servidores nativos

Se necesita un mínimo de dos {{site.data.keyword.baremetal_short}} para un clúster.

Para instancias de vCenter Server desplegadas en V2.1 o releases posteriores, puede añadir un máximo de 59 {{site.data.keyword.baremetal_short}} para un clúster y puede añadir entre 1 y 59 servidores ESXi simultáneamente.

Para instancias de vCenter Server desplegadas en V2.0 o releases anteriores, puede añadir un máximo de 32 {{site.data.keyword.baremetal_short}} para un clúster. El número de {{site.data.keyword.baremetal_short}} que puede añadir simultáneamente funciona del siguiente modo:
* Para las configuraciones de servidores nativos de tipo **Pequeño**, **Medio** y **Grande**, puede añadir entre 1 y 10 servidores ESXi simultáneamente.
* Para la configuración de servidor nativo **Personalizado**, puede añadir entre 1 y 20 servidores ESXi simultáneamente.

Después del despliegue, puede crear un máximo de cuatro clústeres más. Si selecciona la configuración de servidor nativo **Personalizado** con almacenamiento VMware vSAN, se necesitan 4 servidores para el clúster inicial y los clústeres posteriores al despliegue.

### Valores de almacenamiento

Los valores de almacenamiento dependen de la opción que seleccione de configuración de Servidor nativo y de tipo de almacenamiento.

#### Almacenamiento vSAN

vSAN sólo está disponible para la configuración de servidor nativo personalizado. Puede personalizar el almacenamiento VMware vSAN especificando el número de discos de capacidad vSAN (2, 4, 6 u 8), el tipo de disco y el tamaño que satisfagan sus necesidades de almacenamiento, y la opción de licencia de vSAN.

Si el clúster inicial era un clúster vSAN, los clústeres vSAN adicionales utilizan la misma licencia de vSAN y tienen la misma configuración que el inicial. Esto también se aplica si se ha elegido que se despliegue vSAN en cualquier clúster de la instancia (inicial o adicional). La primera vez se le solicitará la licencia de vSAN (BYOL o adquirida) y la edición. La siguiente vez que seleccione vSAN para un clúster adicional, se reutilizará la licencia especificada inicialmente.

#### Almacenamiento NFS

Cuando seleccione **Almacenamiento de NFS**, puede añadir almacenamiento compartido a nivel de archivo para la instancia donde todas las comparticiones utilizan los mismos valores o pueden especificar distintos valores de configuración para cada compartición de archivos. Especifique las siguientes opciones de NFS:

**Nota:** El número de comparticiones de archivo debe estar comprendido entre 1 y 32.

* **Configurar las comparticiones individualmente**: Seleccione para especificar distintos valores de configuración para cada compartición de archivos.
* **Número de unidades compartidas**: Al utilizar el mismo valor de configuración para cada compartición de archivos, especifique el número de comparticiones de archivos para el almacenamiento compartido de NFS que desee añadir.
* **Almacenamiento**: seleccione la capacidad que se ajuste a sus requisitos de almacenamiento compartido.
* **Rendimiento**: seleccione el valor de IOPS (operaciones de entrada/salida por segundo) por GB en función de sus requisitos de carga de trabajo.
* **AÑADIR NFS**: Seleccione para añadir comparticiones de archivos individuales que utilizarán distintos valores de configuración.

Tabla 2. Opciones de nivel de rendimiento de NFS

| Opción        | Detalles       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Esta opción está diseñada para la mayoría de cargas de trabajo generales. Entre las aplicaciones de ejemplo se encuentran alojamiento de bases de datos pequeñas, copia de seguridad de aplicaciones web o imágenes de disco de máquina virtual para un hipervisor. |
  | 4 IOPS/GB | Esta opción está diseñada para cargas de trabajo de mayor intensidad que tienen un alto porcentaje de datos activos en un momento determinado. Las aplicaciones de ejemplo incluyen bases de datos transaccionales. |
  | 10 IOPS/GB | Esta opción está diseñada para los tipos de carga de trabajo más exigentes, como las analíticas. Las aplicaciones de ejemplo incluyen bases de datos con un gran número de transacciones y otras bases de datos sensibles al rendimiento. Este nivel de rendimiento está limitado a una capacidad máxima de 4 TB por compartición de archivo. |

### Valores de licencia

Especifique la opción de licencia para el componente VMware vSphere en el clúster:
* Para los usuarios de Business Partners, se incluye y se adquiere en su nombre la licencia de vSphere (edición Enterprise Plus).
* Para usuarios que no son Business Partners, puede utilizar las licencias de VMware que proporciona IBM para este componente seleccionando **Incluir con la compra** o puede traer su propia licencia (BYOL) seleccionando **Proporcionaré** e indicando su propia clave de licencia.

### Resumen del pedido

En función de la configuración seleccionada para el clúster, el coste estimado se genera y se muestra al instante en el panel derecho **Resumen de pedido**.

## Procedimiento para añadir clústeres a instancias de vCenter Server

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia a la que desea añadir clústeres.

   **Nota**: asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede añadir clústeres a la instancia.

3. Pulse **Infraestructura** en el panel de navegación izquierdo y pulse **Añadir** en la esquina superior derecha de la tabla **CLÚSTERES**.
4. En la página **Añadir clúster**, escriba el nombre de clúster.
5. Si desea alojar el clúster en un {{site.data.keyword.CloudDataCent_notm}} diferente al que se aloja la instancia, en **Servidor nativo**, marque el recuadro de selección **Seleccione otra ubicación** y elija el {{site.data.keyword.CloudDataCent_notm}} para alojar la instancia.
6. Complete la configuración del servidor nativo.
   * Si ha seleccionado **Preconfigurado**, especifique el valor de **Configuración de servidor nativo** y el valor de **Número de {{site.data.keyword.baremetal_short}}**. Si tiene previsto utilizar vSAN como solución de almacenamiento, tenga en cuenta que se necesitan un mínimo de 4 {{site.data.keyword.baremetal_short}}.
   * Si ha seleccionado **Personalizado**, especifique el valor de **Modelo de CPU**, la cantidad de **RAM** y el valor de **Número de {{site.data.keyword.baremetal_short}}**.
7. Complete la configuración del almacenamiento.
  * Cuando seleccione **Almacenamiento vSAN**, especifique el **Tipo y tamaño de los discos de capacidad vSAN**, el **Número de discos de capacidad vSAN**, y cómo se proporciona la **Licencia de vSAN**.
  * Cuando seleccione **Almacenamiento NFS** y desee añadir y configurar los mismos valores a todas las comparticiones de archivos, especifique el **Número de unidades compartidas**, el **Tamaño** y el **Rendimiento**.
  * Cuando seleccione **Almacenamiento NFS** y desee añadir y configurar las comparticiones de archivos individualmente, seleccione **Configurar recursos compartidos individualmente** y a continuación pulse sobre el icono **+** junto a la etiqueta **Añadir NFS** y seleccione el **Tamaño** y el **Rendimiento** para cada compartición de archivos individual. Debe seleccionar al menos una unidad compartida de archivo.
8. Especifique cómo se proporciona la clave de licencia de vSphere:
  * Para los usuarios de Business Partners, se incluye y se adquiere en su nombre la licencia de vSphere (edición Enterprise Plus).
  * Para los usuarios que no son Business Partners, puede seleccionar una de las siguientes opciones:
      * Si desea que se adquieran nuevas licencias en su nombre, seleccione **Incluir con la compra** para el componente.
      * Si desea utilizar su propia licencia de VMware para el componente, seleccione **Proporcionaré** y escriba su clave de licencia.
9. En el panel **Resumen del pedido**, verifique la configuración del clúster antes de añadir el clúster.
   1. Revise los valores para el clúster.
   2. Revise el coste estimado del clúster. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de añadir el clúster.
   4. Pulse **Suministro**.

### Resultados después de añadir clústeres a instancias de vCenter Server

1. El despliegue del clúster se inicia automáticamente y el estado del clúster pasa a ser **Inicializando**. Puede comprobar el estado del despliegue viendo el historial de despliegue desde la página **Resumen** de la instancia.
2. Cuando el clúster esté listo para ser utilizado, su estado pasará a ser **Listo para su uso**. El clúster recién añadido está habilitado con alta disponibilidad (HA) de vSphere y con el planificador de recursos distribuidos (DRS) de vSphere.

**Importante**: no puede cambiar el nombre del clúster. Si se cambia el nombre del clúster, es posible que las operaciones de adición o eliminación de servidores ESXi en el clúster fallen.

## Visualización de clústeres en instancias de vCenter Server

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
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
4. Pulse un nombre de clúster para ver los detalles de los servidores ESXi y el almacenamiento:

  * Detalles de servidores ESXi:
     * **Nombre**: el nombre del servidor ESXi está en el formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, donde:

       `host_prefix` es el prefijo del nombre de host,

       `n` es la secuencia del servidor,

       `subdomain_label` es la etiqueta de subdominio, y

       `root_domain` es el nombre de dominio raíz.

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
  * Detalles de almacenamiento:
    * **Nombre**: el nombre del almacén de datos.
    * **Tamaño**: la capacidad del almacenamiento.
    * **IOPS/GB**: el nivel de rendimiento del almacenamiento.
    * **Protocolo NFS**: la versión de NFS del almacenamiento.

## Supresión de clústeres de instancias de vCenter Server

Puede que desee suprimir un clúster de una instancia cuando ya no sea necesario.

### Antes de suprimir

* Utilice este procedimiento para suprimir clústeres de instancias que se han desplegado en V2.3 o releases posteriores.
* Para los clústeres desplegados en V2.2 o instancias anteriores, debe actualizar la instancia a V2.3 para poder suprimir los clústeres que ha añadido a la instancia.
* Puede suprimir un único clúster al mismo tiempo. Para suprimir varios clústeres, debe hacerlo de forma secuencial: esperando a que el clúster anterior se suprima antes de intentar suprimir el clúster siguiente.
* Asegúrese de que todos los nodos de un clúster están encendidos y en funcionamiento antes de suprimir el clúster.
* Cuando suprime un clúster, todas las máquinas virtuales (VM) del clúster también se suprimen y no pueden recuperarse. Si desea mantener las VM, mígrelas a otros clústeres.
* El clúster predeterminado no se puede suprimir.

## Procedimiento para suprimir clústeres de instancias de vCenter Server

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia de la que desea suprimir clústeres.

   **Nota**: asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede suprimir clústeres de la instancia.

3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, localice el clúster que desea suprimir y pulse el icono **Suprimir** en la columna **Acciones**.
4. Confirme que ha completado la migración de las máquinas virtuales a otros clústeres, si es necesario, y que desea suprimir el clúster.

### Enlaces relacionados

* [Visualización de instancias de vCenter Server](vc_viewinginstances.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server](vc_addingremovingservers.html)
