---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Redundancia de vSAN de máquina virtual
{: #vum-vsan-redundancy}

Cuando coloca un host de vSphere ESXi en modo de mantenimiento en un clúster vSAN, es necesario que seleccione un modo de evacuación de datos. La selección de la modalidad puede tener un impacto sobre las máquinas virtuales (VM) y los dispositivos que consumen el almacén de datos de vSAN:
* Una **migración de datos completa** evacua todos los datos del host y los mueve a los otros hosts de ESXi de vSphere en el clúster vSAN. Esta modalidad de evacuación da lugar a la mayor cantidad de transferencia de datos y consume más tiempo y recursos. Todos los componentes del almacenamiento local del host seleccionado se migran en otro lugar del clúster. Cuando el host entra en modalidad de mantenimiento, todas las máquinas virtuales y los dispositivos tienen acceso a sus componentes de almacenamiento y siguen cumpliendo con sus políticas de almacenamiento asignadas. La evacuación completa de los datos puede llevar un tiempo largo y puede hacer que la ventana de mantenimiento de una actualización dure mucho tiempo.
* La modalidad **garantizar la evacuación de los datos de accesibilidad** es la opción predeterminada y cuando el host de vSphere ESXi se coloca en modalidad de mantenimiento, vSAN garantiza que todas las máquinas virtuales accesibles o los dispositivos del host lo sigan siendo. Como solo se produce una evacuación de datos parcial, es posible que la VM o el dispositivo ya no cumplan totalmente con la política de almacenamiento de VM durante la evacuación y que no tengan acceso a todas sus réplicas. Si se produce un error mientras el host está en modalidad de mantenimiento y el nivel primario de las anomalías que se toleran se establece en 1, se pierden datos y la máquina virtual o el dispositivo puede dejar de estar disponible.
* En la modalidad **sin migración de datos**, vSAN no evacue ningún dato del host cuando este entra en modalidad de mantenimiento. Aunque esto reduce el tiempo de entrar en modalidad de mantenimiento y, por tanto, reduce la duración de la ventana de mantenimiento, es posible que ya no se pueda acceder a algunas máquinas virtuales o dispositivos.

Esta sección crea una nueva política de almacenamiento de VM que permite seleccionar la modalidad **asegurar la evacuación de datos de accesibilidad** para reducir las ventanas de mantenimiento, pero reducir el riesgo de que un error de un host mientras otro está en modalidad de mantenimiento hace que ya no se pueda acceder a una VM o un dispositivo. Para cualquier VM o dispositivo que no acepte la conversión en no redundante cuando se coloca en host vSAN en modalidad de mantenimiento, siga el proceso siguiente antes de llevar a cabo las acciones de corrección. Se necesita un clúster con al menos seis hosts.

1. Cree un nuevo perfil de vSAN con los valores de RAID 5/6 y FTT = 2 (RAID 6) y, a continuación, aplique esta política frente a las máquinas virtuales o dispositivos necesarios.

2. Espere hasta que la vSAN haya completado la sincronización antes de iniciar cualquier acción de corrección. El estado de finalización se puede comprobar navegando a la **página de supervisión de objetos virtuales vSAN** para el clúster y revisando el **Estado de finalización**.

## Enlaces relacionados
{: #vum-vsan-redundancy-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (demostraciones)
