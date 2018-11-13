---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine ed eliminazione della versione di prova a singolo nodo di VMware vCenter Server sulle istanze di IBM Cloud

La versione di prova a singolo nodo di VMware vCenter Server su {{site.data.keyword.cloud}} è un cloud privato ospitato a singolo tenant che fornisce lo stack VMware vSphere come servizio. Mentre l'ambiente gestito dal client viene normalmente distribuito con un minimo di tre nodi, questa versione di prova a singolo nodo fornisce un percorso a basso costo per sperimentare i vantaggi di un'implementazione cloud ibrida.

Questa versione di prova è ideale per una prova di utilizzo che illustra la velocità dell'automazione avanzata di IBM per la distribuzione iniziale e la facilità di spostamento di carichi di lavoro semplici non di produzione nel cloud. Utilizzando VMware Hybrid Cloud Extension (HCX), puoi estendere in modo sicuro la tua rete di data center in loco nel {{site.data.keyword.CloudDataCent_notm}} riducendo la complessità di rete della configurazione dell'interconnessione. HCX estrae le risorse di rete sottostanti per il tunnel tramite internet pubblicamente in modo da poter spostare facilmente i carichi di lavoro bidirezionalmente senza dover reinserire l'IP delle macchine virtuali (VMs). Con HCX, non c'è bisogno che VMware NSX sia installato in locale ed è compatibile con le versioni più vecchie di vSphere.  

La versione di prova a singolo nodo è solo per una prova di utilizzo. Non eseguire i carichi di lavoro di produzione su questo ambiente. Le funzioni di gestione come l'aggiunta o la rimozione degli host e dei cluster, l'ordine di ulteriori servizi di componenti aggiuntivi e l'applicazione degli aggiornamenti non sono supportate.
{:important}

Questa versione di prova è destinata ad essere utilizzata per un massimo di 90 giorni. Quando hai terminato con la versione di prova, puoi eliminare questo ambiente e quindi eseguire il provisioning di un ambiente ad alta disponibilità che soddisfi le tue esigenze di capacità. Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html).

## Specifiche tecniche per la versione di prova a singolo nodo per le istanze di vCenter Server

I seguenti componenti sono inclusi nella tua versione di prova a singolo nodo dell'istanza di vCenter Server:

La disponibilità e il prezzo delle configurazioni hardware standardizzate possono variare in base al {{site.data.keyword.CloudDataCent_notm}} selezionato per la distribuzione.
{:note}

### Bare Metal Server

Un processore Dual Intel Xeon Gold 5120 (28 core, 2.20 GHz) con 384 GB RAM.

### Rete

