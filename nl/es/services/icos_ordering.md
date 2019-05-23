---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud y configuración de IBM Cloud Object Storage con Veeam
{: #icos_ordering}

Con el release de Veeam Availability Suite 9.5 Actualización 4, Veeam es compatible con IBM Cloud Object Storage (ICOS). La solicitud de IBM Cloud Object Storage no está automatizada al solicitar Veeam en IBM Cloud, pero se puede añadir tras el despliegue.

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

Para añadir un repositorio de escalado dentro de Veeam, consulte
[Adición de repositorios de escalado](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window}. Siga los pasos y vuelva a esta sección para continuar con las tareas siguientes.

## Mantenimiento y gestión del nivel de nube
{: #icos_ordering-manage-cloud}

Para obtener información sobre cómo mantener y gestionar el nivel de nube, consulte
[Gestión de datos de nivel de capacidad](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window}.

## Enlaces relacionados
{: #icos_ordering-related}

* [Visión general de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [Solicitud de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Solicitud de servicios gestionados para Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
