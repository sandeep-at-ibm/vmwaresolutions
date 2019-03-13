---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de instancias de NetApp ONTAP Select
{: #np_orderinginstances}

Para desplegar una plataforma VMware virtualizada con un dispositivo de almacenamiento dedicado y altamente disponible definido mediante software, solicite una instancia de NetApp ONTAP Select.

## Requisitos
{: #np_orderinginstances-req}

Asegúrese de haber realizado las tareas siguientes:
*  Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud}} en la página **Configuración**. Para obtener más información, consulte [Gestión de cuentas y valores de usuario](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Ha revisado los requisitos y las consideraciones del apartado [Requisitos y planificación de las instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning).

No modifique ningún valor definido durante la solicitud o el despliegue de la instancia. Si lo hace, la instancia podría quedar inutilizable. Por ejemplo, si se cierra la red pública, si los servidores y las Instancias de servidor virtual (VSI) se mueven detrás de una media disposición de Vyatta, o si el VSI de IBM CloudBuilder se detiene o se suprime.
{:important}

## Valores del sistema
{: #np_orderinginstances-sys-settings}

Cuando solicite una instancia de NetApp ONTAP Select, debe especificar los siguientes valores básicos.

### Nombre de instancia
{: #np_orderinginstances-instance-name}

El nombre de instancia debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre de instancia debe empezar por un carácter alfabético y terminar por un carácter alfanumérico.
* La longitud máxima del nombre de instancia es de 10 caracteres.
* El nombre de instancia debe ser exclusivo dentro de su cuenta.

## Valores de interfaz de red
{: #np_orderinginstances-network-interface-settings}

Debe especificar los siguientes valores de interfaz de red cuando solicite una instancia de NetApp ONTAP Select.

### Prefijo de nombre de host
{: #np_orderinginstances-host-name-prefix}

El prefijo del nombre de host debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  El prefijo de nombre de host debe empezar y terminar por un carácter alfanumérico.
*  La longitud máxima del prefijo de nombre de host es de 10 caracteres.

### Etiqueta de subdominio
{: #np_orderinginstances-subdomain-label}

La etiqueta de subdominio debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  La etiqueta de subdominio debe empezar por un carácter alfabético y terminar por un carácter alfanumérico.
*  La longitud máxima de la etiqueta de subdominio es de 10 caracteres.
*  La etiqueta de subdominio debe ser exclusiva dentro de su cuenta.

### Nombre de dominio
{: #np_orderinginstances-domain-name}

El nombre del dominio raíz debe cumplir los siguientes requisitos:
* El nombre de dominio debe constar de dos o más series de caracteres separadas por un punto (.)
* La primera serie debe empezar por un carácter alfabético y terminar por un carácter alfanumérico.
* Todas las series, excepto la última, solo pueden incluir caracteres alfanuméricos y caracteres de guión (-).
* La última serie solo puede incluir caracteres alfabéticos.
* La longitud de la última serie debe estar comprendida entre 2 y 24 caracteres.

La longitud máxima del FQDN (nombre de dominio completo) para hosts y máquinas virtuales (VM) es de 50 caracteres. Los nombres de dominio deben cumplir con esta longitud máxima.
{:note}

## Valores de licencia
{: #np_orderinginstances-licensing-settings}

Debe cargar cuatro archivos de licencia de NetApp, uno para cada uno de los cuatro {{site.data.keyword.baremetal_short}}. Póngase en contacto con el equipo de ventas de NetApp para obtener la licencia apropiada para el despliegue de alto rendimiento o de alta capacidad.

## Valores de Servidor nativo
{: #np_orderinginstances-bare-metal-settings}

### Ubicación del centro de datos
{: #np_orderinginstances-dc-location}

Debe seleccionar el {{site.data.keyword.CloudDataCent_notm}} en el que se alojará la instancia.

### Configuración de servidor nativo
{: #np_orderinginstances-bare-metal-config}

Seleccione una configuración de servidor nativo en función de sus requisitos:
* **Alto rendimiento (Medio)**: Licencia Premium / Dual Intel Xeon E5-2650 v4 (24 núcleos en total, 2,2 GHz) / 128 GB de RAM / Capacidad por nodo de 22 unidades SSD de 1,9 TB / Capacidad efectiva de un clúster de 4 nodos – 59 TB
* **Alto rendimiento (Grande)**: Licencia Premium / Dual Intel Xeon E5-2650 v4 (24 núcleos en total, 2,2 GHz) / 128 GB de RAM / Capacidad por nodo de 22S unidades SSD de 3,8 TB / Capacidad efectiva de un clúster de 4 nodos – 118 TB
* **Alta capacidad** – Licencia Estándar / Dual Intel Xeon E5-2650 v4 (24 núcleos en total, 2,2 GHz) / 64 GB de RAM / Capacidad por nodo de treinta y cuatro unidades SATA de 4 TB / Capacidad efectiva de un clúster de 4 nodos – 190 TB

Las unidades SSD (disco de estado sólido, Solid-State Disk) de 3,8 TB reciben soporte cuando estén disponibles a nivel general en un {{site.data.keyword.CloudDataCent_notm}}.
{:note}

### Número de servidores nativos
{: #np_orderinginstances-bare-metal-number}

El número de servidores ESXi de una instancia de NetApp ONTAP Select es 4 de forma predeterminada. No lo puede modificar. Todos los servidores ESXi comparten la configuración.

## Procedimiento para solicitar instancias de NetApp ONTAP Select
{: #ordering-netapp-ontap-select-instances}

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** en el panel de navegación izquierdo y pulse **NetApp ONTAP Select** en la sección **Centros de datos virtuales**.
2. En la página **NetApp ONTAP Select**, pulse **Crear**.
3. En la página **NetApp ONTAP**, escriba el nombre de la instancia.
4. Complete los valores de interfaz de red escribiendo el **Prefijo de nombre de host**, **Etiqueta de subdominio** y **Nombre de dominio**.
5. Complete los valores de licencia pulsando **Añadir archivos de licencia** para cargar los cuatro archivos de licencia de NetApp que necesitan los cuatro {{site.data.keyword.baremetal_short}}.
6. Complete los valores del servidor nativo:
   1. Seleccione el {{site.data.keyword.CloudDataCent_notm}} que va a alojar la instancia.
   2. Seleccione la configuración del servidor nativo.
7. En el panel **Resumen del pedido**, verifique la configuración de la instancia antes de realizar el pedido.
    1. Revise los valores de la instancia.
    2. Revise el coste estimado de la instancia. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen de pedido, pulse el icono **Imprimir** o **Descargar** de la ventana del PDF.
    3. Asegúrese de que la cuenta a la que se va a realizar el cobro es correcta y luego marque el recuadro de selección **Comprendo que la cuenta que se enumera a continuación se cobrará**.
    4. Pulse el enlace o enlaces de los términos que se aplican a su pedido. Asegúrese de que está de acuerdo con estos términos y marque el recuadro de selección **He leído y acepto los acuerdos de servicio de terceros enumerados a continuación**.
    5. Pulse **Suministro**.

## Resultados
{: #np_orderinginstances-results}

El despliegue de la instancia comienza automáticamente. Recibirá una confirmación de que el pedido se está procesando y puede comprobar el estado del despliegue consultando los detalles de la instancia.

Cuando la instancia se haya desplegado correctamente, los componentes que se describen en [Especificaciones técnicas para las instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#technical-specifications-for-netapp-ontap-select-instances) se instalan en la plataforma virtual de VMware.

Cuando la instancia esté lista para ser utilizada, el estado de la instancia pasará a ser **Listo para su uso** y recibirá una notificación por correo electrónico.

## Qué hacer a continuación
{: #np_orderinginstances-next}

Puede ver y gestionar la instancia de NetApp ONTAP Select que ha solicitado.

Solo debe gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no a través del {{site.data.keyword.slportal}} ni por ningún otro medio fuera de la consola. Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola.
{:important}

**ATENCIÓN:** el hecho de gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} (que se instalaron en la cuenta de {{site.data.keyword.cloud_notm}} al solicitar la instancia) desde fuera de la consola de {{site.data.keyword.vmwaresolutions_short}} podría hacer que el entorno quedara inestable. Estas actividades de gestión incluyen:
*  Añadir, modificar, devolver o eliminar componentes
*  Apagar componentes

   Las excepciones a estas actividades incluyen la gestión de comparticiones del archivo de almacenamiento compartido desde el {{site.data.keyword.slportal}}. Estas actividades incluyen: solicitar, suprimir (lo que puede afectar los almacenes de datos si están montados), autorizar y montar comparticiones del archivo de almacenamiento compartido.

## Enlaces relacionados
{: #np_orderinginstances-related}

* [Visualización de instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [Supresión de instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [Centro de documentación de NetApp ONTAP](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [Conexión de almacenamiento dedicado a despliegues de NetApp ONTAP Select](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