Vengono ordinati i seguenti componenti di rete:
*  Doppi uplink di rete privata e pubblica da 10 Gbps
*  Tre VLAN (Virtual LAN): una VLAN pubblica e due VLAN private
*  Una VXLAN (Virtual eXtensible LAN) con DLR (Distributed Logical Router) per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2). La VXLAN viene distribuita come topologia di instradamento di esempio, che puoi modificare, compilare o rimuovere. Puoi anche aggiungere zone di sicurezza collegando ulteriori VXLAN a nuove interfacce logiche sul DLR.
*  Due gateway dei servizi edge VMware NSX:
  * Un gateway dei servizi edge (ESG) VMware NSX sicuro dei servizi di gestione per il traffico di gestione HTTPS in uscita, distribuito da IBM come parte della tipologia di rete di gestione. Questo ESG viene utilizzato dalle VM di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione. Per ulteriori informazioni, vedi [Configurazione della rete per utilizzare l'ESG gestito dal cliente](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Non puoi accedere a questo ESG e non puoi usarlo. Se lo modifichi, potresti non essere in grado di gestire l'istanza vCenter Server with Hybridity Bundle dalla console {{site.data.keyword.vmwaresolutions_short}}. Inoltre, tieni presente che l'utilizzo di un firewall o la disabilitazione delle comunicazioni ESG ai componenti di gestione IBM esterni causerà l'inutilizzabilità di {{site.data.keyword.vmwaresolutions_short}}.
    {:important}
  * Un gateway dei servizi edge VMware NSX sicuro gestito dal cliente per il traffico del carico di lavoro HTTPS in uscita e in entrata, distribuito da IBM come template che puoi modificare per fornire l'accesso VPN o l'accesso pubblico. Per ulteriori informazioni, vedi [L'edge NSX gestito dal cliente rappresenta un rischio per la sicurezza?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

Per ulteriori informazioni sui componenti di rete ordinati quando si distribuisce il servizio HCX on {{site.data.keyword.cloud_notm}}, vedi [Panoramica di HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### VSI (Virtual Server Instance)

Vengono ordinate le seguenti VSI (Virtual Server Instance):

* Una VSI per IBM CloudBuilder, che viene arrestata al termine della distribuzione dell'istanza.
* Viene distribuita una VSI di Microsoft Windows Server per Microsoft Active Directory (AD) che può essere consultata. La VSI funziona come DNS per l'istanza in cui sono registrati gli host e le macchine virtuali.

### Licenze fornite da IBM e tariffe

Le seguenti licenze sono incluse nella tua versione di prova a singolo nodo dell'ordine dell'istanza di vCenter Server:

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

La versione di prova a singolo nodo delle istanze di vCenter Server non supporta BYOL (Bring Your Own License).
{:note}

Possono essere applicate ulteriori tariffe per supporto e servizi.

## Specifiche tecniche per HCX on IBM Cloud

Per informazioni sulle specifiche tecniche e sulle considerazioni per HCX su {{site.data.keyword.cloud_notm}}, consulta [Panoramica di VMware HCX on IBM Cloud](../services/hcx_considerations.html).

## Requisiti e pianificazione per ordinare la versione di prova a singolo nodo delle istanze di vCenter Server

Assicurati di completare le seguenti attività:
* L'account {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti per l'account {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).
*  Configura le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Gestione di account utente e impostazioni](../vmonic/useraccount.html).
* Controlla i requisiti del nome dell'istanza:  
 * Sono consentiti solo caratteri alfanumerici e trattini (-).
 * Il nome dell'istanza deve iniziare e terminare con un carattere alfanumerico.
 * La lunghezza massima del nome dell'istanza è di 10 caratteri.
 * Il nome dell'istanza deve essere univoco all'interno del tuo account.
* Controlla che il {{site.data.keyword.CloudDataCents_notm}} soddisfi i requisiti per l'infrastruttura fisica. Per ulteriori informazioni, consulta la sezione *Disponibilità di {{site.data.keyword.CloudDataCent_notm}}* in [Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_planning.html#ibm-cloud-data-center-availability).
<!--* Ensure the that you meet the following prerequisites for the on-premises HCX instance:
 * VMware vSphere and vCenter 5.5 or higher
 * The VMware HCX Manager must reside in the same security zone as the on-premises vSphere environment
 * The VMware HCX Manager must be able to reach the public Internet to update firewall rules to allow outbound traffic
 * The vSphere environment must have distributed switches-->

## Procedura per ordinare la versione di prova a singolo nodo delle istanze di vCenter Server

1. Nella pagina **Single-node Trial for VMware vCenter Server on  {{site.data.keyword.cloud_notm}}**, fai clic sulla scheda **vCenter Server** e quindi su **Continue**.
2. Nella pagina **Single-node Trial for VMware vCenter Server**, completa le istruzioni per richiedere un account dell'infrastruttura {{site.data.keyword.cloud_notm}} o fornisci i tuoi **Nome utente** e **Chiave API** esistenti e fai clic su **Retrieve**.
3. Immetti il nome dell'istanza.
4. Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.  

 Il {{site.data.keyword.CloudDataCent_notm}} è pre-selezionato. Seleziona un'ubicazione {{site.data.keyword.CloudDataCent_notm}} diversa, se necessario.
 {:note}
5. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza prima di effettuare l'ordine.
   1. Esamina le impostazioni per l'istanza.
   2. Esamina il costo stimato dell'istanza. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di ordinare l'istanza.
   4. Fai clic su **Fornitura**.

### Risultati

La distribuzione dell'istanza inizia automaticamente e viene ordinata la chiave di attivazione del servizio HCX on {{site.data.keyword.cloud_notm}}.

#### Processo di distribuzione per HCX on IBM Cloud

La distribuzione di HCX on {{site.data.keyword.cloud_notm}} è automatizzata. Le seguenti istruzioni vengono completate dal processo automatico di {{site.data.keyword.vmwaresolutions_short}}:
1. Dall'infrastruttura {{site.data.keyword.cloud_notm}}, vengono ordinate tre sottoreti per HCX:
   * Una sottorete portatile privata per la gestione HCX.
   * Una sottorete portatile privata per le interconnessioni HCX. Questa sottorete viene utilizzata se per **Tipo di interconnessione HCX** si seleziona l'opzione **Rete privata**.
   * Una sottorete portatile pubblica per l'attivazione e la manutenzione con VMware. Se per **Tipo di interconnessione HCX** si seleziona l'opzione **Rete pubblica**, questa sottorete viene utilizzata anche per le interconnessioni HCX.

   Gli indirizzi IP nelle sottoreti ordinate per HCX devono essere gestiti dall'automazione di VMware on {{site.data.keyword.cloud_notm}}. Questi indirizzi IP non possono essere assegnati alle risorse VMware, come VM ed Edge NSX, create da te. Se hai bisogno di ulteriori indirizzi IP per le tue risorse VMware, devi ordinare le tue proprie sottoreti da {{site.data.keyword.cloud_notm}}.
   {:important}
2. Se per il **Tipo di interconnessione HCX** è stata selezionata la **Rete privata**, viene creato un gruppo di porte denominato **SDDC-DPortGroup-HCX-Private** sul DVS (Distributed Virtual Switch) privato.
3. Viene ordinata una chiave di attivazione HCX da VMware.
4. Vengono creati tre pool di risorse e cartelle VM per HCX, necessari per interconnessioni HCX, componenti HCX locali e componenti HCX remoti.
5. Viene distribuita e configurata una coppia di gateway dei servizi edge (ESG) VMware NSX per il traffico di gestione HCX:
   * Le interfacce di uplink pubblico e privato vengono configurate utilizzando le sottoreti ordinate.
   * Gli ESG vengono configurati come una coppia di dispositivi edge di grandi dimensioni con l'alta disponibilità (HA) abilitata.
   * Le regole del firewall e le regole NAT (Network Address Translation) vengono configurate per consentire il traffico HTTPS in entrata e in uscita da e verso HCX Manager.
   * Vengono configurate le regole di bilanciamento del carico e i pool di risorse. Le regole e i pool di risorse sono utilizzati per inoltrare il traffico in entrata correlato a HCX ai dispositivi virtuali appropriati di HCX Manager, vCenter Server e PSC (Platform Services Controller).
   * Viene applicato un certificato SSL per crittografare il traffico HTTPS in entrata correlato a HCX che arriva tramite gli ESG.

   L'edge di gestione HCX è dedicato al traffico di gestione HCX tra i componenti HCX in loco e i componenti HCX lato cloud. Non modificare l'edge di gestione HCX o utilizzarlo per le estensioni di rete HCX. Crea, invece, edge separati per le estensioni di rete. Inoltre, l'utilizzo di un firewall o la disabilitazione delle comunicazioni dell'edge di gestione HCX ai componenti di gestione IBM privati o all'Internet pubblico potrebbe influire negativamente sulla funzionalità di HCX.
   {:important}

6. HCX Manager on {{site.data.keyword.cloud_notm}} viene distribuito, attivato, e configurato:
   * HCX Manager viene registrato con vCenter Server.
   * Vengono configurati HCX Manager, vCenter Server, PSC e NSX Manager.
   * Viene configurata la flotta HCX.
   * Vengono configurati i contenitori di distribuzione HCX locali e remoti.
7. Il nome host e l'indirizzo IP di HCX Manager vengono registrati con il server DNS di VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Visualizzazione dei dettagli dell'istanza

Puoi controllare lo stato della distribuzione visualizzando i dettagli dell'istanza. Per informazioni sulla visualizzazione dei dettagli dell'istanza, vedi:

* [Visualizzazione delle istanze vCenter Server](vc_viewinginstances.html)
* [Visualizzazione delle istanze VMware HCX on IBM Cloud in loco](../services/standalone_viewingserviceinstances.html)

Una volta che l'istanza è stata distribuita correttamente, i componenti descritti nelle sezioni *Specifiche tecniche* di questo argomento sono installati sulla tua piattaforma virtuale VMware e sull'HCX in loco sulla chiave di attivazione del servizio {{site.data.keyword.cloud_notm}} disponibile nell'HCX in loco nella pagina dei dettagli di {{site.data.keyword.cloud_notm}}.

Lo stato dell'istanza viene modificato in **Pronto per l'utilizzo** e ricevi una notifica per email.

### Operazioni successive

Configura il servizio HCX on {{site.data.keyword.cloud_notm}} e installa la chiave di attivazione in loco.

1. Individua la chiave di attivazione in loco nella pagina **Istanze distribuite**.
  1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** dal riquadro di navigazione a sinistra.
  2. Nella tabella **Istanze di vCenter Server**, controlla la colonna **Tipo** per individuare l'istanza della versione di prova a singolo nodo e prendi nota del nome dell'istanza.
  3. Scorri fino alla tabella **Istanze HCX in loco** e controlla la colonna **Nome** per individuare l'istanza che ha lo stesso nome dell'istanza a singolo nodo.
  4. Prendi nota della chiave nel campo **Chiave di attivazione**.
2. Vai a [VMware HCX](https://hcx.vmware.com/#/vm-documentation) e utilizza la chiave di attivazione per installare l'istanza in loco di VMware HCX on {{site.data.keyword.cloud_notm}} e completa il processo di configurazione. Per ulteriori informazioni, consulta *Procedura presto disponibile*.

Devi gestire i componenti dell'infrastruttura {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console.
Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console e il tuo ambiente potrebbe diventare instabile.
{:important}

## Procedura per eliminare la versione di prova a singolo nodo delle istanze di vCenter Server

Per rilasciare i componenti che hai ordinato in una versione di prova a singolo nodo dell'istanza vCenter Server, elimina l'istanza.

Per ulteriori informazioni, vedi [Eliminazione delle istanze vCenter Server](vc_deletinginstance.html).

### Link correlati

* [Registrazione di un account {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Glossario dei termini HCX](../services/hcx_glossary.html)
* [Documentazione di VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Panoramica di vCenter Server with Hybridity Bundle](vc_hybrid_overview.html)
* [Considerazioni sulla rete per le istanze vCenter Server with Hybridity Bundle](vc_hybrid_networkingonvcenterserver.html)
* [Ordine di istanze vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html)
