---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Preguntas frecuentes generales sobre IBM Cloud for VMware Solutions
{: #faq}

Encuentre las respuestas a las preguntas más frecuentes sobre {{site.data.keyword.vmwaresolutions_full}}.

## ¿Qué cuentas de usuario necesito para IBM Cloud for VMware Solutions?
{: #faq-user-accts}
{: faq}

* **Cuenta de IBMid**. Se necesita esta cuenta para acceder a la consola de {{site.data.keyword.vmwaresolutions_short}}. La consola es una interfaz de usuario autónoma, independiente del {{site.data.keyword.slportal}}. Para obtener más información, consulte
[Iniciación](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started).
* **Cuenta de {{site.data.keyword.cloud_notm}}**. Se necesita esta cuenta para el suministro. Puede registrarse para una cuenta de {{site.data.keyword.cloud_notm}} utilizando un **IBMid** existente o creando un nuevo **IBMid**.
* **Cuenta de infraestructura de {{site.data.keyword.cloud_notm}}**. Esta cuenta, conocida anteriormente como la cuenta de **IBM SoftLayer**, se utiliza para iniciar la sesión en el portal de clientes de infraestructura de {{site.data.keyword.cloud_notm}} que proporciona alguna función adicional para gestionar los productos y servicios de la infraestructura. Puede obtener una cuenta de infraestructura de {{site.data.keyword.cloud_notm}} actualizando su **cuenta de {{site.data.keyword.cloud_notm}}** a un tipo de cuenta de Pago según uso, o enlazando su cuenta de infraestructura de {{site.data.keyword.cloud_notm}} (SoftLayer) existente con su cuenta de {{site.data.keyword.cloud_notm}}. La cuenta de infraestructura de {{site.data.keyword.cloud_notm}} que está utilizando debe cumplir determinados requisitos. Para obtener más información, consulte [Registro para las cuentas necesarias](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account) y [Requisitos de cuenta de infraestructura de {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## ¿Cómo puedo asociar mis credenciales de la infraestructura IBM Cloud a la consola de IBM Cloud for VMware Solutions?
{: #faq-associate-credentials}
{: faq}

La primera vez que solicite su instancia, siga las instrucciones de la página **Valores** de la consola para localizar y copiar el nombre de usuario de la infraestructura de {{site.data.keyword.cloud_notm}} y la clave de API del {{site.data.keyword.slportal}}. Las credenciales de la infraestructura {{site.data.keyword.cloud_notm}} se almacenan en la consola de {{site.data.keyword.vmwaresolutions_short}} tras el primer pedido. Los siguientes pedidos utilizan automáticamente las credenciales almacenadas.

## ¿Cómo se facturan mis consumos de la plataforma virtual VMware?
{: #faq-billing}
{: faq}

Todos los costes correspondientes a la infraestructura física y virtual y a las licencias resultantes de la instancia se cargan en su cuenta de {{site.data.keyword.cloud_notm}}. Cuando solicite una instancia, debe tener una cuenta de {{site.data.keyword.cloud_notm}} y especificar la clave de {{site.data.keyword.slapi_short}} asociada a la cuenta.

## ¿Cuáles son las diferencias entre una instancia de vCenter Server y un clúster de VMware vSphere?
{: #faq-vcs-cf-vss}
{: faq}

Todos los tipos de instancias proporcionan opciones de despliegue para entornos virtuales VMware. Sin embargo, la diferencia es el grado de personalización y de automatización.

* Cuando solicita una instancia de VMware vCenter Server, despliega un entorno virtual VMware con recursos personalizados de cálculo, de almacenamiento y de red. Para obtener más información sobre los componentes desplegados, consulte [Especificaciones técnicas para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs).
* Al solicitar un clúster de VMware vSphere, obtendrá el máximo de flexibilidad para diseñar y crear su entorno VMware alojado mientras incorpora hardware compatible con VMware. Sin embargo, {{site.data.keyword.cloud_notm}} no automatiza la instalación, la configuración ni la activación de los componentes opcionales de VMware para el clúster de VMware vSphere.
* Las funciones que reciben soporte de las instancias de vCenter Server y los clústeres de vSphere son diferentes. Para obtener más información, consulte [Gráfico de comparación de ofertas](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

## ¿Qué se incluye en una instancia de vCenter Server?
{: #faq-vcs}
{: faq}

Para obtener más información, consulte [Especificaciones técnicas para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs).

## ¿Qué se incluye en un clúster de vSphere?
{: #faq-vss}
{: faq}

Para obtener más información, consulte [Componentes de VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview).

## ¿Está altamente disponible una instancia de vCenter Server de dos nodos?
{: #is-a-two-node-vcenter-server-instance-highly-available}
{: faq}

Se recomienda desplegar las cargas de trabajo de producción en entornos que tengan al menos tres nodos.

VMware vSphere DRS (Distributed Resource Scheduler) y VMware HA (alta disponibilidad) están habilitados de forma predeterminada. Sin embargo, la práctica recomendada de VMware sugiere que coloque cada uno de los tres controladores
NSX en un nodo individual.

En el despliegue mínimo de dos nodos, un nodo tiene un controlador NSX y el otro nodo tiene dos controladores NSX. Si se desactiva el nodo con dos controladores NSX, las operaciones de controlador NSX se colocan en modalidad de solo lectura y las máquinas virtuales (VM) nuevas o las VM vMotion pueden experimentar problemas de red.

Cuando se añade un tercer nodo a un clúster de dos nodos, vCenter Server vuelve a equilibrar automáticamente los tres controladores NSX entre los tres nodos y crea un entorno altamente disponible.

## ¿Puedo definir una configuración de alta disponibilidad de VMware vCenter 6.5?
{: #faq-ha}
{: faq}

No, no se recomienda. Podrían producirse errores en las funciones de {{site.data.keyword.vmwaresolutions_short}}.

## ¿Se puede cambiar el nombre de los clústeres?
{: #faq-rename-cluster}
{: faq}

Para instancias de vCenter Server, el primer clúster que se crea durante el despliegue tiene el nombre predeterminado **cluster1**. Puede cambiar el nombre del clúster predeterminado en el cliente de VMware vSphere. Cuando añada un clúster a una instancia de vCenter Server, puede especificar el nombre que desee en la consola de {{site.data.keyword.vmwaresolutions_short}}.

Para instancias de Cloud Foundation, el nombre de clúster predeterminado no se puede cambiar.
{:note}

## ¿Cómo se gestionan los parches?
{: #faq-patches}
{: faq}

IBM proporciona actualizaciones continuas del código de IBM desplegando la instancia de servidor virtual (VSI) de IBM CloudDriver a petición. IBM no proporciona actualizaciones continuas de los servicios complementarios, como Zerto on {{site.data.keyword.cloud_notm}} o Veeam on {{site.data.keyword.cloud_notm}}. La obtención y la instalación de estas actualizaciones es responsabilidad del usuario.

Las actualizaciones de VMware se aplican de distinta forma en función del tipo de instancia.

### Instancias de VMware Cloud Foundation
{: #faq-patches-cf}

Las actualizaciones de los componentes vSphere ESXi, NSX, vCenter, Platform Services Controller y SDDC Manager se proporcionan a través de la consola de {{site.data.keyword.vmwaresolutions_short}}.

### Instancias de VMware vCenter Server
{: #faq-patches-vcs}

Para instancias desplegadas al nivel de la versión V2.1 o posteriores o actualizadas a las mismas, se aplicarán parches a los clústeres y servidores ESXi con las actualizaciones más recientes, pero no necesariamente las últimas, de ESXi de VMware.

El usuario es el responsable de todas las demás actualizaciones de los componentes de VMware, lo que incluye asegurarse de que los clústeres y servidores ESXi recién desplegados tienen las actualizaciones más recientes que necesita.
{:important}

Para las instancias desplegadas en V2.0 o posteriores, VMware Update Manager (VUM) está integrado en vCenter Server. Puede configurar VUM para descargar actualizaciones de ESXi desde VMware.

Para más información, consulte los siguientes recursos:
* [Soporte de VMware](https://www.vmware.com/support.html)
* [Aplicación de actualizaciones a instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)
* [Aplicación de actualizaciones a instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_applyingupdates)

## ¿Representa NSX Edge de servicios de gestión un riesgo para la seguridad?
{: #faq-mgmt-nsx}
{: faq}

Aunque VMware NSX Edge para servicios de gestión está en una subred pública, se siguen las siguientes medidas de seguridad para garantizar que no representa un riesgo para la seguridad:
*  Se configura el cortafuegos de NSX Edge de modo que solo permita el tráfico HTTPS de salida (puerto TCP 443) iniciado por las máquinas virtuales de gestión.
*  Se utiliza SNAT (conversión de direcciones de red) para que las direcciones IP privadas no resulten visibles fuera de la red privada.
*  Se inhabilita el acceso remoto para el dispositivo NSX Edge de servicios de gestión.
*  Se utilizan contraseñas aleatorias y cifradas para acceder al NSX Edge de servicios de gestión desde la red privada.

## ¿Representan NSX Edge gestionado por el cliente un riesgo para la seguridad?
{: #faq-customer-nsx}
{: faq}

Aunque el Edge NSX gestionado por cliente está conectado a la VLAN pública, se utilizan medidas de seguridad para garantizar que no representa un riesgo de seguridad. Se han adoptado las medidas de seguridad siguientes:
*  Se coloca una regla de cortafuegos para permitir solo el tráfico saliente desde el rango de direcciones IP de la subred privada.
*  Se coloca una regla SNAT (conversión de direcciones de red de origen) (inhabilitada de forma predeterminada) para convertir todas las direcciones IP de la subred privada en una dirección IP única en la subred pública.
*  Se inhabilita el acceso remoto para el dispositivo NSX Edge gestionado por el cliente.
*  Se utilizan contraseñas aleatorias y cifradas para acceder al NSX Edge gestionado por el cliente desde la red privada.

## ¿Cómo elijo los centros de datos para mis instancias?
{: #faq-data-center}
{: faq}

Los despliegues de instancia tienen requisitos de infraestructura física estrictos, que varían entre {{site.data.keyword.CloudDataCents_notm}}. Al realizar el pedido de la instancia, los centros de datos disponibles se listan dentro de las regiones y puede seleccionar el que desee de la lista.

Para obtener más información, consulte las secciones _Disponibilidad de IBM Cloud Data Center_ en:
* [Requisitos y planificación de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Requisitos y planificación de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Requisitos y planificación de VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [Requisitos y planificación de las instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning)

## ¿Cuánto se tarda en desplegar mi instancia?
{: #faq-deploy}
{: faq}

Puede comprobar el estado del despliegue de la instancia visualizando el historial de despliegues en la página de detalles de la instancia desde la consola de {{site.data.keyword.vmwaresolutions_short}}.

## ¿Utiliza VMware vSphere on IBM Cloud el sistema de automatización para instalar, configurar y activar la pila de VMware?
{: #faq-vss-automation}
{: faq}

No. VMware vSphere on {{site.data.keyword.cloud_notm}} no utiliza la automatización avanzada que se encuentra en las plataformas Cloud Foundation ni vCenter Server. Según lo que solicite, la plataforma proporciona licencias opcionales de VMware, servidores ESXi y, si lo desea, un par de alta disponibilidad de cortafuegos físicos FortiGate. Si se crea un nuevo clúster, también se suministran tres nuevas VLAN: una VLAN pública y dos VLAN privadas.

VMware ESXi se instala automáticamente en cada servidor nativo, pero el usuario es el responsable de instalar los componentes adicionales de VMware, como vCenter Server o NSX. Aunque vSphere on {{site.data.keyword.cloud_notm}} garantiza que el hardware compatible con VMware se solicita en función de los componentes de VMware seleccionado, no existe ninguna automatización para configurar ni activar el entorno de VMware. El usuario es el responsable de diseñar y planificar la arquitectura del entorno alojado por IBM.

## ¿Cómo puedo ver una lista de todas las notificaciones?
{: #faq-notification}
{: faq}

Para ver el historial completo de notificaciones, pulse **Notificaciones** en el panel de navegación izquierdo.

## ¿Qué pasa si tengo un problema con IBM Cloud for VMware Solutions?
{: #faq-support}
{: faq}

Si necesita ayuda con {{site.data.keyword.vmwaresolutions_short}}, póngase en contacto con el equipo de soporte de IBM a través de uno de los canales de soporte. Para obtener más información, consulte [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

## Enlaces relacionados
{: #faq-related}

* [Notificaciones](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [Instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Acceso a la consola](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [Cuentas de usuario y valores](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
