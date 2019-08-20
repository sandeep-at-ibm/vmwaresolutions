---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	Recopilación de los metadatos
{: #vum-metadata}

VUM descarga metadatos sobre las actualizaciones, parches o extensiones mediante un proceso automático predefinido que puede modificar. A intervalos regulares configurables, VUM se pone en contacto con VMware o con orígenes de terceros, para recopilar los metadatos más recientes sobre actualizaciones, parches o extensiones disponibles. Sin embargo, los valores predeterminados de VMware son aceptables para su uso en la instancia de VMware vCenter Server on {{site.data.keyword.cloud}}. Puede cambiarlos según sea necesario para ajustarlos a los requisitos de la empresa.

VUM muestra las líneas base gestionadas por el sistema que se generan mediante vSAN. Las líneas base gestionadas por el sistema actualizan su contenido periódicamente de forma automática, lo que requiere que VUM tenga acceso constante a Internet. Las líneas base del sistema vSAN normalmente se renuevan cada 24 horas.

Puede utilizar las líneas base gestionadas por el sistema para actualizar los clústeres vSAN a los parches críticos recomendados, los controladores, las actualizaciones o la última versión de host ESXi admitido para vSAN.

Para la mayoría de las empresas, los valores predeterminados de VMware para VUM se consideran adecuados. A continuación se proporciona información sobre cómo cambiar estos valores si desea utilizar valores distintos para su empresa.

##	Descargar planificación
{: #vum-metadata-download-schedule}

Las actualizaciones son actualizaciones de dispositivos virtuales, parches de host y extensiones y, de forma predeterminada, se descargan diariamente las actualizaciones de VUM. Para cambiar la planificación de la descarga, acceda al cliente web de vSphere; para ello vaya a **Inicio** > **Gestor de actualizaciones** > **Gestionar** > **Valores** y seleccione **Descargar planificación** y, a continuación, pulse **Editar**.

##	Planificación de comprobación de notificación
{: #vum-metadata-notif-check-schedule}

Las notificaciones son información sobre los retiros de parches, los nuevos arreglos y las alertas, y, de forma predeterminada, VUM descarga las notificaciones por hora. Para cambiarlo, es necesario acceder al cliente web de vSphere. Para ello, vaya a **Inicio** > **Gestor de actualizaciones** > **Gestionar** > **Valores** y seleccione **Planificación de comprobación de notificación** y, a continuación, pulse **Editar**.

##	Configuración de máquina virtual
{: #vum-metadata-vm-settings}

Para cambiar los valores de la máquina virtual (VM), acceda al cliente web de vSphere. Vaya a **Inicio** > **Gestor de actualizaciones** > **Gestionar** > **Valores** y **Valores de VM** y, a continuación, pulse **Editar**.

##	Valores de host/clúster
{: #vum-metadata-host-settings}

Para cambiar los valores de Host/Clúster, acceda al cliente web de vSphere, vaya a **Inicio** > **Actualizar gestor** > **Gestionar** > **Valores** y **Host/Configuración de clúster** y, a continuación, pulse **Editar**.

## Enlaces relacionados
{: #vum-metadata-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (demostraciones)
