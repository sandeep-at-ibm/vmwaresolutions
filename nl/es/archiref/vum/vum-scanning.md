---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-03"

---

# Exploración y revisión

Cuando explora hosts, máquinas virtuales y dispositivos virtuales, los evalúa frente a las líneas base y los grupos de línea base para determinar su nivel de conformidad. Se escanean los objetos de inventario y se revisan los resultados para determinar la forma en que cumplen con las líneas base y los grupos de línea base. Los resultados de la exploración se pueden filtrar por búsqueda de texto, selección de grupos, selección de línea base y selección de estado de conformidad. Puede iniciar los escaneos siguientes:
*	**Inicie manualmente una exploración de hosts ESXi de vSphere**: puede explorar hosts de ESXi en el inventario de vSphere frente a las líneas base y los grupos de línea base conectados.
*	**Inicie manualmente una exploración de máquinas y dispositivos virtuales**: puede explorar máquinas y dispositivos virtuales en el inventario de vSphere frente a las líneas base y los grupos de línea base conectados.
*	**Inicie manualmente una exploración de un objeto de contenedor**: inicie una exploración simultánea de hosts, máquinas y dispositivos virtuales, explorando un objeto contenedor que es un centro de datos o una carpeta de centro de datos.
*	**Planifique una exploración**: puede configurar el cliente web de vSphere para explorar máquinas virtuales, dispositivos virtuales y hosts ESXi en momentos específicos o a los intervalos que le convengan.

##	Iniciación manual de una exploración de hosts ESXi de vSphere

1.	Pulse el botón **Explorar para actualizaciones** y seleccione **Parches y extensiones y actualizaciones** y, a continuación, pulse **Aceptar**.
2.	Cuando se complete la exploración, seleccione **Parches de host críticos** y la revisión de los puntos débiles de cada host
3.	Al pulsar el número en el Número de parches, una ventana muestra el detalle del parche.
4.	Revíselo y repítalo para los **parches no críticos**.

Tenga en cuenta que los archivos de registro VUM se pueden localizar en _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_

##	Iniciación manual de una exploración de máquinas y dispositivos virtuales

Puede explorar máquinas y dispositivos virtuales en el inventario de vSphere frente a las líneas base y los grupos de línea base conectados. Las máquinas y los dispositivos virtuales que seleccione se exploran con las líneas base conectadas, en función de las opciones que seleccione. También se exploran todos los objetos hijo, por lo que cuanto mayor sea la infraestructura virtual y mayor en la jerarquía de objetos que inicia la exploración, más tiempo se tarda en realizar la exploración y más precisa es la vista de conformidad.

1.	Mediante el cliente web de vSphere, seleccione **Inicio** > **Máquinas y plantillas**.
2.	Pulse con el botón derecho del ratón en una _máquina virtual_, _ dispositivo virtual_ o una _ carpeta de máquinas y dispositivos virtuales _ y pulse **Explorar para actualizaciones**.
3.	Seleccione los tipos de actualizaciones que desee explorar. Las opciones son _Actualizaciones de dispositivos virtuales, actualizaciones de hardware de máquina virtual_ y _actualizaciones de VMware Tools_.
4.	Pulse **Explorar**.

##	Iniciación manual de una exploración de un objeto contenedor

Iniciar una exploración simultánea de hosts, máquinas virtuales y dispositivos virtuales explorando un objeto de contenedor que es un centro de datos o una carpeta de centro de datos.
1.	Mediante el cliente web de vSphere, seleccione **Inicio** > **Máquinas y plantillas**.
2.	Pulse con el botón derecho del ratón en _datacenter_ o _datacenter folder_ y pulse **explorar para actualizaciones**.
3.	Seleccione los tipos de actualizaciones que desee explorar. Las opciones son _Actualizaciones de dispositivos virtuales, actualizaciones de hardware de máquina virtual_ y _actualizaciones de VMware Tools_.
4.	Pulse **Explorar**.

##	Planificación de una exploración

Puede configurar el cliente web de vSphere para explorar máquinas virtuales, dispositivos virtuales y hosts ESXi de vSphere en momentos específicos o a los intervalos que le convengan.

1.	El uso del cliente web de vSphere selecciona un objeto del inventario. También se exploran todos los objetos hijo del objeto que seleccione.
2.	Seleccione el **separador Supervisar** y pulse el botón **Valores**.
3.	Seleccione **Tareas planificadas** y pulse **Planificar una nueva tarea**.
4.	Seleccione **Explorar para actualizaciones** en la lista desplegable que aparece. Se abre el asistente Explorar actualizaciones.
5.	En la página Editar valores, seleccione los tipos de actualizaciones para los que desee explorar el objeto de inventario. Debe seleccionar al menos un tipo de exploración. En la página Planificar opciones, describa y planifique la tarea de exploración.
6.	Especifique un nombre exclusivo, y, opcionalmente, una descripción para la tarea de exploración. Pulse **Cambiar** para establecer la frecuencia y la hora de inicio de la tarea de exploración. Pulse **Aceptar**.
7.	La tarea de exploración aparece en la vista Tareas planificadas del cliente web de vSphere.

### Enlaces relacionados

* [VMware HCX on IBM Cloud Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demos)
