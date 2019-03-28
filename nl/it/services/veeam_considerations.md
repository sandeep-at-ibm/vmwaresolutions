---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di Veeam on IBM Cloud
{: #veeam_considerations}

Il servizio Veeam on {{site.data.keyword.cloud}} si integra perfettamente con i tuoi hypervisor VMware per aiutare la tua azienda a raggiungere l'alta disponibilità. Questo servizio fornisce obiettivi di tempo e punti di ripristino per le tue applicazioni e i tuoi dati. Gli obiettivi di tempo e punti di ripristino possono essere forniti in meno di 15 minuti dopo il completamento della configurazione. Utilizzando questo servizio, controlli il backup e il ripristino di tutte le VM (Virtual Machine) per la tua infrastruttura direttamente dalla console Veeam.

Questo servizio è disponibile solo per le istanze distribuite nella V1.8 o successive. La versione Veeam corrente installata è la 9.5u4.
{:note}

## Specifiche tecniche per Veeam on IBM Cloud
{: #veeam_considerations-specs}

Nel servizio Veeam on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### VSI
{: #veeam_considerations-specs-vsi}

* VSI singola con Veeam Backup and Replication 9.5 OS Add-on
* Windows Server 2016 Standard Edition (64 bit)
* Core 4 x 2,0 GHz
* 8 GB di RAM
* Uplink di rete privata da 1 Gbps
* Disco da 100 GB (SAN)

### Archiviazione per i backup
{: #veeam_considerations-specs-storage}

* Archiviazione iSCSI endurance (2000, 4000, 8000 o 12000 GB)
* Prestazioni di archiviazione (0,25, 2 p 4 IOPS/GB)

### Rete
{: #veeam_considerations-specs-networking}

Un indirizzo IP primario privato.

### Licenze e tariffe
{: #veeam_considerations-specs-licenses}

Veeam Backup and Replication 9.5 Enterprise Plus (licenza da 10, 25, 50, 100 o 200 VM).

### Gestione
{: #veeam_considerations-specs-mgmt}

Backup di gestione configurati per impostazione predefinita con un massimo di 5 VM e 2000 GB di archiviazione.

## Considerazioni sull'istallazione di Veeam on IBM Cloud
{: #veeam_considerations-install}

Il repository di archiviazione e il server Veeam si trovano nel pod e nel data center originali. Pertanto, le prestazioni delle operazioni di backup per i cluster remoti potrebbero ridursi.

## Considerazioni sulla rimozione di Veeam on IBM Cloud
{: #veeam_considerations-remove}

La rimozione del servizio Veeam on {{site.data.keyword.cloud_notm}} arresta tutti i backup ed elimina tutti i backup precedenti. I backup delle VM di gestione vengono arrestati e l'eliminazione dei backup precedenti è irreversibile. Se le VM di gestione sono danneggiate, non possono essere ripristinate.

## Link correlati
{: #veeam_considerations-related}

* [Ordine di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Richiesta di servizi gestiti per Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web Veeam](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
