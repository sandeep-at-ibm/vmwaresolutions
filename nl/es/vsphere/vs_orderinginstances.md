---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de clústeres nuevos de vSphere
{: #vs_orderinginstances}

Para desplegar una plataforma virtualizada de VMware altamente personalizable, solicite un clúster de VMware vSphere on {{site.data.keyword.cloud}}. Siga este procedimiento para definir un clúster nuevo de vSphere.

Este procedimiento le guía por la selección de componentes de VMware, los valores de Servidor nativo de {{site.data.keyword.cloud_notm}}, los valores de almacenamiento y las opciones de red para crear un nuevo clúster. Después de realizar el pedido, la configuración del clúster se captura, de modo que puede volver y continuar para escalar el clúster si es necesario. Una vez finalizado el pedido, puede configurar manualmente el clúster de VMware en función de sus requisitos.

## Requisitos
{: #vs_orderinginstances-req}

Asegúrese de haber realizado las tareas siguientes:
*  Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Gestión de cuentas y valores de usuario](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Ha revisado los requisitos y las consideraciones del apartado [Requisitos y planificación de clústeres de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).

## Valores del sistema
{: #vs_orderinginstances-sys-settings}

Debe especificar los siguientes valores de sistema cuando solicite un nuevo clúster de vSphere.

### Nombre de clúster
{: #vs_orderinginstances-cluster-name}

El nombre del clúster debe ser exclusivo dentro de su cuenta.

## Valores de licencia
{: #vs_orderinginstances-licensing-settings}

Seleccione los componentes de VMware que desea solicitar con el clúster y especifique la opción de licencia de los componentes.

### Paquetes de componentes para los usuarios de IBM Business Partner
{: #vs_orderinginstances-component-bundles-for-bp-users}

Si es un usuario de IBM Business Partner, puede seleccionar un paquete de licencias de componente al solicitar un nuevo clúster de vSphere. Están disponibles los paquetes siguientes:

Tabla 1. Paquetes de componentes de Business Partner de IBM para clústeres de vSphere

| Paquete | Componentes                   |
|:------------------------- |:----------------------- |
| Standard with Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Advanced                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Advanced with Networking | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Advanced with Networking and Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

También puede incluir los siguientes componentes de VMware en su pedido:
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

Para los usuarios de IBM Business Partner, la opción Traiga su propia licencia (BYOL) no está disponible.
{:note}

### Componentes individuales para usuarios que no sean de Business Partner
{: #vs_orderinginstances-individual-components-for-non-bp-users}

Si no es un Business Partner, puede seleccionar los siguientes componentes para el clúster de vSphere:
* VMware vSphere Enterprise Plus
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

El componente de VMware vSAN no está disponible cuando realiza el pedido de VMware vSphere Enterprise Plus 6.0. Si tiene previsto utilizar su propia licencia para VMware vSphere Enterprise Plus 6.0, se abrirá un tíquet de la infraestructura de {{site.data.keyword.cloud_notm}} en su nombre. El tíquet solicita que las licencias de vSphere de los {{site.data.keyword.baremetal_short}} solicitados se sustituyan por las licencias que se proporcionen.
{:note}

### Opciones de licencia
{: #vs_orderinginstances-licensing-options}

Tiene las siguientes opciones para las licencias de los componentes seleccionados de VMware:
* **Incluir licencia con la compra**: en este caso, se adquiere una nueva licencia para el componente VMware en su nombre. Se genera una licencia de VMware combinada que se adapte al tamaño del clúster del pedido.
* **Proporcionaré la licencia**: En este caso, utilizará su propia licencia para el componente de VMware.

Si elige adquirir alguna licencia, excepto para vSphere Enterprise Plus y vCenter Server, y ha solicitado varios servidores ESXi, se abre automáticamente una incidencia de {{site.data.keyword.cloud_notm}} en su nombre para combinar las claves de licencia. El usuario es el responsable de realizar el seguimiento de la incidencia para asegurarse de utilizar las claves de licencia que genera el equipo de DevOps.

El uso de claves de licencia individuales junto con las claves de licencia combinadas no cumple los requisitos de pago de las licencias que necesitará.
{:important}

## Valores de Servidor nativo
{: #vs_orderinginstances-bare-metal-settings}

### Ubicación del centro de datos
{: #vs_orderinginstances-dc-location}

Seleccione el {{site.data.keyword.CloudDataCent_notm}} en el que se va a alojar el clúster.

**Notas:**
* Si selecciona un componente vSAN, la lista de ubicaciones se filtra por disponibilidad de SSD.
* El centro de datos FRA05 no da soporte al servidor nativo Broadwell.
* El centro de datos LON05 no da soporte al servidor nativo Certificado por SAP ni Broadwell.

### Skylake
{: #vs_orderinginstances-skylake}

Si selecciona **Skylake**, puede elegir la combinación de CPU y RAM del servidor nativo que se ajuste a sus necesidades. Las opciones disponibles dependen de si ha seleccionado el componente VMware vSAN.

Tabla 2. Opciones para {{site.data.keyword.baremetal_short}} Skylake

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Certificado por SAP
{: #vs_orderinginstances-sap}

El separador **Certificado por SAP** no está disponible si ha seleccionado previamente VMware vSAN. Si selecciona **Certificado por SAP**, no puede modificar los valores de CPU o RAM.

En función de sus requisitos, seleccione una configuración de servidor nativo:
  * Procesador Dual Intel Xeon Gold 6140 / 36 núcleos en total, 2,3 GHz / 192 GB de RAM
  * Procesador Dual Intel Xeon Gold 6140 / 36 núcleos en total, 2,3 GHz / 384 GB de RAM
  * Procesador Dual Intel Xeon Gold 6140 / 36 núcleos en total, 2,3 GHz / 768 GB de RAM
  * Procesador Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz / 512 GB de RAM
  * Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,2 GHz / 1024 GB de RAM
  * Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,2 GHz / 2048 GB de RAM
  * Procesador Quad Intel Xeon E7-8890 v4 / 96 núcleos en total, 2,2 GHz / 4096 GB de RAM

### Broadwell
{: #vs_orderinginstances-broadwell}

Si selecciona **Broadwell**, puede elegir la combinación de CPU y RAM del servidor nativo que se ajuste a sus necesidades. Las opciones disponibles dependen de si ha seleccionado el componente VMware vSAN.

Tabla 3. Opciones para {{site.data.keyword.baremetal_short}} Broadwell

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 núcleos en total, 2,0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 núcleos en total, 2,1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Número de servidores nativos
{: #vs_orderinginstances-bare-metal-number}

El número de servidores ESXi que desea añadir al clúster vSphere. Todos los servidores ESXi tienen la misma configuración.
* Si ha seleccionado el componente VMware NSX, se necesitan un mínimo de tres servidores.
* Si ha seleccionado el componente VMware vSAN, se necesitan un mínimo de cuatro servidores.

## Valores de almacenamiento
{: #vs_orderinginstances-storage-settings}

Para pedidos sin vSAN, se solicitan servidores ESXi con un chasis de 12 discos, con dos discos para el sistema operativo (SO) ESXi.

Para pedidos con vSAN, se solicitan servidores ESXi con un chasis de 12 discos y se solicitan cuatro discos: dos para el SO ESXi y dos reservados para la colocación en memoria caché. Estos valores se configuran de forma predeterminada y no se puede cambiar. Puede solicitar más discos de capacidad seleccionando **Tipo y tamaño de disco para discos de capacidad vSAN** y **Número de discos de capacidad vSAN**.

Si selecciona el componente VMware vSAN para el clúster, especifique los valores siguientes.
* **Tipo y tamaño de disco para discos de capacidad vSAN**: Seleccione una opción para los discos de capacidad que necesite.
* **Número de discos de capacidad de vSAN**: Especifique el número de discos de capacidad que desea añadir.
* Si desea añadir discos de capacidad por encima del límite de ocho, marque el recuadro **Intel Optane de alto rendimiento**. Esta opción proporciona dos bahías de disco de capacidad adicional para un total de 10 discos de capacidad y es útil para cargas de trabajo que requieren menos latencia y un rendimiento de IOPS más alto.

  La opción **Intel Optane de alto rendimiento** solo está disponible para los modelos de CPU de Skylake Dual Intel Xeon Gold 5120 y Dual Intel Xeon Gold 6140.
  {:note}

* Revise los valores **Tipo de disco para discos de memoria caché vSAN** y **Número de discos de memoria caché de vSAN**. Estos valores dependen de si ha marcado el recuadro **Intel Optane de alto rendimiento**.

## Valores de interfaz de red
{: #vs_orderinginstances-network-interface-settings}

Debe especificar los siguientes valores de interfaz de red cuando solicite un nuevo clúster de vSphere.

### Prefijo de nombre de host
{: #vs_orderinginstances-host-name-prefix}

El nombre de host se utiliza para todos los pedidos de servidores nativos. Se recomienda utilizar el nombre de host para todas las máquinas virtuales de gestión, como por ejemplo vCenter Server y NSX.

El prefijo del nombre de host debe cumplir los siguientes requisitos:
* El nombre debe empezar y terminar por un carácter alfanumérico.
* Solo se permiten caracteres alfanuméricos y el guión (-).
* La longitud máxima es de 10 caracteres.

### Etiqueta de subdominio
{: #vs_orderinginstances-subdomain-label}

La etiqueta de subdominio debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  La etiqueta de subdominio debe empezar y terminar por un carácter alfanumérico.
*  La longitud máxima de la etiqueta de subdominio es de 10 caracteres.
*  La etiqueta de subdominio debe ser exclusiva dentro de su cuenta.

### Nombre de dominio
{: #vs_orderinginstances-domain-name}

El nombre de dominio se utiliza para todos los {{site.data.keyword.baremetal_short}} y debe cumplir los siguientes requisitos:
* El nombre debe constar de dos o más series de caracteres separadas por un punto (.)
* Solo se permiten caracteres alfanuméricos y el guión (-).
* Cada serie de caracteres debe comenzar por un carácter alfabético y terminar por un carácter alfanumérico y la última serie solo puede contener caracteres alfabéticos.
* La longitud de la última serie debe estar comprendida entre 2 y 24 caracteres.
* La longitud de otras series de caracteres debe estar comprendida entre 1 y 63 caracteres.
* La longitud máxima del nombre de dominio es de 189 caracteres.

### Red pública o privada
{: #vs_orderinginstances-public-private-network}

Los valores de habilitación de la tarjeta de interfaz de red (NIC) se basan en la selección de **Red pública y privada** o de **Solo red privada**. Los siguientes servicios de complemento necesitan NIC públicos y no están disponibles si selecciona la opción privada:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### VLAN
{: #vs_orderinginstances-vlans}

Los valores del sistema de redes dependen de si ha seleccionado **Realizar pedido de nuevas VLAN** o **Seleccionar las VLAN existentes**.

Se necesita una VLAN pública y dos VLAN privadas para el pedido del clúster. Las dos VLAN privadas se conectan en modalidad troncal en cada servidor nativo.

#### Realizar pedido de nuevas VLAN
{: #vs_orderinginstances-new-vlans}

Seleccione esta opción para solicitar una VLAN pública nueva y dos VLAN privadas nuevas.

#### Seleccionar las VLAN existentes
{: #vs_orderinginstances-existing-vlans}

En función del {{site.data.keyword.CloudDataCent_notm}} que haya seleccionado, puede que haya VLAN públicas y privadas existentes disponibles.

  Cuando seleccione reutilizar las VLAN públicas y privadas existentes, especifique las VLAN y las subredes:
  * **VLAN pública** es para acceder a la red pública.
  * **VLAN privada** es para la conectividad entre los centros de datos y los servicios de {{site.data.keyword.cloud_notm}}.
  * **VLAN privada secundaria** es para las características de VMware, como vSAN.
  * **Subred primaria** se asigna a hosts físicos para acceder a la red pública.
  * **Subred primaria privada** se asigna a hosts físicos para el tráfico de gestión.

**Importante:**
* Asegúrese de que la configuración del cortafuegos en las VLAN seleccionadas no bloquee el tráfico de datos de gestión.
* Asegúrese de que todas las VLAN que seleccione estén en el mismo pod. Los servidores ESXi no se pueden suministrar en VLAN en pods mixtos.

#### Par de alta disponibilidad de FortiGate Physical Appliance 300 Series
{: #vs_orderinginstances-fortigate-physical-appliance}

También puede seleccionar si desea incluir el par de alta disponibilidad de dispositivos físicos FortiGate serie 300 para proteger el entorno de nube. Para obtener más información, consulte [Visión general de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations).

## Resumen del pedido
{: #vs_orderinginstances-order-summary}

En función de sus configuraciones, el coste estimado se genera y se muestra al instante en el panel **Resumen de pedido** a la derecha. Pulse **Detalles sobre precios** para generar un documento PDF que proporcione los detalles de la estimación.

## Procedimiento para solicitar clústeres de vSphere
{: #vs_orderinginstances-procedure}

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** en el panel de navegación izquierdo y pulse **VMware vSphere** en la sección **Centros de datos virtuales**.
2. En la página **VMware vSphere on IBM Cloud**, pulse **Crear**.  
   Asegúrese de que está en el separador **Crear nuevo** y de que se muestra **Nuevo clúster** en la lista **Configuraciones de clúster**.
3. Escriba el nombre del clúster.
4. Seleccione los componentes de VMware:
  * Si es un Business Partner de IBM, seleccione un paquete de licencias y cualquier otro componente de VMware disponible adicional.
  * Si no es un Business Partner, seleccione el componente, la edición, si la hay, y especifique la opción de licencia.
  Cuando opta por traer su propia licencia (BYOL) para VMware vSphere Enterprise Plus, se abre automáticamente una incidencia de {{site.data.keyword.cloud_notm}} en su nombre para solicitar que las licencias predeterminadas de vSphere de los {{site.data.keyword.baremetal_short}} solicitados se sustituyan por las licencias que proporcione.   

    **Importante:** El usuario es el responsable de realizar el seguimiento del tíquet para que se sustituya la licencia de vSphere de los servidores ESXi recién solicitados. De esta forma, la infraestructura de {{site.data.keyword.cloud_notm}} permite la cancelación del cargo inicialmente suministrado por la licencia de vSphere de la infraestructura de {{site.data.keyword.cloud_notm}}. Para sustituir la licencia de ESXi vSphere, consulte [Configuración de valores de licencia para un host ESXi](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}.
5. Complete los valores del servidor nativo:
   1. Seleccione el {{site.data.keyword.CloudDataCent_notm}} en el que se va a alojar el clúster.
   2. Seleccione la configuración del servidor nativo.
      * Si seleccione **Skylake** o **Broadwell**, especifique el modelo de CPU y el tamaño de RAM.
      * Si selecciona **Certificado por SAP**, especifique el modelo de CPU.
   3. Especifique el número de Servidores nativos.
6. Si ha seleccionado el componente **VMware vSAN**, complete la configuración de almacenamiento de vSAN. Especifique los tipos de disco para la capacidad y los discos de memoria caché y el número de discos. Si desea más almacenamiento, marque el recuadro **Intel Optane de alto rendimiento**.
7. Complete los valores de interfaz de red:
   1. Especifique el prefijo de nombre de host, la etiqueta de subdominio y el nombre de dominio.
   2. Seleccione el valor de red de **Red pública y privada** o **Solo red privada**.
   3. Seleccione la interfaz de red que desea utilizar.
    * Si desea solicitar nuevas VLAN públicas y privadas, pulse **Realizar pedido de nuevas VLAN**.
    * Si desea reutilizar las VLAN públicas y privadas existentes cuando estén disponibles, pulse **Seleccionar las VLAN existentes** y especifique las VLAN y opcionalmente las subredes.
    4. Especifique si desea aplicar el par de alta disponibilidad de dispositivos físicos FortiGate serie 300 para proteger el entorno de nube.  
8. En el panel **Resumen del pedido**, verifique la configuración del clúster y el coste estimado.
   * Para guardar la configuración como una plantilla sin realizar un pedido, pulse **Guardar configuración**.
   * Para realizar el pedido, asegúrese de que la cuenta a la que se va a realizar el cobro es correcta; revise y acepte los términos y, a continuación, pulse **Suministro**.

   Solo se instalan los {{site.data.keyword.baremetal_short}}. El usuario es el responsable de instalar y configurar los distintos componentes después del despliegue del clúster, como por ejemplo VMware vCenter, VMware NSX, VMware vSAN.
   {:note}

### Resultados
{: #vs_orderinginstances-results}

Si ha guardado la configuración del clúster como una plantilla, recibirá una notificación en la consola que indicará que la configuración se ha guardado correctamente; luego podrá encontrar la plantilla en la lista **Configuraciones de clúster**.

Si ha realizado un pedido, el despliegue del clúster se inicia automáticamente y el usuario recibe una confirmación por correo electrónico de que el pedido se está procesando. Cuando el clúster esté listo para ser utilizado, se le notificará por correo electrónico.

A diferencia de las instancias de vCenter Server y Cloud Foundation, los clústeres de vSphere no se muestran en la página **Instancias desplegadas**.
{:note}

## Enlaces relacionados
{: #vs_orderinginstances-related}

* [Solicitud de clústeres de vSphere en función de configuraciones existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Escalado de clústeres existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Escalado de clústeres creados fuera de la consola](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
