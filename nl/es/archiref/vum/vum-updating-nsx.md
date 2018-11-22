---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Actualización de NSX

Esta sección se ha añadido a este documento para proporcionarle un tipo de proceso de actualización para NSX. Debe consultar la guía de VMware correspondiente al proceso de actualización de la versión de NSX a la que está actualizando.

Si tiene que actualizar NSX y vSphere, VMware recomienda completar primero la actualización de NSX y, a continuación, completar la actualización de vSphere como VIB de NSX ya que son específicos de la versión de ESXi que está instalada en el host. Sin embargo, se recomienda utilizar VUM, tal como se documenta en este documento. Si se realiza manualmente, siga este flujo de trabajo, un host cada vez:

1. **Actualizar ESXi**: una vez que finalice la actualización de ESXi, el host sale de la modalidad de mantenimiento; sin embargo, no puede mover las VM conectadas a los conmutadores lógicos al host hasta que se haya completado el siguiente paso.
2. **Actualizar VIB de NSX**: una vez que se hayan actualizado los VIB y que el host se haya eliminado de la modalidad de mantenimiento, puede mover las VM conectadas a los conmutadores lógicos al host.

NSX se actualiza mediante la actualización de NSX Manager, que se descarga de _my.vmware.com_. Por lo tanto, necesita una cuenta en la descarga de la actualización. Si consume licencias de suscripción de {{site.data.keyword.cloud}} con la instancia de VMware vCenter Server on {{site.data.keyword.cloud_notm}}, no podrá descargar las actualizaciones con la cuenta de **my.vmware.com**. Por lo tanto, debe [ponerse en contacto con el soporte de IBM](../../vmonic/trbl_support.html).

Antes de empezar la actualización, compruebe las notas del release de NSX ya que allí se documentan problemas conocidos de actualización y sus soluciones temporales.release de NSX. Mediante las notas del release, verifique que vCenter cumple con los nuevos requisitos del sistema para NSX.

Si ha instalado algún software adicional de los socios de VMware, consulte la documentación del socio para ver los detalles de la compatibilidad y la actualización. Si ha desplegado las instancias primaria y secundaria de vCenter Server y tiene un entorno NSX entre varios vCenter, consulte las notas del release del proceso de actualización correcto.

En un entorno NSX entre vCenter, el dispositivo primario NSX Manager se actualiza primero, seguido de todos los dispositivos NSX Manager secundarios.
**No se admiten degradaciones**, por lo que debe realizar una copia de seguridad de NSX Manager antes de continuar con una actualización. Se realiza una copia de seguridad de todas las configuraciones de NSX Edge, direccionadores lógicos y pasarelas de servicios de extremo como parte de la copia de seguridad de NSX Manager.

Una vez que NSX Manager se ha actualizado correctamente, NSX no se puede degradar. Se aconseja que cualquier actividad de mantenimiento se lleve a cabo en una ventana de mantenimiento acordada, por lo tanto, siga las instrucciones de su empresa. Se recomienda que todos los componentes de NSX se actualicen en una única ventana de parada para minimizar el tiempo de inactividad y reducir problemas de funcionalidad. El proceso de actualización de NSX puede llevar algún tiempo, por lo que es importante comprender el orden de actualización de despliegue de NSX:
* NSX Manager
* Clúster de controlador NSX
* Clústeres de host NSX
* Las pasarelas de Edge Services se pueden actualizar en cualquier momento después de la actualización de NSX Manager
* Siga las instrucciones de las notas del release si utiliza Guest Introspection

