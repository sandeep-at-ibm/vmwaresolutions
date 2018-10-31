---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-05"

---

#	Actualizaciones orquestadas

Puede utilizar actualizaciones orquestadas para actualizar el hardware virtual y las herramientas de VMware de máquinas virtuales en el inventario después de actualizar los hosts ESXi de vSphere. Una vez que se han actualizado los hosts, primero se ejecuta la línea base de actualización de VMware Tools, seguido de la línea base de actualización de hardware de la máquina. Las actualizaciones orquestadas se pueden realizar en un clúster, una carpeta o un nivel de centro de datos.

VUM le permite realizar actualizaciones orquestadas de hosts y de máquinas virtuales utilizando grupos de línea base. Se utiliza un grupo de línea base que contiene una sola línea base de actualización de host y varias líneas base de parche o extensión. VUM primero actualiza los hosts y después aplica el parche o las líneas base de extensión. Para realizar una actualización orquestada de máquinas virtuales, utilice un grupo de línea base de máquina virtual que contenga las siguientes líneas base:
* Actualización de VM Hardware para que coincida con el host
* Actualización de VMware Tools para que coincida con el host

Las actualizaciones orquestadas de VUM le permiten actualizar los objetos de inventario en VCSA en un proceso de dos pasos. En primer lugar, los hosts de vSphere ESXi se actualizan después de las actualizaciones de la máquina virtual. Este proceso de dos pasos se puede configurar en un nivel de clúster o puede configurarlo en el host de vSphere ESXi individual o en el nivel de máquina virtual para un control más granular.

En la actualización orquestada, el clúster se corregirá primero frente al grupo de línea base de host, que aplica parches, extensiones y actualizaciones y, una vez actualizado, las máquinas virtuales del clúster se corrigen frente al grupo de línea base de actualización de la máquina virtual que contiene la actualización de hardware de VM para que coincida con las líneas base de Host y VMware Tools.

Si el grupo de línea base también contiene una línea base de actualización, VUM actualiza primero los hosts ESXi de vSphere y después aplica el parche y/o las líneas base de extensión ya que los parches son aplicables a la versión específica del host. Para las máquinas virtuales, primero se actualizan las herramientas de VMware y después se actualiza el hardware virtual.

Por lo tanto, durante la actualización de las herramientas de VMware, si las máquinas virtuales están en estado apagado o suspendido, VUM las encenderá, ejecutará la actualización y restaurará el estado de alimentación original de la máquina virtual. Por lo tanto, si durante la actualización de hardware virtual, las máquinas virtuales deben estar en estado apagado si hay máquinas virtuales encendidas, VUM las cerrará, actualizará el hardware virtual y encenderá la alimentación de nuevo.

De forma predeterminada, la corrección de los hosts de vSphere ESXi se realiza de forma secuencial y se corregirá un host a la vez. Cuando el proceso se haya completado para un host, VUM empezará a corregir el siguiente host. Este valor predeterminado se puede cambiar para habilitar la corrección en paralelo de modo que se pueda corregir más de un host a la vez, sin embargo, esto solo es posible si tiene la capacidad de migración tras error adecuada en el clúster.

Si los hosts de vSphere ESXI forman parte de un clúster vSAN, el proceso de corrección siempre es secuencial incluso si ha seleccionado la corrección en paralelo en el asistente de corrección, ya que solo un host de un clúster vSAN puede estar en modalidad de mantenimiento en cualquier momento. VUM es inteligente y lleva a cabo un cálculo del número de hosts que se pueden corregir en paralelo sin interrumpir la configuración de DRS.

De forma alternativa, puede definir el límite para el número de hosts que se pueden corregir en paralelo durante el asistente de corrección.

El flujo de trabajo siguiente describe el proceso para realizar una actualización orquestada:

## Paso 1

1. Utilice el cliente web de vSphere para iniciar la sesión en VCSA.
2. Seleccione **Inicio** > **Actualizar gestor** y en el **separador Objetos**, seleccione una **instancia de Update Manager**.
3. Pulse el **separador Gestionar** y, a continuación, el **separador Líneas base de host** y pulse **Nuevo grupo de línea base**.
4. Especifique un nombre exclusivo para el grupo de línea base y pulse **Siguiente**.
5. Seleccione una línea base de actualización de host para incluirlo en el grupo de línea base.
6. Opcionalmente, cree una nueva línea base de actualización de host pulsando **Crear una nueva línea base de actualización de host** en la parte inferior de la página Actualizaciones y complete el asistente de Nueva línea base. Pulse **Siguiente**.
7. Seleccione las líneas base de parche que desee incluir en el grupo de línea base.
8. Opcionalmente, cree una línea base de parche nueva pulsando **Crear una nueva línea base de parche de host** en la parte inferior de la página Parches y complete el asistente Línea base nueva. Pulse **Siguiente**.
9. Seleccione las líneas base de extensión que desee incluir en el grupo de línea base.
10. Opcionalmente, cree una nueva línea base de actualización de extensión pulsando **Crear una nueva línea base de extensión** en la parte inferior de la página Actualizaciones y complete el asistente de Nueva línea base.
11. Revise la página Preparado para completar, pulse **Finalizar** y el grupo de línea base de host se muestra en el panel Grupos de línea base.

## Paso 2

1. Cree un grupo de línea base de máquina virtual que contenga la línea base de actualización de VMware Tools para que coincida con la línea base de host y la actualización de hardware de VM para que coincida con la línea base del host, vista VMware Tools.
2. Adjunte el grupo de línea base a un objeto contenedor de vCenter que contenga las máquinas virtuales que desee actualizar.
3. Explore el objeto contenedor para ver el estado de conformidad de las máquinas virtuales en el contenedor. Puede iniciar la exploración manualmente o planificar una tarea de exploración.
4. Revise los resultados de la exploración que se muestran en la vista Conformidad de cliente VUM.
5. Corrija las máquinas virtuales no conformes en el objeto contenedor para que cumplan con el grupo de línea base adjunto. Puede iniciar la corrección manualmente o planificar una tarea de corrección.
* Durante una actualización de VMware Tools, las máquinas virtuales deben estar encendidos. Si una máquina virtual está en un estado apagado o suspendido antes de la corrección, VUM enciende en la máquina. Una vez finalizada la actualización, VUM reinicia la máquina y restaura el estado de alimentación original de la máquina virtual.
* Durante una actualización de hardware de máquina virtual, deben cerrarse las máquinas virtuales. Una vez finalizada la corrección, VUM restaura el estado de alimentación original de las máquinas virtuales. Si una máquina virtual está encendida, VUM se desactiva de la máquina, actualiza el hardware virtual y, a continuación, se enciende en la máquina virtual.

Ahora puede utilizar estos grupos de línea base en los procesos de exploración, revisión, transferencia y corrección.

### Enlaces relacionados

* [VMware HCX on IBM Cloud Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demos)
