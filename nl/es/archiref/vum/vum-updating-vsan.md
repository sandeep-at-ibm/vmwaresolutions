---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

# Actualización de clústeres vSAN
{: #vum-updating-vsan}

vSAN genera líneas base de sistema y grupos de línea base para su uso con VUM y puede utilizar estas líneas base recomendadas para actualizar software, parches y extensiones para los hosts vSphere ESXi de la instancia de VMware vCenter Server on {{site.data.keyword.cloud_notm}} utilizando vSAN. vSAN 6.6.1 y posterior generan recomendaciones automáticas más adelante para clústeres vSAN. vSAN combina información en la Guía de compatibilidad de VMware y en el catálogo Release de vSAN con información sobre los releases de vSphere ESXi instalados.

Estas actualizaciones recomendadas proporcionan el mejor release disponible para mantener el hardware en un estado admitido.
* **Líneas base de sistema VSAN**: las recomendaciones de compilación de vSAN se proporcionan a través de las líneas base del sistema vSAN para VUM. vSAN genera un grupo de línea base para cada clúster vSAN, que se muestran en el panel Líneas base del separador Líneas base y grupos. VUM explora automáticamente cada clúster vSAN para comprobar la conformidad con el grupo de línea base. Sin embargo, para actualizar el clúster vSAN, debe corregir manualmente la línea base del sistema. Mediante VUM, puede solucionar la línea base del sistema vSAN en un único host o en todo el clúster.
* **Catálogo de release vSAN**: el catálogo de releases de vSAN mantiene información sobre los releases disponibles, el orden de preferencias para los releases y los parches críticos necesarios para cada release. vSAN requiere conectividad a Internet para acceder al catálogo de releases. No es necesario estar inscrito en el Programa de mejora de la experiencia del cliente (CEIP) para que vSAN acceda al catálogo de releases.
* Trabajar con **Recomendaciones de compilaciones de vSAN**:VUM comprueba los releases de ESXi de vSphere instalados en la información de la lista de compatibilidad de hardware (HCL) en la guía de compatibilidad de VMware. Determina la vía de acceso de actualización correcta para cada clúster vSAN, basándose en el catálogo de release vSAN actual. vSAN también incluye las actualizaciones de controladores y parches para el release recomendado en su línea base de sistema. Las recomendaciones de compilación vSAN garantizan que cada clúster vSAN permanece en el estado de compatibilidad de hardware actual o mejor. Si el hardware del clúster vSAN no se incluye en HCL, vSAN recomienda una actualización a la última versión.

La actualización del clúster de vSAN se realiza en la secuencia de tareas siguientes:
* **Habilitar el flujo de trabajo de estado en línea de vSAN**: este flujo de trabajo habilita las líneas base vSAN en VUM de modo que las actualizaciones se puedan revisar y corregir. Es necesario que se lleve a cabo inicialmente solo para habilitar vSAN con VUM
* **Requisitos previos**: Comprender los requisitos previos, el proceso y las restricciones
* **Actualizar el vCenter Server Appliance**. Para obtener más información, consulte [Actualización de VCSA y vCenters enlazados con SSO](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa).
* **Actualizar los hosts ESXi de vSphere**: Para obtener más información, consulte [Creación de líneas base y cómo adjuntarlas a objetos de inventario](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines).
* **Actualizar el formato de disco de vSAN**: Consulte Actualizar el formato de disco de vSAN. La actualización del formato de disco es opcional, pero para obtener los mejores resultados, actualice los objetos para que utilicen la última versión. El formato en disco expone su entorno a todo el conjunto de características de vSAN.

## Habilitar el flujo de trabajo de estado en línea de vSAN
{: #vum-updating-vsan-enable-vsan-workflow}

Utilice las tareas de la sección siguiente para hacer que las líneas base vSAN estén disponibles en VUM. vSAN 6.6.1 y posterior proporciona un proceso de actualización automatizado para garantizar que un clúster de vSAN esté actualizado con el mejor release disponible para mantener la instancia de VMware vCenter Server on {{site.data.keyword.cloud_notm}} en un estado soportado con:
* **Recomendaciones de la versión vSAN**: se generan automáticamente mediante la información de la Guía de compatibilidad de VMware, el Catálogo de releases vSAN y detección de la configuración de hardware subyacente. Esto también incluye los controladores necesarios y las actualizaciones de parches para el release recomendado en su línea base del sistema.
* **Recomendaciones de compilación vSAN**: garantiza que los clústeres permanezcan en el estado actual de compatibilidad de hardware o en mejores condiciones.

Asegúrese de que el VCSA sea vCenter 6.5 Parche 2 o versión más nueva antes de continuar, ya que esto arregla algunos problemas de uso de proxy. Para obtener más información, consulte [Actualización de VCSA y vCenters enlazados con SSO](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa).

Para ver las actualizaciones de vSAN en VUM, se sigue el flujo de trabajo de estado en línea de vSAN. Por lo tanto, vSAN Online Health necesita conectarse a `vcsa.vmware.com` y a `vmware.com` para realizar estas comprobaciones de estado en línea para habilitar el flujo de trabajo de estado en línea de vSAN que necesitamos:
* Configurar el VCSA para que utilice el proxy.
* Configurar vSAN para que utilice el proxy.
* Habilitar el Programa de mejora de la experiencia del cliente (CEIP).
* Realizar una carga de prueba y valide que la carga ha funcionado.

El primer paso consiste en añadir las credenciales de my.vmware.com al motor de recomendaciones de compilación vSAN. Después de un inicio de sesión satisfactorio, vSAN genera un grupo de línea base de actualizaciones recomendadas para cada clúster vSAN. Las líneas base de sistema vSAN se muestran en el panel de líneas base del separador Líneas y grupos.

### Configurar el VCSA para que utilice el proxy
{: #vum-updating-vsan-config-vcsa-proxy}

1.	Desde el navegador web del servidor de gestión, conéctese a la interfaz de gestión de VCSA `https://<vCenter ip>:5480`
2.	Mediante las credenciales de la consola de IBM Cloud for VMware Solutions, inicie sesión en la interfaz de gestión de VCSA como usuario root.
3.	En la interfaz de gestión de dispositivos del servidor de vCenter, pulse **Redes** y pulse **Gestionar**.
4.	Para configurar un servidor proxy, pulse **Editar** en el panel Valores de proxy.
5.	Seleccione **Utilizar un servidor proxy**, especifique los valores del servidor proxy y pulse **Aceptar**.

Ha habido informes en los que la información de proxy solo se establece para HTTP pero no para HTTPS. Para configurar la información de proxy también para el tráfico HTTPS, debe habilitarse en primer lugar. Después de iniciar una sesión en el VCSA mediante SSH, utilice el mandato proxy.get para ver la configuración y confirme que los parámetros HTTPS no están establecidos.

Si los parámetros HTTPS no están establecidos, utilice el mandato siguiente:
  `proxy.set --protocol https --server ``<proxy ip>`` --port 3128`

### Configure vSAN para utilizar el proxy
{: #vum-updating-vsan-config-vsan-proxy}

1. Vaya a **Inicio** > **Hosts y clústeres**, seleccione el **clúster vSAN** en el panel de navegación y, a continuación, seleccione el separador **Configurar** y vaya a **vSAN** y, a continuación, **General**. Desplácese hasta la sección **Conectividad de Internet** y pulse **Editar**.
2. Especifique la dirección IP y el número de puerto del proxy, pulse **Aceptar**.

### Habilitar el Programa de mejora de la experiencia del cliente (CEIP)
{: #vum-updating-vsan-enable-ceip}

Este es un paso opcional. Al utilizar el cliente web de vSphere, vaya a **Inicio** > **Administración** > **Programa de mejora de la experiencia del cliente** y, a continuación, pulse **Unirse**.

### Realizar una carga de prueba y validar que la carga ha funcionado
{: #vum-updating-vsan-complete-upload}

1. Al utilizar el cliente web de vSphere, vaya a **Inicio** > **Hosts y clústeres**. Seleccione el clúster necesario, seleccione a continuación el separador **Supervisar** y la página **vSAN** y, a continuación, pulse
**Estado**. Pulse **Habilitar estado en línea**.
2. Pulse **Volver a probar** y espere a que se complete el proceso.
3. Aparece una nueva marca de comprobación en Estado denominada _Conectividad de estado en línea_ y **Habilitar estado en línea** cambia a **Volver a probar con estado en línea**.
4. Pulse **Volver a probar con estado en línea** para iniciar la primera carga y espere a que se complete el proceso, revisando el estado en el panel Tareas recientes. El nombre de la prueba cambia a Estado en línea (última comprobación: ahora mismo).
5. Cuando se haya completado, en la ventana Estado, desplácese hasta la Recomendación de compilación de vSAN, expándala y pulse **Estado de motor de recomendación de compilación de vSAN**.
6. Pulse **Iniciar sesión en my.vmware.com** y especifique sus credenciales. Cuando se completa el proceso, el **Resultado de la prueba** cambia al estado **Pasado**.
7. Pulse el separador **Update Manager** y el clúster vSAN se añadirá a las líneas base.

## Requisitos previos
{: #vum-updating-vsan-prereq}

Antes de comenzar el proceso de actualización de vSAN, asegúrese de que se cumplan los requisitos siguientes:
* Revise los artículos de la base de conocimientos de VMware y revise los problemas de compatibilidad conocidos entre la versión de vSAN actual y la versión de vSAN de destino deseada
* **El entorno de vSphere está actualizado**:
  - El VCSA debe estar en un nivel de parche igual o superior al de los hosts de ESXi de vSphere. Actualice VCSA si es necesario
  - Todos los hosts deben ejecutar la misma versión de ESXi. Si las versiones del host ESXi de vSphere no coinciden, actualícelo
* **Todos los discos vSAN deben estar en buen estado**:
  - No hay ningún disco que falle ni falta ningún disco. Esto se puede determinar en la vista **Gestión de discos vSAN** en el cliente web de vSphere. **Inicio** > **Hosts y clústeres**, seleccione luego el **Clúster vSAN** y pulse el separador **vSAN** y, a continuación, **Discos físicos**. Desplácese por todos los discos y revise el estado de salud de vSAN.
  - No hay objetos vSAN inaccesibles. Esto se puede verificar con el **Servicio de estado vSAN** pulsando **Inicio** > **Hosts y clústeres** y, a continuación, seleccione el **clúster vSAN**. Pulse el separador **Supervisar**, **vSAN** y, a continuación, pulse **Estado**. Revise los resultados de la prueba.
  - No hay ninguna resincronización activa al principio del proceso de actualización; pulse **Inicio** > **Hosts y clústeres** y seleccione el **Clúster vSAN**, pulse el separador **vSAN** y, a continuación, pulse **Componentes de resincronización**. _El recuento de componentes de resincronización debe ser 0_. Se espera cierta actividad de resincronización durante el proceso de actualización, ya que los datos deben sincronizarse después de que se haya reiniciado el host.
* **Preparación del host ESXi de vSphere**: cuando mueva un host a la modalidad de mantenimiento en un clúster vSAN, tiene tres opciones:
  - **Sin migración de datos**: si selecciona esta opción, vSAN no evacuará ningún dato de este host. Si apaga o elimina el host del clúster, es posible que no pueda acceder a algunas máquinas virtuales (VM).
  - **Garantizar la disponibilidad**: si selecciona esta opción, vSAN le permite mover el host a la modalidad de mantenimiento más rápidamente que la migración de datos completa y permite el acceso a las VM del entorno.
  - **Migración de datos completa**
* **Salir de la modalidad de mantenimiento y resincronización**: cuando el host de vSphere ESXi se actualiza y se mueve fuera de la modalidad de mantenimiento, se produce una resincronización. Puede verlo mediante el cliente web. Asegúrese de que se haya completado antes de pasar al siguiente host. Se está produciendo una resincronización, ya que el host que se ha actualizado ahora puede volver a contribuir al almacén de datos de vSAN. Es vital esperar a que esta resincronización se haya completado para asegurarse de que no se hayan perdido datos.
* **Después de empezar una actualización del clúster vSAN**:
  - No intente actualizar un clúster mediante la introducción de nuevas versiones en el clúster y la migración de cargas de trabajo.
  - Si se introducen nuevos hosts, asegúrese de que sean de la misma versión inicial y de actualizarlos junto con el resto del clúster.
  - Si añade o sustituye discos durante una actualización, asegúrese de que se hayan formateado con la versión del formato en disco existente adecuado, según sea necesario.
  - Por lo tanto, determinados cambios de comportamiento de vSAN están controlados por el formato en disco y es importante que no se introduzcan versiones de formato en disco más nuevos en un clúster de versiones mixtas.

## Actualizar el vCenter Server Appliance
{: #vum-updating-vsan-upgrade-vcsa}

Para obtener más información, consulte [Actualización de VCSA y vCenters enlazados con SSO](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa).

##	Actualizar los hosts ESXi de vSphere
{: #vum-updating-vsan-upgrade-hosts}

Para obtener más información, consulte [Creación de líneas base y cómo adjuntarlas a objetos de inventario](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines).

##	Actualizar el formato de disco de vSAN
{: #vum-updating-vsan-upgrade-vsan}

La consola de Ruby vSphere (RVC) es una interfaz de línea de mandatos basada en Ruby para vSphere y se puede utilizar para gestionar VMware vSphere ESXi y vCenter. El inventario de vSphere se presenta en una estructura de árbol, lo que le permite navegar y ejecutar mandatos en objetos de vCenter.

Muchas tareas administrativas básicas se pueden realizar de forma mucho más eficiente que pulsar en el vSphere Client. RVC se implementa totalmente en el VCSA y se le acusa de una conexión SSH con el dispositivo.
1. Ejecute SSH en VCSA e inicie sesión utilizando la raíz y la contraseña que se proporciona en la consola de ICVS.
2. En el indicador, escriba: `rvc Administrator@vsphere.local@localhost` y pulse **Intro**.
3. Especifique la contraseña del administrador que se proporciona en la consola de ICVS. Ahora estará en la raíz del sistema de archivos virtual, escriba ls y, a continuación, pulse **Intro**; verá lo siguiente:
  `0 /
  1 localhost/``

5. Escriba `cd 1`, especifique y, a continuación, `ls` y pulse **Intro**. Verá lo siguiente: `0/datacenter1 (centro de datos)`

6. Escriba `cd 0`, especifique y, a continuación, `ls` y pulse **Intro**. Verá lo siguiente:

  `0 storage/  1 computers [host]/  2 networks [network]/  3 datastores [datastore]/  4 vms [vm]/`

7. Escriba `cd 1`, pulse **Intro** y, a continuación, `ls` y pulse **Intro**. Verá el clúster: `0 cluster1 (clúster)` `

8. Utilice los mandatos VSAN sobre este clúster. Para comprobar el tipo de estado de disco escriba `vsan.disks_stats 0` y pulse **Intro**.

9. Asegúrese de que todos los discos estén en buen estado. A continuación, inicie la actualización escribiendo `vsan.ondisk_upgrade 0` y pulse **Intro**.

10. En función del tamaño de vSAN, esta tarea puede tardar un montón de tiempo. Cuando se haya completado, escriba `vsan.objstatusreport 0` y, a continuación, pulse **Intro** para verificar que las versiones de objeto se hayan actualizado al nuevo formato en disco.

11. La actualización del clúster VSAN se ha completado. Escriba `exit` y pulse **Intro** para salir de RVC.

## Enlaces relacionados
{: #vum-updating-vsan-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (demostraciones)
