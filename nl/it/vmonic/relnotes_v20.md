---

copyright:

  years:  2016, 2019

lastupdated: "2017-11-20"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Note sulla release per la V2.0

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## FortiGate Virtual Appliance on IBM Cloud

Il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware Cloud Foundation e VMware vCenter Server della V2.0 e successive. Questo servizio distribuisce una coppia ad alta disponibilità (HA) di dispositivi FortiGate Virtual Appliance al tuo ambiente, che ti aiuta a ridurre i rischi implementando controlli di sicurezza critici all'interno della tua infrastruttura virtuale.

Ordina istanze con il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} incluso quando ordini la tua istanza oppure aggiungi questo servizio alle tue istanze esistenti in un secondo momento utilizzando la scheda **Servizi** nella pagina dei dettagli dell'istanza. A seconda dei tuoi requisiti, seleziona una delle tre dimensioni di distribuzione e opzioni di licenza per questo servizio. Dopo aver installato correttamente il servizio, gestisci e configura le regole del firewall per i dispositivi FortiGate Virtual Appliance dalla console FortiGate.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Componenti e considerazioni per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_considerations.html)
* [Gestione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managingfortinetvm.html)

## Installazione di più servizi per F5 on IBM Cloud e FortiGate Virtual Appliance on IBM Cloud

Puoi ora installare più istanze del servizio F5 on {{site.data.keyword.cloud_notm}} e del servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} per un'istanza Cloud Foundation o vCenter Server. Se selezioni il servizio F5 o il servizio FortiGate durante l'ordine della tua istanza, devi specificare un nome per l'istanza del servizio per distinguerla dalle ulteriori istanze di servizio che installerai in seguito.

Una volta completata la distribuzione dell'istanza, puoi aggiungere altre istanze del servizio F5 o FortiGate installando il servizio sulla scheda **Aggiungi servizi** della pagina dei dettagli dell'istanza. Puoi aggiungere solo un'istanza del servizio alla volta e dei ripetere il processo per tutte le istanze che vuoi aggiungere per un servizio.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)

## Aggiornamenti per FortiGate Security Appliance on IBM Cloud

In questa release, il servizio Fortinet on {{site.data.keyword.cloud_notm}} viene rinominato in FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}. La coppia di dispositivi FortiGate Security Appliance (FSA) del servizio è configurata per essere protetta per impostazione predefinita quando viene distribuita nella tua istanza.
* Se distribuisci una coppia di FSA come parte di una nuova istanza Cloud Foundation o vCenter Server, i FSA vengono configurati per consentire solo le comunicazioni in uscita richieste dalla tua istanza alla rete pubblica e negare tutte le altre comunicazioni.
* Se distribuisci una coppia di FSA come parte di un'istanza Cloud Foundation o vCenter Server esistente, i FSA vengono configurati con una regola esplicita per consentire tutte le comunicazioni di gestione in uscita richieste dalla tua istanza alla rete pubblica e vengono configurati anche con una regola che consente tutte le altre comunicazioni per garantire che il traffico dell'applicazione esistente non venga interrotto.

In tutti i casi, devi gestire attentamente la configurazione dei FSA per consentire solo le comunicazioni necessarie e negare tutte le altre comunicazioni.

## Coerenza del formato del nome di dominio completo

Il nome di dominio completo (FQDN) è ora rappresentato in modo coerente per tutte le istanze. Quando effettui un ordine, puoi immettere il tuo proprio prefisso del dominio secondario e prefisso del nome host per garantire che venga seguita la convenzione di settore per il formato FQDN. Ad esempio, `host-name-prefix<n>.subdomain-prefix.domain-name`.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)

## Stime di carico di lavoro e archiviazione durante un ordine dell'istanza

* Durante un ordine di VMware vSphere on {{site.data.keyword.cloud_notm}}, ti viene fornita una stima del numero di macchine virtuali che possono essere eseguite sull'istanza ordinata.
* Durante un ordine di Cloud Foundation e vCenter Server, ti viene fornita una stima della capacità di archiviazione utilizzabile per l'istanza ordinata.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)

