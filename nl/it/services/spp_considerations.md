---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations}

Il servizio {{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} fornisce una soluzione efficiente e scalabile per la protezione, il riutilizzo e il recupero dei dati per gli ambienti virtuali. Puoi implementare il servizio come soluzione autonoma o integrarlo con il tuo ambiente IBM Spectrum Protect per scaricare copie per la governance di dati e archiviazione a lungo termine.

Questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alla V2.2 o successive. La versione {{site.data.keyword.IBM}} Spectrum Protect Plus corrente installata è la V10.1.2.
{:note}

## Specifiche tecniche per IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-specs}

Nel servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Risorse vCenter
{: #spp_considerations-vcenter}

* VM server che esegue il server IBM Spectrum Protect Plus
   * Sistema operativo Linux 3.10.0-693.11.1.el7.x86_64
   * Core da 4 x 2,0 GHz
   * 32 GB di RAM
   * Disco da 370 GB
* VM secondaria che esegue il server IBM Spectrum Protect Plus vSnap e il proxy VADP
   * Sistema operativo Linux 3.10.0-693.11.1.el7.x86_64
   * CPU e RAM configurate in base alle dimensioni di archiviazione selezionate e alle indicazioni di dimensionamento di [IBM Spectrum Protect Plus Blueprint](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)
   * Disco da 150 GB

### Archiviazione per i backup
{: #spp_considerations-backup-storage}

Archiviazione personalizzabile per i backup con le seguenti opzioni:
* Numero di archiviazione file: 1 - 10
* Ogni archiviazione di file endurance: 500, 1000, 2000, 4000, 8000 o 12000 GB
* Prestazioni di archiviazione: 0,25, 2 o 4 IOPS/GB

Consulta [IBM Spectrum Protect Plus blueprint and sizing tool](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) per la pianificazione e il dimensionamento.

### Archiviazione per la gestione
{: #spp_considerations-mgmt-storage}

Un'archiviazione di file endurance da 1000 GB, 2 IOPS/GB che ospita la VM (Virtual Machine) IBM Spectrum Protect Plus e che è in esecuzione sulla stessa sottorete dell'archiviazione di backup.

### Rete
{: #spp_considerations-network}

Due indirizzi IP privati portatili.

### Licenze e tariffe
{: #spp_considerations-license}

* IBM Spectrum Protect Plus (da 10 fino ad un massimo di 1000 licenze VM in incrementi di 10)
* Licenza IBM Spectrum Protect Plus offerta tramite la console {{site.data.keyword.vmwaresolutions_short}} (numero di VM in pacchetti di 10) o come BYOL

## Considerazioni sull'istallazione di IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-install}

Esamina le seguenti considerazioni prima di installare il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

* Assicurati che la CPU e la memoria nel cluster predefinito della tua istanza siano sufficienti per la VM (Virtual Machine) IBM Spectrum Protect Plus.
* Assicurati che i montaggi NFS disponibili sui server ESXi siano sufficienti in base alla versione dei server ESXi.

  Le istanze distribuite (o di cui viene eseguito l'upgrade) alla V2.2 o release successive hanno un'impostazione di parametro `NFS.MaxVolumes` in VMware. Questo parametro definisce il numero massimo di montaggi NFS su un server ESXi e può essere impostato su un massimo di 256, che è specifico per la versione del server ESXi. Per ulteriori informazioni, vedi [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

  Il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} può utilizzare fino a 11 dei volumi NFS su ogni server ESXi nel cluster predefinito della tua istanza. Inoltre, il servizio crea montaggi NFS temporanei per scopi di backup e ripristino. Pertanto, devi impostare il numero di montaggi NFS su un minimo di 64 per garantire che il servizio possa essere installato e funzioni correttamente.

## Considerazioni sulla rimozione di IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-remove}

Esamina le seguenti considerazioni prima di rimuovere il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}:
* Assicurarti che tutte le configurazioni dei lavori di backup vengano rimosse insieme alle operazioni di backup o ripristino attive.
* Quando rimuovi il servizio, l'archiviazione per il repository di backup viene rimossa dalla VM di IBM Spectrum Protect Plus e l'ordine di archiviazione viene annullato, il che elimina i dati del repository di backup in modo permanente.
* Quando rimuovi il servizio, viene rimossa anche l'archiviazione di backup che viene ordinata per il servizio. Tutti i backup diventano inaccessibili durante la rimozione del servizio.

## Link correlati
{: #spp_considerations-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestione di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)
* [Ordine di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [Documentazione di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
