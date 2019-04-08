---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Exploración y revisión
{: #vum-scanning}

Cuando explora hosts, máquinas virtuales (VM) y dispositivos virtuales, los evalúa frente a las líneas base y los grupos de línea base para determinar su nivel de conformidad. Se escanean los objetos de inventario y se revisan los resultados para determinar la forma en que cumplen con las líneas base y los grupos de línea base. Los resultados de la exploración se pueden filtrar por búsqueda de texto, selección de grupos, selección de línea base y selección de estado de conformidad. Puede iniciar los escaneos siguientes:
*	**Inicie manualmente una exploración de hosts ESXi de vSphere**: puede explorar hosts de ESXi en el inventario de vSphere frente a las líneas base y los grupos de línea base conectados.
*	**Inicie manualmente una exploración de máquinas y dispositivos virtuales**: puede explorar VM y dispositivos virtuales en el inventario de vSphere frente a las líneas base y los grupos de línea base conectados.
*	**Inicie manualmente una exploración de un objeto de contenedor**: inicie una exploración simultánea de hosts, VM y dispositivos virtuales, explorando un objeto contenedor que es un centro de datos o una carpeta de centro de datos.
*	**Planifique una exploración**: puede configurar el cliente web de vSphere para explorar VM, dispositivos virtuales y hosts ESXi en momentos específicos o a los intervalos que le convengan.

## Iniciación manual de una exploración de hosts ESXi de vSphere
{: #vum-scanning-scan-hosts}

1. Pulse el botón **Explorar para actualizaciones**, seleccione **Parches y extensiones y actualizaciones** y luego pulse **Aceptar**.
2. Cuando se complete la exploración, seleccione **Parches de host críticos**. En el panel inferior, revise los detalles del parche para cada host pulsando el número en **Número de parches**. Una ventana muestra la información del parche.
3. Revíselo y repítalo para los **parches no críticos**.

  Los archivos de registro VUM se encuentran en la siguiente vía de acceso: _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_

## Iniciación manual de una exploración de máquinas y dispositivos virtuales
{: #vum-scanning-scan-vm-va}

Puede explorar VM y dispositivos virtuales en el inventario de vSphere frente a las líneas base y los grupos de línea base conectados. Las VM y los dispositivos que seleccione se exploran con las líneas base conectadas, en función de las opciones que seleccione. Se exploran todos los objetos hijo, por lo que cuanto mayor sea la infraestructura virtual y mayor en la jerarquía de objetos que inicia la exploración, más tiempo se tarda en realizar la exploración y más precisa es la vista de conformidad.

1.	Mediante el cliente web de vSphere, seleccione **Inicio** > **Máquinas y plantillas**.
2.	Pulse con el botón derecho del ratón en una _máquina virtual_, _dispositivo virtual_ o una _carpeta de máquinas y dispositivos virtuales_ y pulse **Explorar para actualizaciones**.
3.	Seleccione los tipos de actualizaciones que desee explorar. Las opciones son _Actualizaciones de dispositivos virtuales, actualizaciones de hardware de máquina virtual_ y _actualizaciones de VMware Tools_.
4.	Pulse **Explorar**.

##	Iniciación manual de una exploración de un objeto contenedor
{: #vum-scanning-scan-container}

Iniciar una exploración simultánea de hosts, VM virtuales y dispositivos virtuales explorando un objeto de contenedor que es un centro de datos o una carpeta de centro de datos.
1.	Mediante el cliente web de vSphere, seleccione **Inicio** > **Máquinas y plantillas**.
2.	Pulse con el botón derecho del ratón en _datacenter_ o _datacenter folder_ y pulse **explorar para actualizaciones**.
3.	Seleccione los tipos de actualizaciones que desee explorar. Las opciones son _Actualizaciones de dispositivos virtuales, actualizaciones de hardware de máquina virtual_ y _actualizaciones de VMware Tools_.
4.	Pulse **Explorar**.

##	Planificación de una exploración
{: #vum-scanning-schedule}

Puede configurar el cliente web de vSphere para explorar VM, dispositivos virtuales y hosts ESXi de vSphere en momentos específicos o a los intervalos que le convengan.

1.	Mediante el cliente web de vSphere, seleccione un objeto del inventario. También se exploran todos los objetos hijo del objeto que seleccione.
2.	Seleccione el **separador Supervisar** y pulse el botón **Valores**.
3.	Seleccione **Tareas planificadas** y pulse **Planificar una nueva tarea**.
4.	Seleccione **Explorar para actualizaciones** en la lista desplegable que aparece. Se abre el asistente Explorar actualizaciones.
5.	En la página Editar valores, seleccione los tipos de actualizaciones para los que desee explorar el objeto de inventario. Debe seleccionar al menos un tipo de exploración. En la página Planificar opciones, describa y planifique la tarea de exploración.
6.	Especifique un nombre exclusivo, y, opcionalmente, una descripción para la tarea de exploración. Pulse **Cambiar** para establecer la frecuencia y la hora de inicio de la tarea de exploración. Pulse **Aceptar**.
7.	La tarea de exploración aparece en la vista Tareas planificadas del cliente web de vSphere.

## Enlaces relacionados
{: #vum-scanning-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demostraciones)
