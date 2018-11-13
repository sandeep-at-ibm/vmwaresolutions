---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Progettazione dell'infrastruttura fisica

L'infrastruttura fisica comprende i seguenti componenti:

<dl class="dl">
  <dt class="dt dlterm">Calcolo fisico</dt>
  <dd class="dd">Il calcolo fisico fornisce l'elaborazione fisica e la memoria che viene utilizzata dall'infrastruttura di virtualizzazione. Per questa progettazione, i componenti di calcolo sono forniti da {{site.data.keyword.baremetal_long}} e sono elencati nella [Guida alla compatibilità hardware per VMware](https://www.vmware.com/resources/compatibility/search.php).</dd>
  <dt class="dt dlterm">Archiviazione fisica</dt>
  <dd class="dd">L'archiviazione fisica fornisce la capacità di archiviazione non elaborata utilizzata dall'infrastruttura di virtualizzazione. I componenti di archiviazione sono forniti da {{site.data.keyword.baremetal_short}} o tramite array NAS (Network Attached Storage) condiviso utilizzando NFS v3.</dd>
  <dt class="dt dlterm">Rete fisica</dt>
  <dd class="dd">La rete fisica fornisce la connettività di rete nell'ambiente che viene quindi utilizzato dalla virtualizzazione di rete. La rete è fornita dalla rete dei servizi {{site.data.keyword.cloud_notm}} e include servizi supplementari come DNS e NTP.</dd>
</dl>

Per ulteriori informazioni sui componenti fisici, vedi la distinta base per l'[istanza Cloud Foundation](../../sddc/sd_bom.html) o l'[istanza vCenter Server](../../vcenter/vc_bom.html).

Per ulteriori informazioni sull'archiviazione, vedi [Architettura dell'archiviazione condivisa](https://www.ibm.com/cloud/garage/files/AttachedStorageSolutionArchitecture_v1.0.pdf).

## Progettazione dell'host fisico

L'host fisico si riferisce ai {{site.data.keyword.baremetal_short}} nell'ambiente che fornisce risorse di calcolo. I {{site.data.keyword.baremetal_short}} applicati in questa soluzione sono certificati da VMware ed elencati nella guida [VMware HCG](http://www.vmware.com/resources/compatibility/search.php).

Le configurazioni del server disponibili nella soluzione soddisfano o superano i requisiti minimi per installare, configurare e gestire vSphere ESXi. Sono disponibili varie configurazioni per soddisfare diversi requisiti. Per l'elenco dettagliato delle specifiche esatte utilizzate per la soluzione VMware on {{site.data.keyword.cloud_notm}}, vedi la distinta base per l'[istanza Cloud Foundation](../../sddc/sd_bom.html) o l'[istanza vCenter Server](../../vcenter/vc_bom.html).

I {{site.data.keyword.baremetal_short}} risiedono in {{site.data.keyword.cloud_notm}}.
{:note}

Ogni istanza Cloud Foundation inizia con una distribuzione a 4 host e ogni istanza vCenter Server inizia con una distribuzione a 3 o 4 host a seconda della scelta della soluzione di archiviazione.

L'host fisico utilizza due dischi collegati localmente da assegnare all'hypervisor vSphere ESXi. Puoi assegnare altri dischi utilizzando vSAN come descritto nella sezione _Progettazione dell'archiviazione fisica_ o utilizzando NetApp ONTAP come descritto in [Architettura di NetApp ONTAP Select](https://www.ibm.com/cloud/garage/files/IBM_Cloud_for_VMware_Solutions_NetApp_Architecture.pdf). Ogni
host fisico ha connessioni di rete ridondanti da 10 Gbps per l'accesso alla rete pubblica e privata.

Il Bare Metal Server ha le seguenti specifiche:
* CPU: Dual Intel Xeon, configurazione core e velocità variabile
* Memoria: configurazione variabile, da 128 GB o superiore
* Rete: 4 x 10 Gbps
* Numero di unità: 2 o più

## Progettazione della rete fisica

Questa sezione descrive la rete fisica fornita da {{site.data.keyword.cloud_notm}} e le connessioni all'host fisico (VLAN, MTU) associate agli host fisici.

La rete fisica di {{site.data.keyword.cloud_notm}} è suddivisa in tre reti distinte: pubblica, privata e di gestione. Per un'illustrazione delle tre reti e del modo in cui funzionano, vedi [Rete {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud-computing/bluemix/our-network).

### Rete pubblica

I {{site.data.keyword.CloudDataCents_notm}} e i PoP (point of presence) di rete dispongono di più connessioni da 1 Gbps o 10 Gbps ai vettori di rete di transito e peering di alto livello.

Il traffico di rete esterno proveniente da qualsiasi parte del mondo si collega al PoP di rete più vicino e viaggia direttamente, attraverso la rete, verso il suo data center, minimizzando il numero di hop e handoff di rete tra provider.

All'interno del data center, {{site.data.keyword.cloud_notm}} fornisce 1 Gbps o 10 Gbps di larghezza di banda di rete ai singoli server tramite una coppia di switch FCS (front-end customer switch) separati aggregati ai peer. Questi switch aggregati sono collegati a una coppia di router FCR (front-end customer router) separati per la rete L3.

Questa progettazione multilivello consente alla rete di ridimensionarsi tra rack, righe e pod all'interno di un {{site.data.keyword.CloudDataCent_notm}}.

### Rete privata

Tutti i {{site.data.keyword.CloudDataCents_notm}} e i PoP sono connessi mediante il backbone di rete privata. La rete privata è separata dalla rete pubblica e consente la connettività ai servizi nei {{site.data.keyword.CloudDataCents_notm}} in tutto il mondo. Lo spostamento dei dati tra i {{site.data.keyword.CloudDataCents_notm}} avviene tramite più connessioni da 10 Gbps o 40 Gbps alla rete privata.

Analogamente alla rete pubblica, la rete privata è multilivello in quanto i server e gli altri componenti dell'infrastruttura sono connessi a switch BCS (back-end customer switch) aggregati. Questi switch aggregati sono collegati a una coppia di router BCR (back-end customer router) separati per la rete L3. La rete privata supporta anche la possibilità di utilizzare i frame Jumbo (MTU 9000) per connessioni all'host fisico.

### Rete di gestione

Oltre alle reti pubbliche e private, ogni server {{site.data.keyword.cloud_notm}} è connesso a una rete di gestione fuori banda. Questa rete di gestione, accessibile tramite VPN, consente l'accesso IPMI (Intelligent Platform Management Interface) al server indipendentemente dalla CPU, dal firmware e dal sistema operativo per scopi di manutenzione e amministrazione.

### Blocchi di IP primari e portatili

{{site.data.keyword.cloud_notm}} assegna due tipi di indirizzi IP da utilizzare all'interno dell'infrastruttura {{site.data.keyword.cloud_notm}}:
* Gli indirizzi IP primari sono assegnati a dispositivi, server virtuali e Bare Metal forniti da {{site.data.keyword.cloud_notm}}. Non assegnare alcun indirizzo IP in questi blocchi.
* Gli indirizzi IP portatili ti vengono forniti per l'assegnazione e la gestione in base alle esigenze.

Gli indirizzi IP primari o portatili possono essere resi instradabili a qualsiasi VLAN all'interno dell'account del cliente quando lo **spanning della VLAN** è abilitato all'interno del {{site.data.keyword.slportal}} o l'account è configurato come account **VRF (Virtual Routing and Forwarding)**.

### Spanning della VLAN

**VLAN Spanning** è un'impostazione dell'account {{site.data.keyword.slportal}} che consente di instradare l'un l'altro il blocco di IP della sottorete primaria e portatile di tutte le VLAN all'interno dell'account. Se l'impostazione **VLAN Spanning** è disabilitata, i blocchi di IP possono ancora essere instradati ai servizi {{site.data.keyword.cloud_notm}}, ma non l'uno all'altro.

Per consentire la connessione trasparente tra varie sottoreti in cui risiedono i componenti della soluzione, devi abilitare **VLAN Spanning** nell'account {{site.data.keyword.slportal}} in cui sono distribuite le istanze Cloud Foundation e vCenter Server.

### VRF (Virtual Routing and Forwarding)

Puoi anche configurare l'account del {{site.data.keyword.slportal}} come account VRF per fornire funzioni simili allo spanning della VLAN, consentendo l'instradamento automatico tra i blocchi di IP della sottorete. Tutti gli account con connessioni Direct-Link devono essere convertiti o creati come account VRF.

La console {{site.data.keyword.vmwaresolutions_short}} non è in grado di rilevare se VRF è abilitato nel {{site.data.keyword.slportal}}. Riceverai un'avvertenza che ti ricorda di verificare di aver abilitato lo **spanning della VLAN** o VRF nel tuo account del {{site.data.keyword.slportal}}.

### Connessioni all'host fisico

Ogni host fisico nella progettazione ha due coppie ridondanti di connessioni Ethernet da 10-Gbps in ogni switch ToR (Top of Rack) {{site.data.keyword.cloud_notm}} (pubblico e privato). Gli adattatori sono configurati come connessioni individuali (non collegate) per un totale di 4 connessioni da 10-Gbps. Ciò consente alle connessioni della scheda dell'interfaccia di rete (NIC) di funzionare indipendentemente l'una dall'altra.

Figura 1. Connessioni NIC all'host fisico

![Connessioni NIC all'host fisico](physical_nic_connection.svg "Connessioni NIC all'host fisico")

### VLAN

Le offerte {{site.data.keyword.vmwaresolutions_short}} sono progettate con 3 VLAN, una pubblica e due private, assegnate al momento della distribuzione. Come mostrato nella Figura 2, la VLAN pubblica è assegnata a eth1 e eth3 e le VLAN private sono assegnate a eth0 e eth2.

La VLAN pubblica e la prima VLAN privata create e assegnate in questa progettazione sono prive di tag per impostazione predefinita all'interno di {{site.data.keyword.cloud_notm}}. La VLAN privata aggiuntiva viene trascinata sulle porte dello switch fisico e contrassegnata con tag all'interno dei gruppi di porte VMware che utilizzano queste sottoreti.

In questa progettazione, la rete privata è composta da due VLAN. Alla prima di queste VLAN (indicata qui come VLAN privata A) sono assegnate tre sottoreti:
* La prima sottorete è un intervallo di sottoreti di IP privati primari che {{site.data.keyword.cloud_notm}} assegna agli host fisici.
* La seconda sottorete è utilizzata per le macchine virtuali di gestione come vCenter Server Appliance e Platform Services Controller
* La terza sottorete è utilizzata per i VTEP (VXLAN Tunnel Endpoint) assegnati a ciascun host tramite VMware NSX Manager.

Oltre alla VLAN privata A, esiste una seconda VLAN privata (qui indicata come VLAN privata B) per supportare le funzioni di VMware, come vSAN e vMotion, e per la connettività al NAS (Network Attached Storage). Pertanto, la VLAN è divisa in due o tre sottoreti portatili.

* La prima sottorete viene assegnata a un gruppo di porte kernel per il traffico vMotion.
* Le restanti sottoreti vengono utilizzate per il traffico di archiviazione:
   * Se si utilizza vSAN, una sottorete viene assegnata ai gruppi di porte kernel utilizzati per il traffico vSAN.
   * Se si utilizza NAS, una sottorete viene assegnata a un gruppo di porte dedicato al traffico NFS.

Tutte le sottoreti configurate come parte di una distribuzione automatizzata di vCenter Server o Cloud Foundation utilizzano intervalli gestiti da {{site.data.keyword.cloud_notm}}. Ciò serve a garantire che qualsiasi indirizzo IP possa essere indirizzato a qualsiasi data center all'interno dell'account {{site.data.keyword.cloud_notm}} ogni volta che hai bisogno della connessione.

Tutto ciò è riepilogato nella Tabella 1.

Tabella 1. Riepilogo VLAN e sottorete

| VLAN | Tipo | Descrizione |
|:---- |:---- |:----------- |
| Pubblica| Primaria  | Assegnata agli host fisici per l'accesso alla rete pubblica. Non utilizzata al momento della distribuzione iniziale. |
| Privata A | Primaria  | Sottorete singola assegnata agli host fisici assegnati da {{site.data.keyword.cloud_notm}}. Utilizzata dall'interfaccia di gestione per il traffico di gestione vSphere. |
| Privata A | Portatile | Sottorete singola assegnata alle macchine virtuali che funzionano come componenti di gestione |
| Privata A | Portatile | Sottorete singola assegnata al VTEP NSX |
| Privata B | Portatile | Sottorete singola assegnata per vSAN, se in uso |
| Privata B | Portatile | Sottorete singola assegnata per NAS, se in uso |
| Privata B | Portatile | Sottorete singola assegnata per vMotion |

In questa progettazione, tutti gli host e le macchine virtuali supportati dalla VLAN sono configurati in modo che puntino al router del cliente della “rete privata” di back-end {{site.data.keyword.cloud_notm}} come rotta predefinita. Sebbene le istanze vCenter Server e Cloud Foundation consentano l'utilizzo di SDN (Software-Defined Networking), le sovrapposizioni di rete create all'interno di un'istanza VMware che includono l'instradamento alle sottoreti interne non sono note ai router gestiti da {{site.data.keyword.cloud_notm}}. Pertanto, potresti dover creare rotte statiche all'interno dell'istanza VMware su alcuni o su tutti i componenti di gestione.

Le connessioni alla rete privata sono configurate per utilizzare una dimensione MTU dei frame Jumbo pari a 9000 per migliorare le prestazioni per trasferimenti di dati di grandi dimensioni, come archiviazione e vMotion. Questa è la MTU massima consentita in VMware e da {{site.data.keyword.cloud_notm}}. Le connessioni alla rete pubblica utilizzano una MTU Ethernet standard di 1500. Questo valore deve essere mantenuto poiché qualsiasi modifica potrebbe causare la frammentazione dei pacchetti su Internet.

## Progettazione dell'archiviazione fisica

La progettazione dell'archiviazione fisica consiste nella configurazione dei dischi fisici installati negli host fisici e nella configurazione dell'archiviazione a livello di file condivisa. Ciò include i dischi del sistema operativo dell'hypervisor vSphere ESXi e quelli utilizzati per l'archiviazione delle macchine virtuali (VM). L'archiviazione per le VM può essere composta di dischi locali virtualizzati da VMware vSAN o di un'archiviazione a livello di file condivisa.

### Dischi del sistema operativo

L'hypervisor vSphere ESXi è progettato per essere installato in una ubicazione persistente. Di conseguenza, gli host fisici contengono due dischi SATA da 1-TB nella configurazione RAID-1 per supportare la ridondanza per l'hypervisor vSphere ESXi.

### Archiviazione delle macchine virtuali

Questa progettazione consente di utilizzare VMware vSAN o l'archiviazione a livello di file condivisa come archivio dati primario per le VM.

### Dischi vSAN

Se utilizzato, VMware vSAN viene configurato utilizzando una configurazione all-flash. Questa progettazione consente diverse opzioni di configurazione, tra cui chassis 2U e 4U, vari numeri di dischi e varie dimensioni del disco. Tutte le configurazioni utilizzano due gruppi di dischi vSAN, con un SSD (Solid State Disk) per la cache e uno o più SSD per la capacità. Tutte le unità che vengono assegnate per il consumo di vSAN sono configurate in RAID-0 a singolo disco.

Per ulteriori informazioni sulle configurazioni supportate, vedi la distinta base per l'[istanza Cloud Foundation](../../sddc/sd_bom.html) o l'[istanza vCenter Server](../../vcenter/vc_bom.html).

### Archiviazione a livello di file condivisa tra gli host

Quando si utilizza l'archiviazione a livello di file condivisa, una condivisione NFS da 2-TB è collegata agli host che comprendono il cluster VMware iniziale. Questa condivisione, che è nota come condivisione di gestione, viene utilizzata per i componenti di gestione come VMware vCenter Server, PSC (Platform Services Controller) e VMware NSX. L'archiviazione viene collegata utilizzando il protocollo NFSv3 e può supportare fino a 4000 IOPS.

Figura 2. Condivisioni NFS collegate alla distribuzione VMware

![Condivisioni NFS collegate alla distribuzione VMware](physical_nfs.svg "Condivisioni NFS collegate alla distribuzione VMware: condivisione di gestione e condivisione specificata dal cliente")

Puoi assegnare e montare più condivisioni di file per i tuoi carichi di lavoro al momento dell'acquisto o successivamente nella console. Puoi scegliere tra le opzioni di capacità di archiviazione file Endurance {{site.data.keyword.cloud_notm}} e i livelli di prestazioni disponibili nel {{site.data.keyword.CloudDataCent_notm}} corrispondente. Tutte le condivisioni vengono collegate utilizzando il protocollo NFSv3. Inoltre, è possibile collegare le condivisioni file NFSv3 applicando l'offerta NetApp ONTAP Select.

I {{site.data.keyword.CloudDataCents_notm}} che offrono il livello di prestazioni di 10 IOPS/GB includono anche la crittografia dei dati inattivi gestita dal provider (crittografia AES-256) e sono supportati dall'archiviazione all-flash. Il livello di prestazioni di 10 IOPS/GB è limitato a una capacità massima di 4 TB. Per ulteriori informazioni sul NAS condiviso utilizzato in questa soluzione, vedi [Architettura dell'archiviazione condivisa](https://www.ibm.com/cloud/garage/files/AttachedStorageSolutionArchitecture_v1.0.pdf).

### Link correlati

* [Distinta base di Cloud Foundation](../../sddc/sd_bom.html)
* [Distinta base di vCenter Server](../../vcenter/vc_bom.html)
* [Architettura dell'archiviazione condivisa](https://www.ibm.com/cloud/garage/files/AttachedStorageSolutionArchitecture_v1.0.pdf)
* [Architettura di NetApp ONTAP Select](https://www.ibm.com/cloud/garage/files/IBM_Cloud_for_VMware_Solutions_NetApp_Architecture.pdf)
