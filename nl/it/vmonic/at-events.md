---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

# Eventi di {{site.data.keyword.cloudaccesstrailshort}}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tenere traccia di come utenti e applicazioni interagiscono con {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.Bluemix_notm}}.

Il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.Bluemix_notm}}. Per ulteriori informazioni, vedi [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla).

## Tabella eventi di {{site.data.keyword.cloudaccesstrailshort}}

Controlla la seguente tabella per la descrizione delle colonne nella tabella degli eventi di Activity Tracker.

Tabella 1. Descrizione della tabella degli eventi di Activity Tracker

| Colonna                | Tipo di valore | Descrizione |
|:----------------------|:-----------|:------------|
| Time                  | N/A        | La data e l'ora in cui è stato creato l'evento. |
| initiator.name        | Stringa     | L'ID IBM dell'utente che inizia l'azione. |
| target_name           | Stringa     | La risorsa su cui viene eseguita l'azione. |
| target.typeURI        | Stringa     | L'UUID (Universally Unique Identifier) della destinazione su cui viene eseguita l'azione. |
| action                | Stringa     | L'azione che attiva l'evento. I valori validi sono `create`, `update` e `delete`. |
| outcome               | Stringa     | Il risultato dell'azione. Il valore è `success`, `failure` o `pending`. |
| reason_reasonCode     | Intero    | Il codice motivo del risultato. |
| initiator_host_address| Stringa     | L'indirizzo IP da cui proviene la richiesta. |

Per ulteriori informazioni, vedi [Campi evento di Activity Tracker](/docs/services/cloud-activity-tracker/at_event.html).

## Traccia degli eventi di gestione dell'istanza

Quando gestisci gli account utente, le istanze, i cluster e i servizi in {{site.data.keyword.vmwaresolutions_short}}, viene generato un evento che viene inviato al **dominio dell'account** in Activity Tracker.

Controlla la seguente tabella per le azioni che generano e inviano eventi di gestione ad Activity Tracker.

Tabella 2. Descrizione delle azioni che generano eventi di gestione

