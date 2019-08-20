---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: HCX updates, HCX management console, login HCX console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}


# Gestión de VMware HCX on IBM Cloud
{: #managinghcx}

## Acceso a las consolas de gestión de HCX on IBM Cloud
{: #managinghcx-accessing-consoles}

Para gestionar el servicio HCX on {{site.data.keyword.cloud}}, debe acceder a la consola de HCX Cloud o a la consola de administración de HCX Manager:
1. Utilice el VPN de la infraestructura de {{site.data.keyword.cloud_notm}} o un servidor de gestión para permitir el acceso a la dirección IP del dispositivo virtual HCX Manager (HCX Manager). Encontrará la dirección IP en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} en la consola de {{site.data.keyword.vmwaresolutions_short}}.
2. Para acceder a la consola de Cloud HCX, pulse **Ver consola de HCX Cloud** en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} e inicie una sesión utilizando las credenciales de vCenter Server.
3. Para acceder a la consola de administración de HCX Manager, pulse **Ver la consola de administración de HCX Manager** en la página de detalles del servicio HCX on {{site.data.keyword.cloud_notm}} e inicie una sesión utilizando las credenciales de HCX Manager que aparecen en la misma página de detalles del servicio.

Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Aplicación de actualizaciones a HCX on IBM Cloud
{: #managinghcx-updates}

HCX on {{site.data.keyword.cloud_notm}} se despliega con la última compilación probada de la tecnología de VMware Hybrid Cloud Extension. VMware envía actualizaciones a estas compilaciones regularmente, lo que incluye arreglos importantes y características nuevas. Estas compilaciones se envían a instalaciones de HCX on {{site.data.keyword.cloud}} automáticamente, incluidas instalaciones de HCX locales.

Para aplicar los arreglos de mantenimiento enviados a su entorno, debe utilizar la Consola de administración de HCX Manager en el centro de datos local y la instancia de vCenter Server on {{site.data.keyword.cloud_notm}}.

Si no ve una actualización de compilación que está esperando, si tiene problemas con HCX, o si desea que se envíe al sistema la última compilación de HCX enviada inmediatamente, abra una incidencia de soporte siguiendo los pasos de [Cómo ponerse en contacto con el soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

## Enlaces relacionados
{: #managinghcx-related}

* [Visión general de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [Glosario de términos de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Visión general de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}
* [Documentación de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
