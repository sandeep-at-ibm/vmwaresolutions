---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Transferencia y corrección
{: #vum-staging}

Los parches y las extensiones se pueden realizar opcionalmente antes de la corrección para asegurarse de que se descarguen de VUM al host de vSphere ESXi sin aplicar los parches o las extensiones inmediatamente. Durante la corrección, VUM aplica los parches, las extensiones y las actualizaciones a los objetos de inventario. Los parches de transferencia y las extensiones aceleran el proceso de corrección porque los parches y las extensiones ya están disponibles localmente en los hosts.

Si durante el proceso de corrección un host no puede entrar en la modalidad de mantenimiento, VUM informa de un error y el proceso de corrección se detiene y falla. Los hosts ESXi de vSphere que ya se han corregido permanecen en el nivel actualizado.

Para que el proceso de corrección funcione sin problemas, es aconsejable inhabilitar algunas de las características de clúster como DPM, Control de Admisión de alta disponibilidad y Tolerancia de errores, así como desconectar cualquier dispositivo extraíble de las máquinas virtuales (VM) para evitar problemas de DRS al migrar las VM a otros hosts.
Además, mientras ejecuta el asistente de corrección, puede generar informes para verificar que no haya valores incoherentes en el nivel de host/VM que pueden hacer que falle el proceso de corrección.

1. Mediante el cliente web de vSphere, seleccione **Inicio** > **Hosts y clústeres**.
2. Pulse con el botón derecho del ratón en un centro de datos, clúster o host y, a continuación, pulse **Parches de transferencias**.
3. En la página de selección de línea base del asistente de transferencia, seleccione el parche y las líneas base de extensión para transferir.
4. Seleccione los hosts a los que se aplican los parches y las extensiones y pulse **Siguiente**. Si ha seleccionado transferir parches y extensiones a un único host, se selecciona de forma predeterminada.
5. Opcionalmente, desmarque los parches y las extensiones que desee excluir de la operación de transferencia. Para buscar dentro de la lista de parches y extensiones, escriba el texto en el recuadro de texto del recuadro Filtro. Pulse **Siguiente**.
6. Revise la página **Preparado para completar** y pulse **Finalizar**.

El número de parches y extensiones transferidos para el host específico se muestra en la columna Parches y extensiones en el panel inferior del separador Update Manager. Una vez que se haya completado correctamente una corrección, se suprimirán del host todos los parches y las extensiones transferidos, se instalen o no durante la corrección.
La corrección es el proceso en el que VUM aplica parches, extensiones y actualizaciones a hosts ESXi, VM o dispositivos virtuales de vSphere después de que se haya completado una exploración y de que los objetos seleccionados cumplan con los requisitos. Puede corregir los hosts, las VM o los dispositivos virtuales individuales o en una carpeta, clúster o un nivel de centro de datos. VUM admite la corrección de los siguientes objetos de inventario utilizando la corrección manual o la planificada:
* Los hosts ESXi para parches, extensiones y correcciones de actualización.
* Encendido, suspendido o apagado de VM y plantillas para las herramientas de VMware Tools y la actualización de hardware de VM.
* Encendido de dispositivos virtuales que se crean con VMware Studio 2.0 y posteriores, para la actualización de dispositivos virtuales.

Si la actualización lo requiere, los hosts se colocan en modalidad de mantenimiento antes de la corrección. El VCSA migra las VM a otros hosts dentro de la instancia de VMware vCenter Server on {{site.data.keyword.cloud}} antes de que el host se ponga en modalidad de mantenimiento.

## Para hosts de un clúster vSAN
{: #vum-staging-hosts-vsan}

Tenga en cuenta el comportamiento siguiente para los hosts que forman parte de un clúster vSAN:
* El proceso de corrección del host puede tardar mucho tiempo en completarse.
* Por diseño, solo el host de un clúster vSAN puede estar en modalidad de mantenimiento en cualquier momento.
* VUM corrige hosts que forman parte de un clúster VSAN de forma secuencial, incluso si establece la opción de corregir los hosts en paralelo.
* Las VM del host que utilicen una política de almacenamiento de VM con el valor 0 para **Número de anomalías tolerables**, es posible que el host experimente retrasos inusuales al entrar en la modalidad de mantenimiento. El retraso se produce porque la vSAN debe migrar los datos de la VM de un disco a otro en el clúster de almacén de datos de vSAN, y esto puede tardar muchas horas. Puede solucionarlo estableciendo el **Número de anomalías tolerables** en "1" para la política de almacenamiento de la máquina virtual, lo que dará lugar a la creación de dos copias de los archivos de la VM en el almacén de datos de vSAN.
* Si alguna VM del host utiliza una política de almacenamiento de VM con el valor 1 para **Número de anomalías tolerables**, la VM pasará a ser no redundante cuando el host entre en modalidad de mantenimiento. Si esto no es aceptable, consulte [Redundancia de vSAN de máquina Virtual](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-vsan-redundancy).

Para corregir los hosts y clústeres, siga estos pasos:
1. Utilice el cliente web de vSphere, seleccione **Inicio** > **Hosts y Clústeres**.
2. Desde el navegador de objetos de inventario, seleccione un centro de datos, un clúster o un host, pulse el separador **Actualizar gestor** y pulse **Corregir**. Si ha seleccionado un objeto contenedor, se corrigen todos los hosts bajo el objeto seleccionado. Se abre el asistente Corregir.
3. Seleccione **Líneas base de parche** o **Líneas base de extensión** en función del tipo de actualización que desee realizar en el host. En la página Seleccionar línea base del asistente Corregir, seleccione el **grupo de línea base** y las **líneas base** que desee aplicar.
4. Seleccione los hosts de destino que desee corregir y pulse **Siguiente**. Si opta por corregir un único host y no un objeto contenedor, el host está seleccionado de forma predeterminada.
5. De forma opcional, en la página **Parches y extensiones**, desmarque los parches o extensiones específicos para excluirlos del proceso de corrección y pulse **Siguiente**.
6. De forma opcional, en la página **Opciones avanzadas**, seleccione la opción de programar la corrección para más tarde y especifique un nombre único y una descripción opcional para la tarea. El tiempo que se establece para la tarea planificada es el tiempo en el VCSA. Opcionalmente, seleccione la opción para ignorar los avisos sobre los dispositivos no admitidos en el host ni los que ya no admitan el almacén de datos VMFS para continuar con la corrección. Pulse **Siguiente**.
7. En la página **Opciones de corrección** del host, en el menú desplegable **Estado de alimentación de la máquina virtual**, puede seleccionar el cambio en el estado de alimentación de las VM y de los dispositivos virtuales que se ejecutan en los hosts que se van a corregir. Un host no puede especificar la modalidad de mantenimiento hasta que las VM del host estén apagadas, suspendidas o migradas con vMotion a otros hosts en un clúster DRS. Algunas actualizaciones requieren que un host entre en modalidad de mantenimiento antes de la corrección. Las VM y los dispositivos no se pueden ejecutar cuando un host está en modalidad de mantenimiento. Para reducir el tiempo de inactividad de corrección de host a expensas de la disponibilidad de la VM, puede optar por concluir o suspender VM y dispositivos virtuales antes de la corrección. En un clúster DRS, si no apaga las VM, la corrección requiere más tiempo, pero las VM están disponibles durante todo este proceso porque se migran con vMotion a otros hosts. Las selecciones son las siguientes:

- **Apagar máquinas virtuales**: apagar todas las VM y dispositivos virtuales antes de la corrección.
- **Suspender máquinas virtuales**: suspender todas las VM y dispositivos virtuales en ejecución antes de la corrección.
- **No cambiar el estado de la máquina virtual**: dejar las VM y dispositivos virtuales en su estado de alimentación actual.

8. Opcionalmente, seleccione **Inhabilitar cualquier dispositivo de soporte extraíble conectado a la máquina virtual en el host**. VUM no corrige los hosts en los que las VM tienen unidades de CD, DVD o disquete conectadas. En entornos de clúster, los dispositivos de soporte conectados pueden impedir la vMotion si el host de destino no tiene un dispositivo idéntico o una imagen ISO montada, lo que a su vez impide que el host de origen entre en modalidad de mantenimiento. Después de la corrección, VUM vuelve a conectar los dispositivos de soporte extraíbles si todavía están disponibles.
9. Opcionalmente, seleccione **Volver a intentar especificar la modalidad de mantenimiento en caso de error**, especifique el número de reintentos y especifique el tiempo que se debe esperar entre reintentos. VUM espera el período de retraso de reintento y vuelva a intentar poner el host en modo de mantenimiento las veces que lo indique en el campo Número de reintentos.

No hay ningún requisito en una instancia de vCenter Server para seleccionar el recuadro de selección en Valores de parche de ESXi para permitir que el gestor de actualizaciones se active con los hosts ESXi encendidos con arranque PXE.
10. Pulse **Siguiente**.
11. Si ha corregido los hosts en un clúster, edite las opciones de corrección del clúster. La página **Opciones de corrección del clúster** solo está disponible cuando se corrigen los clústeres. Puede seleccionar las opciones siguientes:
* **Inhabilite la gestión de alimentación distribuida (DPM)** si está habilitada para cualquiera de los clústeres seleccionados: VUM no corregirá los clústeres con DPM activo. DPM supervisa el uso de recursos de las VM en ejecución en el clúster. Si hay suficiente exceso de capacidad, el DPM recomienda mover las VM a otros hosts del clúster y colocar el host original en modalidad de espera para conservar la alimentación. La extracción de hosts en modalidad de espera puede interrumpir la corrección.
* **Inhabilite el control de admisión de alta disponibilidad** si está habilitado para cualquiera de los clústeres seleccionados: VUM no corregirá clústeres con el control de admisión de alta disponibilidad activo. El control de admisión es una política que utiliza la alta disponibilidad de VMware para garantizar la capacidad de migración tras error dentro de un clúster. Si el control de admisión de alta disponibilidad durante la corrección, es posible que las VM dentro de un clúster no se migren con vMotion.
* **Inhabilite la tolerancia a errores** si está habilitada. Esto afecta a todas las VM con tolerancia a errores en los clústeres seleccionados. Si se activa la tolerancia a errores para cualquiera de las VM de un host, VUM no corregirá dicho host. Para habilitar la tolerancia a errores, los hosts en los que se ejecutan las VM primarias y secundarias deben ser de la misma versión y tener el mismo parche instalado. Si aplica parches diferentes a estos hosts, no se puede volver a habilitar la tolerancia a errores.
* **Habilitar la corrección en paralelo para los hosts en los clústeres seleccionados**: Corrige los hosts en clústeres de forma paralela. Si el valor no está seleccionado, VUM corregirá secuencialmente los hosts de un clúster. Puede seleccionar una de las opciones siguientes para la corrección en paralelo:
  - Puede dejar que VUM evalúe continuamente la cantidad máxima de hosts que puede corregir simultáneamente sin interrumpir los valores de DRS.
  - Puede especificar un número límite de hosts corregidos simultáneamente en cada clúster que haya corregido. Tenga en cuenta que VUM corregirá de forma simultánea solo los hosts en los que las VM estén apagadas o suspendidas. Puede apagar o suspender las VM desde el menú Estado de alimentación de VM en el panel Opciones de modalidad de mantenimiento de la página Opciones de corrección de host. Por diseño, solo el host de un clúster vSAN puede estar en modalidad de mantenimiento en cualquier momento. VUM corrige los hosts que forman parte de un clúster vSAN secuencialmente, incluso si selecciona la opción de corregirlos en paralelo.
* **Migre las máquinas virtuales apagadas y suspendidas a otros hosts del clúster** si un host debe entrar en modalidad de mantenimiento. El gestor de actualizaciones migra las VM suspendidas y apagadas de los hosts que deben especificar la modalidad de mantenimiento en otros hosts del clúster. Puede optar por apagar o suspender las VM antes de la corrección en el panel **Valores de modalidad de mantenimiento**.
12. En la página Preparado para completar, puede pulsar **Prever corrección** para generar un informe de opciones de corrección de clúster y pulsar **Aceptar**. Se abre un recuadro de diálogo de opciones de corrección del clúster. Puede exportar el informe o copiar las entradas de su propio registro y pulsar **Siguiente**.
13. Revise la página **Preparado para completar** y pulse **Finalizar**.

## Enlaces relacionados
{: #vum-staging-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demostraciones)
