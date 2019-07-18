---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server Hybridity add cluster, view cluster vCenter Server Hybridity, delete cluster vCenter Server Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Adición, visualización y supresión de clústeres para instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_addingviewingclusters}

Los servidores ESXi que ha configurado al solicitar una instancia se agrupan como **cluster1** de forma predeterminada.

Puede añadir clústeres a la instancia de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity) para ampliar la capacidad de cálculo y de almacenamiento. Dentro de un clúster, gestione los servidores ESXi para mejorar la asignación de recursos y la alta disponibilidad. Cuando ya no sea necesario, suprima los clústeres añadidos de la instancia.

## Adición de clústeres a instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_addingviewingclusters-adding}

### Antes de añadir clústeres
{: #vc_hybrid_addingviewingclusters-before-add}

* Siempre que sea posible, añada clústeres utilizando la consola de {{site.data.keyword.vmwaresolutions_full}}, ya que los cambios que realice en el cliente web de VMware vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}. Por lo tanto, añada clústeres a vCenter Server solo para clústeres locales o clústeres que no pueda o no vaya a gestionar en la consola de
{{site.data.keyword.vmwaresolutions_short}}.
* Para las instancias que se han desplegado en V2.5 y posteriores o que se han actualizado a las mismas, el número de clústeres, hosts y máquinas virtuales determina el límite máximo para el número de clústeres que puede añadir. Debe respetar las directrices de dimensionamiento de VMware y los límites para el despliegue. Para obtener más información sobre los límites máximos, consulte [Máximos de configuración de VMware](https://configmax.vmware.com/home){:external}.
* Para instancias que se han desplegado en (o se han actualizado a) V2.3 y V2.4, puede añadir hasta 10 clústeres.

### Valores del sistema
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

Cuando añada un clúster a una instancia de vCenter Server con el paquete híbrido (Hybridity), debe especificar los valores siguientes.

#### Nombre de clúster
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

El nombre del clúster debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre del clúster debe empezar y terminar por un carácter alfanumérico.
* La longitud máxima del nombre del clúster es de 30 caracteres.
* El nombre del clúster debe ser exclusivo dentro de la instancia de vCenter Server con el paquete híbrido (Hybridity).

#### Ubicación del centro de datos
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

La ubicación del {{site.data.keyword.CloudDataCent_notm}} del clúster está definido en {{site.data.keyword.CloudDataCent_notm}} en la instancia de vCenter Server de forma predeterminada. Puede desplegar el clúster en un {{site.data.keyword.CloudDataCent_notm}} distinto del de la instancia desplegada, pero debe asegurarse de que la latencia de red entre los dos {{site.data.keyword.CloudDataCents_notm}} sea inferior a 150 ms. Para comprobar la latencia de red, utilice una herramienta como [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass).

Si despliega el clúster en otro {{site.data.keyword.CloudDataCent_notm}} o en otro pod de la infraestructura de {{site.data.keyword.cloud_notm}}, se solicitan tres VLAN más para su uso con el {{site.data.keyword.baremetal_short}} solicitado.

### Valores de Servidor nativo
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

Puede elegir **Skylake** o **Broadwell**. Las opciones pueden variar dependiendo de la versión en que se desplegó inicialmente la instancia.

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

Cuando selecciona **Skylake**, puede elegir la combinación de CPU y RAM según sus necesidades.

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
{: caption="Tabla 1. Opciones para servidores nativos Skylake" caption-side="top"}

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

Cuando selecciona **Broadwell**, puede elegir la combinación de CPU y RAM según sus necesidades.

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 núcleos en total, 1,9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 núcleos en total, 2,2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Tabla 2. Opciones para servidores nativos Broadwell" caption-side="top"}

#### Número de servidores nativos
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

* Todos los servidores que solicite tienen la misma configuración.
* Puede solicitar entre 4 y 59 servidores.

### Valores de almacenamiento vSAN
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

Se incluye VMware vSAN 6.6 en el pedido de la instancia de vCenter Server con el paquete híbrido (Hybridity). Especifique las siguientes opciones de vSAN:
* **Tipo y tamaño de disco para discos de capacidad vSAN**: Seleccione una opción para los discos de capacidad que necesite.
* **Número de discos de capacidad de vSAN**: Especifique el número de discos de capacidad que desea añadir.
* Si desea añadir discos de capacidad por encima del límite de 10, marque el recuadro **Intel Optane de alto rendimiento**. Esta opción proporciona dos bahías de disco de capacidad adicional para un total de 12 discos de capacidad y es útil para cargas de trabajo que requieren menos latencia y un rendimiento de IOPS más alto.

  La opción **Alto rendimiento con Intel Optane** está disponible únicamente para los modelos de CPU Skylake.
  {:note}

* Revise los valores **Tipo de disco para discos de memoria caché vSAN** y **Número de discos de memoria caché de vSAN**. Estos valores dependen de si ha marcado el recuadro **Intel Optane de alto rendimiento**.
* **Licencia de vSAN**: Seleccione la edición de licencia de VMware vSAN 6.6 (Advanced o Enterprise).

### Valores de licencia
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

Licencias proporcionadas por IBM para los siguientes componentes de VMware:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (edición Advanced o Enterprise)

### Valores de interfaz de red
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

Los valores de tarjeta de interfaz de red (NIC) se basan en la selección de **Red pública y privada** o de **Solo red privada**. Los siguientes servicios de complemento necesitan NIC públicos y no están disponibles con la opción privada:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### Resumen del pedido
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

En función de la configuración seleccionada para el clúster, el coste estimado se genera y se muestra al instante en el panel derecho **Resumen de pedido**. Pulse **Detalle de precios** para generar un documento PDF con el resumen de coste de los recursos de {{site.data.keyword.vmwaresolutions_short}}.

También puede añadir los recursos suministrados a la herramienta de estimación {{site.data.keyword.cloud_notm}}, pulsando **Añadir a estimación**. Esto es útil si desea estimar el coste de los recursos estimare {{site.data.keyword.vmwaresolutions_short}} seleccionados junto con otros recursos de {{site.data.keyword.cloud_notm}} que le podría interesar adquirir.

## Procedimiento para añadir clústeres a instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para ver los clústeres que contiene.

   Asegúrese de que el estado de la instancia sea **Listo para su uso**. De lo contrario, no puede añadir clústeres a la instancia.
   {:note}

3. Pulse **Infraestructura** en el panel de navegación izquierdo y pulse **Añadir** en la esquina superior derecha de la tabla **CLÚSTERES**.
4. En la página **Añadir clúster**, escriba el nombre de clúster.
5. Puede alojar el clúster en un {{site.data.keyword.CloudDataCent_notm}} diferente al que se aloja la instancia. Para ello, en **Servidor nativo**, marque el recuadro de selección **Seleccionar una ubicación diferente** y elija el {{site.data.keyword.CloudDataCent_notm}} para alojar la instancia.
6. Seleccione el **Modelo de CPU**, la cantidad de **RAM** y el **Número de servidores nativos** de la configuración del servidor nativo.
7.  Seleccione **Almacenamiento vSAN** y especifique los tipos de disco para la capacidad y los discos de memoria caché y el número de discos. Si desea más almacenamiento, marque el recuadro **Intel Optane de alto rendimiento**.
8. Seleccione la edición de licencia para vSAN VMware para la configuración de licencia.
9. Seleccione el valor de red de **Red pública y privada** o **Solo red privada**.
10. En el panel **Resumen del pedido**, verifique la configuración del clúster antes de añadir el clúster.
   1. Revise los valores para el clúster.
   2. Revise el coste estimado del clúster. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de añadir el clúster.
   4. Pulse **Suministro**.

### Resultados después de añadir clústeres a instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_addingviewingclusters-adding-results}

1. El despliegue del clúster se inicia automáticamente y el estado del clúster pasa a ser **Inicializando**. Puede comprobar el estado del despliegue viendo el historial de despliegue en la página **Resumen** de la instancia.
2. Cuando el clúster esté listo para ser utilizado, su estado pasará a ser **Listo para su uso**. El clúster recién añadido está habilitado con alta disponibilidad (HA) de vSphere y con el planificador de recursos distribuidos (DRS) de vSphere.

No puede cambiar el nombre de clúster. Si se cambia el nombre del clúster, es posible que las operaciones de adición o eliminación de servidores ESXi en el clúster fallen.
{:important}

## Procedimiento para visualizar clústeres a instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
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
4. Pulse un nombre de clúster para ver los detalles de los servidores ESXi, el almacenamiento y la interfaz de red:

  * Detalles de servidores ESXi:
     * **Nombre**: el nombre del servidor ESXi tiene el formato
`<host_prefix><n>.<subdomain_label>.<root_domain>`, donde:

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
  * Interfaz de red - Detalles de VLAN:
    * **Número de VLAN**: número de VLAN exclusivo.
    * **Descripción**: descripción de la VLAN.
    * **Ubicación**: ubicación del centro de datos.
    * **Ruta principal**: la ruta principal de la VLAN.
    Pulse **Ver recurso** para acceder a los detalles de la VLAN.
  * Interfaz de red - Detalles de subred:
    * **Nombre**: nombre de la subred. Pulse sobre el nombre para acceder a los detalles de la subred.
    * **Tipo**: tipo de subred (primaria o portátil).
    * **Descripción**: descripción de la subred.
  * Interfaz de red - Detalles de IP:
    * **IP**: dirección IP.
    * **Estado**: estado de la dirección IP.
    * **Descripción**: descripción de la dirección IP.

## Supresión de clústeres de instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_addingviewingclusters-deleting}

Puede que desee suprimir un clúster de una instancia cuando ya no sea necesario.

### Antes de suprimir
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* Siempre que sea posible, suprima los clústeres utilizando la consola de {{site.data.keyword.vmwaresolutions_full}}, ya que los cambios que realice en el cliente web de VMware vSphere no se sincronizan con la consola de {{site.data.keyword.vmwaresolutions_short}}. Por lo tanto, suprima clústeres de vCenter Server solo para clústeres locales o clústeres que no pueda o no vaya a gestionar en la consola de
{{site.data.keyword.vmwaresolutions_short}}.
* Puede suprimir un único clúster al mismo tiempo. Para suprimir varios clústeres, debe hacerlo en secuencia: esperando a que el clúster anterior se suprima antes de suprimir el clúster siguiente.
* Asegúrese de que todos los nodos de un clúster estén encendidos y operativos antes de suprimir el clúster.
* Cuando se suprime un clúster, todas las VM (máquinas virtuales) del clúster también se suprimen y no se pueden recuperar. Si desea mantener las VM, mígrelas a otros clústeres.
* El clúster predeterminado no se puede suprimir.

## Procedimiento para suprimir clústeres de instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia de la que desea suprimir clústeres.

   Asegúrese de que la instancia está en el estado **Listo para su uso**. Si no es así, no puede eliminar clústeres de la instancia.
   {:note}

3. Pulse **Infraestructura** en el panel de navegación izquierdo. En la tabla **CLÚSTERES**, localice el clúster que desea suprimir y pulse el icono **Suprimir** en la columna **Acciones**.

## Enlaces relacionados
{: #vc_hybrid_addingviewingclusters-related}

* [Visualización de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
