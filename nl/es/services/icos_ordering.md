---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

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
[Crear una nueva instancia de servicio](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-order-storage#creating-a-new-service-instance). Siga los pasos y vuelva a esta sección para continuar con las tareas siguientes.

## Creación de un grupo
{: #icos_ordering-bucket}

Para crear un grupo, consulte
[Crear algunos grupos para almacenar los datos](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-getting-started-tutorial#gs-create-buckets). Siga los pasos y vuelva a esta sección para continuar con las tareas siguientes.

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
