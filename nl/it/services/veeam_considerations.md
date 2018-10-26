---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Panoramica di Veeam on IBM Cloud

Il servizio Veeam on {{site.data.keyword.cloud}} si integra perfettamente con i tuoi hypervisor VMware per aiutare la tua azienda a raggiungere l'alta disponibilità. Questo servizio fornisce obiettivi di tempo e punti di ripristino per le tue applicazioni e i tuoi dati. Gli obiettivi di tempo e punti di ripristino possono essere forniti in meno di 15 minuti dopo il completamento della configurazione. Utilizzando questo servizio, controlli il backup e il ripristino di tutte le macchine virtuali (VM) per la tua infrastruttura direttamente dalla console Veeam.

**Disponibilità:** questo servizio è disponibile solo per le istanze distribuite nelle release della V1.8 o successive.

## Specifiche tecniche per Veeam on IBM Cloud

Nel servizio Veeam on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### VSI

* VSI singola con Veeam Backup and Replication 9.5 OS Add-on
* Windows Server 2016 Standard Edition (64 bit)
* Core 4 x 2,0 GHz
* 8 GB di RAM
* Uplink di rete privata da 1 Gbps
* Disco da 100 GB (SAN)

### Archiviazione per i backup

* Archiviazione iSCSI endurance (2000, 4000, 8000 o 12000 GB)
* Prestazioni di archiviazione (0,25, 2 p 4 IOPS/GB)

### Rete

Un indirizzo IP primario privato.

### Licenze e tariffe

Veeam Backup and Replication 9.5 Enterprise Plus (licenza da 10, 25, 50, 100 o 200 VM).

### Gestione

Backup di gestione configurati per impostazione predefinita con un massimo di 5 VM e 2000 GB di archiviazione.

## Considerazioni sull'istallazione di Veeam on IBM Cloud

Il repository di archiviazione e il server Veeam si trovano nel pod e nel data center originali. Pertanto, le prestazioni delle operazioni di backup per i cluster remoti potrebbero ridursi.

## Considerazioni sulla rimozione di Veeam on IBM Cloud

La rimozione del servizio Veeam on {{site.data.keyword.cloud_notm}} arresta tutti i backup ed elimina tutti i backup precedenti. I backup delle VM di gestione vengono arrestati e l'eliminazione dei backup precedenti è irreversibile. Se le VM di gestione sono danneggiate, non possono essere ripristinate.

### Link correlati

* [Ordine di Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Richiesta di servizi gestiti per Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web Veeam](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
