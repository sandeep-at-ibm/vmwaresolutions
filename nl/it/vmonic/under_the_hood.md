---

copyright:

  years:  2019

lastupdated: "2019-06-28"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions: informazioni approfondite
{: #under_the_hood}

## Distribuisci e gestisci gli ambienti virtualizzati VMware
{: #under_the_hood-deploy}

Analizza in modo approfondito l'architettura di {{site.data.keyword.vmwaresolutions_full}}, un'offerta di {{site.data.keyword.cloud_notm}} che fornisce la distribuzione e la gestione degli ambienti virtualizzati VMware. In questa esercitazione, ti mostriamo i componenti dell'offerta in modo da poter vedere come operano insieme per consentire il provisioning e la manutenzione l'ambiente nel cloud pubblico.

## Due società, una soluzione semplificata
{: #under_the_hood-two-companies}

Già da tempo, gli utenti distribuiscono gli ambienti virtualizzati VMware su IBM Public Cloud, da soli o con l'aiuto di servizi professionali. Nel febbraio 2016, [IBM e VMware hanno annunciato una partnership](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external} per automatizzare il processo di distribuzione del software e degli ambienti VMware in {{site.data.keyword.cloud_notm}}. Uno dei primi frutti di questa partnership è stata la possibilità di ordinare varie distribuzioni e licenze di prodotti dalla console {{site.data.keyword.vmwaresolutions_short}} e successivamente di offrire [VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external} in {{site.data.keyword.cloud_notm}}. Inoltre, IBM e VMware hanno collaborato per produrre congiuntamente un'[architettura di riferimento standard e una prescrizione di distribuzione per VMware](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external} in IBM Public Cloud.

Nell'autunno del 2016, IBM e VMware hanno rilasciato insieme {{site.data.keyword.vmwaresolutions_short}}. Questa serie di offerte si basa sulle tecnologie di virtualizzazione di VMware, tra cui il calcolo virtualizzato (VMware vSphere), la rete (VMware NSX) e, facoltativamente, l'archiviazione virtualizzata (VMware vSAN). Questi ambienti sono appropriatamente chiamati data center definiti dal software.

{{site.data.keyword.vmwaresolutions_short}} si basa sulla tecnologia VMware per semplificare notevolmente la distribuzione e la gestione di questi data center definiti dal software in IBM Public Cloud. Utilizzando {{site.data.keyword.vmwaresolutions_short}}, è ora possibile distribuire parti dell'architettura di riferimento standard su {{site.data.keyword.cloud_notm}} automaticamente anziché manualmente. Gli ambienti che in precedenza richiedevano settimane per essere distribuiti e configurati possono ora essere forniti in poche ore.

Questa facilità di distribuzione ti consente di concentrarti sull'implementazione di soluzioni su VMware anziché sulla creazione del tuo ambiente. Con gli ambienti subito a tua disposizione, puoi creare sia soluzioni cloud ibride tra il tuo cloud privato e IBM Public Cloud, sia soluzioni native del cloud su IBM Public Cloud. Combinando più distribuzioni, puoi aggiungere facilmente le funzionalità di ripristino di emergenza o di alta disponibilità alle tue soluzioni.

Adesso, analizziamo nei particolari l'architettura di {{site.data.keyword.vmwaresolutions_short}}. Acquisirai informazioni sui diversi componenti che fanno parte della soluzione e sul modo in cui operano insieme per consentire il provisioning e la gestione del tuo data center definito dal software in {{site.data.keyword.cloud_notm}}. Imparerai anche a conoscere la topologia della rete e le varie opzioni disponibili per la connessione al tuo ambiente.

## Nozioni di base su IBM Cloud for VMware Solutions

Per il provisioning e la gestione dei tuoi data center definiti dal software viene utilizzata la [console {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}. Accedi alla console utilizzando il tuo account ID IBM.

Dal catalogo VMware Solutions, puoi eseguire il provisioning di uno dei diversi tipi di ambienti di virtualizzazione. La soluzione di virtualizzazione in primo piano è *VMware vCenter Server on {{site.data.keyword.cloud_notm}}*, che offre l'hypervisor vSphere di VMware, VMware vCenter Server, VMware NSX e, facoltativamente, VMware vSAN. Puoi anche eseguire il provisioning di questo ambiente con ulteriori servizi aggiuntivi che forniscono servizi di backup, ripristino di emergenza, migrazione, sicurezza, conformità e rete.

Prima di ordinare un'istanza vCenter Server, devi configurare la tua chiave API dell'infrastruttura {{site.data.keyword.cloud_notm}} nel catalogo VMware Solutions. Per farlo, fai clic sul link [Impostazioni](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external} nel menu di sinistra della console e immetti il tuo nome utente e la tua chiave API dove vengono richieste le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}}. Il sistema verifica che la tua chiave API e il tuo account dispongano delle autorizzazioni e delle impostazioni appropriate per distribuire l'istanza.

Quando ordini l'istanza vCenter Server, devi prima scegliere il suo nome e la versione di VMware vSphere. Tutte le istanze VMware vengono distribuite insieme ai controller di dominio Microsoft Active Directory e, ai fini del Single Sign-On, devi designare la tua istanza come sito primario o secondario. Un'istanza primaria è la prima o l'unica istanza nel tuo dominio Single Sign-On. Puoi distribuire più istanze secondarie e associarle allo stesso dominio Single Sign-On di un'istanza primaria esistente. Successivamente, scegli se portare le tue proprie licenze VMware o quale edizione della licenza vuoi noleggiare da {{site.data.keyword.cloud_notm}}. Infine, scegli la regione e il data center {{site.data.keyword.cloud_notm}} per la tua istanza, nonché le caratteristiche della CPU e della memoria per gli host presenti nel tuo cluster.

Nella parte successiva della pagina dell'ordine, immetti le caratteristiche di archiviazione e di rete per la tua istanza. Puoi scegliere tra l'archiviazione vSAN e NFS per il tuo cluster, con la possibilità di scegliere la dimensione e il numero di dischi Flash vSAN e l'edizione della licenza vSAN oppure la dimensione, il conteggio e le prestazioni dei volumi di archiviazione NFS. Per la rete, scegli il prefisso del nome host per i tuoi host e il dominio secondario e il dominio per il cluster. Hai la possibilità di distribuire i controller Active Directory come singola VSI (virtual server instance) {{site.data.keyword.cloud_notm}} o due macchine virtuali all'interno del tuo cluster per cui devi fornire la licenza e l'attivazione.

Nella parte inferiore della pagina dell'ordine di vCenter Server, puoi scegliere tra vari servizi aggiuntivi che puoi distribuire per la tua istanza VMware e che vengono fatturati sul tuo account {{site.data.keyword.cloud_notm}}. Alcuni servizi richiedono una configurazione aggiuntiva, che specifichi come parte del modulo d'ordine.

Il modulo d'ordine calcola e visualizza una stima del prezzo in base alle tue selezioni. Hai l'opportunità di riesaminare questa stima e i vari termini e le condizioni prima di effettuare l'ordine.

### Opzioni di distribuzione
{: #under_the_hood-deploy-options}

Il modulo d'ordine di vCenter Server ti presenta varie opzioni di CPU, memoria e archiviazione per la tua istanza. Nuove opzioni sono rese disponibili regolarmente, quindi controlla il catalogo {{site.data.keyword.cloud_notm}} per le ultime informazioni sulla disponibilità.

{{site.data.keyword.cloud_notm}} distribuisce la tua istanza vCenter Server utilizzando tre VLAN: una pubblica e due private. La VLAN pubblica è connessa a interfacce doppie da 10 GbE ed è in gran parte riservata per l'uso, a tua discrezione, della connettività pubblica o del tunneling per le distribuzioni del tuo carico di lavoro. Tuttavia, al momento della distribuzione, una coppia di Gateway dei servizi edge NSX viene distribuita sulla VLAN pubblica per consentire ad alcuni servizi aggiuntivi di connettersi alla rete pubblica per scopi di licenza e fatturazione. Le VLAN private sono connesse a interfacce doppie da 10 GbE separate: la prima VLAN privata viene utilizzata per le comunicazioni di gestione e VTEP NSX, mentre la seconda viene utilizzata per vMotion e per il traffico di archiviazione NFS.

Il provisioning delle istanze VMware può essere eseguito in 35 diversi {{site.data.keyword.CloudDataCents_notm}}. {{site.data.keyword.cloud_notm}} esegue il provisioning di nuovi data center di volta in volta. Controlla il catalogo {{site.data.keyword.cloud_notm}} per l'elenco più aggiornato delle ubicazioni disponibili.

### Distribuzione delle istanze
{: #under_the_hood-inst-deploy}

Quando ordini una nuova istanza VMware vCenter, scegli la sua ubicazione e la sua specifica. {{site.data.keyword.vmwaresolutions_short}} utilizza quindi il tuo nome utente e la tua chiave API {{site.data.keyword.cloud_notm}} selezionati in precedenza per orchestrare l'intero processo di ordinazione, installazione e configurazione del tuo ambiente di virtualizzazione. Questo include:

1. Ordine di VLAN e sottoreti per la rete.
2. Ordine di {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} con vSphere Hypervisor installato.
3. Distribuzione e configurazione di VMware vCenter Server con Platform Services Controller integrato, VMware NSX Manager, Controller e Gateway dei servizi edge.
4. Ordine e configurazione dell'archiviazione del tuo cluster, tra cui VMware vSAN o l'archiviazione Endurance {{site.data.keyword.cloud_notm}}.
5. Distribuzione di un componente di gestione IBM chiamato IBM CloudDriver.
6. Distribuzione e configurazione di tutti i servizi aggiuntivi che hai selezionato per la tua istanza.
7. Convalida dell'installazione e della configurazione dell'ambiente.

Selezioni il {{site.data.keyword.CloudDataCent_notm}} in cui vuoi eseguire il provisioning della tua istanza. Se l'hardware è disponibile nel {{site.data.keyword.CloudDataCent_notm}} che hai selezionato, il processo di provisioning delle istanze richiede in genere meno di 24 ore.

Una volta eseguito il provisioning della tua istanza, se sei connesso al tuo account {{site.data.keyword.cloud_notm}} tramite una VPN, puoi connetterti al tuo vCenter Server direttamente dal browser web della tua workstation.

In genere, i componenti dell'istanza sono accessibili dai loro nomi host anziché dai loro indirizzi IP. Per poter eseguire la connessione e l'autenticazione con vCenter, devi assicurarti che il nome host di vCenter e PSC (Platform Services Controller) possa essere risolto dalla tua workstation aggiungendolo al file host della workstation come mostrato nell'Elenco 1. Puoi trovare il nome host e l'indirizzo IP nella console {{site.data.keyword.vmwaresolutions_short}}, nella scheda **Riepilogo** della tua istanza. Potresti anche voler aggiungere i nomi host e gli indirizzi IP dei tuoi host vSphere al tuo file host.

*Elenco 1. File host*

<pre># vCenter e PSC (Platform Services Controller) del sito di Dallas
10.208.85.196  vcenter-dallas.dallas.example.com
# Host del sito di Dallas
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

Dopo che la tua istanza è stata distribuita, puoi gestirla dalla console. Le funzionalità di gestione comprendono la possibilità di effettuare ognuna delle seguenti operazioni:

* Distribuire e rimuovere nodi dal tuo cluster
* Distribuire e rimuovere cluster aggiuntivi nello stesso data center e pod o in data center e pod alternativi
* Distribuire e rimuovere servizi aggiuntivi per la tua istanza
* Eseguire l'upgrade di alcune edizioni di licenza per la tua istanza

La console {{site.data.keyword.vmwaresolutions_short}} fornisce una vista dettagliata di ciascuna delle tue istanze vCenter Server. Per ogni istanza, la scheda **Riepilogo** include un link alla console vCenter e altri dettagli sui componenti dell'istanza e di gestione. La scheda **Infrastruttura** mostra i dettagli sui cluster, gli host, l'archiviazione e la rete dell'istanza e ti consente di aggiungere o rimuovere cluster, host e archiviazione. Nella scheda **Aggiorna e applica patch**, puoi eseguire l'upgrade di alcune edizioni di licenza. Nella scheda **Servizi**, puoi visualizzare e gestire i servizi aggiuntivi distribuiti per la tua istanza. La scheda **Cronologia distribuzione** mostra una cronologia di tutte le azioni eseguite sulla tua istanza.

## Componenti di IBM Cloud for VMware Solutions
{: #under_the_hood-comp}

Vari componenti diversi operano insieme per consentire il provisioning e la gestione del tuo ambiente. La maggior parte di questi componenti viene distribuita nel tuo account {{site.data.keyword.cloud_notm}}. Poiché la soluzione dipende dalla combinazione di tutti questi componenti, non devi modificare o annullare alcuno di questi componenti dal tuo account {{site.data.keyword.cloud_notm}}. Il modo corretto per rimuovere un'istanza in esecuzione consiste nell'utilizzare la console anziché annullare i singoli componenti.

Sebbene si tratti di un ambiente di virtualizzazione integrato, i costi dei vari componenti di virtualizzazione (come le licenze VMware), componenti dell'infrastruttura (server bare metal, VLAN, sottoreti e archiviazione) e componenti di gestione sono dettagliati nella fattura che ricevi da {{site.data.keyword.cloud_notm}}.

### Console IBM Cloud for VMware Solutions
{: #under_the_hood-console}

Accedi alla [console {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external} per creare e gestire le tue istanze. Questa parte della soluzione è responsabile dell'ordine e del provisioning iniziale del tuo ambiente e anche della sua gestione in corso. Le tue istanze distribuite comunicano con la console utilizzando la rete privata di {{site.data.keyword.cloud_notm}}.

### Componente IBM CloudBuilder
{: #under_the_hood-ibm-cb}

Quando esegui il provisioning di una nuova istanza, la console distribuisce una VSI (virtual server instance) temporanea nel tuo account {{site.data.keyword.cloud_notm}}. Questo server virtuale è noto come IBM CloudBuilder. Esegue l'installazione e la configurazione di tutti i componenti dell'istanza e la convalida dell'ambiente. Una volta completato il provisioning, CloudBuilder viene eliminato.

### Componente IBM CloudDriver
{: #under_the_hood-ibm-cd}

Proprio come CloudBuilder, IBM CloudDriver è una VSI (virtual server instance) temporanea distribuita nel tuo account {{site.data.keyword.cloud_notm}} per eseguire le operazioni successive sulla tua istanza. Viene distribuito secondo necessità per configurare o rimuovere host, cluster, archiviazione o servizi nella tua istanza.

### Componenti VMware
{: #under_the_hood-vmware-comp}

Per tutte le istanze, vSphere Hypervisor è installato sui server bare metal. {{site.data.keyword.cloud_notm}} distribuisce quindi un dispositivo vCenter Server Appliance con PSC (Platform Services Controller) integrato, un NSX Manager, tre controller NSX e due coppie di gateway dei servizi edge NSX nel cluster di gestione VMware.

### Componenti aggiuntivi
{: #under_the_hood-add-comp}

A seconda della tua scelta, una VSI Microsoft Windows o due macchine virtuali Microsoft Windows vengono distribuite insieme o all'interno del tuo cluster come server Active Directory per i componenti di gestione. Puoi facoltativamente aggiungere i tuoi propri server Active Directory come ulteriori origini di identità per l'accesso alla gestione.

Indipendentemente da come scegli di fornire la continuità delle operazioni di business per i tuoi carichi di lavoro, {{site.data.keyword.cloud_notm}} consiglia vivamente di eseguire il backup dei componenti di gestione della tua istanza. La console {{site.data.keyword.vmwaresolutions_short}} ti consente di distribuire un server di backup IBM Spectrum Protect Plus integrato o un server di backup Veeam Backup & Replication insieme alla tua istanza. Questi servizi di backup possono essere utilizzati come parte di una [soluzione di backup completa](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup) per la tua istanza.

### Licenze
{: #under_the_hood-licenses}

{{site.data.keyword.cloud_notm}} fornisce diverse licenze VMware (come vCenter Server e NSX), che vengono installate nella tua istanza e fatturate sul tuo account {{site.data.keyword.cloud_notm}}.

## Architettura di rete di IBM Cloud for VMware Solutions
{: #under_the_hood-network}

L'istanza vCenter Server si connette a una VLAN pubblica per l'utilizzo con i tuoi carichi di lavoro distribuiti. La VLAN pubblica è in gran parte riservata per il tuo uso a tua discrezione, ma una coppia di Gateway di servizi edge NSX è connessa alla VLAN pubblica consentendo ad alcuni servizi aggiuntivi di comunicare in uscita per scopi di licenza e fatturazione. È possibile distribuire un'istanza senza utilizzare la rete pubblica, nel qual caso non tutti i servizi aggiuntivi sono supportati e potresti dover fornire un proxy web per abilitare l'uso di determinati servizi aggiuntivi.

La tua istanza vCenter Server ha due VLAN private che vengono collegate insieme sull'interfaccia di rete privata per i tuoi hypervisor. La prima VLAN privata viene utilizzata per la connettività di gestione (ad esempio per le comunicazioni di vCenter con gli hypervisor) e da NSX per il tunneling di tutto il traffico VXLAN per i tuoi carichi di lavoro distribuiti. La seconda VLAN privata viene utilizzata per vMotion e per il traffico di archiviazione. Il traffico di archiviazione può essere un protocollo NFS o vSAN.

{{site.data.keyword.cloud_notm}} fornisce alcuni servizi aggiuntivi su queste VLAN private. I tuoi server Active Directory comunicano con i server DNS {{site.data.keyword.cloud_notm}} sulla VLAN di gestione privata. I tuoi host e altri componenti comunicano con i server NTP {{site.data.keyword.cloud_notm}} sulla VLAN di gestione privata. I componenti IBM CloudBuilder e CloudDriver comunicano con la console {{site.data.keyword.vmwaresolutions_short}} utilizzando anche questa VLAN. I tuoi host si connettono all'archiviazione Endurance {{site.data.keyword.cloud_notm}} sulla VLAN di archiviazione privata.

### Connessione alla tua istanza
{: #under_the_hood-connect-inst}

Hai diverse opzioni per stabilire la connessione alle tue istanze. Puoi connetterti direttamente agli indirizzi IP privati nella tua istanza (ad esempio, vCenter) utilizzando la [VPN {{site.data.keyword.cloud_notm}}](https://www.softlayer.com/VPN-Access){:external}. Puoi anche ordinare i [dispositivi di rete {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/network-appliances){:external} e i [firewall hardware o virtuali {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/network-security) quali FortiGate e vSRX per il tuo account. {{site.data.keyword.cloud_notm}} offre anche dei [link diretti](https://www.ibm.com/cloud/direct-link){:external} tra la rete e le VLAN nel tuo account {{site.data.keyword.cloud_notm}}.

Per accedere alle tue VM distribuite, puoi applicare gli indirizzi IP pubblici direttamente alle VM. Tuttavia, puoi utilizzare anche le funzionalità dei dispositivi di rete e firewall {{site.data.keyword.cloud_notm}} per configurare un accesso pubblico più sicuro alle tue VM utilizzando NAT e firewall. Puoi anche distribuire i server Edge NSX e utilizzare questi server per configurare la connettività VPN o NAT per le tue VM.

## Conclusione
{: #under_the_hood-conclusion}

In questa esercitazione, hai appreso le funzionalità di base di {{site.data.keyword.vmwaresolutions_short}} per la distribuzione e la gestione di ambienti di virtualizzazione VMware standardizzati nel cloud pubblico. Poiché puoi eseguire il provisioning di questi ambienti in tempi rapidissimi, puoi concentrare i tuoi sforzi sulla distribuzione delle tue applicazioni e soluzioni su di essi e sulla connessione dei cloud per il ripristino di emergenza o l'alta disponibilità.

Abbiamo esplorato i vari componenti che vengono distribuiti nel tuo account {{site.data.keyword.cloud_notm}}, che sono mostrati nel tuo estratto conto di {{site.data.keyword.cloud_notm}} e operano insieme per mantenere in esecuzione il tuo ambiente. Infine, abbiamo considerato l'architettura di rete della soluzione insieme ad alcune opzioni per stabilire la connettività con l'ambiente, utilizzando varie opzioni di connettività sicure per mantenere le comunicazioni private o utilizzando varie opzioni per la connettività Internet pubblica.

Ora che hai una panoramica chiara di tutto ciò che devi sapere per iniziare, vai avanti e distribuisci subito il tuo prossimo ambiente di virtualizzazione VMware su {{site.data.keyword.cloud_notm}}.

## Link correlati
{: #under_the_hood-related}

* [Introduzione](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [Architettura di VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