## Aggiornamenti per le istanze VMware Cloud Foundation

La release corrente applica i seguenti aggiornamenti e miglioramenti dei componenti per le nuove distribuzioni:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware SDDC Manager 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX per vSphere 6.3.4
* VMware ESXi 6.5, Patch Release ESXi650-201710401-BG. Aggiorna i VIB esx-base, esx-tboot, vsan e vsanhealth (2151061). Per ulteriori informazioni sui dettagli delle patch, vedi [VMware vCenter Server Appliance Photon OS Security Patches](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}.

Le istanze esistenti (dalle release della V1.9 e precedenti) non possono essere aggiornate alle versioni del componente in questo elenco.
{:note}

Per ulteriori informazioni sui componenti, vedi [Panoramica di Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html).

### Supporto cluster per le istanze Cloud Foundation

Puoi ora utilizzare i cluster per gestire i server ESXi nelle istanze Cloud Foundation distribuite nelle release della V2.0 e successive per una migliore gestione delle risorse e alta disponibilità. I server ESXi che hai configurato quando hai ordinato un'istanza vengono raggruppati sotto forma di **SDDC-Cluster** per impostazione predefinita.

Puoi visualizzare i dettagli del cluster o aggiungere fino a un totale di cinque cluster a un'istanza attraverso la scheda **Infrastruttura** della pagina dei dettagli dell'istanza. Quando espandi o contrai la capacità di un'istanza, puoi selezionare il cluster a cui aggiungere o da cui rimuovere i server ESXi. Per ulteriori informazioni, vedi [Aggiunta e visualizzazione di cluster per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingviewingclusters.html).

### Supporto per l'archiviazione vSAN personalizzata per le istanze Cloud Foundation

Puoi ora personalizzare la configurazione dell'archiviazione vSAN selezionando il numero e la dimensione delle unità di archiviazione vSAN come parte del tuo ordine dell'istanza.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Panoramica di Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)

### Scelta dell'edizione della licenza VMware vSAN per le istanze Cloud Foundation: Advanced o Enterprise

Puoi ora selezionare l'edizione della licenza vSAN che preferisci durante l'ordine dell'istanza Cloud Foundation. Puoi acquistare la licenza come parte del tuo ordine o utilizzare l'opzione BYOL (Bring Your Own License). Per ulteriori informazioni, vedi [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html).

### Nuove configurazioni standardizzate di IBM Bare Metal Server per le istanze Cloud Foundation

Per Bare Metal Server sono ora disponibili le seguenti impostazioni di configurazione:
* Small (Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz / 128 GB di RAM / 12 dischi)
* Large (Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz / 512 GB di RAM / 12 dischi)

Lo chassis ha spazio per 12 dischi. Non vengono riempiti tutti gli slot. La configurazione **Small** fornisce due unità Micron 5100 MAX da 1,9 TB e la configurazione **Large** fornisce quattro unità Micron 5100 PRO da 3,8 TB.
{:note}

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Panoramica di Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)

## Aggiornamenti per le istanze VMware vCenter Server

La release corrente applica i seguenti aggiornamenti dei componenti per le nuove distribuzioni:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX per vSphere 6.3.4

Gli ordini personalizzati di vCenter Server con o senza il componente VMware vSAN includono sempre un server con chassis da 12 dischi. Questo server comporta un costo leggermente superiore per i {{site.data.keyword.baremetal_short}} per il caso di ordine diverso da vSAN nel PDF di stima dei prezzi.
{:note}

Per ulteriori informazioni sui componenti, vedi [Panoramica di vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html).

### Supporto della configurazione multisito per le istanze vCenter Server

Puoi ora distribuire una singola istanza vCenter Server in aggiunta alle istanze secondarie che vengono collegate a un'istanza primaria. Il modello di configurazione multisito utilizza una topologia "hub and spoke" con un sito primario e un massimo di sette siti secondari.

Per ulteriori informazioni, vedi [Configurazione multisito per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_multisite.html).

### Supporto per l'archiviazione vSAN personalizzata per le istanze vCenter Server

