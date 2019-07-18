---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

---

# Resolución de problemas
{: #opsprocs-trouble}

Para identificar problemas de su instancia de vCenter Server, los administradores del sistema deben identificar los síntomas del problema, determinar cuál de los componentes de la solución se ven afectados, investigar y proponer un arreglo o un método alternativo y probar el arreglo.

* Identificar los síntomas - Hay muchas causas que pueden llevar a un infrarrendimiento o no rendimiento de su instancia. El primer paso para una resolución de problemas eficaz consiste en identificar exactamente qué es lo que va mal. Estos síntomas pueden notificarse desde sucesos y alarmas de vSphere, Operations Management en	{{site.data.keyword.cloud}} o a través del servicio de atención al usuario, procedente de uno de sus usuarios.
* Aislar los componentes afectados - Una vez que ha identificado los síntomas del problema, debe identificar los componentes de hardware o de software que se ven afectados y que pueden estar provocando este problema y los que no están implicados. Para ayudarle en este paso, dispone de herramientas tales como vCenter Operations Management en {{site.data.keyword.cloud_notm}}.
* Proponer un arreglo o un método alternativo - Una vez que comprenda los síntomas y haya aislado los componentes, puede investigar posibles arreglos y métodos alternativos. Los administradores del sistema también utilizan el Portal de {{site.data.keyword.cloud_notm}}, incluyendo los escenarios de resolución de problemas de este documento, IBM ServiceNow y la base de conocimiento de VMware. Además, hay muchos wikis y blogs que pueden ser de ayuda. Para resoluciones aún más rápidas, Operations Management en {{site.data.keyword.cloud_notm}} incluye una serie de remedios para problemas identificados.
* Probar las posibles soluciones - Cuando ya sabe cuáles son los síntomas del problema, los componentes afectados y ya ha propuesto un arreglo o un método alternativo, los administradores del sistema prueban de forma sistemática las soluciones hasta resolver el problema.

vSphere incluye un subsistema configurable por el usuario de sucesos y alarmas que hace un seguimiento de los sucesos que se producen en todo el entorno de vSphere y almacena los datos en archivos de registro y en la base de datos de vCenter. Este subsistema también permite a los administradores del sistema especificar las condiciones bajo las que se desencadenan las alarmas. Las alarmas cambian de estado, desde avisos a alertas más serias a medida que cambian las condiciones del sistema, y pueden desencadenar acciones de alarma automatizadas, tales como enviar un correo electrónico al equipo de administración del sistema. Esta funcionalidad es útil cuando desea que se le informe, o que se emprenda una acción inmediata, cuando se producen determinados sucesos o condiciones en un objeto o grupo de objetos de inventario específico.

Otras herramientas adicionales, como las incorporadas en la arquitectura de Operations Management on {{site.data.keyword.cloud_notm}} proporcionan una mayor asistencia en: identificar síntomas, aislar los componentes afectados y proponer un arreglo o solución temporal.

## Directrices
{: #opsprocs-trouble-guidelines}

Las directrices siguientes se consideran las mejores prácticas para la resolución de problemas en {{site.data.keyword.vmwaresolutions_short}}:
* Aborde la resolución de problemas de forma sistemática.
* Los síntomas están relacionados con disponibilidad, utilización o configuración:
 *  Disponibilidad - Estos síntomas están relacionados con la disponibilidad de componentes de hardware y software y se caracterizan por una falta de respuesta. A menudo, el diseño de alta disponibilidad enmascara estos problemas para que no afecten directamente a las cargas de trabajo y a los usuarios.
 * Utilización - Estos síntomas se relacionan con la capacidad y el rendimiento y se caracterizan por una lenta velocidad de ejecución o la falta de capacidad de carga. La gestión proactiva de la capacidad reduce drásticamente estos problemas.
 * Configuración - Estos problemas se descubren normalmente en la prestación de nuevos servicios o en el resultado de la aplicación de un cambio. Los valores incorrectos pueden aflorar como síntomas de disponibilidad o de utilización. Por ejemplo, una dirección IP incorrecta se visualiza como un problema de disponibilidad, mientras que unos valores de RAM de máquina virtual (MV) demasiado bajos pueden dar síntomas de utilización.
* Intente aislar el problema en un componente del entorno.
* Tome notas para poder rastrear los pasos.
* Entienda y documente sus versiones de software.
* Documente el uso de las subredes y de la dirección IP, incluyendo las direcciones VIP y NAT.
* Tanga diagramas en su red. Necesita varios diagramas que muestren las capas físicas (underlay) y lógicas (overlay).
* Comprenda los cambios recientes en el entorno.
* Investigue el impacto del arreglo, no cierre la sesión de las interfaces de gestión.
* Asegúrese de tener copias de seguridad de todos los componentes clave, por si se tienen que volver a cargar o restablecer.
* No cambie más de una cosa a la vez.
* Documente cada cambio y su resultado.
* Al hacer una solicitud de soporte, asegúrese de documentar cuidadosamente y proporcionar la información pertinente. Tenga claro los síntomas que está viendo e identifique los componentes que cree que son defectuosos. Asegúrese de utilizar la terminología correcta. Intente minimizar cualquier malentendido o ambigüedad en su elección de palabras.
* Los archivos de configuración de vSphere ESXi and vCenter Server controlan el comportamiento del sistema, debe saber dónde se encuentran. La mayoría de los valores de los archivos de configuración se establecen durante la instalación, pero se pueden modificar después de ésta.
* Los archivos de registro capturan los mensajes generados por el kernel y los distintos subsistemas y servicios. Los servicios de vSphere ESXi y vCenter mantienen archivos de registro separados. Debe saber dónde están ubicados y
cómo se puede acceder a ellos.
* Comprenda cómo utilizar las herramientas de administración de sistemas populares para obtener ayuda en los diagnósticos.

Para obtener más información, consulte [Directrices para la resolución de problemas KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}.

## Resolución de problemas con archivos de registro
{: #opsprocs-trouble-logs}

Los archivos de registro son una excelente fuente de información para resolver problemas. El gran número de archivos de registro y la ingente cantidad de entradas en cada archivo de registro es difícil de diagnosticar. En la sección [Resolución de problemas con archivos de registro KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window} se detalla dónde se encuentran estos archivos de registro en el entorno de VMware. Debido al número de archivos de registro y a la ingente cantidad de entradas de cada registro, puede considerar la posibilidad de utilizar las herramientas de Operations Management on {{site.data.keyword.cloud_notm}} para ayudar a capturar y analizar los registros de sucesos.

## Resolución de problemas con escenarios comunes
{: #opsprocs-trouble-common}

Como ayuda para aislar los componentes afectados, esta documentación sobre la resolución de problemas comunes se ha clasificado como sigue:

* Máquinas virtuales: estos temas de resolución de problemas proporcionan directrices para los problemas potenciales de las máquinas virtuales.
* Hosts: estos temas de resolución de problemas proporcionan directrices para los problemas en los hosts ESXi de vSphere.
* Clúster: estos temas de resolución de problemas proporcionan directrices sobre disponibilidad y gestión de recursos.
* Almacenamiento: estos temas de resolución de problemas proporcionan directrices para resolver problemas relacionados con el almacenamiento vSAN y NFS.
* Red: estos temas de resolución de problemas proporcionan directrices para resolver problemas de red.
* vCenter: estos temas de resolución de problemas proporcionan directrices para resolver problemas de vCenter.
* Licencias: estos temas de resolución de problemas proporcionan directrices para resolver problemas de licencias. Estos problemas generalmente están relacionados con clientes que han traído sus propias licencias a {{site.data.keyword.cloud_notm}}.

### Máquinas virtuales
{: #opsprocs-trouble-common-vm}

Tabla 1. Resolución de problemas de máquinas virtuales

| Título | Descripción |
|---|---|
| Resolución de problemas genérico de VM | Para obtener más información, consulte [Resolución de problemas en máquinas virtuales](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window}. |
| Problemas de rendimiento de VM | Para obtener información sobre cómo identificar los síntomas de los problemas de rendimiento de las VM, incluyendo sistema operativo invitado que arranca demasiado lento, aplicaciones que tienen un bajo rendimiento, aplicaciones que tardan mucho en iniciarse o aplicaciones que no responden, consulte [Resolución de problemas de rendimiento de máquinas virtuales ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003){:new_window}. |
| Recuperar VM huérfanas | Para obtener información sobre cómo recuperar VM huérfanas, que son VM que existen en la base de datos de vCenter pero no las reconoce el host ESXi de vSphere, consulte [Knowledge - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window}. |
| Una VM no se enciende | Para obtener más información, consulte [Resolución de problemas de una máquina virtual que no se enciende (2001005)](https://kb.vmware.com/s/article/2001005){:new_window}. |
| La VM no se enciende después de clonarla o desplegarla desde una plantilla | Este [artículo de VMware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window} examina los problemas que pueden afectar a una VM después de ser clonada o desplegada desde una plantilla. |
| Las herramientas de VMware están obsoletas o no instaladas - Las herramientas de VMware deben estar instaladas en las VM y se deben mantener al día. | [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window} proporciona directrices para realizar estas tareas. |
| Dispositivos de red de VM antiguos | Si los dispositivos de red de VM no se mantienen al día, el rendimiento de la red y
el rendimiento de la aplicación pueden verse afectados. Para obtener más información sobre cómo desplegar un nuevo dispositivo y controlador de red, consulte [Elección de un adaptador de red para una máquina virtual (1001805)](https://kb.vmware.com/s/article/1001805){:new_window}. |
| Límite de memoria de máquina virtual | A menudo se utilizan límites de memoria. No obstante, si un SO invitado no puede acceder a la memoria que necesita, es posible que la aplicación que hay en el SO invitado tenga un rendimiento deficiente. Para obtener más información sobre cómo resolver el problema, consulte [Configuración de los valores de asignación de recursos](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window}. |
| Instantáneas de VM | Aunque las instantáneas son útiles, la cantidad y la antigüedad de las instantáneas de una VM tienen un impacto directo en el rendimiento de la VM. Para obtener información sobre cómo resolver el problema, consulte [Consolidar instantáneas](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window}. |
| Registro de VM | Si el registro no se ha configurado correctamente, la capacidad del almacén de datos podría verse afectada negativamente. Para obtener información sobre cómo resolver el problema, consulte [Configuración de niveles de registro para el sistema operativo invitado](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window}. |
| Resolución de problemas de conexión de red | Los síntomas pueden incluir VM que no se pueden conectar a la red, o que no hay conectividad de red hacia o desde una máquina virtual. Para obtener información sobre cómo resolver el problema, consulte [Resolución de problemas de conexión de red de máquinas virtuales (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}.  |
| Determinar si varias CPU virtuales provocan problemas de rendimiento  | Para obtener información sobre la resolución de problemas en máquinas virtuales que experimentan problemas de rendimiento cuando se configuran con varias CPU, consulte [Determinar si varias CPU virtuales provocan problemas de rendimiento (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. Estos problemas pueden incluir: bajas velocidades de transferencia al copiar datos a o desde una máquina virtual, trabajos de copia de seguridad que superan el tiempo de espera o son muy lentos, o una máquina virtual con un bajo rendimiento.  |
| Una VM se ha apagado o reiniciado  | Para obtener información sobre cómo resolver el problema, consulte [Determinar por qué se ha apagado o reiniciado una máquina virtual (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. |
| Una o más de las máquinas virtuales tiene un tiempo de respuesta pobre |  Para obtener información sobre cómo aislar un problema de rendimiento en un host ESXi de vSphere, consulte [Resolución de problemas de rendimiento de máquinas virtuales ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. Los problemas de rendimiento pueden deberse a restricciones de CPU, sobreasignación de memoria, latencia de almacenamiento o latencia de red. |

### Hosts ESXi de vSphere
{: #opsprocs-trouble-common-host}

Tabla 2. Resolución de problemas típicos de hosts ESXi de vSphere

| Título | Descripción |
|---|---|
| Mandatos ESXI | Para ver una descripción general de las interfaces de línea de mandato en vSphere, los mandatos de shell ESXi
y los mandatos de la vCLI (interfaz de línea de mandatos de VMware® vSphere), consulte [Iniciación a las interfaces de línea de mandatos de vSphere](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window}. |
| Estados de host de alta disponibilidad de vSphere | Si vCenter informa de un estado de host de alta disponibilidad de vSphere que indica una condición de error en el host, es necesario corregirlo pues este problema puede evitar que HA de vSphere vuelva a iniciar máquinas virtuales después de un error. Para obtener más información, consulte [Resolución de problemas de Estados de host de HA de vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}. |
| El host de vSphere ESXi se encuentra en un estado que no responde | Para obtener información sobre la resolución de problemas de un host de vSphere ESXi que aparece como No Responde, Desconectado o cuando las VM del host aparecen como no disponibles en vCenter, consulte [Los hosts ESX/ESXi no responden y se muestran en gris (1019082)](https://kb.vmware.com/s/article/1019082){:new_window}. |
| Al encender una máquina virtual, aparece el error `No se ha encontrado el archivo`. | Para obtener información sobre cómo volver a crear un archivo de descriptor de disco virtual perdido (VMDK), consulte [Recreación de un archivo de descriptor de disco de máquina virtual que falta (1002511)](https://kb.vmware.com/s/article/1002511){:new_window}. |
| Problemas de rendimiento de VM | Para obtener información sobre cómo aislar un problema de rendimiento en un host ESXi de vSphere, consulte [Resolución de problemas de rendimiento de máquinas virtuales ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. Los problemas de rendimiento pueden deberse a restricciones de CPU, sobreasignación de memoria, latencia de almacenamiento o latencia de red. |
| El servidor nativo está inactivo | Si el servidor nativo que ejecuta vSphere ESXi no responde o está inactivo, inicie sesión en la IU de gestión o la consola de {{site.data.keyword.cloud_notm}} y compruebe el estado. Si es necesario, abra un caso para obtener ayuda con el servidor nativo. Para obtener más información, consulte [Cómo trabajar con casos de soporte](/docs/get-support?topic=get-support-open-case#open-case){:new_window}. |
| El host ESXi de vSphere está desconectado o no responde  | Para obtener más información, consulte [Resolución de problemas de un host ESXi/ESX que no responde (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window}. |
| Pantalla púrpura de la muerte  | La Pantalla púrpura de la muerte (PSOD - Purple Screen of Death) es un error grave de kernel, y el kernel de vSphere ESXi (vmkernel) desencadena esta medida de seguridad en respuesta a un suceso o error que es irrecuperable y significaría que, de continuar la ejecución, se pondrían en elevado peligro los servicios y las VM. Cuando se produce este error y el host ESXi de vSphere se detiene, termina todos los servicios que se estén ejecutando en el mismo, junto con todas las VM que aloje. Las máquinas virtuales no se apagan ordenadamente, sino que se apagan de forma abrupta. Si el host forma parte de un clúster y ha configurado la alta disponibilidad, estas máquinas virtuales se vuelven a iniciar en los otros sistemas principales del clúster. Para obtener más información, consulte [Knowledge - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window}. |

### Almacenamiento
{: #opsprocs-trouble-common-storage}

Tabla 3. Resolución de problemas de almacenamiento típicos

| Título | Descripción |
|---|---|
| Resolución de problemas de almacenamiento | Para obtener más información sobre rendimiento lento, errores imprevisibles, daños en el disco o en las VM, consulte [Resolución de problemas de almacenamiento al utilizar productos de VMware (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window}. |
| Resolución de problemas de vSAN | Para obtener más información, consulte [Manejo de errores en vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window}.  |
| Error de disco de vSAN | Para obtener más información sobre cómo identificar un disco erróneo y cómo solicitar su sustitución, consulte [Un disco duro/disco magnético de un grupo de discos de VMware vSAN da error (2077185)](https://kb.vmware.com/s/article/2077185){:new_window}. |
| Borrar problemas de estado de vSAN | En página de supervisión del cliente web de VMware vSphere, puede ver alertas y avisos relacionados con problemas de estado de vSAN. Para obtener información sobre cómo borrar estos problemas, consulte [Alertas y avisos de estado de SAN Virtual](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}.|
| Reequilibrio de vSAN | Si los discos informan de errores durante la comprobación de estado, indica que el clúster está desequilibrado y hay discos que utilizan mucho espacio, mientras que otros utilizan poco, y se debe ejecutar un reequilibrio proactivo. Esto inicia manualmente un reequilibrio de los objetos en un clúster vSAN. Para obtener más información sobre el reequilibrio proactivo de vSAN y cuándo puede ser aplicable, consulte [Reequilibrado proactivo de vSAN (2149809)](https://kb.vmware.com/s/article/2149809){:new_window}. |
| Iniciar prueba de salud de vSAN | Si sospecha que hay un problema con vSAN, puede iniciar una prueba de estado para verificar que los componentes del clúster están funcionando como se espera. La ejecución de la prueba de creación de VM crea una máquina virtual en cada host del clúster y, a continuación, la suprime. Si estas tareas se ejecutan correctamente, significa que los componentes del clúster funcionan como se espera y el clúster funciona bien. A continuación, se utiliza la prueba de rendimiento de red para detectar y diagnosticar problemas de conectividad, y para asegurarse de que el ancho de banda de red entre los hosts es adecuado. Para obtener más información, consulte [Pruebas proactivas](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window}. |
| Supervisión del rendimiento de vSAN | Para obtener más información, consulte [Supervisión del rendimiento de vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window}. Hay gráficos de rendimiento disponibles para clústeres, hosts, discos físicos, máquinas virtuales y discos virtuales. |
| Resolución de problemas de vSAN | Para obtener más información, consulte [Manejo de errores y resolución de problemas de vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window}. |


### Red
{: #opsprocs-trouble-common-network}

Tabla 4. Resolución de problemas típicos de red

| Título | Descripción |
|---|---|
|  /var/log de NSX Edge se está llenando en el Edge activo | Para obtener información sobre una solución temporal si recibe un aviso de que el disco de Edge se está llenando y descubre que la partición /var/log se está llenando, consulte [/var/log de NSX Edge se está llenando en el Edge activo (50108355)](https://kb.vmware.com/s/article/50108355){:new_window}.  |
| Prueba del ancho de banda de HCX  | Para obtener información sobre cómo utilizar `perftest` para encontrar el ancho de banda disponible dentro de los túneles HCX si cree que tiene un problema de ancho de banda de red con HCX, consulte [Pasos para ejecutar Perftest en HCX (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window}. Se realizan pruebas bidireccionales para cada `perftest`. Para el par de pasarelas, una se encuentra dentro del centro de datos de origen, que llamamos OnPrem y el otro está en {{site.data.keyword.cloud_notm}}. La forma como funciona el rendimiento de `perftest` es que el emisor intente enviar tan rápido como el enlace pueda soportar. Por lo tanto, para cada prueba, podrá ver una tasa de "remitente" mayor que la de "destinatario". Se
puede considerar la tasa de "destinatario" como un resultado de rendimiento en un solo sentido. |
| Resolución de problemas de HCX | Para obtener más información, consulte [Resolución de problemas de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting). |
| Estado de sincronización de HCX con 0% de progreso y 0 bytes con estado Error | Para obtener más información, consulte [La réplica de HCX está en Estado de sincronización de HCX con 0% de progreso y 0 bytes con estado Error (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window}. |
| Rendimiento de red de la VM bajo | Revise los valores de NIC virtual de la VM. VMware recomienda a NIC virtuales VMXNET 3 para las máquinas virtuales, puesto que es la última generación de NIC paravirtualizados diseñados para el rendimiento. Compruebe la compatibilidad de VMXNET 3 utilizando la lista de compatibilidad de VMware y, si es compatible, cambie el NIC virtual para un mejor rendimiento de red. Para obtener más información, consulte [Resolución de problemas de red](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}. |

### vCenter
{: #opsprocs-trouble-common-vcenter}

Tabla 5. Resolución de problemas típicos de vCenter

| Título | Descripción |
|---|---|
| Acceso a la consola de máquina virtual | Para obtener más información, consulte [Knowledge - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window}. |
| El nuevo certificado de servidor de vCenter no parece que se cargue | Tras reemplazar los certificados predeterminados de vCenter Server, los nuevos certificados parece que no se cargan. Para obtener más información, consulte [El nuevo certificado de servidor de vCenter no parece que se cargue](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window}. |
| vCenter Server no se puede conectar a los hosts gestionados | Tras reemplazar los certificados predeterminados de vCenter Server y reiniciar el sistema, vCenter Server no se puede conectar a los hosts gestionados. Para obtener más información, consulte [vCenter Server no se puede conectar a los hosts gestionados](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window}. |
| No se puede configurar vSphere HA cuando se utilizan certificados SSL personalizados | Después de instalar los certificados SSL personalizados, los intentos de habilitar la alta disponibilidad (HA) de vSphere fallan. Para obtener más información, consulte [No se puede configurar vSphere HA cuando se utilizan certificados SSL personalizados](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window}. |

### Licencias
{: #opsprocs-trouble-common-licenses}

Tabla 6. Resolución de problemas típicos de licencias

| Título | Descripción |
|---|---|
|  Configuración de licencias no compatible o incorrecta | Para obtener más información, consulte [Resolución de problemas de licencias de host](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window}. |
|  Una VM no se enciende | Puede que haya un problema de licencias si no puede encender una máquina virtual en un host ESXi de vSphere y recibe el mensaje ``El período de evaluación de 60 días del host ha vencido o la licencia del host ha caducado``. Para obtener más información, consulte [No se puede encender una máquina virtual](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window}. |
| Una característica no está disponible o no se puede cambiar una configuración  | Para obtener más información, consulte [No se puede configurar o utilizar una característica](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window}.  |


## Enlaces relacionados
{: #opsprocs-trouble-links}

* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [Visión general de resolución de problemas de vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-C70D5A5E-7D84-446C-B8CE-0766AA7351A4.html){:new_window}
* [Resolución de problemas de vSphere con registros](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window}
* [Gestión de operaciones en {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [Recopilación de registros de soporte](https://kb.vmware.com/s/article/1010705){:new_window}
* [Supervisión de sucesos, alarmas y acciones automatizadas](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [Archivos de registro del sistema de vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [Consideraciones sobre el cambio de artefactos de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
