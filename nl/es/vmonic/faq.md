---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Preguntas frecuentes generales sobre IBM Cloud for VMware Solutions

Encuentre las respuestas a las preguntas más frecuentes sobre {{site.data.keyword.vmwaresolutions_full}}.

## ¿Qué cuentas de usuario necesito para IBM Cloud for VMware Solutions?

* **Cuenta de IBMid**. Se necesita esta cuenta para acceder a la consola de {{site.data.keyword.vmwaresolutions_short}}. La consola es una interfaz de usuario autónoma, independiente del {{site.data.keyword.slportal_full}}. Para obtener más información, consulte
[Iniciación](../index.html).
* **Cuenta de {{site.data.keyword.cloud_notm}}**. Se necesita esta cuenta para el suministro. Puede registrarse para una cuenta de {{site.data.keyword.cloud_notm}} actualizando su **cuenta de IBMid** a una cuenta de tipo Pago según uso. La cuenta de {{site.data.keyword.cloud_notm}} que utilice debe cumplir ciertos requisitos. Para obtener más información, consulte [Registro de una cuenta de {{site.data.keyword.cloud_notm}} ](signing_softlayer_account.html) y [Requisitos de una cuenta de {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).

## ¿Cómo puedo asociar mis credenciales de la infraestructura IBM Cloud a la consola de IBM Cloud for VMware Solutions?

La primera ver que solicite su instancia, siga las instrucciones de la página de credenciales de la infraestructura {{site.data.keyword.cloud_notm}} para localizar y copiar el nombre de usuario de {{site.data.keyword.cloud_notm}} y la clave de API del {{site.data.keyword.slportal}}. Las credenciales de la infraestructura {{site.data.keyword.cloud_notm}} se almacenan en la consola de {{site.data.keyword.vmwaresolutions_short}} tras el primer pedido. Los siguientes pedidos utilizan automáticamente las credenciales almacenadas.

## ¿Cómo se facturan mis consumos de la plataforma virtual VMware?

Todos los costes correspondientes a la infraestructura física y virtual y a las licencias resultantes de la instancia se cargan en su cuenta de {{site.data.keyword.cloud_notm}}. Cuando solicite una instancia, debe tener una cuenta de {{site.data.keyword.cloud_notm}} y especificar la clave de {{site.data.keyword.slapi_short}} asociada a la cuenta.

## ¿Cuáles son las diferencias entre una instancia de vCenter Server, una instancia de Cloud Foundation y un clúster de VMware vSphere?

Todos los tipos de instancias proporcionan opciones de despliegue para entornos virtuales VMware. Sin embargo, la diferencia es el grado de personalización y de automatización.

* Cuando solicita una instancia de VMware vCenter Server, despliega un entorno virtual VMware con recursos personalizados de cálculo, de almacenamiento y de red. Para obtener más información sobre los componentes desplegados, consulte la sección _Especificaciones técnicas de vCenter Server_ en [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html).
* Cuando solicita una instancia de VMware Cloud Foundation, despliega una plataforma unificada de centro de datos definido por software (SDDC). Para obtener más información sobre los componentes desplegados, consulte [Componentes de una instancia de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-instance-components).
* Al solicitar un clúster de VMware vSphere, obtendrá el máximo de flexibilidad para diseñar y crear su entorno VMware alojado mientras incorpora hardware compatible con VMware. Sin embargo, {{site.data.keyword.cloud_notm}} no automatiza la instalación, la configuración ni la activación de los componentes opcionales de VMware para el clúster de VMware vSphere.
* Las funciones que reciben soporte para las instancias de vCenter Server, las instancias de Cloud Foundation y los clústeres de vSphere son diferentes. Para obtener más información, consulte [Gráfico de comparación de ofertas](inst_comp_chart.html).

## ¿Qué se incluye en una instancia de vCenter Server?

Para obtener más información, consulte la sección _Especificaciones técnicas de vCenter Server_ en [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html).

## ¿Qué se incluye en una instancia de Cloud Foundation?

Para obtener más información, consulte [Componentes de una instancia de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## ¿Qué se incluye en un clúster de vSphere?
Para obtener más información, consulte [Componentes de VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html).

## ¿Está altamente disponible una instancia de vCenter Server de dos nodos?

Se recomienda desplegar las cargas de trabajo de producción en entornos que tengan al menos tres nodos.

Aunque VMware vSphere DRS (Distributed Resource Scheduler) y VMware HA (alta disponibilidad) están habilitados de forma predeterminada, la práctica recomendada de VMware sugiere que coloque cada uno de los tres controladores
NSX en un nodo individual.

En el despliegue mínimo de dos nodos, un nodo tiene un controlador NSX y el otro nodo tiene dos controladores NSX. Si se desactiva el nodo con dos controladores NSX, las operaciones de controlador NSX se colocan en modalidad de solo lectura y las máquinas virtuales (VM) nuevas o las VM vMotion pueden experimentar problemas de red.

Cuando se añade un tercer nodo a un clúster de dos nodos, vCenter Server vuelve a equilibrar automáticamente los tres controladores NSX entre los tres nodos y crea un entorno altamente disponible.

## ¿Puedo definir una configuración de alta disponibilidad de VMware vCenter 6.5?

No, no se recomienda. Podrían producirse errores en las funciones de {{site.data.keyword.vmwaresolutions_short}}.

## ¿Se puede cambiar el nombre de los clústeres?

Para instancias de vCenter Server, el primer clúster que se crea durante el despliegue tiene el nombre predeterminado **cluster1**. Puede cambiar el nombre del clúster predeterminado en el cliente de VMware vSphere. Cuando añada un nuevo clúster a una instancia de vCenter Server, puede especificar el nombre que desee en la consola de {{site.data.keyword.vmwaresolutions_short}}.

**Nota**: para instancias de Cloud Foundation, el nombre de clúster predeterminado no se puede cambiar.

##¿Cómo se gestionan los parches?

IBM proporciona actualizaciones continuas del componente IBM CloudDriver que se ponen a disponibilidad de los usuarios a través de la consola de {{site.data.keyword.cloud_notm}} para VMware Solutions. IBM no proporciona actualizaciones continuas de los servicios complementarios, como Zerto on {{site.data.keyword.cloud_notm}} o Veeam on {{site.data.keyword.cloud_notm}}. La obtención y la instalación de estas actualizaciones es responsabilidad del usuario.

Las actualizaciones de VMware se aplican de distinta forma en función del tipo de instancia de VMware que haya desplegado:

* Para instancias de VMware Cloud Foundation, las actualizaciones de los componentes vSphere ESXi, NSX, vCenter, Platform Services Controller y SDDC Manager se proporcionan a través de la consola de {{site.data.keyword.vmwaresolutions_short}}.
* Para instancias de VMware vCenter Server:
  * Para instancias desplegadas al nivel de la versión V2.1 o posteriores o actualizadas a las mismas, se aplicarán a los clústeres y servidores ESXi parches con las actualizaciones más recientes, pero no necesariamente las últimas, de ESXi de VMware.
  * El usuario es el responsable de todas las demás actualizaciones de los componentes de VMware, lo que incluye asegurarse de que los clústeres y servidores ESXi recién desplegados tienen las actualizaciones más recientes que necesita.
  * Para las instancias desplegadas en V2.0 o posteriores, VMware Update Manager (VUM) está integrado en vCenter Server. Puede configurar VUM de modo que descargue las actualizaciones de ESXi de VMware.

Para obtener más información, consulte:
* [Soporte de VMware](https://www.vmware.com/support.html)
* [Aplicación de actualizaciones a instancias de vCenter Server](../vcenter/vc_applyingupdates.html)
* [Aplicación de actualizaciones a instancias de Cloud Foundation](../sddc/sd_applyingupdates.html)

## ¿Representa NSX Edge de servicios de gestión un riesgo para la seguridad?

Aunque VMware NSX Edge para servicios de gestión está en una subred pública, se siguen medidas de seguridad para garantizar que no representa un riesgo para la seguridad. Estas medidas son:
*  Se configura el cortafuegos de NSX Edge de modo que solo permita el tráfico HTTPS de salida (puerto TCP 443) iniciado por las máquinas virtuales de gestión.
*  Se utiliza SNAT (conversión de direcciones de red) para que las direcciones IP privadas no resulten visibles fuera de la red privada.
*  Se inhabilita el acceso remoto para el dispositivo NSX Edge de servicios de gestión.
*  Se utilizan contraseñas aleatorias y cifradas para acceder al NSX Edge de servicios de gestión desde la red privada.

## ¿Representan NSX Edge gestionado por el cliente un riesgo para la seguridad?

Aunque el Edge NSX gestionado por cliente está conectado a la VLAN pública, se utilizan medidas de seguridad para garantizar que no representa un riesgo de seguridad. Estas medidas son:
*  Se coloca una regla de cortafuegos para permitir solo el tráfico saliente desde el rango de direcciones IP de la subred privada.
*  Se coloca una regla SNAT (conversión de direcciones de red de origen) (inhabilitada de forma predeterminada) para convertir todas las direcciones IP de la subred privada en una dirección IP única en la subred pública.
*  Se inhabilita el acceso remoto para el dispositivo NSX Edge gestionado por el cliente.
*  Se utilizan contraseñas aleatorias y cifradas para acceder al NSX Edge gestionado por el cliente desde la red privada.

## ¿Cómo elijo los centros de datos para mis instancias?

Los despliegues de instancia tienen requisitos de infraestructura física estrictos, que varían entre {{site.data.keyword.CloudDataCents_notm}}. Al realizar el pedido de la instancia, los centros de datos disponibles se listan dentro de las regiones y puede seleccionar el que desee de la lista.

Para obtener más información, consulte las secciones _Disponibilidad de IBM Cloud Data Center_ en:
* [Requisitos y planificación de instancias de vCenter Server](../vcenter/vc_planning.html)
* [Requisitos y planificación de instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_planning.html)
* [Requisitos y planificación de instancias de Cloud Foundation](../sddc/sd_planning.html)
* [Requisitos y planificación de VMware vSphere on IBM Cloud](../vsphere/vs_planning.html)
* [Requisitos y planificación de las instancias de NetApp ONTAP Select](../netapp/np_planning.html)
* [Requisitos y planificación de instancias de VMware Federal](../vcenter/vc_fed_planning.html)

## ¿Cuánto se tarda en desplegar mi instancia?

Puede comprobar el estado del despliegue de la instancia visualizando el historial de despliegues en la página de detalles de la instancia desde la consola de {{site.data.keyword.vmwaresolutions_short}}.

## ¿Utiliza VMware vSphere on IBM Cloud el sistema de automatización para instalar, configurar y activar la pila de VMware?

No. VMware vSphere on {{site.data.keyword.cloud_notm}} no aprovecha el sistema avanzado de automatización de las plataformas Cloud Foundation y vCenter Server. Según lo que solicite, la plataforma proporciona licencias opcionales de VMware, servidores ESXi y, si lo desea, un par de alta disponibilidad de cortafuegos físicos FortiGate. Si se crea un nuevo clúster, también se suministran tres nuevas VLAN: una pública y dos privadas.

VMware ESXi se instala automáticamente en cada servidor nativo, pero el usuario es el responsable de instalar los componentes adicionales de VMware, como vCenter Server o NSX. Aunque vSphere on {{site.data.keyword.cloud_notm}} garantiza que el hardware compatible con VMware se solicita en función de los componentes de VMware seleccionado, no se utiliza el sistema de automatización para configurar y activar el entorno de VMware. El usuario es el responsable de diseñar y planificar la arquitectura del entorno alojado por IBM.

## ¿Cómo puedo ver una lista de todas las notificaciones?

Para ver el historial completo de notificaciones, pulse **Notificaciones** en el panel de navegación izquierdo.

## ¿Qué pasa si tengo un problema con IBM Cloud for VMware Solutions?

Si necesita ayuda con {{site.data.keyword.vmwaresolutions_short}}, póngase en contacto con el equipo de soporte de IBM a través de uno de los canales de soporte. Para obtener más información, consulte [Cómo ponerse en contacto con el equipo de soporte de IBM](trbl_support.html).

### Enlaces relacionados

* [Notificaciones](notifications.html)
* [Instancias de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Instancias de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Acceso a la consola](loginmethod.html)
* [Cuentas de usuario y valores](useraccount.html)