El flujo de trabajo es el siguiente:
1. Inicie la sesión en el servidor de saltos y abra un navegador.
2. Con las credenciales de _my.vmware.com_, vaya a la sección de descargas y busque _NSX for vSphere_.
3. Seleccione la versión que necesite.
4. En la página de descargas, seleccione **Actualizar paquete compuesto, Descargar ahora**.
5. Descargar a una carpeta adecuada.
6. **Actualizar NSX Manager**:
  - Inicie la sesión en el dispositivo virtual de NSX Manager mediante la dirección IP y las credenciales que están documentadas en la consola IC4VS y pulse el botón Actualizar en la página de inicio.
  - Inicie la sesión en NSX Manager.
  - En **Gestión de dispositivos**, pulse **Copias de seguridad y restaurar**.
  - Pulse Copia de seguridad y especifique un nombre de archivo adecuado. Tenga en cuenta que VMware recomienda reinstalar el dispositivo de NSX Manager antes de restaurar los datos de NSX Manager. Aunque es posible que funcione una operación de restauración en un dispositivo NSX Manager existente, oficialmente no se admite. La práctica recomendada es tomar nota de los valores de IP para el dispositivo NSX Manager para que se puedan utilizar para especificar información de IP y la información de ubicación de copia de seguridad para el dispositivo NSX Manager recién desplegado.
  - En la parte superior derecha, pulse **Cargar paquete** y cargue el archivo que ha descargado de _my.vmware.com_.
  - Lea la información de actualización y seleccione si desea habilitar SSH y participar en el programa VMware Customer Experience Improvement Program.
  - Pulse **Actualizar**.
  - Cuando se complete la carga, se le redirigirá a la página de inicio de sesión de NSX Manager. Inicie la sesión de nuevo y verifique que la versión de software actual que se muestra es correcta.
7. **Actualizar el clúster de controlador NSX**:
  - Utilice el cliente web de vSphere e inicie sesión en VCSA.
  - Vaya a **Inicio** > **Redes y seguridad** > **Instalación**, seleccione el **separador Gestión ** y pulse **Actualizar disponible** en la columna Estado de clúster del controlador.
  - Los controladores del entorno se actualizan y se rearrancan uno por uno. Después de iniciar la actualización, el sistema descarga el archivo de actualización, actualiza los controladores, los vuelve a iniciar y actualiza su estado de actualización.
8. **Actualizar clústeres de host NSX**:
  - Después de actualizar los controladores NSX Manager y NSX, los clústeres de host se actualizan con los VIB de NSX en los hosts ESXi de vSphere.
  - En el cliente web de vSphere, vaya a **Inicio** > **Redes y seguridad** > **Instalación**, seleccione el **separador Preparación del host**. Para cada clúster que desee actualizar, pulse **Actualizar disponible**. El estado de instalación muestra Instalando.
  - El estado de instalación del clúster muestra _No preparado_. Pulse **No preparado** para ver más información y pulse **Resolver todo** para intentar completar la instalación de VIB. El host se coloca en modalidad de mantenimiento y si es necesario se rearranca para completar la actualización. La columna Estado de instalación muestra Instalando. Una vez que se haya completado la actualización, la columna Estado de la instalación muestra una marca de selección verde y la versión actualizada de NSX.
9. **Pasarelas de Edge Services**:
  - Durante el proceso de actualización se despliega un nuevo dispositivo virtual Edge junto con el existente. Cuando el nuevo Edge está listo, las vNIC antiguas de Edge están desconectadas y las nuevas están conectadas. El nuevo Edge envía paquetes de ARP gratuitos (GARP) para actualizar la memoria caché ARP de los conmutadores conectados. Cuando se despliega la alta disponibilidad, el proceso de actualización se realiza dos veces. Este proceso puede afectar temporalmente al reenvío de paquetes.
  - En el cliente web de vSphere, seleccione **Redes y seguridad** > **NSX Edges**. Para cada instancia de NSX Edge, seleccione **Versión de actualización** en el menú **Acciones**.
  - Después de que el NSX Edge se actualice correctamente, el estado está Desplegado y la columna Versión muestra la nueva versión de NSX. Si un Edge no se actualiza y no vuelve a la versión antigua, pulse el icono **Redesplegar Edge NSX Edge** y, a continuación, vuelva a intentar la actualización.

### Enlaces relacionados

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demos)
