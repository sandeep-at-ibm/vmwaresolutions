---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

---

# Note sulla release per la V2.1

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e ulteriori suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correzione Spectre e Meltdown

{{site.data.keyword.vmwaresolutions_short}} ha rilasciato patch da VMware in risposta alle vulnerabilità note come Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Per ulteriori informazioni, vedi [Risoluzione delle vulnerabilità Spectre e Meltdown](../vmonic/trbl_fix_spectre.html).

## VMware HCX on IBM Cloud

Il servizio HCX on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware Cloud Foundation e VMware vCenter Server che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.1 o successive. Questo servizio può estendere senza problemi le reti dei tuoi data center in loco in {{site.data.keyword.cloud_notm}}, il che consente la migrazione bidirezionale delle macchine virtuali (VM) tra i data center in loco e {{site.data.keyword.cloud_notm}} senza alcuna modifica. Stabilendo un bridge di livello 2, HCX sfrutta l'ottimizzazione WAN, la deduplicazione, la compressione e la crittografia per migrare più rapidamente e in sicurezza i dati su un tunnel VPN o Direct Link. La migrazione in blocco delle VM è retrocompatibile con VMware vSphere 5.1 o superiore. Se utilizzi vSphere 6.0 o superiore in loco, puoi eseguire la migrazione live (alimentata) vMotion delle VM dalla posizione in loco a un {{site.data.keyword.CloudDataCent_notm}}. Non è necessario che VMware NSX sia installato nel tuo data center quando utilizzi HCX.

Puoi ordinare le istanze Cloud Foundation o vCenter Server con il servizio HCX on {{site.data.keyword.cloud_notm}} incluso al momento dell'ordine della tua istanza o aggiungere questo servizio alle tue istanze esistenti in un secondo momento utilizzando la scheda **Servizi** nella pagina dei dettagli dell'istanza.

Puoi anche ordinare un'istanza HCX in loco per la licenza e l'attivazione dell'installazione di HCX in loco.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Considerazioni su HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)
* [Gestione di HCX on {{site.data.keyword.cloud_notm}}](../services/managinghcx.html)
* [Considerazioni sulle istanze HCX in loco](../services/standalone_considerations.html)
* [Ordine di istanze HCX in loco](../services/standalone_orderingserviceinstances.html)

## Modello BYOL (Bring Your Own License) più flessibile per VMware Cloud Foundation e vCenter Server

È ora possibile utilizzare l'opzione BYOL (Bring Your Own License) o acquistare la licenza di sottoscrizione fornita da IBM durante la creazione di un cluster per le istanze VMware Cloud Foundation e VMware vCenter Server della V2.1 e successive, consentendoti di sfruttare la chiave del componente esistente o di noleggiare la licenza da IBM. Prima della V2.1, non potevi acquistare la licenza fornita da IBM per un componente VMware specifico se utilizzavi BYOL. Al momento, solo VMware vSphere e VMware vSAN sono disponibili per la licenza in ciascun cluster.

Inoltre, quando aggiungi nodi a un cluster concesso in licenza con la tua chiave, la console ti richiede di fornire una nuova chiave di licenza se il numero di nodi supera la capacità della chiave.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Aggiunta e visualizzazione di cluster per le istanze Cloud Foundation](../sddc/sd_addingviewingclusters.html)
* [Aggiunta e visualizzazione di cluster per le istanze vCenter Server](../vcenter/vc_addingviewingclusters.html)
* [Domande frequenti su BYOL](../vmonic/faq_byol.html)

## Aggiornamenti dei componenti del servizio Zerto on IBM Cloud

Per il servizio Zerto on {{site.data.keyword.cloud_notm}} distribuito nelle istanze Cloud Foundation e vCenter Server della V2.1 e successive, viene fornito Zerto Virtual Replication 5.5u2. I dispositivi Zerto Virtual Replication Appliance (VRA) vengono ora distribuiti nell'archivio dati di gestione (vSAN o Endurance) piuttosto che nell'archivio dati locale per motivi di prestazioni. Se disponi di VRA esistenti, dovresti prendere in considerazione la possibilità di migrare la loro archiviazione nell'archivio dati di gestione per ottenere prestazioni migliori.

Per ulteriori informazioni, vedi [Panoramica di Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html).

## Aggiornamenti per le istanze VMware vCenter Server

### Impostazioni di configurazione MTU della rete

Per le release della V2.1 o successive, le nuove istanze vCenter Server vengono ordinate con l'impostazione DVS (Distributed Virtual Switch) pubblico con dimensione MTU di 1500 (predefinito). Per ulteriori informazioni, vedi la sezione _Impostazioni di configurazione MTU della rete_ in [Distinta base di vCenter Server](../vcenter/vc_bom.html).

