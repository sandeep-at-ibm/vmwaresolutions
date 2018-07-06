---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Adición, visualización y supresión de clústeres para instancias de vCenter Server con el paquete híbrido (Hybridity)

Los servidores ESXi que ha configurado al solicitar una instancia se agrupan como **cluster1** de forma predeterminada.

Puede añadir clústeres a la instancia de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity) para ampliar la capacidad de cálculo y de almacenamiento. Dentro de un clúster, puede gestionar los servidores ESXi para mejorar la asignación de recursos y la alta disponibilidad. Cuando ya no sea necesario, puede suprimir los clústeres añadidos de la instancia.

## Adición de clústeres a instancias de vCenter Server con el paquete híbrido (Hybridity)

Puede añadir hasta 10 clústeres a la instancia de vCenter Server con el paquete híbrido (Hybridity).

### Valores del sistema

Cuando añada un clúster a una instancia de vCenter Server con el paquete híbrido (Hybridity), debe especificar los valores siguientes.

#### Nombre de clúster

El nombre del clúster debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre del clúster debe empezar y terminar por un carácter alfanumérico.
* La longitud máxima del nombre del clúster es de 30 caracteres.
* El nombre del clúster debe ser exclusivo dentro de la instancia de vCenter Server con el paquete híbrido (Hybridity).

#### Ubicación del centro de datos

La ubicación del {{site.data.keyword.CloudDataCent}} del clúster está definido en {{site.data.keyword.CloudDataCent_notm}} en la instancia de vCenter Server de forma predeterminada. Puede desplegar el clúster en un {{site.data.keyword.CloudDataCent_notm}} distinto del de la instancia desplegada, pero debe asegurarse de que la latencia de red entre los dos {{site.data.keyword.CloudDataCents_notm}} sea inferior a 150 ms. Para comprobar la latencia de red, puede utilizar una herramienta como [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Si despliega el clúster en otro {{site.data.keyword.CloudDataCent_notm}} o en otro pod de la infraestructura de {{site.data.keyword.cloud_notm}}, se solicitan tres VLAN adicionales para que las utilice con el {{site.data.keyword.baremetal_short}} solicitado.

### Valores de Servidor nativo

#### Personalizado

Especifique el modelo de CPU y la RAM del servidor nativo. Las opciones disponibles pueden variar dependiendo de la versión en que se desplegó inicialmente la instancia.

Tabla 2. Opciones para servidores nativos personalizados

| Opciones de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 96 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Número de servidores nativos

Se necesita un mínimo de dos {{site.data.keyword.baremetal_short}} para un clúster.

Puede añadir un máximo de 59 {{site.data.keyword.baremetal_short}} para un clúster y puede añadir entre 1 y 59 servidores ESXi simultáneamente.

Después del despliegue, puede crear un máximo de cuatro clústeres más. Para almacenamiento VMware vSAN, se necesitan 4 servidores para el clúster inicial y los clústeres posteriores al despliegue.

### Valores de almacenamiento vSAN

Se incluye VMware vSAN 6.6 en el pedido de la instancia de vCenter Server con el paquete híbrido (Hybridity). Debe especificar **Advanced** o **Enterprise** para la edición de licencia.

* **Tipo y tamaño de disco para discos de capacidad vSAN**: seleccione la capacidad que se ajuste a sus requisitos de almacenamiento compartido.
* **Número de discos de capacidad vSAN**: seleccione el número de discos para el almacenamiento compartido vSAN que desea añadir. Las cantidades de disco deben ser 2, 4, 6 u 8.
* Seleccione la edición de licencia de VMware vSAN 6.6 (Advanced o Enterprise).

### Valores de licencia

Licencias de VMware proporcionadas por IBM para:
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Advanced o Enterprise) 6.3

### Resumen del pedido

En función de la configuración seleccionada para el clúster, el coste estimado se genera y se muestra al instante en el panel derecho **Resumen de pedido**.

## Procedimiento para añadir clústeres a instancias de vCenter Server con el paquete híbrido (Hybridity)

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para ver los clústeres que contiene.

   **Nota**: asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede añadir clústeres a la instancia.

3. Pulse **Infraestructura** en el panel de navegación izquierdo y pulse **Añadir** en la esquina superior derecha de la tabla **CLÚSTERES**.
4. En la página **Añadir clúster**, escriba el nombre de clúster.
5. Si desea alojar el clúster en un {{site.data.keyword.CloudDataCent_notm}} diferente al que se aloja la instancia, en **Servidor nativo**, marque el recuadro de selección **Seleccione otra ubicación** y elija el {{site.data.keyword.CloudDataCent_notm}} para alojar la instancia.
6. Seleccione el **Modelo de CPU**, la cantidad de **RAM** y el **Número de servidores nativos** de la configuración del servidor nativo.
7.  Seleccione **Almacenamiento vSAN** y seleccione el **Número de discos de capacidad vSAN** y el **Tipo y tamaño de disco para discos de capacidad vSAN** de la configuración de almacenamiento.
8. Seleccione la edición de licencia para vSAN VMware para la configuración de licencia.
9. En el panel **Resumen del pedido**, verifique la configuración del clúster antes de añadir el clúster.
   1. Revise los valores para el clúster.
   2. Revise el coste estimado del clúster. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de añadir el clúster.
   4. Pulse **Suministro**.

### Resultados después de añadir clústeres a instancias de vCenter Server con el paquete híbrido (Hybridity)

1. El despliegue del clúster se inicia automáticamente y el estado del clúster pasa a ser **Inicializando**. Puede comprobar el estado del despliegue viendo el historial de despliegue en la página **Resumen** de la instancia.
2. Cuando el clúster esté listo para ser utilizado, su estado pasará a ser **Listo para su uso**. El clúster recién añadido está habilitado con alta disponibilidad (HA) de vSphere y con el planificador de recursos distribuidos (DRS) de vSphere.

**Importante**: no puede cambiar el nombre del clúster. Si se cambia el nombre del clúster, es posible que las operaciones de adición o eliminación de servidores ESXi en el clúster fallen.

## Visualización de clústeres en instancias de vCenter Server con el paquete híbrido (Hybridity)

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para ver los clústeres que contiene.
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

## Supresión de clústeres de instancias de vCenter Server con el paquete híbrido (Hybridity)

Puede que desee suprimir un clúster de una instancia cuando ya no sea necesario.

### Antes de suprimir

* Puede suprimir un único clúster al mismo tiempo. Para suprimir varios clústeres, debe hacerlo de forma secuencial: esperando a que el clúster anterior se suprima antes de intentar suprimir el clúster siguiente.
* Asegúrese de que todos los nodos de un clúster están encendidos y en funcionamiento antes de suprimir el clúster.
* Cuando suprime un clúster, todas las máquinas virtuales (VM) del clúster también se suprimen y no pueden recuperarse. Si desea mantener las VM, mígrelas a otros clústeres.
* El clúster predeterminado no se puede suprimir.

## Procedimiento para suprimir clústeres de instancias de vCenter Server con el paquete híbrido (Hybridity)

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia de la que desea suprimir clústeres.

   **Nota**: asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede eliminar clústeres de la instancia.

3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, localice el clúster que desea suprimir y pulse el icono **Suprimir** en la columna **Acciones**.

## Enlaces relacionados

* [Visualización de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_viewinginstances.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservers.html)
