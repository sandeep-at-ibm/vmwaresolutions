---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-05"

---

# Acerca de IBM Cloud for VMware Solutions

{{site.data.keyword.vmwaresolutions_full}} le permite integrar de forma rápida y sencilla o migrar sus cargas de trabajo locales de VMware a {{site.data.keyword.cloud_notm}} mediante la infraestructura escalable, segura y de alto rendimiento {{site.data.keyword.cloud_notm}} y la tecnología de virtualización híbrida VMware líder del sector.

{{site.data.keyword.vmwaresolutions_short}} le permite desplegar fácilmente sus entornos virtuales de VMware y gestionar los recursos de la infraestructura en {{site.data.keyword.cloud_notm}}. Al mismo tiempo, puede seguir utilizando la consola del producto VMware nativo con la que está familiarizado para gestionar las cargas de trabajo de VMware.

## Ventajas de IBM Cloud for VMware Solutions

{{site.data.keyword.vmwaresolutions_short}} ofrece las siguientes ventajas principales:
* **Alcance global**: permite expandir el alcance de su nube híbrida hasta un máximo de 30 {{site.data.keyword.CloudDataCents_notm}} de nivel empresarial de todo el mundo.
* **Integración perfecta**: permite una integración perfecta entre la nube híbrida y la infraestructura de {{site.data.keyword.cloud_notm}}.
* **Suministro rápido**: automatiza el despliegue y la configuración del entorno VMware, lo que le permite desplegar rápidamente un entorno VMware de nivel de empresa con servidores virtuales y {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}} a petición.
* **Simplificación**: le permite consumir una plataforma de nube VMware sin la necesidad de identificar, adquirir, desplegar y gestionar la infraestructura física subyacente (cálculo, almacenamiento y red) y las licencias de software.
* **Flexibilidad en cuanto a ampliación y reducción**: le permite ampliar y reducir fácilmente las cargas de trabajo de VMware según los requisitos de la empresa.
* **Una sola consola de gestión**: proporciona una sola consola para desplegar, acceder y gestionar los entornos de VMware en {{site.data.keyword.cloud_notm}}.

## Ofertas de despliegue

{{site.data.keyword.vmwaresolutions_short}} proporciona opciones de despliegue estandarizados y personalizables de entornos virtuales VMware. Se ofrecen los siguientes tipos de despliegues:
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**: la oferta vCenter Server le permite desplegar un entorno virtual VMware utilizando los recursos de cálculo, almacenamiento y red personalizados que mejor se ajusten a los requisitos de su empresa.
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)**: la oferta vCenter Server con Hybridity es una nube privada alojada que permite ampliar la infraestructura local a la nube de forma rápida y sencilla. El entorno VMware se basa en licencias de centro de datos definido por software de VMware proporcionadas por IBM e incluye VMware Hybrid Cloud Extension (HCX). Utilizando HCX, puede conectarse de forma segura a un entorno vSphere 5.0+ local con sitios de IBM Cloud para ofrecer una infraestructura híbrida y una auténtica movilidad de aplicaciones.
* **VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}**: la oferta Cloud Foundation proporciona un entorno virtual VMware unificado mediante el uso de recursos estándares de cálculo, almacenamiento y red de {{site.data.keyword.cloud_notm}} que están dedicados al despliegue de cada usuario.
* **VMware vSphere on {{site.data.keyword.cloud_notm}}**: la oferta vSphere on {{site.data.keyword.cloud_notm}} proporciona un servicio de virtualización personalizable que combina {{site.data.keyword.baremetal_short}} compatibles con VMware, componentes de hardware y licencias para crear su propio entorno VMware alojado por IBM.
* **NetApp ONTAP Select**: la oferta NetApp ONTAP Select le permite desplegar un clúster de almacenamiento definido por software que se ajusta a sus necesidades de un dispositivo de almacenamiento dedicado y altamente disponible basado en NetApp ONTAP Select.
* **VMware Federal on {{site.data.keyword.cloud_notm}}**: La oferta VMware Federal on {{site.data.keyword.cloud_notm}} ofrece soporte para solicitar una instancia de base vCenter Server además de ofrecer la opción de proteger las instancias desplegadas eliminando la información confidencial y la conexión de gestión abierta para el acceso continuado a la instancia para las funciones de gestión.