### Applicazione automatica di patch e aggiornamenti di VMware ESXi agli host

Nelle istanze VMware vCenter Server della V2.0 e precedenti, le patch non venivano applicate automaticamente agli host ESXi aggiunti a un cluster.

Nelle istanze della V2.1 e successive, l'automazione applica le patch ai nuovi host ESXi in modo che il livello di patch corrisponda al livello esistente al momento del provisioning dell'istanza iniziale. Sei responsabile dell'applicazione manuale di eventuali patch e aggiornamenti futuri.
Quando le patch e gli aggiornamenti VMware diventano disponibili nelle release future, l'automazione eseguirà la scansione degli host ESXi delle tue istanze esistenti e ti invierà un promemoria via e-mail per applicare manualmente le patch e gli aggiornamenti più recenti.

Per ulteriori informazioni, vedi [Applicazione di aggiornamenti alle istanze vCenter Server](../vcenter/vc_applyingupdates.html).

### Stime dei prezzi per gli aggiornamenti delle licenze VMware NSX

Puoi ora visualizzare una stima dei prezzi prima di inoltrare un ordine per l'aggiornamento all'edizione Advanced o Enterprise di VMware NSX. Il prezzo si basa sul numero di host ESXi nell'istanza vCenter Server. Questo acquisto modifica solo la chiave di licenza NSX e aggiorna l'edizione di base di VMware NSX all'edizione Advanced o Enterprise. L'acquisto non aggiorna la versione del software NSX.

Per ulteriori informazioni, vedi [Panoramica di vCenter Server](../vcenter/vc_vcenterserveroverview.html).

### Aumento del numero massimo di server per cluster a più di 32

Per il cluster predefinito in un'istanza, puoi distribuire o espandere fino a 51 server. Per tutti i cluster successivi in un'istanza, puoi distribuire o espandere fino a 59 server. Per ulteriori informazioni, vedi [Aggiunta e visualizzazione di cluster per le istanze vCenter Server](../vcenter/vc_addingviewingclusters.html).

**Nota:** questa funzionalità è disponibile solo per le istanze distribuite nella V2.1 e successive. Le istanze che vengono aggiornate alla V2.1 da release precedenti non dispongono di questa funzionalità.

### Opzioni di configurazione di Bare Metal Server IBM Cloud personalizzata dall'utente

La configurazione dei server bare metal personalizzata dall'utente ora offre il processore Dual Intel Xeon Gold 6140 con 36 core totali, 2,3 GHz.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Panoramica di vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html)

### Configurazioni di singole condivisioni file NFS

Hai ora la possibilità di configurare le condivisioni file NFS su base individuale. Seleziona la dimensione del file e il livello di prestazioni per ogni singola condivisione file o seleziona la stessa dimensione del file e lo stesso livello di prestazioni per tutte le condivisioni file che devi ordinare.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Panoramica di vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html)
* [Aggiunta e visualizzazione di cluster per le istanze vCenter Server](../vcenter/vc_addingviewingclusters.html)

## Aggiornamenti e miglioramenti dell'interfaccia utente

Sono stati apportati miglioramenti in tutta l'interfaccia utente:

* L'opzione **Ordina istanza** è stata rimossa dal riquadro di navigazione a sinistra. Fai clic su **Introduzione** per completare la procedura di ordine di un'istanza.
* Il campo **Prefisso sottodominio** presente nella pagina **Basics** quando si ordina un'istanza è stato rinominato in **Etichetta sottodominio**.
* Oltre a visualizzare la stima dei costi nella pagina **Riepilogo** quando ordini un'istanza vCenter Server o Cloud Foundation primaria o secondaria, puoi ora calcolare una stima dei costi su qualsiasi pannello mentre fornisci i dettagli per il tuo ordine dell'istanza.
* La navigazione breadcrumb viene aggiunta alla pagina **Istanze distribuite** come metodo alternativo di navigazione, riducendo così il numero di passi necessari per raggiungere le pagine principali su queste pagine.
* Sono stati apportati vari miglioramenti ai messaggi di errore e alle descrizioni a comparsa per aiutarti a selezionare l'impostazione appropriata nell'interfaccia utente.

## Documentazione nuova e aggiornata

È disponibile una nuova indicazione di developerWorks con istruzioni dettagliate su come collegare l'archiviazione dedicata alle distribuzioni esistenti di {{site.data.keyword.vmwaresolutions_full}} utilizzando NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi la [procedura per collegare l'archiviazione dedicata a VMware Solutions on IBM  Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/).
