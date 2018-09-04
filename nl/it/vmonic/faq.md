---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Domande frequenti generali su IBM Cloud for VMware Solutions

Trova le risposte alle domande frequenti su {{site.data.keyword.vmwaresolutions_full}}.

## Di quali account utente ho bisogno per IBM Cloud for VMware Solutions?

* **Account ID IBM**. Questo account è richiesto per accedere alla console {{site.data.keyword.vmwaresolutions_short}}. La console è un'interfaccia utente autonoma separata dal {{site.data.keyword.slportal}}. Per ulteriori informazioni, vedi [Introduzione](../index.html).
* **Account {{site.data.keyword.cloud_notm}}**. Questo account è richiesto per il provisioning. Puoi registrarti per un account {{site.data.keyword.cloud_notm}} utilizzando un **ID IBM** esistente oppure creando un nuovo **ID IBM**. 
* **Account dell'infrastruttura {{site.data.keyword.cloud_notm}}**. Questo account, precedentemente noto come account **IBM SoftLayer**, è utilizzato per accedere al portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}} che fornisce alcune funzioni aggiuntive per la gestione di prodotti e servizi dell'infrastruttura. Puoi ottenere un account dell'infrastruttura {{site.data.keyword.cloud_notm}} aggiornando il tuo **account {{site.data.keyword.cloud_notm}}** a un tipo di account Pagamento a consumo oppure collegando il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) esistente al tuo account {{site.data.keyword.cloud_notm}}. L'account dell'infrastruttura {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Registrazione degli account richiesti](signing_softlayer_account.html) e [Requisiti dell'account dell'infrastruttura {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).

## Come posso associare le mie credenziali dell'infrastruttura IBM Cloud alla console IBM Cloud for VMware Solutions?

Quando ordini la tua istanza per la prima volta, segui le istruzioni sulla pagina **Impostazioni** nella console per individuare e copiare il nome utente e la chiave API dell'infrastruttura {{site.data.keyword.cloud_notm}} dal {{site.data.keyword.slportal}}. Le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} vengono memorizzate nella console {{site.data.keyword.vmwaresolutions_short}} dopo il primo ordine. Gli ordini futuri utilizzano automaticamente le credenziali memorizzate.

## Come vengono fatturati i consumi della piattaforma virtuale VMware?

Tutti i costi per l'infrastruttura fisica e virtuale e le licenze risultanti dall'istanza vengono addebitati sul tuo account {{site.data.keyword.cloud_notm}}. Quando ordini un'istanza, devi disporre di un account {{site.data.keyword.cloud_notm}} e fornire la chiave {{site.data.keyword.slapi_short}} associata all'account.

## Quali sono le differenze tra un'istanza vCenter Server, un'istanza Cloud Foundation e un cluster VMware vSphere?

Tutti i tipi di istanza offrono opzioni di distribuzione per gli ambienti virtuali VMware. Tuttavia, la differenza risiede nel grado di personalizzazione e di automazione.

* Quando ordini un'istanza VMware vCenter Server, distribuisci un ambiente virtuale VMware con risorse di calcolo, archiviazione e rete personalizzate. Per ulteriori informazioni sui componenti distribuiti, vedi [Specifiche tecniche per le istanze vCenter Server](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).
* Quando ordini un'istanza VMware Cloud Foundation, distribuisci una piattaforma SDDC (software-defined data center) unificata. Per ulteriori informazioni sui componenti distribuiti, vedi [Specifiche tecniche per le istanze Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).
* Quando ordini un cluster VMware vSphere, ottieni il massimo della flessibilità per progettare e costruire il tuo ambiente VMware ospitato incorporando l'hardware compatibile con VMware. Tuttavia, {{site.data.keyword.cloud_notm}} non automatizza l'installazione, la configurazione e il richiamo dei componenti VMware facoltativi per il cluster VMware vSphere.
* Le funzioni supportate per le istanze vCenter Server, le istanze Cloud Foundation e i cluster vSphere sono diverse. Per ulteriori informazioni, vedi [Tabella di confronto delle offerte](inst_comp_chart.html).

## Cosa è incluso in un'istanza vCenter Server?

Per ulteriori informazioni, vedi [Specifiche tecniche per le istanze vCenter Server](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).

