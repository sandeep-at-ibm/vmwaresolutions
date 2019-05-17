---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-22"

subcollection: vmware-solutions


---

# Pianificazione pre-distribuzione
{: #vcshcx-planning}

Molto del tempo impiegato nella distribuzione HCX è in fase pre-distribuzione. Mentre è normale che il completamento dei progetti di migrazione dei sistemi informatici richieda mesi e anche anni, HCX consente un'esecuzione della migrazione in tempi molto brevi e un avvio immediato della connettività di rete al cloud dopo la distribuzione.

Poiché la distribuzione di HCX per un cliente a livello aziendale di norma coinvolge team di sicurezza, rete, archiviazione e infrastruttura vSphere, ha senso coinvolgere tali team nel modello di verifica (POC, Proof Of Concept), se possibile. Una gestione efficace del progetto e un coinvolgimento in fase iniziale delle parti interessate è di importanza critica per garantire l'ottenimento della velocità di distribuzione e operativa di HCX.

## Come evitare la paralisi dell'analisi
{: #vcshcx-planning-avoiding}

Molti degli ostacoli e buona parte del tempo necessario per la migrazione di una VM (Virtual Machine) o di un gruppo di VM sono da imputare alla necessità di modificare parti dell'ambiente applicativo, alla progettazione di tali modifiche e alla pianificazione del tempo di inattività necessario per apportare tali modifiche. Dopo che le modifiche sono state apportate, diventa difficile ripristinare lo stato ad esse antecedente, contribuendo ulteriormente alla paralisi dell'analisi. Provare a cogliere tutti gli aspetti della migrazione, coordinando i diversi team e cambiando le parti interessate più importanti può ritardare il progetto.

HCX consente la migrazione tra istanze vSphere di una VM o di un gruppo di VM che
rappresenta un'applicazione composita parziale o completa, senza alcuna
modifica all'applicazione. Per tale motivo, ripristinare uno stato antecedente a una migrazione significa
riportare le VM dove si trovavano o riestendere le reti. Ciò rende non necessaria un'ampia parte della pianificazione della migrazione e consente un certo parallelismo nel processo di pianificazione. Dopo la selezione delle applicazioni da spostare e la creazione di una progettazione di rete di alto livello, le applicazioni possono iniziare la migrazione con una configurazione minima sull'istanza cloud mentre progettazione e connettività di rete finali vengono elaborate.

## Reti estese
{: #vcshcx-planning-stretched-net}

I componenti di estensione della rete della flotta HCX sono molto stabili. Ponendo il caso di uno
specifico cliente con più di 20 VLAN estese nell'ambito della VLAN {{site.data.keyword.cloud}} da 1 Gbps condivisa con altro traffico e tunnel di migrazione HCX, non si rilevano problemi applicativi da attribuire alla rete. I collegamenti di rete sono attivi per più di 6 mesi, in questo modo.

Sono state aggiunte e rimosse ulteriori reti estese senza alcun problema. Anche scegliere un {{site.data.keyword.CloudDataCent_notm}} in stretta prossimità (< 6ms di latenza per questo specifico cliente)
contribuisce alla stabilità della rete, in un contesto in cui quest'ultima è estesa. Lasciare le reti estese attive a lungo termine non dovrebbe essere un fattore negativo nella tua progettazione, visto che disponi di una larghezza di banda sufficiente e di una latenza abbastanza bassa per le tue applicazioni.

## Ciclo di vita della migrazione
{: #vcshcx-planning-mig-lifecycle}

Le seguenti sezioni descrivono le fasi in un tipico ciclo di vita di migrazione HCX, indicando dove i flussi di lavoro possono essere eseguiti in parallelo.

## Inventario vSphere
{: #vcshcx-planning-vsphere-planning}

- Valutazione non dettagliata delle VM in un'applicazione da migrare. Una valutazione di questo tipo implica una comprensione delle VM che partecipano in un'applicazione senza però scendere nei dettagli.
- Se intendi migrare molte VM e la larghezza di banda di rete è limitata tra i siti di origine e cloud, raggruppa ulteriormente le VM in base alla VLAN o alla VXLAN, se NSX viene utilizzato all'origine. Ciò consente un piano di migrazione HCX a cascata in cui i gruppi di VM, in base alla VLAN, vengono migrati e le reti L2 su cui si trovano vengono estese solo fino al punto di rilascio delle VLAN.

Ciò significa che per il gruppo iniziale di reti estese L2 correlate è possibile annullare l'estensione solo quando la progettazione di rete lato cloud è finalizzata e distribuita. Annullare l'estensione comporta il passaggio (swing) dello specifico traffico VXLAN in modo che venga ora instradato tramite l'infrastruttura NSX dell'istanza cloud.

## Configurazione della rete base di riferimento
{: #vcshcx-planning-baseline-net-config}

Crea una rete di perimetro protetta nell'istanza vSphere lato cloud. Ciò di norma consiste in un dispositivo Edge o DLR NSX. Se utilizzi l'instradamento di prossimità HCX, non è necessario creare alcuna regola del firewall o topologia di uplink poiché è un'operazione che può essere completata in un secondo momento o contemporaneamente senza alcuna ripercussione sul traffico L2 esteso.

## 	Estensione di rete
{: #vcshcx-planning-net-extension}

Estendere la rete significa semplicemente prendere la VLAN o VXLAN esistente dall'ambiente vSphere di origine, rappresentata da un gruppo di porte vDS (virtual distributed switch), ed estenderla a una VXLAN NSX sul lato cloud di HCX.

## Test pre-flight
{: #vcshcx-planning-preflight-tests}

I test pre-flight comportano l'esecuzione di una migrazione HCX sia con vMotion sia con la funzione
di migrazione in blocco per stabilire una velocità di trasferimento base di riferimento.

## Migrazione di applicazioni non di produzione
{: #vcshcx-planning-mig-non-prod-apps}

A questo punto, la migrazione delle VM inizia con le fasi pianificate di VM meno critiche. Sviluppo, test e così via utilizzano la connettività internet per la migrazione
e il traffico L2 esteso.

## La progettazione e l'implementazione della rete cloud inizia
{: #vcshcx-planning-cloud-net-begins}

Mentre le migrazioni continuano, le progettazioni di rete lato cloud sono
finalizzate e implementate all'interno dell'istanza vSphere lato cloud.

## Ulteriori considerazioni sulla connettività di rete
{: #vcshcx-planning-connect-considerations}

Mentre le migrazioni continuano, la connettività di rete WAN privata
viene ordinata poiché di solito occorrono dalle poche settimane a mesi perché
venga stabilita con il provider cloud. Dopo che la connettività di rete privata è
stata completata, HCX può essere configurato per utilizzare sia il collegamento di rete privato dedicato
che internet per la migrazione e il traffico L2 esteso.

## Server fisici
{: #vcshcx-planning-physical-servers}

Quando l'obiettivo è la migrazione del data center nel cloud, qualsiasi server fisico
che interagisce con le VM in fase di migrazione può essere valutato per la migrazione in {{site.data.keyword.cloud_notm}} come una VM (P2V), bare metal o rimanere all'origine. Se il server fisico
deve rimanere all'origine, e HCX verrà utilizzato solo durante la migrazione finché non viene
stabilita una rete dedicata, è importante comprendere se risiede su qualsiasi rete estesa nel cloud
con HCX. In questo scenario, HCX sta consentendo la migrazione nel cloud non solo delle VM ma dell'intera subnet.

Per rimuovere HCX alla fine della migrazione, la subnet non può esistere nell'origine e nella
destinazione se deve essere mantenuta la connessione tra i dispositivi fisici e le
VM migrate. Questo implica che qualsiasi dispositivo fisico lasciato indietro al sito di origine che
esiste sulle reti L2 estese deve essere migrato a un'altra subnet di rete di cui sarebbe possibile
l'instradamento al lato cloud. L'accezione a ciò è l'eventuale utilizzo di qualche altra tecnologia L2 estesa.
come ad esempio la VPN NSX L2, per sostituire gli endpoint L2 estesi HCX.

## Migra le applicazioni di produzione e complesse
{: #vcshcx-planning-mig-prod-complex-app}

Le VM con VMDK multiwriter condivisi quali Oracle RAC o MS Exchange /
cluster SQL o VM con associazioni di dispositivi raw sono esempi di VM che richiedono
ulteriori considerazioni prima della migrazione.

## Passaggio (swing) di rete
{: #vcshcx-planning-net-swing}

Il passaggio (swing) di rete si verifica dopo che l'evacuazione delle VM sulle reti lato
di origine è stata completata e la progettazione/implementazione di rete è stata completata
sul lato cloud. La configurazione di HCX per annullare l'estensione delle reti correlate alle
VM completate nei cicli di migrazione consente alle VM migrate di instradare il traffico di rete utilizzando
l'infrastruttura NSX lato cloud.

## Piattaforme client supportate
{: #vcshcx-planning-client-platforms}

Per l'estensione di rete, sono supportati solo i gruppi di porte con un vDS (virtual distributed
switch) vSphere. Ciò implica anche che gli host ESXi autonomi non sono supportati poiché puoi avere solo un
vDS quando gli host ESXi sono gestiti da vCenter.
- vSphere 5.1 (riga di comando solo per vCenter 5.1 tramite la API)
- vSphere 5.5 (IU client web supportata su vCenter 5.5u3 e successive)
- vSphere 6.0
- vSphere 6.5 (vDS deve essere a un livello 6.0)

## Piattaforme cloud supportate
{: #vcshcx-planning-cloud-platforms}

Il provisioning del lato cloud HCX viene eseguito dall'automazione {{site.data.keyword.cloud_notm}}.

## Opzioni di connettività
{: #vcshcx-planning-connect-options}

### Connettività HCX standard
{: #vcshcx-planning-standard-connect}

Come è distribuita dall'automazione {{site.data.keyword.vmwaresolutions_short}}, l'installazione del lato cloud
HCX è configurata per stabilire una connessione sull'internet pubblico per impostazione predefinita.

### Connettività facoltativa
{: #vcshcx-planning-optional-connect}

La connessione sulla rete privata {{site.data.keyword.cloud_notm}} è selezionabile al momento dell'ordinazione.

## Link correlati
{: #vcshcx-planning-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro) 
