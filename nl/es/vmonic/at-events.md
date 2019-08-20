---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Sucesos de Activity Tracker
{: #at-events}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento de cómo interactúan los usuarios y las aplicaciones con {{site.data.keyword.vmwaresolutions_short}} en {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.at_full_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Puede utilizar este servicio para investigar la actividad anormal y las acciones críticas, y cumplir con los requisitos de auditoría de regulación. Además, puede ser alertado sobre las acciones a medida que suceden. Los sucesos se recopilan se ajustan a la normativa de Cloud Auditing Data Federation (CADF). Para obtener más información, consulte [{{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).

## Seguimiento de sucesos de gestión de instancias
{: #at-events-instance-mgmt}

Cuando gestiona las cuentas de usuario, las instancias, los clústeres y los servicios en {{site.data.keyword.vmwaresolutions_short}}, se genera un suceso y se envía a un dominio global o a una instancia del servicio en la ubicación en la que se ha suministrado el servicio. Para obtener más información, consulte [Supervisión de sucesos globales y basados en ubicación](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

La tabla siguiente proporciona las acciones que generan y envían sucesos de gestión a Activity Tracker.

| Acción                                   | Descripción |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` | La clave de API de infraestructuras para una cuenta se actualiza. |
| `vmware-solutions.account-notification.update` | El valor de notificación de una cuenta se actualiza. |
| `vmware-solutions.instance-secure-data.wipe` | Los datos seguros de instancia se borran. |
| `vmware-solutions.instance-bss-account.migrate` |	Una instancia se migra a una cuenta BSS. |
| `vmware-solutions.vcs.create` | Se crea una instancia de vCenter Server. |
| `vmware-solutions.vcs.delete` | Se suprime una instancia de vCenter Server. |
| `vmware-solutions.vcs-host.add` | Se añade un host a una instancia de vCenter Server. |
| `vmware-solutions.vcs-host.remove` | Se elimina un host de una instancia de vCenter Server. |
| `vmware-solutions.vcs.update` | Se actualiza una instancia de vCenter Server. |
| `vmware-solutions.vcs-cluster.create` | Se crea un clúster para una instancia de vCenter Server. |
| `vmware-solutions.vcs-cluster.delete` | Se suprime un clúster para una instancia de vCenter Server. |
| `vmware-solutions.vcs-nsx-license.update` | La licencia de NSX se actualiza para una instancia de servidor vCenter. |
| `vmware-solutions.vcs-nfs-storage.add` | Se añade almacenamiento NFS a una instancia de vCenter Server. |
| `vmware-solutions.vcs-nfs-storage.remove` | Se elimina almacenamiento NFS a una instancia de vCenter Server. |
| `vmware-solutions.vcs-plan.update` | Se actualiza un plan de instancia de vCenter Server. |
| `vmware-solutions.vss.create` | Se crea una instancia de vSphere Server. |
| `vmware-solutions.vss.update` | Se actualiza una instancia de vSphere. |
| `vmware-solutions.vss-template.remove` | Se elimina una plantilla de vSphere. |
| `vmware-solutions.service.create` | Se crea un servicio. |
| `vmware-solutions.service.delete` | Se suprime un servicio. |
{: caption="Tabla 1. Descripción de las acciones que generan sucesos de gestión" caption-side="top"}

## Seguimiento de sucesos para el servicio KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Cuando gestiona claves para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}, se genera un suceso y se envía a un dominio global o a una instancia del servicio en la ubicación en la que se ha suministrado el servicio. Para obtener más información, consulte [Supervisión de sucesos globales y basados en ubicación](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

En la tabla siguiente se proporcionan las acciones que generan y envían sucesos para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}.

| Acción                                      | Descripción                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` | Se crea una clave KMIP. |
| `vmware-solutions.kmip-key.retrieve` | Se recupera una clave KMIP. |
| `vmware-solutions.kmip-key-attributes.retrieve` | Se recuperan los atributos de una clave KMIP. |
| `vmware-solutions.kmip-key.activate` | Se activa una clave KMIP. |
| `vmware-solutions.kmip-key.revoke` | Se revoca una clave KMIP. |
| `vmware-solutions.kmip-key.destroy` | Se destruye una clave KMIP. |
{: caption="Tabla 2. Descripción de las acciones que generan sucesos para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Dónde ver los sucesos
{: #at-events-viewing}

Los sucesos están disponibles en la ubicación de **Frankfurt**.

Solo hay 1 instancia de {{site.data.keyword.at_full_notm}} por ubicación. Para ver los sucesos, debe acceder a la interfaz de usuario web del servicio {{site.data.keyword.at_full_notm}} en la ubicación **EU-DE**. Para obtener más información, consulte [Inicio de la interfaz de usuario web a través de la interfaz de usuario de IBM Cloud](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

## Enlaces relacionados
{: #at-events-related}

* [Suministro de una instancia](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Navegación a la interfaz de usuario web](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [Visión general de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
