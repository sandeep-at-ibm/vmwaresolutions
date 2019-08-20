---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Eventi del Programma di traccia dell'attività
{: #at-events}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tenere traccia di come utenti e applicazioni interagiscono con {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.at_full_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.cloud_notm}}. Puoi utilizzare il servizio per esaminare l'attività anomala e le azioni critiche e rispettare i requisiti di controllo normativi. Inoltre, puoi essere avvertito sulle azioni non appena si verificano. Gli eventi vengono raccolti conformi agli standard CADF (Cloud Auditing Data Federation).
Per ulteriori informazioni, vedi [{{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).

## Traccia degli eventi di gestione dell'istanza
{: #at-events-instance-mgmt}

Quando gestisci gli account utente, le istanze, i cluster e i servizi in {{site.data.keyword.vmwaresolutions_short}}, un evento viene generato e inviato a un dominio globale o a un'istanza del servizio nell'ubicazione in cui viene eseguito il provisioning del servizio. Per ulteriori informazioni, vedi [Monitoraggio degli eventi basati sull'ubicazione e globali](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

La seguente tabella fornisce le azioni che generano e inviano eventi di gestione ad Activity Tracker. 

| Azione                                   | Descrizione |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` | La chiave API dell'infrastruttura per un account viene aggiornata. |
| `vmware-solutions.account-notification.update` | L'impostazione di notifica per un account viene aggiornata. |
| `vmware-solutions.instance-secure-data.wipe` | I dati sicuri dell'istanza vengono eliminati. |
| `vmware-solutions.instance-bss-account.migrate` |	Un'istanza viene migrata a un account BSS. |
| `vmware-solutions.vcs.create` | Viene creata un'istanza vCenter Server. |
| `vmware-solutions.vcs.delete` | Viene eliminata un'istanza vCenter Server. |
| `vmware-solutions.vcs-host.add` | Un host viene aggiunto a un'istanza vCenter Server. |
| `vmware-solutions.vcs-host.remove` | Un host viene rimosso da un'istanza vCenter Server. |
| `vmware-solutions.vcs.update` | Viene aggiornata un'istanza vCenter Server. |
| `vmware-solutions.vcs-cluster.create` | Viene creato un cluster per un'istanza vCenter Server. |
| `vmware-solutions.vcs-cluster.delete` | Viene eliminato un cluster per un'istanza vCenter Server. |
| `vmware-solutions.vcs-nsx-license.update` | La licenza NSX viene aggiornata per un'istanza vCenter Server. |
| `vmware-solutions.vcs-nfs-storage.add` | L'archiviazione NFS viene aggiunta a un'istanza vCenter Server. |
| `vmware-solutions.vcs-nfs-storage.remove` | L'archiviazione NFS viene rimossa da un'istanza vCenter Server. |
| `vmware-solutions.vcs-plan.update` | Il piano di un'istanza vCenter Server viene aggiornato. |
| `vmware-solutions.vss.create` | Viene creata un'istanza vSphere Server. |
| `vmware-solutions.vss.update` | Viene aggiornata un'istanza vSphere Server. |
| `vmware-solutions.vss-template.remove` | Viene rimosso un template vSphere. |
| `vmware-solutions.service.create` | Viene creato un servizio. |
| `vmware-solutions.service.delete` | Viene eliminato un servizio. |
{: caption="Tabella 1. Descrizione delle azioni che generano eventi di gestione" caption-side="top"}

## Traccia di eventi per il servizio KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Quando gestisci le chiavi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}, un evento viene generato e inviato a un dominio globale o a un'istanza del servizio nell'ubicazione in cui viene eseguito il provisioning del servizio. Per ulteriori informazioni, vedi [Monitoraggio degli eventi basati sull'ubicazione e globali](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

La seguente tabella fornisce le azioni che generano e inviano eventi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}. 

| Azione                                      | Descrizione                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` | Viene creata una chiave KMIP. |
| `vmware-solutions.kmip-key.retrieve` | Viene richiamata una chiave KMIP. |
| `vmware-solutions.kmip-key-attributes.retrieve` | Vengono richiamati gli attributi di una chiave KMIP. |
| `vmware-solutions.kmip-key.activate` | Viene attivata una chiave KMIP. |
| `vmware-solutions.kmip-key.revoke` | Viene revocata una chiave KMIP. |
| `vmware-solutions.kmip-key.destroy` | Viene eliminata una chiave KMIP. |
{: caption="Tabella 2. Descrizione delle azioni che generano eventi per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Dove visualizzare gli eventi
{: #at-events-viewing}

Gli eventi sono disponibili nell'ubicazione **Frankfurt**.

C'è solo 1 istanza di {{site.data.keyword.at_full_notm}} per ubicazione. Per visualizzare gli eventi, devi accedere all'IU web del servizio {{site.data.keyword.at_full_notm}} nell'ubicazione **EU-DE**. Per ulteriori informazioni, vedi [Avvio dell'IU web tramite l'IU IBM Cloud](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

## Link correlati
{: #at-events-related}

* [Provisioning di un'istanza](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Passaggio alla IU web](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [Panoramica di KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