## Servicios adicionales

{{site.data.keyword.vmwaresolutions_short}} le permite añadir diversos servicios en el momento de solicitar la instancia o después del despliegue de la misma. Se ofrecen los siguientes servicios:

### FortiGate Security Appliance on IBM Cloud

Este servicio utiliza un par de alta disponibilidad (HA) de dispositivos de seguridad FortiGate (FSA) serie 300 que ofrecen servicios de cortafuegos, direccionamiento, NAT y VPN para proteger la conexión de la red pública a su entorno.

Este servicio solo está disponible para las instancias que se han desplegado en la V1.8 y posteriores releases.

Para obtener más información, consulte [Gestión de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

Este servicio utiliza un par de alta disponibilidad de dispositivos virtuales FortiGate que le pueden ayudar a reducir el riesgo mediante la implementación de controles de seguridad estrictos en su infraestructura virtual.

Este servicio solo está disponible para las instancias que se han desplegado en la V2.0 y posteriores releases.

Para obtener más información, consulte [Gestión de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html).

### F5 on IBM Cloud

Este servicio optimiza el rendimiento y garantiza la disponibilidad y la seguridad para aplicaciones con F5 BIG-IP Virtual Edition (VE).

Este servicio solo está disponible para las instancias que se han desplegado en la V1.9 y posteriores releases.

Para obtener más información, consulte [Gestión de F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html).

### IBM Spectrum Protect Plus on IBM Cloud

Este servicio proporciona una solución eficiente y escalable para la protección de datos, la reutilización de datos y la recuperación de datos para entornos virtuales. Puede implementarlo como una solución autónoma o integrarlo con su entorno IBM Spectrum Protect&trade; Plus para descargar copias para su almacenamiento y gestión de datos a largo plazo.

**Notas**:
* Este servicio solo está disponible para las instancias que se han desplegado en la V2.2 y posteriores releases o que se han actualizado a estos.
* Para instancias que se despliegan en V2.3 o releases posteriores, IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} es el servicio de copia de seguridad predeterminado. El servicio proporciona copias de seguridad automáticas para VM de gestión.
* Para instancias que se despliegan en V2.2, este servicio proporciona protección de datos solo para las VM de carga de trabajo.

Para obtener más información, consulte [Gestión de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html).

### Veeam on IBM Cloud

Este servicio se integra perfectamente con el entorno VMware para ayudarle a gestionar la copia de seguridad y restauración de todas las máquinas virtuales (VM) del entorno, incluida la copia de seguridad y la restauración de los componentes de gestión. Le puede proporcionar un objetivo de punto de recuperación (RPO) de menos de 15 minutos en cuanto a configuración de sus datos.

Este servicio está configurado para hacer una copia de seguridad de las VM de gestión inmediatamente después del despliegue de la instancia.

Este servicio solo está disponible para las instancias que se han desplegado en la V1.8 y posteriores releases.

Para obtener más información, consulte [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html).

### Zerto on IBM Cloud

Este servicio proporciona funciones de réplica y recuperación tras desastre para ayudar a proteger las cargas de trabajo. Para obtener más información, consulte [Gestión de Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html).

### Servicios gestionados de IMI

Estos servicios permiten que IBM Integrated Managed Infrastructure (IMI) ofrezca servicios de gestión remota dinámica para una amplia gama de infraestructuras de nube.

Estos servicios solo están disponibles para instancias de Cloud Foundation.

Para obtener más información, consulte [Solicitud de servicios gestionados de IMI](../services/managing_imi.html).

## Enlaces relacionados

* [Iniciación](../index.html)
* [Visión general de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [NetApp ONTAP Select](../netapp/np_netappoverview.html)
