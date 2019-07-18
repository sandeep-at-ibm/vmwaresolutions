---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-28"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Iniciación a IBM Cloud for VMware Solutions
{: #getting-started}

En esta guía de aprendizaje de iniciación a {{site.data.keyword.vmwaresolutions_full}}, le guiamos a través del proceso de pedido de una instancia y algunos servicios adicionales para el mismo.
{:shortdesc}

## Antes de empezar
{: #getting-started-prereqs}

Antes de empezar a trabajar con {{site.data.keyword.vmwaresolutions_short}}, revise la siguiente información importante sobre los requisitos del navegador, las cuentas de usuario, las opciones de despliegue y los servicios de complemento.

### Requisitos del navegador
{: #getting-started-browser-req}

Se admiten los siguientes navegadores:
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

Microsoft Internet Explorer no recibe soporte.
{:note}

Para ver y trabajar mejor con la consola de {{site.data.keyword.vmwaresolutions_short}}, defina una resolución de pantalla de al menos 1024 px de anchura por 500 px de altura.

### Cuentas de usuario
{: #getting-started-user-accts}

Necesita una cuenta de {{site.data.keyword.cloud_notm}} y una cuenta de infraestructura de {{site.data.keyword.cloud_notm}}. Estas cuentas deben cumplir ciertos requisitos.

| Cuenta | Descripción |
|:------- |:---------- |
| IBMid | Al utilizar el **IBMid**, puede tener un único nombre de usuario de inicio de sesión para todos los productos y servicios de IBM que utilice, incluido {{site.data.keyword.cloud_notm}}. {{site.data.keyword.vmwaresolutions_short}} se proporciona como una solución de infraestructura en el catálogo de {{site.data.keyword.cloud_notm}}. Para acceder a la consola de {{site.data.keyword.vmwaresolutions_short}}, debe tener un **IBMid**.<br><br>Para utilizar **IBMid** para iniciar sesión en la consola de {{site.data.keyword.vmwaresolutions_short}}, debe asociar el **IBMid** con una cuenta de {{site.data.keyword.cloud_notm}}. Cuando inicie una sesión en la consola por primera vez, se le indicará que asocie su **IBMid** existente con una cuenta de {{site.data.keyword.cloud_notm}} o que se registre para conseguir una nueva cuenta de {{site.data.keyword.cloud_notm}}. La nueva cuenta de {{site.data.keyword.cloud_notm}} se asociará automáticamente con el **IBMid**. Debe pasar por este proceso una sola vez.<br><br>Si tiene problemas para asociar su **IBMid** con una cuenta de {{site.data.keyword.cloud_notm}}, consulte [Resolución de problemas para acceder a {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-accessing#accessing). |
| Cuenta de IBM Cloud | Para solicitar y utilizar servicios de {{site.data.keyword.cloud_notm}}, se necesita una cuenta de {{site.data.keyword.cloud_notm}}. La información de facturación está asociada a la cuenta de {{site.data.keyword.cloud_notm}}. El coste de la infraestructura física y virtual y las licencias resultantes se cargarán a su cuenta de {{site.data.keyword.cloud_notm}}. |
| Cuenta de la infraestructura IBM Cloud | Para obtener información sobre los requisitos de una cuenta de infraestructura de {{site.data.keyword.cloud_notm}},
consulte [Requisitos para la cuenta de infraestructura de {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).<br><br>Puede enlazar las cuentas de infraestructura de {{site.data.keyword.cloud_notm}} con las cuentas de {{site.data.keyword.cloud_notm}} para utilizar la infraestructura combinada como servicio (IaaS) y los recursos de la plataforma como servicio (PaaS). A continuación, puede acceder a los recursos de IaaS y a los recursos de PaaS desde un solo inicio de sesión. El enlace de las cuentas también le proporciona una sola factura para todos los recursos de PaaS e IaaS que utiliza:<br>Si no tiene una cuenta de infraestructura de {{site.data.keyword.cloud_notm}}, solicite una siguiendo el procedimiento de [Inicio de sesión para una cuenta de infraestructura de IBM Cloud](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts#signing_required_accounts-infra) y, a continuación, enlace la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} con la cuenta de {{site.data.keyword.cloud_notm}} siguiendo el procedimiento de [Cómo cambiar a IBMid y enlazar cuentas](/docs/account?topic=account-unifyingaccounts#unifyingaccounts).<br>Si tiene una cuenta de infraestructura de {{site.data.keyword.cloud_notm}}, puede enlazarla con la cuenta de {{site.data.keyword.cloud_notm}} siguiendo el procedimiento de [Cómo cambiar a IBMid y enlazar cuentas](/docs/account?topic=account-unifyingaccounts#unifyingaccounts).
{: caption="Tabla 1. Cuentas de usuario necesarias" caption-side="top"}

### Ofertas de despliegue
{: #getting-started-depl-offerings}

Revise y elija la oferta de despliegue.

| Oferta de despliegue | Descripción |
|:------------------- |:----------- |
| [VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview) | Con la oferta de vCenter Server, puede desplegar un entorno virtual de VMware utilizando recursos de cálculo, almacenamiento y red personalizados para que se adapten mejor a sus necesidades empresariales.
| [VMware vCenter Server on IBM Cloud con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview) | La oferta de vCenter Server con el paquete híbrido (Hybridity) es una nube privada alojada que permite ampliar la infraestructura local a la nube de forma rápida y sencilla. El entorno VMware se basa en licencias de centro de datos definido por software de VMware proporcionadas por IBM e incluye VMware Hybrid Cloud Extension (HCX). Mediante el uso de HCX, puede conectarse de forma segura a un entorno vSphere 5.0+ local con sitios de {{site.data.keyword.cloud_notm}} para ofrecer una infraestructura híbrida y una auténtica movilidad de aplicaciones.
| [VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview) | La oferta de vSphere on {{site.data.keyword.cloud_notm}} proporciona un servicio de virtualización personalizable que combina {{site.data.keyword.baremetal_short}} compatibles con VMware, componentes de hardware y licencias para crear su propio entorno VMware alojado por IBM. |
| [NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview) | La oferta NetApp ONTAP Select le permite desplegar un clúster de almacenamiento definido por software que se ajusta a sus necesidades de un dispositivo de almacenamiento dedicado y altamente disponible basado en NetApp ONTAP Select. |
{: caption="Tabla 2. Ofertas de despliegue" caption-side="top"}

### Servicios complementarios
{: #getting-started-add-on-services}

Revise y elija los servicios de complemento para la oferta de despliegue.

| Nombre de servicio | Descripción |
|:------------ |:----------- |
| [F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | El servicio F5 on {{site.data.keyword.cloud_notm}} (F5 BIG-IP® Virtual Edition) proporciona servicios de equilibrio inteligente de carga L4-L7 y de gestión del tráfico a escala local y global, potentes funciones de protección de red y de cortafuegos de aplicaciones web y acceso seguro y federado a las aplicaciones. |
| [FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations) | El servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} despliega un par de dispositivos FortiGate Security Appliance (FSA) serie 300 en modalidad altamente disponible para ofrecer servicios de cortafuegos, direccionamiento, NAT y VPN para proteger todos los servidores y máquinas virtuales de la VLAN pública de sus instancias. |
| [FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | El servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} despliega un par de dispositivos FortiGate Virtual Appliance en el entorno, lo que puede ayudar a reducir el riesgo implementando controles de seguridad críticos dentro de su infraestructura virtual. |
| [HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations) | El servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}} aplica y controla el cumplimiento de las normas de seguridad y proporciona funciones detalladas de control de acceso basado en roles (RBAC), aprobación y auditoría. Cuando se combina con HyTrust DataControl, el servicio puede asegurarse de que los datos de las cargas de trabajo y las máquinas virtuales no abandonen una región, un clúster o un servidor ESXi determinados en el {{site.data.keyword.CloudDataCent_notm}}. |
| [HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations) | El servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}} ofrece un cifrado de alta seguridad con claves de gestión integrada para proteger las cargas de trabajo en todo su ciclo de vida. El servicio puede proporcionar cifrado tanto a nivel de sistema operativo como a nivel de datos, lo que significa que se puede cifrar y descifrar cualquier directorio, carpeta o archivo de una carga de trabajo.|
| [HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | El servicio HyTrust KeyControl on {{site.data.keyword.cloud_notm}} simplifica la gestión de las cargas de trabajo cifradas automatizando y simplificando el ciclo de vida de las claves de cifrado. El servicio puede gestionar fácilmente las claves de cifrado a escala utilizando el cifrado compatible con FIPS 140-2. |
| [IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} incorpora la potencia de los microservicios y contenedores al entorno VMware en {{site.data.keyword.cloud_notm}}. Con este servicio, puede ampliar el mismo modelo operativo VMware e {{site.data.keyword.cloud_notm}} privado con el que está familiarizado y las herramientas del entorno local en {{site.data.keyword.cloud_notm}}. |
| [IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations) | El servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} proporciona una solución eficiente y escalable para la protección de datos, la reutilización de datos y la recuperación de datos para entornos virtuales. Puede implementar el servicio como una solución autónoma o integrarlo con su entorno IBM Spectrum Protect para descargar copias para su almacenamiento y gestión de datos a largo plazo. |
| [KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | El servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} ofrece un servicio altamente disponible para gestionar las claves de cifrado que utiliza VMware en {{site.data.keyword.cloud_notm}}. Este servicio ofrece capacidad de tiempo de ejecución que permite a los clientes crear, recuperar, activar, revocar y destruir las claves de cifrado. También proporciona capacidad de gestión para mantener las asociaciones entre las credenciales del cliente y las claves de cifrado. |
| [Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | El servicio Veeam on {{site.data.keyword.cloud_notm}} se puede integrar de forma fácil y directa con sus hipervisores VMware para ayudar a la empresa a alcanzar un alto grado de disponibilidad. Este servicio puede proporcionar objetivos de puntos de recuperación y de tiempo para sus datos y aplicaciones. Los objetivos de puntos de recuperación y de tiempo se pueden proporcionar menos de 15 minutos después de finalizar la configuración. Con este servicio, puede controlar directamente las copias de seguridad y las operaciones de restauración de todas las máquinas virtuales de la infraestructura desde la consola de Veeam. |
| [VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations) | El servicio HCX on {{site.data.keyword.cloud_notm}} permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) de {{site.data.keyword.cloud_notm}} y al mismo sin realizar ninguna conversión ni cambio.|
| [Zerto on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | El servicio Zerto on {{site.data.keyword.cloud_notm}} ofrece funciones de réplica y de recuperación tras desastre, que se pueden integrar en las ofertas de despliegue para proteger y recuperar los datos del entorno virtual VMware en {{site.data.keyword.cloud_notm}}. |
{: caption="Tabla 3. Servicios de complementos disponibles para las ofertas de despliegue" caption-side="top"}

## Paso 1: Acceso a la consola de IBM Cloud for VMware Solutions
{: #getting-started-step1}

La consola de {{site.data.keyword.vmwaresolutions_short}} es la interfaz con la que solicita y gestiona sus despliegues. Cada despliegue se gestiona como una instancia en la consola. La consola es una interfaz de usuario autónoma, independiente del portal de clientes de infraestructura de {{site.data.keyword.cloud_notm}}.

Para acceder a la consola de {{site.data.keyword.vmwaresolutions_short}}:
1. Vaya a https://cloud.ibm.com/infrastructure/vmware-solutions/console.
2. Inicie sesión en la consola con su **IBMid**.

## Paso 2: Configuración de la cuenta de usuario y valores
{: #getting-started-step2}

Antes de solicitar una instancia, debe escribir el nombre de usuario y la clave de API de la cuenta de infraestructura de {{site.data.keyword.cloud_notm}} en la página **Valores** de la consola.

Para obtener información sobre cómo configurar la cuenta de usuario y los valores, consulte [Gestión de cuentas de usuario y valores](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Paso 3: Solicitud de una instancia
{: #getting-started-step3}

Una vez que haya decidido una oferta de despliegue, que se gestiona como una instancia en la consola, inicie el proceso de solicitud.

Para obtener información sobre cómo solicitar una instancia, consulte los temas siguientes en función de la selección de la oferta de despliegue:
* [Pedido de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Solicitud de clústeres nuevos de vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Solicitud de instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Paso 4: Visualización de la instancia
{: #getting-started-step4}

Después de colocar un pedido de instancia en el **Paso 3**, el despliegue de la instancia se inicia automáticamente. Puede realizar un seguimiento del estado del despliegue visualizando los detalles de la instancia. Cuando haya finalizado el despliegue de la instancia, puede ver el resumen y la información detallada de la instancia y sus servicios de complemento también en la página de detalles de la instancia.

Para obtener información sobre cómo ver la instancia que ha solicitado, consulte los temas siguientes:
* [Visualización de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Visualización de instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Visualización de instancias de NetApp ONTAP Select](/docs/services/vmwaresolutions/services?topic=vmware-solutions-np_viewinginstances#np_viewinginstances)
