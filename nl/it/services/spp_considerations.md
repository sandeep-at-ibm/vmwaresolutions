---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Panoramica di IBM Spectrum Protect Plus on IBM Cloud

Il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} fornisce una soluzione efficiente e scalabile per la protezione dei dati, il riutilizzo dei dati e il recupero dei dati per gli ambienti virtuali. Puoi implementare il servizio come soluzione autonoma o integrarlo con il tuo ambiente IBM Spectrum Protect Plus per scaricare copie per la governance di dati e archiviazione a lungo termine.

**Disponibilità**: questo servizio è disponibile solo per le istanze che sono distribuite o aggiornate alle release della V2.2 o successive.

**Note:**
* Se accetti la selezione del servizio predefinito per le istanze distribuite nelle release della V2.4 o successive, viene installato IBM Spectrum Protect Plus V10.1.1 Patch 1. Il servizio fornisce automaticamente il supporto per il ripristino delle macchine virtuali (VM) di gestione.
* Se accetti la selezione del servizio predefinito per le istanze distribuite nella V2.3, viene installato IBM Spectrum Protect Plus V10.1.1. Il servizio fornisce automaticamente il backup per le VM di gestione.
* Se installi il servizio per le istanze distribuite nella V2.2, viene installato IBM Spectrum Protect Plus V10.1.0. Il servizio fornisce la protezione dei dati solo per le VM del carico di lavoro.


## Componenti di IBM Spectrum Protect Plus on IBM Cloud

Nel servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Risorse vCenter

* Una singola macchina virtuale (VM) che esegue il server IBM Spectrum Protect Plus
* Core da 4 x 2,0 GHz
* 32 GB di RAM
* Disco da 370 GB

### Archiviazione per i backup

Archiviazione personalizzabile per i backup con le seguenti opzioni:
* Numero di archiviazione file: 1, 2, 3 o 4
* Ogni archiviazione di file endurance: 500, 1000, 2000, 4000, 8000 o 12000 GB
* Prestazioni di archiviazione: 0,25, 2 o 4 IOPS/GB

### Archiviazione per la gestione

Un'archiviazione di file endurance (500 GB, 2 IOPS/GB) che ospita la macchina virtuale IBM Spectrum Protect Plus e in esecuzione sulla stessa sottorete dell'archiviazione di backup ordinata per il servizio.

### Rete

Un indirizzo IP privato portatile.

### Licenze e tariffe

IBM Spectrum Protect Plus può essere concesso in licenza nella console {{site.data.keyword.vmwaresolutions_short}} per 10 a un massimo di 1000 VM con incrementi di 10. Puoi anche utilizzare l'opzione BYOL (Bring Your Own License) e caricare il file di licenza durante il processo di installazione.

## Considerazioni sull'istallazione di IBM Spectrum Protect Plus on IBM Cloud

Esamina le seguenti considerazioni prima di installare il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

* Assicurati che la CPU e la memoria nel cluster predefinito della tua istanza siano sufficienti per la macchina virtuale IBM Spectrum Protect Plus.
* Assicurati che i montaggi NFS disponibili sui server ESXi siano sufficienti in base alla versione dei server ESXi.

  Le istanze Cloud Foundation e vCenter Server distribuite o aggiornate alle release della V2.2 o successive hanno un'impostazione di parametro `NFS.MaxVolumes` in VMware. Questo parametro definisce il numero massimo di montaggi NFS su un server ESXi e può essere impostato su un massimo di 256, che è specifico per la versione del server ESXi. Per ulteriori informazioni, vedi [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

  Il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} può consumare fino a cinque volumi NFS su ciascun server ESXi nel cluster predefinito della tua istanza. Inoltre, il servizio creerà montaggi NFS temporanei per scopi di backup e ripristino. Pertanto, devi impostare il numero di montaggi NFS su un minimo di 64 per garantire che il servizio possa essere installato e funzioni correttamente.

## Considerazioni sulla rimozione di IBM Spectrum Protect Plus on IBM Cloud

Esamina le seguenti considerazioni prima di rimuovere il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}:
* Assicurati che tutte le configurazioni dei lavori di backup vengano rimosse e che non vi siano operazioni di backup o ripristino attive.
* Quando rimuovi il servizio, l'archiviazione per il repository di backup viene rimossa dalla VM di IBM Spectrum Protect Plus e l'ordine di archiviazione viene annullato, il che elimina i dati del repository di backup in modo permanente.
* Quando rimuovi il servizio, viene rimossa anche l'archiviazione di backup ordinata per il servizio. Pertanto, tutti i backup diventano inaccessibili durante la rimozione del servizio.

## Link correlati

* [IBM Spectrum Protect Plus on IBM Cloud Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestione di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Ordine di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [Documentazione di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
