---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Preparazione dell'ambiente di installazione
{: #hcxclient-planning-prep-install}

L'installazione di VMware HCX on IBM Cloud ha i seguenti requisiti software:
* vSphere 5.5 U3 o vSphere 6.0u2 o superiore.
* Se viene utilizzato NSX, la versione 6.2.2 o superiore. NSX è obbligatorio per la migrazione della politica.
* Per utilizzare il vMotion tra cloud, si applicano le stesse limitazioni dell'affinità tra i cloud come se fossero in loco. Per ulteriori informazioni, consulta [VMware EVC and CPU Compatibility FAQ](https://kb.vmware.com/s/article/1005764).

## Configurazione della connettività di rete
{: #hcxclient-planning-config-net}

HCX deve attraversare internet pubblico e le linee private e connettersi ai componenti del data center, come ad esempio le reti, gli switch e i gruppi di porte.
* [Requisiti di accesso alla porta](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req) elenca le porte che devono essere aperte in modo che i dispositivi virtuali HCX possano essere installati correttamente.
* Sia l'ambiente vSphere in loco che l'ambiente cloud VCS HCX devono consentire la sincronizzazione dell'orologio NTP (Network Time Protocol) con i dispositivi in loco vSphere e i dispositivi VCS HCX. La porta UDP 123 deve essere accessibile alle reti e ai dispositivi virtuali HCX.

## Ambiente in loco
{: #hcxclient-planning-on-prem-env}

Prima di installare HCX, verifica che il tuo ambiente possa supportare le attività che desideri eseguire. L'ambiente in loco deve supportare le seguenti attività prima che possa essere installato HCX.
* Virtual Center con vSphere 5.5 Aggiornamento 3 o 6.0 Aggiornamento 2.
* Le funzioni di migrazione della politica e vMotion richiedono NSX versione 6.2.2 o superiore.
* Un account del servizio vSphere con il ruolo di sistema di amministratore vCenter Server assegnato.
* Nel vCenter, lo spazio disco necessario per l'installazione dei dispositivi HCX.
* Indirizzi IP sufficienti per le VM in loco di cui è stato eseguito il provisioning durante l'installazione.
* Porte e firewall aperti come richiesto e documentato nei requisiti di accesso alla porta.
* Se il server SSO (single sign-on) è remoto, devono essere identificati l'URL del vCenter, il server SSO esterno o il PSC (Platform Services Controller) che esegue il servizio di ricerca esterno. Quando l'HCX Manager viene registrato con il vCenter, deve essere fornito questo URL.
* Se un vCenter non dispone di una propria istanza interna del servizio di ricerca, potrebbe essere per uno dei seguenti motivi:
  * vCenter 6.0u2 esegue un PSC (Platform Services Controller) esterno.
  * Il vCenter è nella modalità di collegamento (in cui il vCenter secondario utilizza il servizio SSO dal vCenter primario o da un servizio SSO esterno).

## Verifica dell'ambiente di installazione di livello 2
{: #hcxclient-planning-verify-layer-2-inst}

L'estensione della rete di livello 2 ha i seguenti requisiti:
* Un vSphere Enterprise Plus Edition.
* Il vSphere vCenter deve soddisfare i seguenti requisiti per supportare l'estensione di livello 2:
  * Licenza di vSphere Enterprise Plus
  * È necessario un vDS (vSphere Distributed Switch). Lo switch distribuito è disponibile con vSphere Enterprise Plus Edition.
  * Quando installato, il dispositivo del servizio del concentratore di livello 2 in loco deve avere accesso a una porta vNIC e a tutte le VLAN per essere esteso.
  * Se la rete deve essere estesa su internet pubblico o su una VPN (su un percorso alternativo), la VM (Virtual Machine) L2C in VCS richiede un indirizzo IP. L'indirizzo IP remoto è obbligatorio per configurare il concentratore di livello 2.
  * Se vuoi più concentratori di livello 2, ognuno di essi deve avere un indirizzo IP in loco e nel cloud.

## Pianificazione pre-distribuzione
{: #hcxclient-planning-predepl}

Molto del tempo impiegato nella distribuzione HCX è in fase pre-distribuzione. Mentre è normale che il completamento dei progetti di migrazione dei sistemi informatici richieda mesi e anche anni, HCX consente un'esecuzione della migrazione in tempi brevi e un avvio immediato della connettività di rete al cloud dopo la distribuzione.

Poiché la distribuzione di HCX per un cliente a livello aziendale di norma coinvolge team di sicurezza, rete, archiviazione e infrastruttura vSphere, ha senso coinvolgere tali team nel modello di verifica (POC, Proof Of Concept), se possibile. Una gestione efficace del progetto e un coinvolgimento in fase iniziale delle parti interessate è di importanza critica per garantire l'ottenimento della velocità di distribuzione e operativa di HCX.

## Come evitare la paralisi dell'analisi
{: #hcxclient-planning-avoiding}

Molti degli ostacoli e buona parte del tempo necessario per la migrazione di una VM (Virtual Machine) o di un gruppo di VM sono da imputare alla necessità di modificare parti dell'ambiente applicativo, alla progettazione di tali modifiche e alla pianificazione del tempo di inattività necessario per apportare tali modifiche. Dopo che le modifiche sono state apportate, diventa difficile ripristinare lo stato ad esse antecedente, contribuendo ulteriormente alla paralisi dell'analisi. Provare a cogliere tutti gli aspetti della migrazione, coordinando i diversi team e cambiando le parti interessate più importanti può ritardare il progetto.

HCX consente la migrazione tra istanze vSphere di una VM o di un gruppo di VM che
rappresenta un'applicazione composita parziale o completa, senza alcuna
modifica all'applicazione. Per tale motivo, ripristinare uno stato antecedente a una migrazione significa
riportare le VM dove si trovavano o riestendere le reti. Ciò rende non necessaria un'ampia parte della pianificazione della migrazione e consente un certo parallelismo nel processo di pianificazione. Dopo la selezione delle applicazioni da spostare e la creazione di una progettazione di rete di alto livello, le applicazioni possono iniziare la migrazione con una configurazione minima sull'istanza cloud mentre progettazione e connettività di rete finali vengono elaborate.

## Reti estese
{: #hcxclient-planning-stretched-net}

I componenti di estensione della rete della flotta HCX sono molto stabili. Ponendo il caso di uno
specifico cliente con più di 20 VLAN estese nell'ambito della VLAN {{site.data.keyword.cloud}} da 1 Gbps condivisa con altro traffico e tunnel di migrazione HCX, non si rilevano problemi applicativi da attribuire alla rete. I collegamenti di rete sono attivi per più di 6 mesi, in questo modo.

Sono state aggiunte e rimosse ulteriori reti estese senza alcun problema. Anche scegliere un {{site.data.keyword.CloudDataCent_notm}} che è vicino (< 6 ms di latenza per questo specifico cliente) contribuisce alla stabilità della rete, in un contesto in cui quest'ultima è estesa. Lasciare le reti estese attive a lungo termine non dovrebbe essere un fattore negativo nella tua progettazione, visto che disponi di una larghezza di banda sufficiente e di una latenza abbastanza bassa per le tue applicazioni.

## Ciclo di vita della migrazione
{: #hcxclient-planning-mig-lifecycle}

Le seguenti sezioni descrivono le fasi in un tipico ciclo di vita di migrazione HCX, indicando dove i flussi di lavoro possono essere eseguiti in parallelo.

## Inventario vSphere
{: #hcxclient-planning-vsphere-planning}

- Valutazione non dettagliata delle VM in un'applicazione da migrare. Una valutazione di questo tipo implica una comprensione delle VM che partecipano in un'applicazione senza però scendere nei dettagli.
- Se intendi migrare molte VM e la larghezza di banda di rete è limitata tra i siti di origine e cloud, raggruppa ulteriormente le VM in base alla VLAN o alla VXLAN, se NSX viene utilizzato all'origine. Ciò consente un piano di migrazione HCX a cascata in cui i gruppi di VM, in base alla VLAN, vengono migrati e le reti L2 su cui si trovano vengono estese solo fino al punto di rilascio delle VLAN.

Ciò significa che per il gruppo iniziale di reti estese L2 correlate è possibile annullare l'estensione solo quando la progettazione di rete lato cloud è finalizzata e distribuita. Annullare l'estensione comporta il passaggio (swing) dello specifico traffico VXLAN in modo che venga ora instradato tramite l'infrastruttura NSX dell'istanza cloud.

## Configurazione della rete base di riferimento
{: #hcxclient-planning-baseline-net-config}

Crea una rete di perimetro protetta nell'istanza vSphere lato cloud. Ciò di norma consiste in un dispositivo Edge o DLR NSX. Se utilizzi l'instradamento di prossimità HCX, non è necessario creare alcuna regola del firewall o topologia di uplink poiché è un'operazione che può essere completata in un secondo momento o contemporaneamente senza alcuna ripercussione sul traffico L2 esteso.

## Estensione di rete
{: #hcxclient-planning-net-extension}

Estendere la rete significa semplicemente prendere la VLAN o VXLAN esistente dall'ambiente vSphere di origine, rappresentata da un gruppo di porte vDS (virtual distributed switch), ed estenderla a una VXLAN NSX sul lato cloud di HCX.

## Test pre-flight
{: #hcxclient-planning-preflight-tests}

I test pre-flight comportano l'esecuzione di una migrazione HCX sia con vMotion sia con la funzione
di migrazione in blocco per stabilire una velocità di trasferimento base di riferimento.

## Migrazione di applicazioni non di produzione
{: #hcxclient-planning-mig-non-prod-apps}

La migrazione delle VM inizia con le fasi pianificate di VM meno critiche. Sviluppo, test e così via utilizzano la connettività internet per la migrazione
e il traffico L2 esteso.

## La progettazione e l'implementazione della rete cloud inizia
{: #hcxclient-planning-cloud-net-begins}

Mentre le migrazioni continuano, le progettazioni di rete lato cloud sono
finalizzate e implementate all'interno dell'istanza vSphere lato cloud.

## Ulteriori considerazioni sulla connettività di rete
{: #hcxclient-planning-connect-considerations}

Mentre le migrazioni continuano, la connettività di rete WAN privata
viene ordinata poiché di solito occorrono dalle poche settimane a mesi perché
venga stabilita con il provider cloud. Dopo che la connettività di rete privata è
stata completata, HCX può essere configurato per utilizzare sia il collegamento di rete privato dedicato
che internet per la migrazione e il traffico L2 esteso.

## Server fisici
{: #hcxclient-planning-physical-servers}

Quando l'obiettivo è la migrazione del data center nel cloud, qualsiasi server fisico
che interagisce con le VM in fase di migrazione può essere valutato per la migrazione in {{site.data.keyword.cloud_notm}} come una VM (P2V), bare metal o rimanere all'origine. Se il server fisico deve rimanere all'origine, e HCX verrà utilizzato solo durante la migrazione finché non viene stabilita una rete dedicata, è importante comprendere se risiede su qualsiasi rete estesa nel cloud
con HCX. In questo scenario, HCX sta consentendo la migrazione nel cloud non solo delle VM ma dell'intera sottorete.

Per rimuovere HCX alla fine della migrazione, la sottorete non può esistere nell'origine e nella
destinazione se deve essere mantenuta la connessione tra i dispositivi fisici e le
VM migrate. Questo implica che qualsiasi dispositivo fisico lasciato indietro al sito di origine che
esiste sulle reti L2 estese deve essere migrato a un'altra sottorete di rete di cui sarebbe possibile
l'instradamento al lato cloud. L'accezione a ciò è l'eventuale utilizzo di qualche altra tecnologia L2 estesa.
come ad esempio la VPN NSX L2, per sostituire gli endpoint L2 estesi HCX.

## Migra le applicazioni di produzione e complesse
{: #hcxclient-planning-mig-prod-complex-app}

Le VM con VMDK multiwriter condivisi quali Oracle RAC o MS Exchange /
cluster SQL o VM con associazioni di dispositivi raw sono esempi di VM che richiedono
ulteriori considerazioni prima della migrazione.

## Passaggio (swing) di rete
{: #hcxclient-planning-net-swing}

Il passaggio (swing) di rete si verifica dopo che l'evacuazione delle VM sulle reti lato
di origine è stata completata e la progettazione/implementazione di rete è stata completata
sul lato cloud. La configurazione di HCX per annullare l'estensione delle reti correlate alle VM completate nei cicli di migrazione consente alle VM migrate di instradare il traffico di rete utilizzando l'infrastruttura NSX lato cloud.

## Piattaforme client supportate
{: #hcxclient-planning-client-platforms}

Per l'estensione di rete, sono supportati solo i gruppi di porte con un vDS (virtual distributed
switch) vSphere. Ciò implica anche che gli host ESXi autonomi non sono supportati poiché puoi avere solo un vDS quando gli host ESXi sono gestiti da vCenter.
- vSphere 5.1 (riga di comando solo per vCenter 5.1 tramite la API)
- vSphere 5.5 (IU client web supportata su vCenter 5.5u3 e successive)
- vSphere 6.0
- vSphere 6.5 (vDS deve essere a un livello 6.0)

## Piattaforme cloud supportate
{: #hcxclient-planning-cloud-platforms}

Il provisioning del lato cloud HCX viene eseguito dall'automazione {{site.data.keyword.cloud_notm}}.

## Opzioni di connettività
{: #hcxclient-planning-connect-options}

### Connettività HCX standard
{: #hcxclient-planning-standard-connect}

Come è distribuita dall'automazione {{site.data.keyword.vmwaresolutions_short}}, l'installazione del lato cloud
HCX è configurata per stabilire una connessione sull'internet pubblico per impostazione predefinita.

## Link correlati
{: #hcxclient-planning-related}

* [Glossario di componenti e termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Distribuzione client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Rete di servizi in loco HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrazioni VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitoraggio di parametri e componenti](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