## Cosa è incluso in un'istanza Cloud Foundation?

Per ulteriori informazioni, vedi [Specifiche tecniche per le istanze Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## Cosa è incluso in un cluster vSphere?
Per ulteriori informazioni, vedi [Componenti di VMware vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_vsphereclusteroverview.html).

## Un'istanza vCenter Server a due nodi è altamente disponibile?

Si consiglia di distribuire i carichi di lavoro di produzione in ambienti con almeno tre nodi.

VMware vSphere DRS (Distributed Resource Scheduler) e VMware HA (High Availability) sono abilitati per impostazione predefinita. Tuttavia, le procedure ottimali di VMware suggeriscono di posizionare ciascuno dei tre controller NSX su un singolo nodo.

Nella distribuzione minima a due nodi, un nodo ha un controller NSX e l'altro nodo ha due controller NSX. Se il nodo con due controller NSX si interrompe, le operazioni del controller NSX vengono messe in modalità di sola lettura e le nuove VM (macchine virtuali) o le VM vMotion potrebbero riscontrare dei problemi di rete.

Quando un terzo nodo viene aggiunto a un cluster a due nodi, vCenter Server ribilancia automaticamente i tre controller NSX tra i tre nodi e crea un ambiente altamente disponibile.

## Posso impostare la configurazione HA per VMware vCenter 6.5?

No, non è consigliato. Potrebbero verificarsi degli errori nelle funzioni di {{site.data.keyword.vmwaresolutions_short}}.

## È possibile rinominare i cluster?

Per le istanze vCenter Server, il primo cluster creato durante la distribuzione ha il nome predefinito **cluster1**. Puoi rinominare il cluster predefinito nel client VMware vSphere. Quando aggiungi un cluster a un'istanza vCenter Server, puoi specificare il nome che vuoi nella console {{site.data.keyword.vmwaresolutions_short}}.

**Nota**: per le istanze Cloud Foundation, il nome cluster predefinito non può essere modificato.

##Come vengono gestite le patch?

IBM fornisce aggiornamenti continui al codice IBM distribuendo la VSI (Virtual Server Instance) IBM CloudDriver su richiesta. IBM non fornisce aggiornamenti continui ai servizi aggiuntivi come Zerto on {{site.data.keyword.cloud_notm}} o Veeam on {{site.data.keyword.cloud_notm}}. Ottenere e installare questi aggiornamenti è sotto la tua responsabilità.

Gli aggiornamenti di VMware vengono applicati in modo diverso in base al tipo di istanza VMware che hai distribuito:

* Per le istanze VMware Cloud Foundation, vengono forniti aggiornamenti ai componenti vSphere ESXi, NSX, vCenter, Platform Services Controller e SDDC Manager tramite la console {{site.data.keyword.vmwaresolutions_short}}.
* Per le istanze VMware vCenter Server:
  * Per le istanze distribuite o aggiornate alla V2.1 o superiore, i cluster e i server ESXi appena distribuiti verranno corretti con i recenti, ma non necessariamente ultimi, aggiornamenti ESXi da VMware.
  * Sei responsabile di tutti gli altri aggiornamenti ai componenti VMware, inclusa la garanzia che i cluster e i server ESXi appena distribuiti dispongano di tutti gli aggiornamenti più recenti necessari.
  * Per le istanze distribuite nella V2.0 o superiore, VMware Update Manager (VUM) è integrato nel tuo vCenter Server. Puoi configurare VUM per scaricare gli aggiornamenti ESXi da VMware.

Per ulteriori informazioni, consulta le seguenti risorse:
* [Supporto VMware](https://www.vmware.com/support.html)
* [Applicazione di aggiornamenti alle istanze vCenter Server](../vcenter/vc_applyingupdates.html)
* [Applicazione di aggiornamenti alle istanze Cloud Foundation](../sddc/sd_applyingupdates.html)

## L'edge NSX dei servizi di gestione rappresenta un rischio per la sicurezza?

Sebbene l'edge VMware NSX per i servizi di gestione si trovi in una sottorete pubblica, sono state adottate misure di sicurezza per garantire che non costituisca un rischio per la sicurezza. Queste misure sono:
*  Il firewall edge NSX è configurato per consentire solo il traffico HTTPS in uscita (porta TCP 443) avviato dalle macchine virtuali di gestione.
*  SNAT (Source Network Address Translation) viene utilizzato in modo che gli indirizzi IP privati non siano visibili all'esterno della rete privata.
*  L'accesso remoto per il dispositivo edge NSX dei servizi di gestione è disabilitato.
*  Le password per accedere all'edge NSX dei servizi di gestione dalla rete privata sono casuali e crittografate.

## L'edge NSX gestito dal cliente rappresenta un rischio per la sicurezza?

Sebbene l'edge NSX gestito dal cliente sia connesso alla VLAN pubblica, sono state adottate misure di sicurezza per garantire che non costituisca un rischio per la sicurezza. Sono in vigore le seguenti misure di sicurezza:
*  È presente una regola del firewall per consentire solo il traffico in uscita dall'intervallo di indirizzi IP della sottorete privata.
*  È presente una regola SNAT (Source Network Address Translation) (disabilitata per impostazione predefinita) per tradurre tutti gli indirizzi IP dalla sottorete privata in un singolo indirizzo IP sulla sottorete pubblica.
*  L'accesso remoto per il dispositivo edge NSX gestito dal cliente è disabilitato.
*  Le password per accedere all'edge NSX gestito dal cliente dalla rete privata sono casuali e crittografate.

## Come scelgo i data center per le mie istanze?

Le distribuzioni delle istanze hanno requisiti rigorosi in materia di infrastruttura fisica, che variano tra i {{site.data.keyword.CloudDataCents_notm}}. Quando effettui l'ordine dell'istanza, i data center disponibili vengono elencati all'interno delle regioni e puoi selezionare quello che vuoi dall'elenco.

Per ulteriori informazioni, vedi le sezioni _Disponibilità dei data center IBM Cloud_ in:
* [Requisiti e pianificazione per le istanze vCenter Server](../vcenter/vc_planning.html)
* [Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_planning.html)
* [Requisiti e pianificazione per le istanze Cloud Foundation](../sddc/sd_planning.html)
* [Requisiti e pianificazione per VMware vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [Requisiti e pianificazione per le istanze NetApp ONTAP Select](../netapp/np_planning.html)
* [Requisiti e pianificazione per le istanze VMware Federal](../vcenter/vc_fed_planning.html)

## Quanto tempo ci vuole per distribuire la mia istanza?

Puoi controllare lo stato della distribuzione dell'istanza visualizzando la cronologia di distribuzione nella pagina dei dettagli dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}.

## VMware vSphere on IBM Cloud utilizza l'automazione per installare, configurare e richiamare lo stack VMware?

No. VMware vSphere on {{site.data.keyword.cloud_notm}} non utilizza l'automazione avanzata disponibile nelle piattaforme di Cloud Foundation e vCenter Server. In base a quello che ordini, la piattaforma fornisce licenze VMware opzionali, server ESXi e, facoltativamente, una coppia HA di firewall fisici FortiGate. Se viene creato un nuovo cluster, vengono fornite anche tre nuove VLAN: una VLAN pubblica e due VLAN private.

VMware ESXi viene installato automaticamente su ciascun server bare metal, ma sei responsabile dell'installazione di eventuali componenti VMware aggiuntivi come vCenter Server o NSX. Anche se vSphere on {{site.data.keyword.cloud_notm}} garantisce che l'hardware compatibile con VMware sia ordinato in base ai componenti VMware selezionati, non esiste alcuna automazione per configurare e richiamare l'ambiente VMware. Sei responsabile della progettazione e dell'architettura dell'ambiente ospitato da IBM.

## Come posso visualizzare un elenco di tutte le notifiche?

Per visualizzare la cronologia completa delle notifiche, fai clic su **Notifiche** nel riquadro di navigazione a sinistra.

## Cosa faccio se ho un problema con IBM Cloud for VMware Solutions?

Se hai bisogno di assistenza con {{site.data.keyword.vmwaresolutions_short}}, contatta il supporto IBM attraverso uno dei canali di supporto. Per ulteriori informazioni, vedi [Come contattare il supporto IBM](trbl_support.html).

### Link correlati

* [Notifiche](notifications.html)
* [Istanze Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Istanze vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Accesso alla console](loginmethod.html)
* [Account utente e impostazioni](useraccount.html)
