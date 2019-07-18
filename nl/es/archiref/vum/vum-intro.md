---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-21"

subcollection: vmware-solutions


---

# Introducción a VMware Update Manager
{: #vum-intro}

La finalidad de este documento es proporcionarle, como administrador del sistema de la instancia de {{site.data.keyword.vmwaresolutions_full}} vCenter Server, instrucciones sobre cómo configurar VMware Update Manager (VUM) para mantener la moneda del entorno de vCenter Server.

VUM permite la gestión centralizada y automatizada de parches y versiones para VMware vSphere y le permite realizar las siguientes tareas en el entorno VMware vCenter Server on {{site.data.keyword.cloud_notm}}:
* Actualizar y aplicar un parche a los hosts ESXi de vSphere.
* Instalar y actualizar software de terceros en los hosts.
* Actualizar el hardware de máquina virtual, las herramientas de VMware y los dispositivos virtuales.

En este documento también se describen los procesos para mantener los siguientes componentes de la instancia de vCenter Server:
* vCenter Server Appliance
* NSX
* vSAN

Este documento describe la implementación de un servidor proxy, basado en CentOS y en Squid, para habilitar VUM para acceder a los repositorios de VMware. Cuando VUM solicita un recurso desde el servidor de actualización en VMware, la solicitud se envía primero al servidor proxy y, a continuación, el servidor proxy envía la solicitud al servidor de actualizaciones a través de la Pasarela de servicios externos (ESG). Una vez que el servidor proxy ha obtenido el recurso, este lo envía a VUM.

![Diagrama de visión general](../../images/vum-vcsproxy.svg "Diagrama de visión general")

Actualmente, vCenter Server despliega vSphere 6.5, lo que significa que VUM ahora está integrado en vCenter Server Appliance (VCSA), y como el componente de cliente VUM es un plug-in que se ejecuta en el cliente web de vSphere, se habilita automáticamente después del despliegue de VCSA. Sin embargo, VUM no tiene acceso a Internet para acceder a los repositorios de VMware.

Esta configuración documentada utiliza el modelo de despliegue VUM "all-in-one" conectado a Internet que utiliza la red pública de {{site.data.keyword.cloud_notm}} para proporcionar acceso a Internet para descargar actualizaciones y parches.

Los clientes que requieren el uso de conexiones de internet alternativas deben investigar el servicio de descargas de VMware vSphere Update Manager (UMDS), que queda fuera del ámbito de esta publicación.

Aunque VUM se puede configurar para importar actualizaciones desde un repositorio compartido o importar parches y extensiones manualmente desde un archivo comprimido, estos temas no se tratan en este documento.

En vSphere 6.5, ya no se da soporte al registro de VUM en un VCSA durante la instalación del servidor VUM en un sistema Windows independiente en el que no puede desplegar VUM en una VM dentro del entorno de vCenter Server.

Este documento está organizado en las secciones siguientes:
* [Visión general de VMware Update Manager](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-overview): se describe el proceso VUM y se ofrece una introducción a los términos clave necesarios para comprender las operaciones y la interfaz de usuario de la herramienta.
* **Instalación, configuración y uso**: se describen los pasos necesarios para que VUM funcione en una instancia de vCenter Server:
  - [Configuración inicial](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config): una tarea que se realiza una sola vez para:
      - Configurar la red NSX para permitir que el servidor proxy acceda a Internet.
      - Instalar y configurar un servidor proxy para proporcionar acceso a Internet para VUM.
      - Que la configuración inicial de VUM utilice el servidor proxy.
  - [Recopilación de los metadatos](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-metadata): VUM descarga metadatos sobre las actualizaciones, parches o extensiones mediante un proceso automático predefinido que puede modificar. A intervalos regulares configurables, VUM se pone en contacto con VMware o con orígenes de terceros, para recopilar los metadatos más recientes sobre actualizaciones, parches o extensiones disponibles.
  - [Creación de líneas base](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines): utilice las líneas base predefinidas y los grupos de línea base o cree unos personalizados. Las líneas base y los grupos de línea base se adjuntan a los objetos de inventario.
  - [Exploración y revisión](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-scanning): se escanean los objetos de inventario y se revisan los resultados para determinar cómo cumplen con las líneas base y los grupos de línea base. Los resultados de la exploración se pueden filtrar por búsqueda de texto, selección de grupos, selección de línea base y selección de estado de conformidad.
  - [Transferencia y corrección](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-staging): los parches y las extensiones se pueden transferir opcionalmente en etapas antes de la corrección para asegurarse de que se descarguen en el host. Durante la corrección, VUM aplica los parches, las extensiones y las actualizaciones a los objetos de inventario.

En este documento se da por supuesto que ha desplegado una instancia de vCenter Server primaria o varias instancias de vCenter Server primarias separadas. Si tiene instancias de vCenter Server primarias y secundarias desplegadas y que utilizan el inicio de sesión único (SSO), consulte [vCenters enlazados por SSO](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa).

Si ha desplegado un vCenter Server mediante vSAN, consulte primero [Actualización de clústeres vSAN](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vsan).

Si desea actualizar la automatización de la gestión de la infraestructura de {{site.data.keyword.cloud_notm}}, utilice la consola de {{site.data.keyword.vmwaresolutions_short}}.

La [consola de {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console) le permite llevar a cabo las siguientes acciones:
*	Actualizar licencias por ejemplo, actualizar NSX Base a otra versión
*	Iniciar actualizaciones en la plataforma vCenter Server, por ejemplo pasar a la versión 2.5
*	Ver el estado de las actualizaciones
*	Ver las actualizaciones instaladas

Este recurso solo habilita la actualización automatizada de los componentes de gestión de las instancias de vCenter Server. Las actualizaciones de producto de VMware deben aplicarse siguiendo los procedimientos que se detallan en este documento.

## Enlaces relacionados
{: #vum-intro-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (demostraciones)
