---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-17"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Eventi del Programma di traccia dell'attività
{: #at-events}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tenere traccia di come utenti e applicazioni interagiscono con {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.cloud_notm}}.

Il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Informazioni su {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

## Tabella degli eventi del Programma di traccia dell'attività
{: #at-events-table}

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

Per ulteriori informazioni, vedi [Campi evento di Activity Tracker](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event).

## Traccia degli eventi di gestione dell'istanza
{: #at-events-instance-mgmt}

Quando gestisci gli account utente, le istanze, i cluster e i servizi in {{site.data.keyword.vmwaresolutions_short}}, viene generato un evento che viene inviato al **dominio dell'account** in Activity Tracker.

Controlla la seguente tabella per le azioni che generano e inviano eventi di gestione ad Activity Tracker.

Tabella 2. Descrizione delle azioni che generano eventi di gestione

| Azione                                   | Descrizione | Risultato |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` |	La chiave API dell'infrastruttura per un account viene aggiornata. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.account-notification.update` | L'impostazione di notifica per un account viene aggiornata. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | I dati sicuri dell'istanza vengono eliminati. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	Un'istanza viene migrata a un account BSS. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.create` |	Viene creata un'istanza vCenter Server. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.delete` |	Viene eliminata un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.add` |	Un host viene aggiunto a un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.remove` |	Un host viene rimosso da un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.update`	|Viene aggiornata un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.create`	| Viene creato un cluster per un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete`	| Viene eliminato un cluster per un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update`	| La licenza NSX viene aggiornata per un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add`	| Viene eseguito l'upgrade di un bundle di ibridità per un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove`	| Il bundle di ibridità viene rimosso da un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add`	| L'archiviazione NFS viene aggiunta a un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove`	| L'archiviazione NFS viene rimossa da un'istanza vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-plan.update`	| Il piano di un'istanza vCenter Server viene aggiornato. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.create`	|Viene creata un'istanza vSphere Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.update`	|Viene aggiornata un'istanza vSphere Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss-template.remove` |	Viene rimosso un template vSphere. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.create`	| Viene creato un servizio. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.delete`	|Viene eliminato un servizio. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` | Viene eseguito un upgrade del bundle di ibridità a `version`. | `pending`<br>`success`<br>`failure` |

## Traccia di eventi per il servizio KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Quando gestisci le chiavi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}, viene generato un evento che viene inviato al **dominio dell'account** in Activity Tracker.

Controlla la seguente tabella per le azioni che generano e inviano eventi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Tabella 3. Descrizione delle azioni che generano eventi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Azione                                      | Descrizione                               | Risultato |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` |	Viene creata una chiave KMIP. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` |	Viene richiamata una chiave KMIP. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` |	Vengono richiamati gli attributi di una chiave KMIP. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.activate` |	Viene attivata una chiave KMIP. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` |	Viene revocata una chiave KMIP. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` |	Viene eliminata una chiave KMIP. | `pending`<br>`success`<br>`failure` |

## Dove visualizzare gli eventi
{: #at-events-viewing}

Gli eventi di {{site.data.keyword.cloudaccesstrailshort}} si trovano nel **dominio dell'account** di {{site.data.keyword.cloudaccesstrailshort}} disponibile nella regione {{site.data.keyword.cloud_notm}} in cui vengono generati gli eventi.

## Link correlati
{: #at-events-related}

* [Provisioning di Activity Tracker](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [Passaggio al dashboard Activity Tracker nella console {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [Panoramica di KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
