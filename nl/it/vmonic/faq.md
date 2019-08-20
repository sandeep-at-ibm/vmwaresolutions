---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-01"

keywords: FAQ, user account, patch management

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Domande frequenti generali su IBM Cloud for VMware Solutions
{: #faq}

Trova le risposte alle domande frequenti su {{site.data.keyword.vmwaresolutions_full}}.

## Di quali account utente ho bisogno per IBM Cloud for VMware Solutions?
{: #faq-user-accts}
{: faq}

* **Account ID IBM**. Questo account è richiesto per accedere alla console {{site.data.keyword.vmwaresolutions_short}}. La console è un'interfaccia utente autonoma separata dal {{site.data.keyword.slportal}}. Per ulteriori informazioni, vedi [Introduzione](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started).
* **Account {{site.data.keyword.cloud_notm}}**. Questo account è richiesto per il provisioning. Puoi registrarti per un account {{site.data.keyword.cloud_notm}} utilizzando un **ID IBM** esistente oppure creando un nuovo **ID IBM**.
* **Account dell'infrastruttura {{site.data.keyword.cloud_notm}}**. Questo account viene utilizzato per accedere al portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}} che fornisce alcune funzioni aggiuntive per la gestione di prodotti e servizi dell'infrastruttura. Puoi ottenere un account dell'infrastruttura {{site.data.keyword.cloud_notm}} eseguendo l'upgrade del tuo account **{{site.data.keyword.cloud_notm}}** a un tipo di account fatturabile oppure collegando il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} esistente al tuo account {{site.data.keyword.cloud_notm}}. L'account dell'infrastruttura {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Registrazione degli account richiesti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts) e [Requisiti dell'account dell'infrastruttura {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).

## Come posso associare le mie credenziali dell'infrastruttura IBM Cloud alla console IBM Cloud for VMware Solutions?
{: #faq-associate-credentials}
{: faq}

Quando ordini la tua istanza per la prima volta, segui le istruzioni sulla pagina **Impostazioni** nella console per individuare e copiare il nome utente e la chiave API dell'infrastruttura {{site.data.keyword.cloud_notm}} dal {{site.data.keyword.slportal}}. Le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} vengono memorizzate nella console {{site.data.keyword.vmwaresolutions_short}} dopo il primo ordine. Gli ordini futuri utilizzano automaticamente le credenziali memorizzate.

## Come vengono fatturati i consumi della piattaforma virtuale VMware?
{: #faq-billing}
{: faq}

Tutti i costi per l'infrastruttura fisica e virtuale e le licenze risultanti dall'istanza vengono addebitati sul tuo account {{site.data.keyword.cloud_notm}}. Quando ordini un'istanza, devi disporre di un account {{site.data.keyword.cloud_notm}} e fornire la chiave {{site.data.keyword.slapi_short}} associata all'account.

## Quali sono le differenze tra un'istanza vCenter Server e un cluster VMware vSphere?
{: #faq-vcs-cf-vss}
{: faq}

Tutti i tipi di istanza offrono opzioni di distribuzione per gli ambienti virtuali VMware. Tuttavia, la differenza risiede nel grado di personalizzazione e di automazione.

* Quando ordini un'istanza VMware vCenter Server, distribuisci un ambiente virtuale VMware con risorse di calcolo, archiviazione e rete personalizzate. Per ulteriori informazioni sui componenti distribuiti, vedi [Specifiche tecniche per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs).
* Quando ordini un cluster VMware vSphere, ottieni il massimo della flessibilità per progettare e costruire il tuo ambiente VMware ospitato mentre incorpori l'hardware compatibile con VMware. Tuttavia, {{site.data.keyword.cloud_notm}} non automatizza l'installazione, la configurazione e il richiamo dei componenti VMware facoltativi per il cluster VMware vSphere.
* Le funzioni supportate dalle istanze vCenter Server e dai cluster vSphere sono diverse. Per ulteriori informazioni, vedi [Tabella di confronto delle offerte](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

## Cosa è incluso in un'istanza vCenter Server?
{: #faq-vcs}
{: faq}

Per ulteriori informazioni, vedi [Specifiche tecniche per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs).

## Cosa è incluso in un cluster vSphere?
{: #faq-vss}
{: faq}

Per ulteriori informazioni, vedi [Componenti di VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview).

## Un'istanza vCenter Server a due nodi è altamente disponibile?
{: #is-a-two-node-vcenter-server-instance-highly-available}
{: faq}

Si consiglia di distribuire i carichi di lavoro di produzione in ambienti con almeno tre nodi.

VMware vSphere DRS (Distributed Resource Scheduler) e VMware HA (High Availability) sono abilitati per impostazione predefinita. Tuttavia, le procedure ottimali di VMware suggeriscono di posizionare ciascuno dei tre controller NSX su un singolo nodo.

Nella distribuzione minima a due nodi, un nodo ha un controller NSX e l'altro nodo ha due controller NSX. Se il nodo con due controller NSX si interrompe, le operazioni del controller NSX vengono messe in modalità di sola lettura e le nuove VM (Virtual Machine) o le VM vMotion potrebbero riscontrare dei problemi di rete.

Quando un terzo nodo viene aggiunto a un cluster a due nodi, vCenter Server ribilancia automaticamente i tre controller NSX tra i tre nodi e crea un ambiente altamente disponibile.

## Posso impostare la configurazione di VMware vCenter HA?
{: #faq-ha}
{: faq}

Puoi configurare vCenter HA, ma il supporto della configurazione non è fornito da {{site.data.keyword.vmwaresolutions_short}}.

## È possibile rinominare i cluster?
{: #faq-rename-cluster}
{: faq}

Per una nuova istanza vCenter Server, puoi impostare il nome del cluster iniziale creato durante la distribuzione. Quando aggiungi un cluster a un'istanza vCenter Server, puoi specificare il nome che vuoi nella console {{site.data.keyword.vmwaresolutions_short}}.

## Come vengono gestite le patch?
{: #faq-patches}
{: faq}

IBM fornisce aggiornamenti continui al codice IBM distribuendo la VSI (Virtual Server Instance) IBM CloudDriver su richiesta. IBM non fornisce aggiornamenti continui ai servizi aggiuntivi come Zerto on {{site.data.keyword.cloud_notm}} o Veeam on {{site.data.keyword.cloud_notm}}. Ottenere e installare questi aggiornamenti è sotto la tua responsabilità.

Per le istanze VMware vCenter Server distribuite o di cui è stato eseguito l'upgrade alla V2.1 o superiore, i server e i cluster ESXi appena distribuiti vengono corretti con i recenti aggiornamenti ESXi da parte di VMware, ma non necessariamente con gli aggiornamenti più recenti.

Sei responsabile di tutti gli altri aggiornamenti ai componenti VMware, inclusa la garanzia che i cluster e i server ESXi appena distribuiti dispongano di tutti gli aggiornamenti più recenti necessari.
{:important}

Per le istanze distribuite nella V2.0 o superiore, VMware Update Manager (VUM) è integrato nel tuo vCenter Server. Puoi configurare VUM per scaricare gli aggiornamenti ESXi da VMware.

Per ulteriori informazioni, consulta le seguenti risorse:
* [Supporto VMware](https://www.vmware.com/support.html){:external}
* [Applicazione di aggiornamenti alle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)

## L'edge NSX dei servizi di gestione rappresenta un rischio per la sicurezza?
{: #faq-mgmt-nsx}
{: faq}

Sebbene l'edge VMware NSX per i servizi di gestione si trovi su una sottorete pubblica, vengono adottate le seguenti misure di sicurezza per garantire che non costituisca un rischio per la sicurezza:
*  Il firewall edge NSX è configurato per consentire solo il traffico HTTPS in uscita (porta TCP 443) avviato dalle VM (Virtual Machine) di gestione.
*  SNAT (Source Network Address Translation) viene utilizzato in modo che gli indirizzi IP privati non siano visibili all'esterno della rete privata.
*  L'accesso remoto per il dispositivo edge NSX dei servizi di gestione è disabilitato.
*  Le password per accedere all'edge NSX dei servizi di gestione dalla rete privata sono casuali e crittografate.

## L'edge NSX gestito dal cliente rappresenta un rischio per la sicurezza?
{: #faq-customer-nsx}
{: faq}

Sebbene l'edge NSX gestito dal cliente sia connesso alla VLAN pubblica, sono state adottate misure di sicurezza per garantire che non costituisca un rischio per la sicurezza. Sono in vigore le seguenti misure di sicurezza:
*  È presente una regola del firewall per consentire solo il traffico in uscita dall'intervallo di indirizzi IP della sottorete privata.
*  È presente una regola SNAT (disabilitata per impostazione predefinita) per tradurre tutti gli indirizzi IP dalla sottorete privata in un singolo indirizzo IP sulla sottorete pubblica.
*  L'accesso remoto per il dispositivo edge NSX gestito dal cliente è disabilitato.
*  Le password per accedere all'edge NSX gestito dal cliente dalla rete privata sono casuali e crittografate.

## Come scelgo i data center per le mie istanze?
{: #faq-data-center}
{: faq}

Le distribuzioni delle istanze hanno requisiti rigorosi in materia di infrastruttura fisica, che variano tra i {{site.data.keyword.CloudDataCents_notm}}. Quando effettui l'ordine dell'istanza, i data center disponibili vengono elencati all'interno delle regioni e puoi selezionare quello che vuoi dall'elenco.

Per ulteriori informazioni, vedi le sezioni _Disponibilità dei data center IBM Cloud_ in:
* [Requisiti e pianificazione per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Requisiti e pianificazione per VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [Requisiti e pianificazione per le istanze NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning)

## Quanto tempo ci vuole per distribuire la mia istanza?
{: #faq-deploy}
{: faq}

Puoi controllare lo stato della distribuzione dell'istanza visualizzando la cronologia di distribuzione nella pagina dei dettagli dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}.

## VMware vSphere on IBM Cloud utilizza l'automazione per installare, configurare e richiamare lo stack VMware?
{: #faq-vss-automation}
{: faq}

No. VMware vSphere on {{site.data.keyword.cloud_notm}} non utilizza l'automazione avanzata dalla piattaforma vCenter Server. In base a quello che ordini, la piattaforma fornisce licenze VMware opzionali, server ESXi e, facoltativamente, una coppia HA di firewall fisici FortiGate. Se viene creato un nuovo cluster, vengono fornite anche tre nuove VLAN: una VLAN pubblica e due VLAN private.

VMware ESXi viene installato automaticamente su ciascun server bare metal, ma sei responsabile dell'installazione di eventuali componenti VMware aggiuntivi come vCenter Server o NSX. Anche se vSphere on {{site.data.keyword.cloud_notm}} garantisce che l'hardware compatibile con VMware sia ordinato in base ai componenti VMware selezionati, non esiste alcuna automazione per configurare e richiamare l'ambiente VMware. Sei responsabile della progettazione e dell'architettura dell'ambiente ospitato da IBM.

## Come posso visualizzare un elenco di tutte le notifiche?
{: #faq-notification}
{: faq}

Per visualizzare la cronologia completa delle notifiche, fai clic su **Notifiche** nel riquadro di navigazione a sinistra.

## Cosa faccio se ho un problema con IBM Cloud for VMware Solutions?
{: #faq-support}
{: faq}

Se hai bisogno di assistenza con {{site.data.keyword.vmwaresolutions_short}}, contatta il supporto IBM attraverso uno dei canali di supporto. Per ulteriori informazioni, vedi [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

## Link correlati
{: #faq-related}

* [Notifiche](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [Istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Accesso alla console](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
