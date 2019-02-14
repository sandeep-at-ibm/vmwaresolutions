---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-09"

---

# Sucesos de {{site.data.keyword.cloudaccesstrailshort}}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento de cómo interactúan los usuarios y las aplicaciones con {{site.data.keyword.vmwaresolutions_short}} en {{site.data.keyword.Bluemix_notm}}.

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.Bluemix_notm}}. Para obtener
más información, consulte [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla).

## Tabla de sucesos de {{site.data.keyword.cloudaccesstrailshort}}

Consulte la tabla siguiente para ver la descripción de las columnas en la tabla de sucesos de Activity Tracker.

Tabla 1. Descripción de la tabla de sucesos de Activity Tracker

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

Para obtener más información, consulte [Campos de sucesos de Activity Tracker](https://console.bluemix.net/docs/services/cloud-activity-tracker/at_event.html#at_event).

## Seguimiento de sucesos de gestión de instancias

Cuando gestiona las cuentas de usuario, las instancias, los clústeres y los servicios en {{site.data.keyword.vmwaresolutions_short}}, se genera un suceso y se envía al **dominio de la cuenta** en Activity Tracker.

Consulte la tabla siguiente para ver las acciones que generan y envían sucesos de gestión a Activity Tracker.

Tabla 2. Descripción de las acciones que generan sucesos de gestión

| Acción                                   | Descripción | Resultado |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.user_account.update`    | <ul><li>Se ha recibido la solicitud de actualizar la cuenta de usuario.</li><li>Se ha respondido a la solicitud de actualizar la cuenta de usuario.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>Se ha recibido la solicitud de actualizar notificaciones.</li><li>Se ha respondido a la solicitud de actualizar notificaciones.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>Se ha recibido la solicitud de borrar datos seguros.</li><li>Se ha respondido a la solicitud de borrar datos seguros.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>Se ha recibido la solicitud de migrar a la cuenta bss.</li><li>Se ha respondido a la solicitud de migrar a la cuenta bss.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.order`                 | <ul><li>Se ha recibido la solicitud de solicitar una instancia de Cloud Foundation.</li><li>Se ha respondido a la solicitud de solicitar una instancia de Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.delete`                | <ul><li>Se ha recibido la solicitud de suprimir una instancia de Cloud Foundation.</li><li>Se ha respondido a la solicitud de suprimir una instancia de Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.add_hosts`             | <ul><li>Se ha recibido la solicitud de añadir servidores ESXi a una instancia de Cloud Foundation.</li><li>Se ha respondido a la solicitud de añadir servidores ESXi a una instancia de Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.remove_hosts`          | <ul><li>Se ha recibido la solicitud de suprimir servidores ESXi de una instancia de Cloud Foundation.</li><li>Se ha respondido a la solicitud de suprimir servidores ESXi de una instancia de Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.create_cluster`        | <ul><li>Se ha recibido la solicitud de crear un clúster para una instancia de Cloud Foundation.</li> <li>Se ha respondido a la solicitud de crear un clúster para una instancia de Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.delete_cluster`        | <ul><li>Se ha recibido la solicitud de suprimir un clúster de una instancia de Cloud Foundation.</li><li>Se ha respondido a la solicitud de suprimir un clúster de una instancia de Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.schedule_update`       | <ul><li>Se ha recibido la solicitud de planificar una actualización para una instancia de Cloud Foundation.</li><li>Se ha respondido a la solicitud de planificar una actualización para una instancia de Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>Se ha recibido la solicitud de solicitar una instancia de vCenter Server.</li><li>Se ha respondido a la solicitud de solicitar una instancia de vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>Se ha recibido la solicitud de suprimir una instancia de vCenter Server.</li><li>Se ha respondido a la solicitud de suprimir una instancia de vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>Se ha recibido la solicitud de añadir servidores ESXi a una instancia de vCenter Server.</li><li>Se ha respondido a la solicitud de añadir servidores ESXi a una instancia de vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>Se ha recibido la solicitud de suprimir servidores ESXi de una instancia de vCenter Server.</li><li>Se ha respondido a la solicitud de suprimir servidores ESXi de una instancia de vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>Se ha recibido la solicitud de planificar una actualización para una instancia de vCenter Server.</li><li>Se ha respondido a la solicitud de planificar una actualización para una instancia de vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>Se ha recibido la solicitud de crear un clúster para una instancia de vCenter Server.</li><li>Se ha respondido a la solicitud de crear un clúster para una instancia de vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>Se ha recibido la solicitud de suprimir un clúster de una instancia de vCenter Server.</li> <li>Se ha respondido a la solicitud de suprimir un clúster de una instancia de vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>Se ha recibido la solicitud de actualizar la licencia de VMware NSX.</li><li>Se ha respondido a la solicitud de actualizar la licencia de VMware NSX.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>Se ha recibido la solicitud de actualizar una instancia de vCenter Server a una instancia de vCenter Server con el paquete híbrido (Hybridity).</li><li>Se ha respondido a la solicitud de actualizar una instancia de vCenter Server a una instancia de vCenter Server con el paquete híbrido (Hybridity).</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>Se ha recibido la solicitud de solicitar un clúster de vSphere.</li><li>Se ha respondido a la solicitud de solicitar un clúster de vSphere.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>Se ha recibido la solicitud de actualizar un clúster de vSphere.</li><li>Se ha respondido a la solicitud de actualizar un clúster de vSphere.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>Se ha recibido la solicitud de guardar la configuración de un clúster de vSphere.</li><li>Se ha respondido a la solicitud de guardar la configuración de un clúster de vSphere.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>Se ha recibido la solicitud de solicitar una instancia de NetApp ONTAP Select.</li><li>Se ha respondido a la solicitud de solicitar una instancia de NetApp ONTAP Select.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>Se ha recibido la solicitud de suprimir una instancia de NetApp ONTAP Select.</li><li>Se ha respondido a la solicitud de suprimir una instancia de NetApp ONTAP Select.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>Se ha recibido la solicitud de actualizar la configuración de un servicio.</li><li>Se ha respondido a la solicitud de actualizar la configuración de un servicio.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>Se ha recibido la solicitud de solicitar un servicio para una instancia.</li><li>Se ha respondido a la solicitud de solicitar un servicio para una instancia.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>Se ha recibido la solicitud de suprimir un servicio de una instancia.</li><li>Se ha respondido a la solicitud de suprimir un servicio de una instancia.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>Se ha recibido la solicitud de actualizar una instancia de vCenter Server existente a una instancia de vCenter Server con el paquete híbrido (Hybridity).</li><li>Se ha respondido a la solicitud de actualizar una instancia de vCenter Server existente a una instancia de vCenter Server con el paquete híbrido (Hybridity).</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service.deploy` | Se ha ejecutado la acción de desplegar un servicio en una instancia. | `success` |
| `vmware-solutions.service.undeploy` | Se ha ejecutado la acción de eliminar un servicio de una instancia. | `success` |

## Seguimiento de sucesos para el servicio KMIP for VMware on IBM Cloud

Cuando gestiona claves para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}, se genera un suceso y se envía al **dominio de cuenta** de Activity Tracker.

Consulte la tabla siguiente para ver las acciones que generan y envían sucesos para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} .

Tabla 3. Descripción de las acciones que generan sucesos para el servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Acción                                      | Descripción                               | Resultado |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>Se ha recibido la solicitud de crear una clave.</li><li>Se ha respondido a la solicitud de crear una clave.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>Se ha recibido la solicitud de obtener el contenido de una clave.</li><li>Se ha respondido a la solicitud de obtener el contenido de una clave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>Se ha recibido la solicitud de obtener los atributos de una clave.</li><li>Se ha respondido a la solicitud de obtener los atributos de una clave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>Se ha recibido la solicitud de activar una clave.</li><li>Se ha respondido a la solicitud de activar una clave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>Se ha recibido la solicitud de revocar una clave.</li><li>Se ha respondido a la solicitud de revocar una clave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>Se ha recibido la solicitud de destruir una clave.</li><li>Se ha respondido a la solicitud de destruir una clave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>Se ha recibido la solicitud de buscar la versión de KMIP for VMware on {{site.data.keyword.cloud_notm}}.</li><li>Se ha respondido a la solicitud de buscar la versión de KMIP for VMware on {{site.data.keyword.cloud_notm}}.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |

## Dónde ver los sucesos

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el **dominio de la cuenta** de {{site.data.keyword.cloudaccesstrailshort}} que está disponible en la región de {{site.data.keyword.Bluemix_notm}} en la que se han generado los sucesos.

### Enlaces relacionados

* [Suministro de Activity Tracker](../../cloud-activity-tracker/how-to/provision.html)
* [Navegación al panel de control de Activity Tracker en la consola de {{site.data.keyword.cloud_notm}}](../../cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html)
* [Visión general de KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_standalone_considerations.html)
