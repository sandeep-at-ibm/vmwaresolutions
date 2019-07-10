---

copyright:

  years: 2016, 2019

lastupdated: "2019-05-31"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# ID de usuario de IBM
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}} mantiene un conjunto de usuarios en la cuenta que utiliza la automatización de
{{site.data.keyword.cloud_notm}} cuando realiza operaciones como añadir hosts, clústeres o almacenamiento a la instancia de VMware. Los usuarios de su cuenta también se pueden utilizar para la instalación y configuración de servicios mediante la automatización de servicios de {{site.data.keyword.cloud_notm}}. Revise las secciones siguientes para ver los ID de usuario de automatización de {{site.data.keyword.cloud_notm}}.

Las operaciones de la instancia de VMware fallarán si los ID de usuario de IBM se suprimen, se inhabilitan, o si se cambian sus contraseñas.
{:important}

## ID de usuario de vCenter y Platform Services Controller
{: #audit_user_ids-vcenter-psc}

A partir de V2.5, {{site.data.keyword.vmwaresolutions_short}} utiliza los ID de usuario siguientes para añadir un origen de identidad, incorporado de forma predeterminada, en vCenter.

Tabla 1. ID de usuario de vCenter y Platform Services Controller

| Usuario     | ID de usuario      | Método | Descripción |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Utilizado para la configuración de VMware, por ejemplo, configurar la alta disponibilidad de VMware y crear conmutadores distribuidos. Se utiliza tras el despliegue para emparejar instancias primarias y secundarias de vCenter Server. |
| Cliente | customerroot | SSH    | Creado solo para uso del cliente. |
| IBM      | automation@``root_domain``<br/>(usuario de Active Directory) | HTTP | Utilizado tras el despliegue para añadir y eliminar hosts y clústeres, y para desplegar y configurar máquinas virtuales para servicios complementarios. |
| Cliente | Administrator@vsphere.local | HTTP | Creado solo para uso del cliente. |

HTTP se utiliza para la configuración de vCenter, así como para las operaciones de VMware como añadir hosts, clústeres o almacenamiento para la gestión de recursos de vCenter.
{:note}

## ID de usuario de NSX Manager
{: #audit_user_ids-nsx-mgr}

Tabla 2. ID de usuario de NSX Manager

| Usuario     | ID de usuario      | Descripción |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(usuario de Active Directory) | Se utiliza tras el despliegue para añadir direcciones IP de NSX VTEP, gestionar la configuración de host y clúster al añadir hosts y clústeres, y gestionar la configuración ESG para servicios complementarios que requieren acceso a la red pública para la notificación de licencias, activación o uso. |
| Cliente | arrendatario        | Creado solo para uso del cliente. |

## ID de usuario del host ESXi
{: #audit_user_ids-esxi}

Tabla 3. ID de usuario del host ESXi

| Usuario     | ID de usuario      | Descripción |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Se utiliza tras el despliegue para añadir almacenamiento NFS adicional, configurar rutas para dicho almacenamiento y ejecutar todo el código de validación del servidor. |
| Cliente | root         | Creado solo para uso del cliente. |

## ID de usuario de Microsoft Active Directory
{: #audit_user_ids-ad}

Tabla 4. ID de usuario de Active Directory

| Usuario     | ID de usuario       | Descripción |
|:---------|:------------- |:------------|
| IBM      | automation    | Se utiliza para añadir un host, añadir una máquina virtual para el servicio y configurar entradas DNS y Active Directory. |
| Cliente | Administrador | Creado solo para uso del cliente. |

## Identificadores de usuarios de servicio
{: #audit_user_ids-services}

Tabla 5. Identificadores de usuarios de servicio

| ID de usuario                                    | Descripción |
|:-------------------------------------------|:----------- |
| prod-BigIP-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio F5 on {{site.data.keyword.cloud_notm}}. |
| prod-Caveonix-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}. |
| prod-Fortigate-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}. |
| prod-FortigateVM-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustCC-``ID_5_letras``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustDC-``ID_5_letras``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustKC-``ID_5_letras``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}. |
| prod-KMIPAdapter-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}. |
| prod-ICP-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio {{site.data.keyword.cloud_notm}} Private Hosted. |
| prod-SPPlus-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. |
| prod-Veeam-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio Veeam on {{site.data.keyword.cloud_notm}}. |
| prod-HCX-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio VMware HCX on {{site.data.keyword.cloud_notm}}. |
| prod-Zerto-``ID_dinámico``-@``nombre del dominio`` | Se utiliza para la instalación y configuración del servicio Zerto on {{site.data.keyword.cloud_notm}}. |

Los ID dinámicos son de ocho a diez letras de longitud. {:note}

## Enlaces relacionados
{: #audit_user_ids-related}

* [Consideraciones sobre el cambio de artefactos de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Sucesos de Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
