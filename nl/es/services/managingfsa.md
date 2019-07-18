---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: FortiGate Security console, FortiGate 300 console, login FortiGate console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestión de FortiGate Security Appliance on IBM Cloud
{: #managingfsa}

Después de que se instale correctamente el servicio FortiGate Security Appliance on {{site.data.keyword.cloud}}, podrá gestionar y configurar reglas de cortafuegos para FSA desde la consola de FortiGate.

Debe asegurarse de que las reglas de cortafuegos de FSA están definidas de modo que permiten comunicaciones HTTPS de salida (puerto TCP 443) iniciadas por los componentes de gestión como, por ejemplo, el gestor virtual de Zerto para comunicar con la base de datos de gestión externa en la infraestructura de {{site.data.keyword.cloud_notm}} en Internet. Las comunicaciones HTTPS salientes (puerto TCP 443) se originan en la dirección IP pública de los servicios de gestión de VMware NSX Edge Services Gateway (ESG) de su instancia.
{:important}

## Acceso a la consola de FortiGate serie 300
{: #managingfsa-access-console}

Para gestionar el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, debe acceder a la consola de FortiGate® serie 300 de una de estas formas:
* Inicie una sesión en el cliente web de FortiOS utilizando las credenciales que encontrará en la página de detalles del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.
* Acceda a la consola mediante una conexión SSH utilizando las credenciales que encontrará en la página de detalles del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.

Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Enlaces relacionados
{: #managingfsa-related}

* [Visión general de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sitio web fortinet.com](https://www.fortinet.com/){:external}
* [Biblioteca de documentos de Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:external}
