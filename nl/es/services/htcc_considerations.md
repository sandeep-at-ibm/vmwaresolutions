---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: HyTrust CloudControl, HTCC, tech specs HTCC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de HyTrust CloudControl on IBM Cloud
{: #htcc_considerations}

El servicio HyTrust CloudControl on {{site.data.keyword.cloud}} aplica y controla el cumplimiento de las normas de seguridad e incluye el control de acceso basado en roles (RBAC), aprobación y auditoría. Cuando el servicio se combina con HyTrust DataControl, el servicio garantiza que las máquinas virtuales y los datos de carga de trabajo no dejen una región, clúster o servidor ESXi particular dentro del {{site.data.keyword.CloudDataCent_notm}}.

Este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en, o que se han actualizado a, V2.3 o releases posteriores. La versión actual de HyTrust CloudControl que está instalada es la 5.5.1.
{:note}

## Especificaciones técnicas para HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-specs}

Los siguientes componentes se solicitan y se incluyen en el servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust CloudControl
{: #htcc_considerations-appliance}

* CPU: 4 vCPU
* RAM: 16 GB
* Disco: 70 GB VMDK residente en vSAN en un clúster convergente
* Red: ubicada en una red portátil privada respaldada por VLAN para la gestión

### Alta disponibilidad
{: #htcc_considerations-ha}

Se despliegan dos dispositivos CloudControl en una configuración activa-pasiva.

### Licencias y tarifas
{: #htcc_considerations-licenses}

Licencia por host: se solicita una licencia de HyTrust CloudControl por cada host del entorno.

## Consideraciones al eliminar HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-remove}

Antes de eliminar el servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, asegúrese de inhabilitar **Blindaje de la contraseña raíz**, si está configurado, y de suprimir todos los hosts protegidos de HyTrust CloudControl.

## Enlaces relacionados
{: #htcc_considerations-related}

* [Solicitud de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Gestión de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sitio web de HyTrust](https://www.hytrust.com/)
