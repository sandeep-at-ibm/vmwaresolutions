---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Veeam, Veeam install, tech specs Veeam

subcollection: vmware-solutions


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

* VSI singola con Veeam Backup and Replication 9.5 OS Add-on e Veeam Availability Suite 9.5
* Windows Server 2016 Standard Edition (64 bit)
* Core 4 x 2,0 GHz
* 8 vCPU, 32 GB di RAM
* Uplink di rete privata da 1 Gbps
* Disco da 100 GB (SAN)

### Archiviazione per i backup
{: #veeam_considerations-specs-storage}

* Archiviazione iSCSI Endurance (2.000, 4.000, 8.000 o 12.000 GB)
* Prestazioni di archiviazione (0,25, 2 p 4 IOPS/GB)

Come parte dell'installazione e della configurazione del servizio Veeam, vengono creati i seguenti repository:
* Per i file di backup della configurazione di Veeam: un repository denominato `IC4V Default Config Backup Repository`. Il percorso alla cartella dove sono archiviati i backup Veeam è `<Drive>:\ConfigBackup\`.
* Per il ridimensionamento incrementale, un repository denominato `IC4V Scale-Out Repository`. Per ulteriori informazioni, vedi [Aggiunta di un repository di ridimensionamento incrementale](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icos_ordering#icos_ordering-scale-repo). 
* Per i backup di VM (Virtual Machine), un repository denominato ``IC4V Default VM Backup Repository``. Il percorso alla cartella dove sono archiviati i backup di VM è ``<Drive>:\VMBackup\`. Questo repository viene aggiunto come estensione al repository ``IC4V Scale-Out'.

### Rete
{: #veeam_considerations-specs-networking}

Un indirizzo IP primario privato.

### Licenze e tariffe
{: #veeam_considerations-specs-licenses}

* Veeam Availability Suite 9.5 (10, 25, 50, 100 o 200 licenze di VM)

## Considerazioni sull'installazione di Veeam on IBM Cloud
{: #veeam_considerations-install}

Il repository di archiviazione e il server Veeam si trovano nel pod e nel data center originali. Pertanto, le prestazioni delle operazioni di backup per i cluster remoti potrebbero ridursi.

## Considerazioni sulla rimozione di Veeam on IBM Cloud
{: #veeam_considerations-remove}

La rimozione del servizio Veeam on {{site.data.keyword.cloud_notm}} arresta tutti i backup ed elimina tutti i backup precedenti. Il backup delle VM di gestione viene arrestato e l'eliminazione dei backup precedenti è irreversibile. Se le VM di gestione sono danneggiate, non possono essere ripristinate.

## Link correlati
{: #veeam_considerations-related}

* [Ordine di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Richiesta di servizi gestiti per Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web Veeam](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