| Azione                                   | Descrizione | Risultato |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.user_account.update`    | <ul><li>Viene ricevuta la richiesta di aggiornare l'account utente.</li><li>Viene data risposta alla richiesta di aggiornare l'account utente.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>Viene ricevuta la richiesta di aggiornare le notifiche.</li><li>Viene data risposta alla richiesta di aggiornare le notifiche.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>Viene ricevuta la richiesta di cancellare i dati protetti.</li><li>Viene data risposta alla richiesta di cancellare i dati protetti.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>Viene ricevuta la richiesta di migrare all'account bss.</li><li>Viene data riposta alla richiesta di migrare all'account bss.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.order`                 | <ul><li>Viene ricevuta la richiesta di ordinare un'istanza Cloud Foundation.</li><li>Viene data risposta alla richiesta di ordinare un'istanza Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.delete`                | <ul><li>Viene ricevuta la richiesta di eliminare un'istanza Cloud Foundation.</li><li>Viene data risposta alla richiesta di eliminare un'istanza Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.add_hosts`             | <ul><li>Viene ricevuta la richiesta di aggiungere server ESXi a un'istanza Cloud Foundation.</li><li>Viene data risposta alla richiesta di aggiungere server ESXi a un'istanza Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.remove_hosts`          | <ul><li>Viene ricevuta la richiesta di eliminare i server ESXi da un'istanza Cloud Foundation.</li><li>Viene data risposta alla richiesta di eliminare i server ESXi da un'istanza Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.create_cluster`        | <ul><li>Viene ricevuta la richiesta di creare un cluster per un'istanza Cloud Foundation.</li> <li>Viene data risposta alla richiesta di creare un cluster per un'istanza Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.delete_cluster`        | <ul><li>Viene ricevuta la richiesta di eliminare un cluster da un'istanza Cloud Foundation.</li><li>Viene data risposta alla richiesta di eliminare un cluster da un'istanza Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcf.schedule_update`       | <ul><li>Viene ricevuta la richiesta di pianificare un aggiornamento per un'istanza Cloud Foundation.</li><li>Viene data risposta alla richiesta di pianificare un aggiornamento per un'istanza Cloud Foundation.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>Viene ricevuta la richiesta di ordinare un'istanza vCenter Server.</li><li>Viene data risposta alla richiesta di ordinare un'istanza vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>Viene ricevuta la richiesta di eliminare un'istanza vCenter Server.</li><li>Viene data risposta alla richiesta di eliminare un'istanza vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>Viene ricevuta la richiesta di aggiungere server ESXi a un'istanza vCenter Server.</li><li>Viene data risposta alla richiesta di aggiungere server ESXi a un'istanza vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>Viene ricevuta la richiesta di eliminare i server ESXi da un'istanza vCenter Server.</li><li>Viene data risposta alla richiesta di eliminare i server ESXi da un'istanza vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>Viene ricevuta la richiesta di pianificare un aggiornamento per un'istanza vCenter Server.</li><li>Viene data risposta alla richiesta di pianificare un aggiornamento per un'istanza vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>Viene ricevuta la richiesta di creare un cluster per un'istanza vCenter Server.</li><li>Viene data risposta alla richiesta di creare un cluster per un'istanza vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>Viene ricevuta la richiesta di eliminare il cluster da un'istanza vCenter Server.</li> <li>Viene data risposta alla richiesta di eliminare il cluster da un'istanza vCenter Server.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>Viene ricevuta la richiesta di aggiornare la licenza di VMware NSX.</li><li>Viene data risposta alla richiesta di aggiornare la licenza di VMware NSX.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>Viene ricevuta la richiesta di aggiornare un'istanza vCenter Server a un'istanza vCenter Server with Hybridity Bundle.</li><li>Viene data risposta alla richiesta di aggiornare un'istanza vCenter Server a un'istanza vCenter Server with Hybridity Bundle.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>Viene ricevuta la richiesta di ordinare un cluster vSphere.</li><li>Viene data risposta alla richiesta di ordinare un cluster vSphere.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>Viene ricevuta la richiesta di aggiornare un cluster vSphere.</li><li>Viene data risposta alla richiesta di aggiornare un cluster vSphere.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>Viene ricevuta la richiesta di salvare la configurazione di un cluster vSphere.</li><li>Viene data risposta alla richiesta di salvare la configurazione di un cluster vSphere.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>Viene ricevuta la richiesta di ordinare un'istanza NetApp ONTAP Select.</li><li>Viene data risposta alla richiesta di ordinare un'istanza NetApp ONTAP Select.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>Viene ricevuta la richiesta di eliminare un'istanza NetApp ONTAP Select.</li><li>Viene data risposta alla richiesta di eliminare un'istanza NetApp ONTAP Select.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>Viene ricevuta la richiesta di aggiornare la configurazione di un servizio.</li><li>Viene data risposta alla richiesta di aggiornare la configurazione di un servizio.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>Viene ricevuta la richiesta di ordinare un servizio per un'istanza.</li><li>Viene data risposta alla richiesta di ordinare un servizio per un'istanza.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>Viene ricevuta la richiesta di eliminare un servizio da un'istanza.</li><li>Viene data risposta alla richiesta di eliminare un servizio da un'istanza.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>Viene ricevuta la richiesta di aggiornare un'istanza vCenter Server esistente a un'istanza vCenter Server with Hybridity Bundle.</li><li>Viene data risposta alla richiesta di aggiornare un'istanza vCenter Server esistente a un'istanza vCenter Server with Hybridity Bundle.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.service.deploy` | Viene eseguita l'azione per distribuire un servizio su un'istanza. | `success` |
| `vmware-solutions.service.undeploy` | Viene eseguita l'azione per rimuovere un servizio da un'istanza. | `success` |

## Traccia di eventi per il servizio KMIP for VMware on IBM Cloud

Quando gestisci le chiavi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}, viene generato un evento che viene inviato al **dominio dell'account** in Activity Tracker.

Controlla la seguente tabella per le azioni che generano e inviano eventi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Tabella 3. Descrizione delle azioni che generano eventi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Azione                                      | Descrizione                               | Risultato |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>Viene ricevuta la richiesta di creare una chiave.</li><li>Viene data risposta alla richiesta di creare una chiave.</li></ul> | <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>Viene ricevuta la richiesta di ottenere il contenuto di una chiave.</li><li>Viene data risposta alla richiesta di ottenere il contenuto di una chiave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>Viene ricevuta la richiesta di ottenere gli attributi di una chiave.</li><li>Viene data risposta alla richiesta di ottenere gli attributi di una chiave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>Viene ricevuta la richiesta di attivare una chiave.</li><li>Viene data risposta alla richiesta di attivare una chiave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>Viene ricevuta la richiesta di revocare una chiave.</li><li>Viene data risposta alla richiesta di revocare una chiave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>Viene ricevuta la richiesta di eliminare una chiave.</li><li>Viene data risposta alla richiesta di eliminare una chiave.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>Viene ricevuta la richiesta di trovare la versione del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}.</li><li>Viene data risposta alla richiesta di trovare la versione del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}.</li></ul> |  <ul><li>`pending`</li><li>`success` o `failure`</li></ul> |

## Dove visualizzare gli eventi

Gli eventi di {{site.data.keyword.cloudaccesstrailshort}} si trovano nel **dominio dell'account** di {{site.data.keyword.cloudaccesstrailshort}} disponibile nella regione {{site.data.keyword.Bluemix_notm}} in cui vengono generati gli eventi.

### Link correlati

* [Provisioning di Activity Tracker](/docs/services/cloud-activity-tracker/how-to/provision.html)
* [Passaggio al dashboard Activity Tracker nella console {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html)
* [Panoramica di KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html)
