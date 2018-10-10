---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Note sulla release per la V2.6

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correzione Spectre e Meltdown

{{site.data.keyword.vmwaresolutions_short}} ha rilasciato patch da VMware in risposta alle vulnerabilità correlate a Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Per ulteriori informazioni, vedi [Risoluzione delle vulnerabilità Spectre e Meltdown](../vmonic/trbl_fix_spectre.html).

## Opzione Alte prestazioni con Intel Optane

Questa release fornisce l'opzione per aggiungere cache ad alte prestazioni per l'archiviazione vSAN quando ordini una nuova istanza o quando aggiungi un nuovo cluster vSAN dopo la distribuzione iniziale.

Questa opzione ti consente di aumentare il numero di dischi con capacità di archiviazione da otto a un massimo di dieci.

L'opzione Alte prestazioni con Intel Optane è disponibile solo per le configurazioni personalizzate con i processori Dual Intel Xeon Gold 5120 e Dual Intel Xeon Gold 6140.

Per ulteriori informazioni, vedi l'argomento relativo all'ordine appropriato per il tipo di istanza o cluster.

## Abilitazione di una rete pubblica o privata

Puoi ora distribuire le istanze vCenter Server e vCenter Server with Hybridity Bundle, oltre ai cluster VMware vSphere, con schede di interfaccia di rete (NIC, network interface card) pubbliche e private abilitate o con NIC solo private abilitate. Questa opzione è disponibile anche quando aggiungi un nuovo cluster alla tua istanza vCenter Server e vCenter Server with Hybridity Bundle.

Alcuni servizi aggiuntivi richiedono schede NIC pubbliche e non sono disponibili se selezioni di abilitare solo una rete privata.

Per ulteriori informazioni, vedi la sezione _Impostazioni dell'interfaccia di rete_ nei seguenti argomenti:

* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html#network-interface-settings)
* [Ordine di istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_orderinginstance.html#network-interface-settings)
* [Ordine di nuovi cluster vSphere](../vsphere/vs_orderinginstances.html#network-interface-settings)

## Eliminazione di server ESXi

Puoi ora eliminare qualsiasi server ESXi dalla tua istanza vCenter Server, vCenter Server with Hybridity Bundle o Cloud Foundation se soddisfi i requisiti minimi per la tua istanza.

Per ulteriori informazioni sui requisiti del server ESXi, vedi i seguenti argomenti:

* [Espansione e contrazione della capacità per le istanze vCenter Server](../vcenter/vc_addingremovingservers.html)
* [Espansione e contrazione della capacità per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservers.html)
* [Espansione e contrazione della capacità per le istanze Cloud Foundation](../sddc/sd_addingremovingservers.html)

## Aggiornamenti per le istanze VMware vCenter Server

Questa release applica i seguenti aggiornamenti e miglioramenti:

* vSphere ESXi 6.5 Aggiornamento 2c
* vCenter Server Appliance 6.5 Aggiornamento 2c
* Platform Services Controller 6.5 Aggiornamento 2c
* NSX for vSphere 6.4.1

## Aggiornamenti per VMware vCenter Server with Hybridity Bundle

### Rimozione di Hybridity Bundle da un'istanza vCenter Server

Puoi ora rimuovere la licenza di Hybridity Bundle dalla tua istanza vCenter Server. Per farlo, devi sostituire le chiavi di licenza a noleggio di VMware NSX e VMware vSAN con le chiavi BYOL (Bring Your Own License) e aprire un ticket di supporto per annullare i costi per le licenze a noleggio.

Per ulteriori informazioni, vedi [Rimozione di Hybridity Bundle da un'istanza vCenter Server](../vcenter/vc_hybrid_deletingbundle.html).

### Disponibilità di vCenter Server with Hybridity Bundle

I Business Partner possono ora ordinare un'istanza vCenter Server with Hybridity Bundle. I Business Partner non possono aggiornare un'istanza vCenter Server esistente a un'istanza vCenter Server with Hybridity Bundle e non possono rimuovere Hybridity Bundle da un'istanza vCenter Server with Hybridity Bundle.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Panoramica di vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [Ordine di istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_orderinginstance.html)

## Aggiornamenti per le istanze VMware Cloud Foundation

Questa release applica i seguenti aggiornamenti e miglioramenti:

* vSphere ESXi 6.5 Aggiornamento 2c
* vCenter Server Appliance 6.5 Aggiornamento 2c
* Platform Services Controller 6.5 Aggiornamento 2c
* NSX for vSphere 6.4.1

## Aggiornamenti per i servizi aggiuntivi

### HyTrust KeyControl on IBM Cloud

Il servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware Cloud Foundation e VMware vCenter Server che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.5 o successive. Il servizio semplifica la gestione dei carichi di lavoro crittografati automatizzando e semplificando il ciclo di vita delle chiavi di crittografia. Il servizio può facilmente gestire le chiavi di crittografia in scala utilizzando la crittografia conforme a FIPS 140-2. Utilizzando questo servizio, puoi gestire le chiavi di crittografia per tutte le tue macchine virtuali e gli archivi di dati crittografati e ridimensionarli per supportare migliaia di carichi di lavoro crittografati nelle grandi distribuzioni.

Puoi ordinare le istanze con il servizio incluso al momento dell'ordine della tua istanza o aggiungere questo servizio alle tue istanze esistenti in un secondo momento.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Componenti e considerazioni per HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/htkc_considerations.html)
* [Gestione di HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/managinghtkc.html)

### HyTrust CloudControl on IBM Cloud

La release corrente installa HyTrust CloudControl 5.4 su tutte le istanze appena distribuite. Per ulteriori informazioni sulle nuove funzioni di HyTrust CloudControl 5.4, vedi [HyTrust CloudControl v 5.4 Online Documentation Set](https://docs.hytrust.com/CloudControl/5.4.0/Online/index.html).

### HyTrust DataControl on IBM Cloud

La release corrente installa HyTrust DataControl 4.2 su tutte le istanze appena distribuite. Per ulteriori informazioni sulle nuove funzioni di HyTrust DataControl 4.2, vedi [What's New in HyTrust DataControl 4.x](https://docs.hytrust.com/DataControl/4.2/Admin_Guide-4.2/Content/Books/aaCommon/New-Changed-4x.htm).

### Supporto di Veeam on IBM Cloud per vSphere ESXi V6.5 Aggiornamento 2c

A partire dalla V2.6, le nuove istanze e i nuovi host vengono forniti utilizzando vSphere ESXi V6.5 Aggiornamento 2c. Se utilizzi Veeam Backup and Replication, Veeam consiglia di aggiornare l'istanza Veeam on {{site.data.keyword.cloud_notm}} alla V9.5u3a o successiva per garantire la migliore compatibilità con vSphere ESXi 6.5 Aggiornamento 2c.

Si consiglia di aggiornare alla V9.5u3a o successiva anche le istanze Cloud Foundation esistenti in cui è installato Veeam on {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni su Veeam on {{site.data.keyword.cloud_notm}}, vedi [Panoramica di Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html).

### VMware HCX on IBM Cloud

La release corrente installa VMware HCX 3.5.1 R106 su tutte le istanze appena distribuite. Per ulteriori informazioni sulle nuove funzioni di HCX 3.5.1 R106, vedi la [Documentazione di VMware NSX Hybrid Connect](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/index.html).

## Documentazione nuova e aggiornata

### Documentazione dell'architettura di riferimento
Il documento dell'architettura {{site.data.keyword.vmwaresolutions_short}} viene aggiornato per includere considerazioni importanti per comprendere le tue responsabilità in merito alla gestione e al funzionamento della tua istanza VMware.

Per ulteriori informazioni, vedi [Considerazioni sulla post-distribuzione per la tua istanza VMware](../archiref/solution/solution_considerations.md).

## Aggiornamenti e miglioramenti dell'interfaccia utente

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.