L'archiviazione vSAN è ora disponibile in vCenter Server sia per le istanze primarie che secondarie. È disponibile solo quando selezioni una configurazione personalizzata dall'utente. Puoi ora selezionare l'edizione della licenza vSAN che preferisci (Advanced o Enterprise) durante l'ordine dell'istanza vCenter Server. Puoi acquistare la licenza come parte del tuo ordine o utilizzare l'opzione BYOL (Bring Your Own License).

Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html).

### BYOL (Bring Your Own License) per le istanze VMware vCenter Server

BYOL è ora disponibile per le istanze vCenter Server. Utilizza una o più delle tue licenze di vCenter Server, vSphere, vSAN e NSX VMware quando ordini le istanze vCenter Server.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)

## Aggiornamenti per VMware vSphere on IBM Cloud

### Nuovi tipi di disco per i server bare metal

Per il componente VMware vSAN, sono disponibili i seguenti tipi di disco per i {{site.data.keyword.baremetal_short}}:
* SED SSD da 960 GB
* SED SSD da 1,9 TB
* SED SSD da 3,8 TB

**Note**:
* Le unità SED SSD da 3,8 TB sono supportate quando vengono rese generalmente disponibili in un {{site.data.keyword.CloudDataCent_notm}}.
* Gli ordini con o senza il componente VMware vSAN includono sempre un server con chassis da 12 dischi. Questo server comporta un costo leggermente superiore per i {{site.data.keyword.baremetal_short}} per il caso di ordine diverso da vSAN nel PDF di stima dei prezzi.

Per ulteriori informazioni, vedi [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html).

## Aggiornamenti per NetApp ONTAP Select on IBM Cloud

### Nuove opzioni per i server bare metal

Per i server bare metal sono ora disponibili le seguenti opzioni di configurazione:
* **Alte prestazioni (Medium)** – Licenza Premium / Dual Intel Xeon E5-2650 v4 (24 core totali, 2,2 GHz) / 128 GB di RAM / Capacità di 22 unità SSD da 1,9 TB per nodo / Capacità effettiva di un cluster a 4 nodi – 59 TB
* **Alte prestazioni (Large)** – Licenza Premium / Dual Intel Xeon E5-2650 v4 (24 core totali, 2,2 GHz) / 128 GB di RAM / Capacità di 22 unità SSD da 3,8 TB per nodo / Capacità effettiva di un cluster a 4 nodi – 118 TB
* **Alta capacità** – Licenza Standard / Dual Intel Xeon E5-2650 v4 (24 core totali, 2,2 GHz) / 64 GB di RAM / Capacità di dieci unità SATA da 4 TB per nodo / Capacità effettiva di un cluster a 4 nodi – 60 TB

Le unità SSD da 3,8 TB sono supportate quando vengono rese generalmente disponibili in un {{site.data.keyword.CloudDataCent_notm}}.
{:note}

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Panoramica di NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp/np_netappoverview.html)
* [Ordine di istanze NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp/np_orderinginstances.html)

## Documentazione nuova e aggiornata

Gli utenti di VMware Cloud Foundation possono utilizzare le istruzioni dettagliate insieme alla piattaforma NSX di VMware su {{site.data.keyword.cloud_notm}} per consentire alle macchine virtuali di comunicare tra loro e su Internet. Per ulteriori informazioni, vedi [Setting up NSX for workload VMs on VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} (VCF)](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}.

## Aggiornamenti e miglioramenti dell'interfaccia utente

* Il numero massimo di server ESXi che possono essere aggiunti a un cluster è ora aggiornato a 32 server. Il numero massimo di cluster continua ad essere cinque.
* Nella pagina **Istanze distribuite**, la colonna **Server ESXi** nelle tabelle di riepilogo dell'istanza è sostituita dalla colonna **Versione**, in cui puoi trovare la versione di release in cui le istanze sono state distribuite o aggiornate.
* La versione di SDDC Manager per le istanze Cloud Foundation è ora disponibile nella pagina dei dettagli dell'istanza.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.
