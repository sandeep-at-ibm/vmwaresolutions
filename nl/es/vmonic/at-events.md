---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-02"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Sucesos de Activity Tracker
{: #at-events}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento de cómo interactúan los usuarios y las aplicaciones con {{site.data.keyword.vmwaresolutions_short}} en {{site.data.keyword.cloud_notm}}.

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte
[Acerca de IBM® Cloud Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#gs_ov).

## Tabla de sucesos de Activity Tracker
{: #at-events-table}

Consulte la tabla siguiente para ver la descripción de las columnas en la tabla de sucesos de Activity Tracker.

| Columna                | Tipo de valor | Descripción |
|:----------------------|:-----------|:------------|
| Time                  | N/D        | Fecha y hora de creación del suceso. |
| initiator.name        | Serie     | El IBMid del usuario que inicia la acción. |
| target_name           | Serie     | El recurso en el que se ejecuta la acción. |
| target.typeURI        | Serie     | El identificador universal exclusivo (UUID) del destino en el que se ejecuta la acción. |
| action                | Serie     | La acción que desencadena el suceso. Los valores válidos son `create`, `update` y `delete`. |
| outcome               | Serie     | El resultado de la acción. El valor puede ser `success`, `failure` o `pending`. |
| reason_reasonCode     | Entero    | El código de razón del resultado. |
| initiator_host_address| Serie     | La dirección IP de la que procede la solicitud. |
{: caption="Tabla 1. Descripción de la tabla de sucesos de Activity Tracker" caption-side="top"}

Para obtener más información, consulte [Campos de sucesos](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-event).

## Seguimiento de sucesos de gestión de instancias
{: #at-events-instance-mgmt}

Cuando gestiona las cuentas de usuario, las instancias, los clústeres y los servicios en {{site.data.keyword.vmwaresolutions_short}}, se genera un suceso y se envía al **dominio de la cuenta** en Activity Tracker.

Consulte la tabla siguiente para ver las acciones que generan y envían sucesos de gestión a Activity Tracker.

| Acción                                   | Descripción | Resultado |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` | La clave de API de infraestructuras para una cuenta se actualiza. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.account-notification.update` | El valor de notificación de una cuenta se actualiza. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.instance-secure-data.wipe` | Los datos seguros de instancia se borran. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.instance-bss-account.migrate` |	Una instancia se migra a una cuenta BSS. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs.create` | Se crea una instancia de vCenter Server. |`pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs.delete` | Se suprime una instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-host.add` | Se añade un host a una instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-host.remove` | Se elimina un host de una instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs.update` | Se actualiza una instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-cluster.create` | Se crea un clúster para una instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-cluster.delete` | Se suprime un clúster para una instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-nsx-license.update` | La licencia de NSX se actualiza para una instancia de servidor vCenter. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-hybridity.add` | El paquete de hibridación se actualiza para una instancia de servidor vCenter. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-hybridity.remove` | El paquete de hibridación se elimina para una instancia de servidor vCenter. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-nfs-storage.add` | Se añade almacenamiento NFS a una instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-nfs-storage.remove` | Se elimina almacenamiento NFS a una instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vcs-plan.update` | Se actualiza un plan de instancia de vCenter Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vss.create` | Se crea una instancia de vSphere Server. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vss.update` | Se actualiza una instancia de vSphere. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.vss-template.remove` | Se elimina una plantilla de vSphere. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.service.create` | Se crea un servicio. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.service.delete` | Se suprime un servicio. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.service-hybridity.upgrade` | Un paquete de hibridación se actualiza a `versión`. | `pendiente`<br>`satisfactorio`<br>`error` |
{: caption="Tabla 2. Descripción de las acciones que generan sucesos de gestión" caption-side="top"}

## Seguimiento de sucesos para el servicio KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Cuando gestiona claves para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}, se genera un suceso y se envía al **dominio de cuenta** de Activity Tracker.

Consulte la tabla siguiente para ver las acciones que generan y envían sucesos para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}.

| Acción                                      | Descripción                               | Resultado |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` | Se crea una clave KMIP. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.kmip-key.retrieve` | Se recupera una clave KMIP. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.kmip-key-attributes.retrieve` | Se recuperan los atributos de una clave KMIP. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.kmip-key.activate` | Se activa una clave KMIP. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.kmip-key.revoke` | Se revoca una clave KMIP. | `pendiente`<br>`satisfactorio`<br>`error` |
| `vmware-solutions.kmip-key.destroy` | Se destruye una clave KMIP. | `pendiente`<br>`satisfactorio`<br>`error` |
{: caption="Tabla 3. Descripción de las acciones que generan sucesos para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Dónde ver los sucesos
{: #at-events-viewing}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el **dominio de la cuenta** de {{site.data.keyword.cloudaccesstrailshort}} que está disponible en la región de {{site.data.keyword.cloud_notm}} en la que se han generado los sucesos.

Utilice {{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA para ver la instancia. Para obtener más información, consulte
[Visualización de sucesos](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events).

## Enlaces relacionados
{: #at-events-related}

* [Suministro de una instancia](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Navegación a la interfaz de usuario web](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [Visión general de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
