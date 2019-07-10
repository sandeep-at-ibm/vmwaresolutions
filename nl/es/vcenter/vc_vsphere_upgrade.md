---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: vSphere upgrade, NSX upgrade, PSC upgrade

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Actualización del software de vSphere de vCenter Server de VMware vSphere 6.5 a 6.7
{: #vc_vsphere_upgrade}

La oferta de vCenter Server on {{site.data.keyword.cloud}} es una solución de despliegue completamente automatizado para la pila SDDC de VMware vSphere, incluyendo vSphere, NSX y, de manera opcional, productos vSAN. Aunque vCenter Server automatiza las partes más complicadas del despliegue, expansión y contratación de una infraestructura basada en VMware basada en SDDC, no es un servicio gestionado. Debido a que vCenter Server tiene una política de soporte de la automatización de versiones de software de VMware SDDC dentro del rango de N-1, debe actualizar las instancias existentes de vCenter Server si desea seguir haciendo uso de la automatización de {{site.data.keyword.vmwaresolutions_short}}.

Las versiones de vCenter Server fuera de los niveles necesarios para el soporte de automatización siguen teniendo soporte, como requiere la política de soporte de VMware, pero ya no funcionarán con la automatización de {{site.data.keyword.vmwaresolutions_short}}. Debe aplicar parches y realizar actualizaciones periódicamente en el software de VMware en el ciclo de vida de una instancia de vCenter Server. Esto incluye la actualización del software de VMware SDDC a una versión admitida por la automatización de {{site.data.keyword.vmwaresolutions_short}} según sea necesario.

El procedimiento siguiente proporciona los pasos necesarios para convertir una instancia basada en vCenter Server VMware vSphere 6.5 en una instancia basada en vCenter Server VMware vSphere 6.7. Estos pasos proporcionan la actualización inicial al nivel 6.7 más reciente de vSphere, NSX y vSAN. Tras esta actualización, es posible que deba utilizar las funciones normales de vSphere para actualizar las herramientas y niveles de hardware de la máquina virtual (VM).

vCenter Server está diseñado para permitir una actualización "continuada". Es decir, las cargas de trabajo de máquina virtual que estén funcionando actualmente seguirán funcionando sin interrupciones si completa el procedimiento siguiente. Las empresas deben llevar a cabo sus políticas de gestión para permitir una actualización y estructurada y comunicada y disponer de un plan de contingencias. No obstante, durante el proceso de actualización de determinadas funciones de gestión, como vCenter y NSX Manager, las interrupciones temporales de funciones de gestión, los cambios de configuración, el apagado y encendido de máquinas virtuales, pueden verse afectados.
{:note}

## Antes de empezar
{: #vc_vsphere_upgrade-prereq}

El tiempo estimado para realizar la actualización es desconocido. Es posible que se pueda tardar varias ventanas de mantenimiento en actualizar por completo un entorno. VMware admite la ejecución de versiones por encima o por debajo del nivel del software SDDC durante el proceso de actualización. No obstante, algunas funciones como vMotion, puede estar limitadas durante este proceso.

Complete los requisitos previos siguientes antes de comenzar la actualización:  
* Es responsabilidad del usuario actualizar las extensiones o complementos dentro del entorno de vCenter Server. Revise la documentación siguiente antes de planificar la actualización:
  * [Notas del release de VMware vCenter Server 6.7 Actualización 1b](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:new_window}
  * [Acerca de la actualización de VMware ESXi](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:new_window}
* Configure vSphere Update Manager (VUM) dentro de la instancia de vCenter Server para descargar las actualizaciones más recientes de VMware vSphere. Para obtener más información, consulte
[Introducción a VMware Update Manager](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro).
* Abra una incidencia de soporte con el equipo de {{site.data.keyword.vmwaresolutions_short}} para notificarles que se va a realizar una actualización. La incidencia seguirá abierta hasta que se registre la instancia en el nivel actualizado en la consola de
{{site.data.keyword.vmwaresolutions_short}}.
* Confirme si la instancia de vCenter Server que va a actualizar estará enlazada o no a otra instancia de vCenter Server como primaria o secundaria en la consola de {{site.data.keyword.vmwaresolutions_short}}. Es necesario actualizar primero los controladores de servicios de plataforma (PSC) de todas las instancias enlazadas como parte de una actualización de sitio concreta.
* Confirme lo siguiente para las instancias basadas en vSAN:
  * Asegúrese de que la herramienta de estado vSAN esté habilitada y que no notifique ningún error crítico. Si hay errores críticos presentes, póngase en contacto con el equipo de soporte de IBM con el ID de la incidencia de soporte de actualización.
  * Asegúrese de que hay espacio en cada nodo para gestionar la reconstrucción de la redundancia de objetos vSAN en caso de que un host ESXi no pueda volver a estar activo durante la actualización. Es posible que necesite reducir el uso de disco o añadir un host ESXi adicional antes de actualizar.  
  * Verifique si el volumen vSAN global está o no por encima del 70 por ciento de utilización. Es posible que necesite reducir el uso de disco o añadir un host ESXi adicional antes de actualizar.
* Si su instancia de vCenter Server se ha iniciado como {{site.data.keyword.vmwaresolutions_short}} V2.5 o posterior, debe ponerse en contacto con el soporte de IBM para obtener la contraseña del ID de usuario **root** para PSC y vCenter, ya que solo una cuenta de servicios con acceso **customerroot** será visible en el portal. Si el ID de usuario **root** de PSC y vCenter es visible con su contraseña, este paso no será necesario.
* Confirme que tiene un ID de usuario de https://my.vmware.com para el cual descargar los archivos binarios de actualización necesarios. Si no es así, póngase en contacto con el soporte de IBM con el ID de incidencia de soporte de la actualización.
* Confirme que VUM se ha configurado para acceder a https://www.vmware.com para descargar parches. Si no se puede configurar debido a las políticas de seguridad, deberá descargar de forma manual los conjuntos de parches más recientes y cargarlos en VUM. Para obtener más información, consulte
[Introducción a VMware Update Manager](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro).

### Preparación del saltador
{: #vc_vsphere_upgrade-prereq-jumpbox}

Debido a que la VPN de acceso de cliente de {{site.data.keyword.cloud_notm}} está limitada a 512 Kbps, se recomienda que suministre una VSI (instancia de servidor virtual) Windows 2012-2016 de {{site.data.keyword.cloud_notm}} o que configure una máquina virtual Windows similar en un entorno de vSphere vCenter Server dentro del mismo {{site.data.keyword.CloudDataCent_notm}}. Esto se utiliza como un saltador a la instancia de vCenter Server para la actualización, y permite descargas rápidas de los archivos binarios en https://my.vmware.com. Aunque es posible colocar esta máquina virtual en la instancia de vCenter Server que se va a actualizar, no se recomienda.

Realice los pasos siguientes para solicitar un saltador de VSI.

Omita el primer paso si ya tiene un saltador de VSI en el entorno.
{:note}

1. Solicite una VSI por hora o por mes desde el [Portal de clientes de infraestructura de IBM Cloud](https://control.softlayer.com/). Solicite los atributos siguientes:
  * Windows 2012 o 2016 Server Standard
  * 2 CPU
  * 16 GB de memoria
  * 100 G de disco
  * 1 Gbps de enlaces ascendentes públicos y privados
2. Cuando se suministre la VSI, configure las listas de control de acceso (ACL) de {{site.data.keyword.cloud_notm}} dentro del panel de control para permitir tanto la entrada como la salida en los enlaces privados y solo la salida en los públicos. Debe utilizar la VPN de acceso de cliente de {{site.data.keyword.cloud_notm}} para las sesiones RDP (protocolo de escritorio remoto) en la VSI de Windows.
3. RDP en la VSI de Windows. Modifique sus valores de sistema de nombres de dominio (DNS) en el adaptador de red privada para que haga referencia solo al servidor AD de Windows dentro de la instancia de vCenter Server que se va a actualizar.
4. Descargue e instale el navegador Google Chrome. Puede utilizar Mozilla Firefox, pero tiene un problema de memoria caché al utilizar pantallas de VUM dentro de la interfaz de usuario de vCenter.
5. Descargue el software de terminal SSH que prefiera. Por ejemplo, Putty.
6. Utilice Google Chrome para acceder a la instancia vCenter Server que se va a actualizar. Utilice
**administrator@vsphere.local** y asegúrese de que puede ver la interfaz de usuario.  
7. Compruebe si existen errores y problemas en el entorno de vSphere como se ha explicado en la sección anterior.
8. Utilice el software de terminal SSH para acceder a PSC y vCenter con las contraseñas del portal o de soporte proporcionadas para
**root**.
9. De manera opcional, utilice el ID de usuario y la contraseña de **root** indicados en el panel de control de SL para acceder a cada host ESXi para verificar la contraseña **root**.

#### Descarga de archivos binarios
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Utilice el recuadro de salto de su VSI de Windows e inicie sesión en su cuenta de https://my.vmware.com para descargar los archivos binarios siguientes:

* Imagen del hipervisor de VMware vSphere 6.7u1 (ESXi ISO), que incluye VMware Tools
* ISO del dispositivo de vCenter 6.7u1b. No es el paquete de actualización.
* Paquete de actualización de NSX para vSphere 6.4.4

Para unidades Intel Optane, descargue el archivo siguiente para utilizarlo como parte del proceso de aplicación de parches posterior a la actualización que utiliza VMware Update Manager.

Localice el archivo ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` para el controlador NVMe de Intel para Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA (750 GB, HHHL) en https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742.

#### Copia de seguridad de los componentes

Antes de comenzar la actualización, realice una copia de seguridad de cada componente. 

* Para obtener información sobre cómo realizar una copia de seguridad de vCenter Server y los PSC, consulte
[Visión general de las opciones de copia de seguridad y restauración de vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window}.
* Para ver consideraciones adicionales e información sobre cómo realizar la copia de seguridad de vCenter Server y los PSC, consulte
[Copia de seguridad basada en archivos de vCenter](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter).
* Para obtener información sobre cómo realizar la copia de seguridad de NSX, consulte
[Copia de seguridad de datos de NSX Manager](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}.

Se recomienda utilizar la copia de seguridad basada en archivos. No hay soporte para la copia de seguridad basada en imágenes (utilizando vSphere Data Protection) en VMware vSphere 6.7.
{:note}

## Procedimiento para actualizar el software de IBM vCenter Server vSphere de 6.5 a 6.7
{: #vc_vsphere_upgrade-procedure}

Si encuentra un problema en cualquier momento durante el proceso de la actualización, utilice la incidencia de actualización de
{{site.data.keyword.vmwaresolutions_short}} que ha abierto al comienzo del proceso para ponerse en contacto con el soporte de IBM. El soporte de IBM abrirá incidencias con el soporte de VMware según sea necesario.

**Importante**:

* Debe utilizar esta vía para asegurarse de que {{site.data.keyword.vmwaresolutions_short}} proporciona al soporte de VMware toda la información que necesita sobre el diseño de vCenter Server, la configuración y la información de {{site.data.keyword.cloud_notm}}. Siguiendo este proceso para garantizar que se comparte información precisa con el soporte de VMware, se acorta la experiencia de soporte. Una vez que el soporte de IBM proporcione la información necesaria al soporte de VMware, puede interactuar directamente con el soporte de VMware según sea necesario.
* Asegúrese de mantener un registro de todas las contraseñas y credenciales nuevas que cree como parte de este proceso de actualización. El soporte de IBM necesitará estas credenciales al final del proceso de actualización para actualizar su base de datos interna.

### Actualización de VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx}

La actualización de VMware NSX puede llevar cierto tiempo, ya que el proceso de actualización actualiza los paquetes de instalación de vSphere en los hosts ESXi y requiere que se rearranque cada uno de los hosts. Planifique la ventana de mantenimiento en consecuencia.

#### Antes de actualizar VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-before}

* Si tiene Zerto for {{site.data.keyword.cloud_notm}} instalado en el entorno, utilice la interfaz de usuario de Zerto para concluir las máquinas virtuales de zVRA en cada host. Seleccione **Permitir siempre a Zerto pasar hosts a la modalidad de mantenimiento durante la corrección** dentro de los valores del sitio de Zerto, sección de políticas, de la interfaz de usuario de Zerto. De lo contrario, Zerto inicia zVRA e impide que continúe la actualización al no permitir que el host ESXi que se va a actualizar pase a la modalidad de mantenimiento.
* Para máquinas virtuales que no tienen herramientas de VMware instaladas, realice una conclusión manual o apague la alimentación antes de la instalación del módulo del host ESXi de NSX. Estas máquinas virtuales impiden que el host ESXi de destino pueda pasar a la modalidad de mantenimiento.

#### Procedimiento para actualizar VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

Consulte la
[Guía de actualización de NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window} para obtener detalles relacionados con el procedimiento siguiente.

1. Lea las notas del release de NSX 6.4.4 para asegurarse de que exista compatibilidad con la configuración de su entorno específico. Para obtener más información, consulte [Notas del release de VMware NSX Data Center for vSphere 6.4.4](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}.
2. Actualice NSX Manager en primer lugar. Si tiene varios entornos de NSX que utilicen la modalidad con enlace cruzado a vCenter, actualice todos los NSX Managers antes de actualizar componentes en el
**Coordinador de actualización** de la interfaz de usuario de NSX.
3. Utilice el **Coordinador de actualización** de la interfaz de usuario de NSX dentro de la interfaz de usuario de vCenter para actualizar los componentes de NSX.
4. Continúe con la revisión y supervisión de la interfaz de usuario de actualización de NSX dentro de la interfaz de usuario de vCenter a medida que se resuelvan posibles problemas para garantizar que la actualización continúa hasta que se actualicen todos los componentes.

### Actualización de Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc}

Si tiene instancias enlazadas de vCenter Server, debe actualizar todas las instancias de PSC en los sitios primario y secundario de vCenter Server. Debido a que las instancias enlazadas de vCenter Server crean una topología de réplica de PSC de estrella (hub and spoke), siendo la instancia primaria de vCenter Server el concentrador, se recomienda que empiece por actualizar el PSC de la instancia primaria de vCenter Server y que actualice luego cada PSC del sitio secundario.

#### Antes de actualizar Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-before}

* Haga que sus contraseñas de root de vCenter y PSC estén disponibles para el procedimiento siguiente. Utilice la consola de
{{site.data.keyword.vmwaresolutions_short}} para ver si la versión de su instancia de vCenter Server se ha actualizado de V2.4 o anterior a V2.7 o posterior.
* En la consola de {{site.data.keyword.vmwaresolutions_short}}, se muestra una única contraseña para root tanto para PSC como para vCenter. No obstante, esta es solo la contraseña de vCenter. Debe [consultar al soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) para la contraseña PSC raíz. 
* Para evitar conflictos, utilice la dirección IP de la parte superior de la misma subred que utilizan actualmente vCenter y el PSC. Debe utilizar una dirección IP temporal para el nuevo despliegue de dispositivo. 

#### Procedimiento para actualizar Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. Inicie sesión en las interfaces de usuario de gestión de dispositivos de vCenter y de PSC, `https://<psc-fqdn>:5480`, para confirmar si ha caducado o no la contraseña de root. Si la fecha de caducidad de la contraseña es **1970**, entonces habrá caducado y deberá habilitar SSH y el shell bash en la interfaz de usuario de gestión de dispositivos de PSC.
    1. Utilice SSH en PSC con el ID y la contraseña de root. Aunque la contraseña haya caducado, le permitirá iniciar sesión.
    2. Utilice el mandato **passwd** de shell para establecer una nueva contraseña de root tanto para PSC como para vCenter.
    3. Guarde las contraseñas que se han mostrado en la consola de
{{site.data.keyword.vmwaresolutions_short}} o que le ha proporcionado el soporte de IBM. Estas contraseñas se reutilizarán más adelante al actualizar los dispositivos.
2. Utilice la función de montaje ISO incorporada en Windows para montar el ISO de vCenter 6.7u1b dentro del saltador.
3. Siga las instrucciones de VMware para actualizar todos los PSC en primer lugar. Para obtener más información, consulte
[Actualización de vCenter Server Appliance 6.0 o 6.5 con una instancia de Platform Services Controller o del inicio de sesión único de vCenter externa utilizando la GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html).

El requisito **Debe ejecutar la actualización de GUI desde una máquina Windows, Linux o Mac que esté en la misma red que el dispositivo que desea actualizar** indicado se aplica a cualquier subred dentro de su cuenta de
{{site.data.keyword.cloud_notm}}.
{:note}

Se recomienda que utilice vCenter como origen y destino de la actualización.

### Actualización de vCenter
{: #vc_vsphere_upgrade-procedure-vcenter}

Para instancias enlazadas a vCenter Server, aunque se recomienda actualizar todas las instancias de vCenter de los sitios primarios y secundarios de vCenter Server, no es necesario hacerlo.

#### Antes de actualizar vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* Haga que sus contraseñas de root de vCenter y PSC estén disponibles para el procedimiento siguiente. Utilice la consola de
{{site.data.keyword.vmwaresolutions_short}} para ver si la versión de su instancia de vCenter Server se ha actualizado de V2.4 o anterior a V2.7 o posterior.
* Para evitar conflictos, utilice la dirección IP de la parte superior de la misma subred que utilizan actualmente vCenter y el PSC. Debe utilizar una dirección IP temporal para el nuevo despliegue de dispositivo. 

#### Procedimiento para actualizar vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. Inicie sesión en las interfaces de usuario de gestión de dispositivos de vCenter y de PSC, ``https://<psc-fqdn>:5480``, para confirmar si ha caducado o no la contraseña de root. Si la fecha de caducidad de la contraseña es **1970**, entonces habrá caducado y deberá habilitar SSH y el shell bash en la interfaz de usuario de gestión de dispositivos de PSC.
    1. Utilice SSH en PSC con el ID y la contraseña de root. Aunque la contraseña haya caducado, le permitirá iniciar sesión.
    2. Utilice el mandato **passwd** de shell para establecer una nueva contraseña de root tanto para PSC como para vCenter.
    3. Guarde las contraseñas que se han mostrado en la consola de
{{site.data.keyword.vmwaresolutions_short}} o que le ha proporcionado el soporte de IBM. Estas contraseñas se reutilizarán más adelante al actualizar los dispositivos.
2. Utilice la función de montaje ISO incorporada en Windows para montar el ISO de vCenter 6.7u1b dentro del saltador.
3. Siga las instrucciones de VMware para actualizar vCenter. Para obtener más información, consulte
[Actualización de vCenter Server Appliance 6.0 o 6.5 con una instancia de Platform Services Controller o del inicio de sesión único de vCenter externa utilizando la GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html). Las instrucciones de VMware son similares al proceso de actualización de PSC. No obstante, en lugar de hacer referencia al PSC, haga referencia al FQDN/IP de vCenter en el proceso de actualización.

**Notas**:
* El requisito **Debe ejecutar la actualización de GUI desde una máquina Windows, Linux o Mac que esté en la misma red que el dispositivo que desea actualizar** indicado se aplica a cualquier subred dentro de su cuenta de
{{site.data.keyword.cloud_notm}}.
* Se recomienda que utilice vCenter como origen y destino de la actualización.

#### Consolidación de la función de PSC en vCenter

1. Una vez que se haya completado correctamente la actualización de PSC y vCenter, inicie sesión en la interfaz de usuario basada en FLEX de vCenter y compruebe el estado de todos los servicios relacionados con vCenter y el PSC en la sección **Configuración del sistema**.  
2. Realice una copia de seguridad del PSC.  Se recomienda utilizar la copia de seguridad basada en archivos. Para obtener más información, consulte [Copia de seguridad basada en archivos en vSphere 6.7](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:new_window}.
3. Vaya al directorio ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge``.
4. Copie el archivo ``converge.json`` a una unidad local de su máquina virtual de salto.
  * Si este es el primer PSC que va a consolidar, deberá eliminar la sección
**replication** del archivo ``json``.
  * Si este es un PSC enlazado de manera posterior, deberá rellenar los atributos solicitados en la sección de réplica (**replication**) del archivo ``json``.
5. Vaya al directorio ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission``.
6. Copie el archivo ``decommission_psc.json`` a una unidad local de su máquina virtual de salto.
7. Edite los archivos ``converge.json`` y ``decommission_psc.json``. Las instrucciones para los campos a editar se encuentran en los archivos ``json``. Se recomienda que se utilice el host ESXi que contiene el PSC en lugar de vCenter en la sección **managing_esxi_or_vc**.
8. Vaya al directorio ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` en una ventana de mandatos.
9. Ejecute ``vcsa-util.exe`` con el conmutador **converge** y la vía de acceso al archivo
``converge.json`` editado anteriormente. Por ejemplo, ``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``.
   1. Escriba **Y** para confirmar que se ha realizado la copia de seguridad del PSC para continuar.
   2. Cuando finalice el proceso, escriba **Y** para confirmar el rearranque de vCenter.

   Si el proceso de convergencia falla con el mensaje ``ERROR converge Failed to get vecs users and permissions``, consulte [Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:new_window} para ver los pasos para resolver el error.
   {:note}

10. Una vez que se haya rearrancado vCenter, compruebe que el funcionamiento sea normal iniciando sesión en la interfaz de usuario de vCenter.
11. Vaya al directorio ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` en una ventana de mandatos.
12. Ejecute ``vcsa-util.exe`` con el conmutador **decommission** y la vía de acceso al archivo
``decommission_psc.json`` editado anteriormente. Por ejemplo, ``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``.
13.	Cuando el mandato finalice correctamente, inicie sesión en la interfaz de usuario flex de vCenter y verifique que el dispositivo de vCenter sea el único que aparece en los entornos no enlazados y que todos los servicios están en buen estado.
14. Suprima el PSC y vCenter anteriores, así como las máquinas virtuales de PSC consolidadas que no se utilicen.
15. Renombre vCenter Server dentro de la interfaz de usuario de vCenter a **<instancename>_vc_separate**. Por ejemplo, si el nombre de la instancia de vCenter Server es **production**, el nombre de la interfaz de usuario de vCenter será
**production_vc_separate**. Esto es necesario para que se pueda reanudar el funcionamiento de la automatización para esta instancia de vCenter Server.  

### Actualización de hosts ESXi
{: #vc_vsphere_upgrade-procedure-esxi}

La función de VMware Update Manager dentro de vCenter se utiliza para actualizar y aplicar parches a los hosts ESXi al nivel 6.7u1. Del mismo modo que la sección de actualización de NSX de este documento, las máquinas virtuales que no puedan usar vMotion a otro host se deben poder concluir sin problemas o, de lo contrario, pueden provocar que se detenga el proceso de actualización.
{:note}

#### Carga del ISO de ESXi en VUM
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. Asegúrese de haber configurado VUM para descargar parches de https://www.vmware.com. Para obtener más información, consulte
[Introducción a VMware Update Manager](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction).
2. Utilice Flex o HTML para abrir la interfaz de usuario de vCenter y acceda a la **Vista de administración de VUM**.
3. En la **Vista de administración de VUM**, seleccione el separador **Imágenes ESXi** y seleccione
**Importar imágenes ESXi**.
4. Busque la imagen **ESXi 6.7u1iso** que se ha descargado de VMware e impórtela en el repositorio de VUM.

#### Procedimiento para actualizar los hosts ESXi
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. En la interfaz de usuario de vCenter, vaya hasta el clúster que contiene los hosts ESXi que se van a actualizar.
2. Pulse el separador **Actualizaciones** del panel de navegación. Vaya a Actualizaciones de host y pulse
**Adjuntar**.
3. Seleccione la línea base (imagen ISO para la actualización de ESXi) que haya cargado en VUM y pulse
**Corregir**.
4. Acepte el Acuerdo de licencia de usuario final y pulse **Aceptar**.
5. Revise los hosts que se van a corregir y confirme los resultados de la comprobación previa a la corrección.

   Debe desconectar cualquier CD o DVD conectado a las máquinas virtuales o el host que contiene dicha máquina no tendrá permitido entrar en la modalidad de mantenimiento.
   {:note}

6. Una vez que la comprobación previa a la corrección se haya realizado con éxito, pulse **Corregir**. Supervise el proceso de actualización con la tarea de entidad de corrección.
7. Una vez finalizada la actualización, revise la sección de resumen del host para confirmar que aparece
``VMware ESXi, 6.7.0``.

Si el proceso de actualización falla inmediatamente y aparece el mensaje de error **el host no puede entrar en la modalidad de mantenimiento**, concluya los ZVA de Zerto y vuelva a intentarlo. Las máquinas virtuales de ZVRA se inician automáticamente a medida que cada servidor sale de la corrección. Para obtener información sobre cómo continuar con la réplica de Zerto durante el proceso de actualización, consulte
[Cómo colocar un host con un VRA asociado en la modalidad](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:new_window}.
{:note}

#### Adición de un parche de controlador NVME de Intel al repositorio de VUM
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

Tal como se describe en la sección de descargas de archivos binarios, debe importar el contenido del archivo
``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` en el repositorio. A continuación, se aplicará en la sección siguiente como una extensión de host ESXi no crítica.

1. Extraiga el archivo ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` en una unidad local de la máquina virtual de salto.
2. Utilice Flex o HTML para abrir la interfaz de usuario de vCenter y acceda a la **Vista de administración de VUM**.
3. En la **Vista de administración de VUM**, seleccione el separador **Repositorio de parches** y seleccione **Importar parches**.
4. Busque el contenido extraído en el directorio de ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` y seleccione el archivo
``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip``. El archivo se importa dentro del repositorio de VUM inmediatamente.

Localice la imagen en el repositorio de parches como una extensión de host **importante**.

#### Aplicación de parches a hosts ESXi
{: #vc_vsphere_upgrade-procedure-esxi-patch}

Después de la instalación, se recomienda que aplique todos los parches críticos y no críticos a los hosts ESXi.

1. Desde la interfaz de usuario de vCenter, seleccione el clúster que contiene los hosts a los que se van a aplicar los parches.
2. Pulse el separador **Actualizaciones** del panel de navegación y seleccione el separador **Actualizaciones de host**. Seleccione **Parches de host críticos (predefinido)**. Repita el procedimiento para actualizar los hosts ESXi.
3. Pulse el separador **Actualizaciones** del panel de navegación y seleccione el separador **Actualizaciones de host**. Seleccione **Parches de host no críticos (predefinido)**. Repita el procedimiento para actualizar los hosts ESXi.

Es posible que necesite concluir de nuevo las máquinas virtuales zVRA de Zerto como parte de este proceso.
{:note}

### Actualización de elementos adicionales
{: #vc_vsphere_upgrade-procedure-addtl}

#### Actualización de la versión del formato de disco de vSAN
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

Actualice la versión del formato de disco de vSAN a la versión 7.

1. Vaya hasta el clúster que contiene la vSAN a actualizar en la interfaz de usuario de vCenter.
2. En el objeto del clúster, seleccione **Configuración > vSAN > General**.
3. Pulse **Prever actualización** para comprobar la compatibilidad de la actualización y ver posibles problemas. Espere a que la comprobación devuelva **Listo para actualizar**.
4. Pulse **Actualizar**. Debido a que la actualización procesa los grupos de discos de uno en uno, puede tardar algún tiempo en completarse dependiendo del tamaño de clúster. De manera opcional, seleccione **Redundancia reducida** durante el proceso. Aunque esto puede reducir significativamente el tiempo que tarda la actualización, puede provocar una pérdida de datos si se produce un fallo de disco durante el proceso de actualización.

#### Actualización del conmutador distribuido virtual
{: #vc_vsphere_upgrade-procedure-addtl-vds}

La actualización del conmutador distribuido virtual (VDS) a v6.6.0 también actualiza el control de E/S de red y añade soporte mejorado para el protocolo de control de agregación de enlaces (LACP).

1.	Si ha desplegado HCX, debe anular el despliegue de la parte de Cloud Gateway de HCX antes de actualizar el VDS en el que reside. Asegúrese de que HCX se actualice a la versión más reciente antes de volver a desplegar Cloud Gateway.
2.	En la interfaz de usuario de vCenter, vaya al separador **Red**.
3.	Pulse el botón derecho del ratón sobre el conmutador distribuido a actualizar (ya sea
**SDDC-Dswitch-Private** o **SDDC-Dswitch-Public**) y seleccione
**Actualizar conmutador distribuido**.

#### Actualización de extensiones y plugins de la interfaz de usuario de vCenter
{: #vc_vsphere_upgrade-procedure-addtl-extension}

Es responsabilidad del usuario actualizar las extensiones o complementos dentro del entorno de vCenter Server. En la interfaz de usuario de vCenter, pulse **Inicio > Administración > Soluciones** para ver el estado y habilitar o inhabilitar extensiones y plugins de vCenter.

#### Actualización de herramientas de VMware
{: #vc_vsphere_upgrade-procedure-addtl-tools}

Utilice la interfaz de usuario de vCenter para realizar actualizaciones de herramientas de invitado de VMware. Es posible que algunas herramientas de VMware sean necesarias en algunas máquinas virtuales más antiguas que se hayan migrado al entorno de vCenter Server.  

#### Actualización del nivel de hardware de la máquina virtual
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

De forma similar a las herramientas de invitado de VMware, una actualización del entorno de vCenter Server puede provocar que máquinas virtuales más antiguas queden en un estado sin soporte en su nivel de hardware actual. Utilice la interfaz de usuario de vCenter para encontrar y actualizar estas máquinas virtuales según sea necesario.  

#### Establecimiento de la modalidad de compatibilidad mejorada de vMotion en Intel Skylake
{: #vc_vsphere_upgrade-procedure-addtl-evc}

Puede establecer los hosts con la generación Intel Skylake de un clúster en la modalidad EVC (compatibilidad mejorada de vMotion) de Skylake después de la actualización. Utilice los pasos siguientes para actualizar la modalidad EVC:

1. En el clúster que contiene los hosts, pulse **Configurar**.
2. En **VMware EVC**, pulse **Editar** y cambie la modalidad EVC a **Generación Intel "Skylake"**.

Para obtener más información, consulte [Soporte de procesador de EVC (compatibilidad mejorada de vMotion) (1003212)](https://kb.vmware.com/s/article/1003212){:new_window}.

#### Reconfiguración de NSX Manager y HCX Manager para que hagan referencia al PSC

1. Desde un navegador web, navegue hasta la interfaz de usuario del dispositivo NSX Manager en
``https://<nsx-manager-ip>`` o ``https://<nsx-manager-hostname>``. Inicie sesión con las credenciales.
2. Desde la página de inicio, pulse **Gestionar registro de vCenter**.
3. Edite el **URL de servicio de búsqueda** para que haga referencia a la IP de vCenter. Utilice el PSC autónomo incorporado
(**El PSC ya no existe**).

## Resultados tras actualizar el software de vSphere de vCenter Server
{: #vc_vsphere_upgrade-results}

La ejecución de la comprobación de estado de vSAN después de que finalice la actualización puede producir avisos acerca de actualizaciones de firmware para los controladores de red y RAID proporcionados por IBM Cloud. Tras determinar los hosts que necesitan actualizaciones de firmware, abra una incidencia con el soporte de IBM para solicitar que se actualice el firmware a las versiones recomendadas.

1. En la interfaz de usuario de vCenter, seleccione el clúster que contiene la vSAN cuyo estado se debe comprobar.
2. Seleccione el separador **Supervisar** y, a continuación, seleccione el separador **vSAN**.
3. Seleccione **Estado** y anote los avisos que se muestran.
4. Si aparece un aviso **Compatibilidad de hardware**, expanda el aviso y pulse sobre el mensaje
**Firmware de controlador certificado por VMware** si está en estado de aviso.
5. Tome nota de los hosts que aparecen con recomendaciones de actualización de firmware.
6. Abra una incidencia con el soporte de IBM para planificar una hora en la que se dejará fuera de servicio el host para permitir actualizaciones de firmware.

Cuando haya finalizado la actualización, actualice la incidencia de soporte con el soporte de IBM. Proporcione las contraseñas nuevas que haya creado como parte de este proceso de actualización. Por ejemplo, proporcione contraseñas para desplegar servicios de gestión de dispositivos PSC y vCenter en la incidencia de soporte. A continuación, el soporte de IBM actualiza la consola de {{site.data.keyword.vmwaresolutions_short}} y la base de datos interna para reanudar la automatización de {{site.data.keyword.vmwaresolutions_short}} en el nivel 6.7. Esto incluye la adición y eliminación de servicios, hosts, el clúster e instancias secundarias de vCenter Server.

## Enlaces relacionados
{: #vc_vsphere_upgrade-related}

* [Notas del release de VMware NSX Data Center for vSphere 6.4.4](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}
* [Guía de actualización de NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
