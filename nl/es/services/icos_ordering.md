---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-11"

keywords: IBM Cloud Object Storage, ICOS configuration, order Cloud Object Storage

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud y configuración de IBM Cloud Object Storage con Veeam
{: #icos_ordering}

Con el release de Veeam Availability Suite 9.5 Actualización 4, Veeam es compatible con IBM Cloud Object Storage (ICOS). La solicitud de IBM Cloud Object Storage no está automatizada al solicitar Veeam on IBM Cloud, pero se puede añadir tras el despliegue.

Para solicitar IBM Cloud Object Storage, realice las tareas siguientes en el orden especificado.

## Creación de una instancia de Object Storage
{: #icos_ordering-obj}

Para crear una instancia de Object Storage, consulte
[Creación de una nueva instancia de servicio](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance). Siga los pasos y vuelva a esta sección para continuar con las tareas siguientes.

## Creación de un grupo
{: #icos_ordering-bucket}

Para crear un grupo, consulte
[Crear algunos grupos para almacenar los datos](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets). Siga los pasos y vuelva a esta sección para continuar con las tareas siguientes.

## Creación de credenciales de servicio
{: #icos_ordering-service-cred}

Para crear credenciales de servicio, incluyendo credenciales HMAC, consulte
[Credenciales de servicio](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials). Siga los pasos y vuelva a esta sección para continuar con las tareas siguientes.

## Adición de un repositorio de escalado
{: #icos_ordering-scale-repo}

* Como parte de la instalación y configuración del servicio Veeam, se crea un repositorio de copia seguridad de
escalado con el nombre `IC4V Scale-Out Repository`. `Repositorio de copia de seguridad de máquina virtual predeterminado de IC4V` se añade al repositorio de escalado como una extensión.
* Al crear el trabajo de copia de seguridad, debe seleccionar `IC4V Scale-Out Repository` como repositorio de copia de seguridad en lugar de `Repositorio de copia de seguridad de configuración predeterminado de IC4V`. El último repositorio está destinado a las copias de seguridad de configuración de Veeam.
* Puede añadir más repositorios a este repositorio predeterminado, como por ejemplo un repositorio de copia de seguridad de tipo Almacenamiento de objetos. Para obtener más información, consulte
[Añadir repositorios de Escalado (Scale-out)](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:external}. Siga los pasos y vuelva a esta sección para continuar con las tareas siguientes.

## Mantenimiento y gestión del nivel de nube
{: #icos_ordering-manage-cloud}

Para obtener más información, consulte [Gestión de datos al nivel de capacidad](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:external}.

## Enlaces relacionados
{: #icos_ordering-related}

* [Visión general de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [Solicitud de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Servicios gestionados para Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Veeam on {{site.data.keyword.cloud_notm}} - Demos](https://www.ibm.com/demos/collection/Veeam-on-IBM-Cloud/){:external}
