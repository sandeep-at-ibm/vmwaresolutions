---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Gestión de IBM Spectrum Protect Plus on IBM Cloud

## Acceso a la consola de gestión de IBM Spectrum Protect Plus

Para gestionar el servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}}, debe acceder a la consola de gestión de IBM Spectrum Protect Plus siguiendo estos pasos:
1. Utilice el VPN de la infraestructura de {{site.data.keyword.cloud_notm}} o un servidor de gestión para permitir el acceso a la dirección IP de la máquina virtual de IBM Spectrum Protect Plus. Encontrará la dirección IP en la página de detalles del servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} en la consola de {{site.data.keyword.vmwaresolutions_short}}.
2. Para acceder a la consola de gestión de IBM Spectrum Protect Plus, pulse **Ver consola de IBM Spectrum Protect Plus** en la página de detalles del servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} e inicie una sesión utilizando las credenciales que aparecen en la misma página de detalles del servicio.

## Aplicación de arreglos para IBM Spectrum Protect Plus on IBM Cloud

El usuario es el responsable de mantener el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} al nivel de la versión más reciente. Puede descargar las actualizaciones necesarias desde la página [Soporte de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus).

Para obtener más información, consulte los temas siguientes:
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)

## Actualización del sistema operativo de la máquina virtual IBM Spectrum Protect Plus

Para actualizar el sistema operativo de la máquina virtual IBM Spectrum Protect Plus, debe iniciar una sesión como usuario **root**. La contraseña del usuario **root** es la misma que la contraseña que encontrará en la página de detalles del servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

## Copia de seguridad y restauración de componentes de gestión para instancias que tienen instalado IBM Spectrum Protect Plus on IBM Cloud

 **Nota**: la información siguiente se aplica a las instalaciones de IBM Spectrum Proteger Plus en instancias desplegadas en (o actualizadas a) V2.3 o posterior. Para instancias de V2.2, este servicio proporciona protección de datos solo para las máquinas virtuales de carga de trabajo.

El servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} está preconfigurado con un trabajo de copia de seguridad de gestión que se ejecuta automáticamente para realizar copia de seguridad de los siguientes componentes de gestión diariamente con un máximo de siete puntos de restauración:
* VMware vCenter Server
* Platform Services Controller (PSC)
* IBM CloudDriver
* **Solo instancias de Cloud Foundation**: VMware SDDC Manager
* **Solo instancias de vCenter Server con HA AD/DNS**: Par de alta disponibilidad de AD/DNS

Si se producen anomalías en los componentes de gestión, puede abrir una incidencia [poniéndose en contacto con IBM Support](../vmonic/trbl_support.html) para solicitar que los componentes de gestión se restauren a una copia de seguridad anterior.

## Enlaces relacionados

* [Visión general de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [Cómo aumentar el almacenamiento de vsnap para IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} con posterioridad al despliegue](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [Documentación de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
