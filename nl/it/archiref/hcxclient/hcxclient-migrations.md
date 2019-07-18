---

copyright:

  years:  2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Migrazioni VMware Hybrid Cloud
{: #hcxclient-migrations}

Dopo il provisioning e l'estensione della rete di servizi HCX e delle estensioni di rete, il passo successivo è la migrazione delle VM.

Ci sono tre tipi di migrazioni:
  - vMotion
  - Migrazione in blocco
  - Migrazione di tipo cold (a freddo)

## Operazione
{: #hcxclient-migrations-operation}

Utilizza il portale di snap-in dell'IU web HCX o i menu di estensione contestuali del client web vSphere per avviare un vMotion tra cloud. In entrambi i casi, viene aperta la stessa procedura guidata di migrazione. Per i menu contestuali, solo una singola VM è selezionata per le operazioni di migrazione. Per il portale, possono essere selezionate più VM.

La migrazione inversa delle VM è possibile solo dal portale dell'IU web che utilizza la casella di spunta **Reverse migration** nella procedura guidata HCX Migration.

## vMotion
{: #hcxclient-migrations-vmotion}

La funzionalità vMotion in HCX estende la funzionalità di vSphere vMotion di operare su diverse versioni di vSphere e separare i domini SSO e diversi tipi di connettività di rete in internet. HCX presume che la rete utilizzata per stabilire connessioni non sia protetta e sposta sempre il traffico servendosi di tunnel crittografati, indipendentemente dal tipo di connettività.

### Concetti e prassi ottimali per vMotion
{: #hcxclient-migrations-best-practices-vmotion}

HCX è essenzialmente un proxy bidirezionale di vMotion. Ogni istanza di HCX emula un singolo host ESXi nel data center vSphere, al di fuori di qualsiasi cluster che sia esso stesso in posizione “frontale” per il componente della flotta gateway cloud (CGW). È presente un host proxy per ogni sito HCX collegato al sito attualmente visualizzato. Quando viene avviato un vMotion su un host remoto, l'host ESXi locale eseguirà il vMotion di tale VM all'host ESXi proxy locale in posizione frontale per il CGW per sta anche mantenendo un tunnel crittografato con il CGW sul lato remoto.

Al tempo stesso, viene avviata una migrazione vMotion dal proxy ESXi remoto all'host ESXi fisico vSphere di destinazione mentre riceve dati dal CGW di origine attraverso il tunnel. Quando si utilizza vMotion, a differenza dell'opzione di migrazione in blocco, viene eseguita solo una singola operazione di migrazione di VM per volta. Per tale motivo, per la migrazione di molte VM, consigliamo di utilizzare vMotion solo quando il tempo di inattività non è un'opzione o se il riavvio della VM comporta un rischio. Tuttavia, come per vMotion standard, la VM può essere attiva durante il processo.

È stato osservato che un singolo vMotion raggiungerà circa 1,7 Gbps sulla LAN e da 300 a 400 Mbps sulla WAN tramite l'ottimizzatore WAN. Questo non significa che 1,7 Gbps sulla LAN equivalgono a 400 Mbps sulla WAN tramite l'ottimizzatore WAN ma, piuttosto, che questi massimi sono stati osservati su specifici ambienti. Un ambiente di questo tipo consisteva in una rete vMotion LAN di 10 GB e di un uplink internet di 1 GB, in condivisione con il traffico web di produzione.

Utilizza vMotion nei seguenti casi:
- L'arresto o l'avvio della VM è problematico oppure il tempo di attività può essere lungo e il suo arresto introdurrebbe dei rischi.
- Per qualsiasi applicazione di tipo cluster che richiede UUID disco, come ad esempio i cluster Oracle RAC. Nota che vMotion non modifica gli UUID disco sulla destinazione.
- Desideri spostare una singola VM il più velocemente possibile.
- La migrazione pianificata non è richiesta.

## Migrazione in blocco
{: #hcxclient-migrations-bulk-mig}

### Concetti e prassi ottimali per la migrazione in blocco
{: #hcxclient-migrations-best-practices-bulk-mig}

La funzionalità di migrazione in blocco di HCX utilizza la replica vSphere per migrare i dati del disco durante la ricreazione della VM sull'istanza HCX vSphere di destinazione. Una migrazione di una VM comporta il seguente flusso di lavoro:
- Creazione di una nuova VM sul lato di destinazione e sui relativi dischi virtuali corrispondenti.
- Replica dei dati VM sulla nuova VM. La replica viene avviata non appena la procedura guidata viene completata, indipendentemente dalla pianificazione di commutazione.
- Spegnimento della VM originale.
- Durante il periodo di spegnimento, si verifica la replica finale di qualsiasi modifica di dati.
- Accensione della nuova VM sul lato di destinazione.
- Ridenominazione e spostamento della VM originale nella cartella cloud in cui era stata spostata.

Sono di seguito indicati i vantaggi offerti dalla migrazione in blocco su vMotion:
- Migrazione di più VM simultaneamente.
- Un utilizzo della larghezza di banda più congruente. vMotion può generare delle fluttuazioni nell'utilizzo della larghezza di banda visibili come picchi e depressioni negli strumenti di monitoraggio di rete o nel'IU di ottimizzazione WAN.
- Utilizza la migrazione in blocco per ottenere un utilizzo complessivo maggiore di una capacità di larghezza di banda di rete rispetto a quella di cui è capace un singolo vMotion.
- Pianifica la migrazione in blocco per passare alle VM appena migrate durante una finestra di interruzione pianificata.
- Consenti la migrazione di VM che attualmente stanno utilizzando delle funzioni di CPU virtuale che sono diverse dal lato cloud. In questi casi, la migrazione vMotion potrebbe avere esito negativo.

Sono di seguito indicati gli svantaggi comportati dalla migrazione in blocco su vMotion:
- La migrazione delle singole VM è molto più lenta che con vMotion.
- La VM è soggetta a un tempo di inattività per un breve lasso di tempo mentre la nuova VM clone viene attivata sul lato di destinazione.
- Le VM che dipendono dall'ordinamento dei dischi e dagli UUID disco (Oracle RAC) possono avere dei problemi e avere dei dischi che vengono visualizzati differentemente quando gli UID vengono modificati, cosa che potrebbe modificare i percorsi del sistema operativi ai dispositivi di disco virtuale.

## Prassi ottimali dei tipi di migrazione
{: #hcxclient-migrations-mig-type-best-practices}

### Cluster di dischi condivisi
{: #hcxclient-migrations-shared-disk-clusters}

I cluster Oracle RAC, MS Exchange e MS-SQL sono esempi di applicazioni in cui due o più VM partecipano a un cluster che richiede un disco condiviso tra tutte le VM o tutti i nodi cluster. L'indicatore multiwriter VMware deve essere abilitato su tutti i nodi VM per i dischi che fanno parte del cluster di applicazioni (dischi virtuali non del sistema operativo). Le VM con l'indicatore multiwriter abilitato per qualsiasi disco virtuale non sono supportate.

Migrazione di un cluster abilitato al disco virtuale multiwriter:
- Utilizza vMotion come disco VM originale e le associazioni UUID vengono mantenute.
- Il cluster rimane attivo in uno stato degradato (nodo singolo) durante la migrazione.
- Il cluster subisce un tempo di inattività prima dell'avvio della migrazione e dopo il completamento della migrazione per riassemblare la configurazione multiwriter nelle VM del cluster.

Completa la seguente procedura per migrare un cluster abilitato al disco multiwriter:
1. Spegni il cluster e tutti i nodi in base alla prassi ottimale per l'applicazione.
2. Annota l'ordine dei dischi, se l'applicazione lo richiede, in ogni VM del nodo per i dischi virtuali configurati multiwriter.
3. Per Oracle e qualsiasi altra applicazione che utilizza la funzione UUID di disco virtuale, accedi a uno specifico ESXi ed esegui il comando `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` per ottenere l'UUID di ciascun file disco virtuale che richiede l'indicatore multiwriter impostato per il cluster.
  Ciò è necessario se la prassi ottimale allinea gli ordini dei dischi con il modo in cui il percorso viene visualizzato nel sistema operativo. vMotion può riordinare i dischi (disk1, disk2, disk3) ma gli UUID rimangono gli stessi.
  Quando la migrazione viene completata, utilizza l'UUID annotato per associare le informazioni sul disco, per creare nuovamente l'ordine di denominazione del disco e l'ID SCSI, se necessario. L'applicazione dovrebbe funzionare in entrambi i modi. Ciò viene utilizzato nei casi in cui un'istanza Oracle abbia molti dischi virtuali associati per la risoluzione dei problemi dell'applicazione.
4. Rimuovi i dischi virtuali da tutte le VM del cluster, fatta eccezione per quello ritenuto primario.
5. Rimuovi l'indicatore multiwriter dalla VM del cluster primario che dovrebbe essere, al momento, la sola a possedere i dischi del cluster.
6. Accendi il cluster primario, se necessario, per un tempo di inattività minimo.
7. Migra tutti i nodi cluster con vMotion. Migra prima il cluster primario. Migra tutti gli altri nodi dopo che sono stati spenti.
8. Quando il disco primario proprietario del nodo completa la migrazione, spegnilo.
9. Se necessario, riassocia l'ordine dei dischi con i corretti UUID disco e ID SCSI. La riassociazione non è necessaria perché l'applicazione funzioni.
10. Riabilita l'indicatore multiwriter sul nodo primario.
11. Avvia il nodo primario e verifica il funzionamento.
12. Associa il disco/ abilita l'indicatore multiwriter su tutte le altre VM del cluster ed eseguine l'accensione.
13. Verifica il restante funzionamento del cluster.

### VM generali
{: #hcxclient-migrations-general-vms}

Una volta creata la fiducia nel funzionamento di HCX, è necessario utilizzare la migrazione in blocco. La migrazione in blocco è necessaria per le applicazioni ridondanti. Ad esempio, i server web e laddove devono essere migrate molte centinaia o migliaia di VM.

### VM che utilizzano NAS collegato direttamente
{: #hcxclient-migrations-vms-direct-nas}

NFS viene di solito utilizzato per condividere i dati tra molti server, come ad esempio il contenuto di server web. iSCSI può essere utilizzato nei nodi VM formati da un cluster di applicazioni, come ad esempio email o RDBMS, ed è di norma più sensibile alla latenza di NFS.

In entrambi i casi, se è possibile tenere bassa la latenza a {{site.data.keyword.CloudDataCent_notm}} (< ~7 ms per iSCSI e qualunque cosa l'applicazione tolleri per NFS) e si consente il funzionamento dell'applicazione con una larghezza di banda di ~1 Gbps o meno, la rete NAS può essere estesa con HCX in un'ubicazione {{site.data.keyword.cloud_notm}}. Dopo l'esecuzione di tale operazione, le VM possono essere migrate o sottoposte a vMotion con HCX.

Dopo la migrazione, è possibile eseguire il mirroring del volumi iSCSI con il sistema operativo a un'altra soluzione di archiviazione cloud locale e i dati NFS possono essere replicati a qualsiasi soluzione cloud. Le considerazioni sono:
- Latenza (iSCSI o tolleranza dell'applicazione per NFS)
- Larghezza di banda (~1 Gbps per ogni rete estesa)
- Larghezza di banda di collegamento sottostante

Dopo il ciclo di vita della migrazione, esegui dei test con le applicazioni di sviluppo o preparazione prima di provare sulla produzione. QoS può essere adottato per il traffico tunnel sottostante (udp 500 / 4500) tra i dispositivi HCX L2C che supportano reti L2 estese sensibili alla latenza.

## Passaggio (swing) di rete
{: #hcxclient-migrations-network-swing}

Se l'obiettivo è l'evacuazione del data center in {{site.data.keyword.cloud_notm}}, il penultimo passo prima della rimozione di HCX è il passaggio (swing) di rete. Il passaggio (swing) di rete consegue una migrazione della sottorete di rete che ospita le VM migrate dal data center di origine su una rete di sovrapposizione NSX all'interno di {{site.data.keyword.cloud_notm}}.

Il passaggio (swing) di rete comporta la seguente procedura:
- Verifica che dalla rete vengano evacuati tutti i carichi di lavoro e che qualsiasi dispositivo collegato in rete non VM venga spostato a un'altra rete, migrato funzionalmente al cloud o dichiarato obsoleto.
- Verifica che qualsiasi topologia NSX o topologia di rete che supporta {{site.data.keyword.cloud_notm}} sia completata per supportare il passaggio (swing) di rete. Ad esempio, i firewall e i protocolli di instradamento dinamico.
- Esegui un flusso di lavoro di rete di annullamento dell'estensione HCX nell'IU e seleziona il dispositivo NSX di instradamento appropriato per prendere il controllo del gateway predefinito della rete non estesa.
- Esegui qualsiasi modifica di instradamento esterna, che può includere: l'inserimento di instradamento modificato per le reti che erano state migrate, la rimozione delle rotte al sito di origine dalla rete migrata e la verifica che la rotta a tale sottorete migrata nella WAN stia ancora funzionando per le applicazioni che non erano state migrate.
- Una verifica da parte del proprietario dell'applicazione delle applicazioni migrate da tutti i punti di accesso possibili: internet, intranet e VPN.

Diciamo che desideri eseguire il passaggio (swing) di rete di una specifica applicazione che ha tutte le VM migrate al cloud. Ad esempio:
- Stai utilizzando un vyatta sul lato della rete privata per inserire rotte nel tuo cloud MPLS e per eseguire il tunneling ai dispositivi di instradamento edge su MPLS in modo da poter evitare lo spazio IP {{site.data.keyword.cloud_notm}}.
- Hai il tuo account impostato con un VRF {{site.data.keyword.cloud_notm}}.
- Alcune applicazioni sono dietro un vIP (virtual IP) con un carico bilanciato di rete. Questi vIP si trovano sulla tua sottorete di proprietà che si trova su un F5 virtuale dietro vyatta.

Mentre l'aggiunta di un instradamento più specifico in MPLS per le reti di cui viene eseguito il passaggio (swing) a {{site.data.keyword.cloud_notm}} tramite HCX funziona correttamente per altre reti, non funziona per i singoli vIP perché si sta aggiungendo una rotta /32.

Soluzione: è prassi comune che i fornitori WAN escludano mediante filtro le rotte /32 che vengono aggiunte. Collabora con il fornitore WAN per consentirlo.

Sono di seguito riportate delle considerazioni e delle implicazioni:
- Le applicazioni che condividono sottorete, vLAN e VXLAN devono essere spostate insieme.
- Le applicazioni dietro un programma di bilanciamento del carico che utilizza un IP instradabile interno possono richiedere delle modifiche dell'instradamento se non possono essere spostate insieme oppure se non è desiderabile farlo. Ad esempio, se c'è un rischio percepito eccessivo dal coinvolgimento di troppe applicazioni in un singolo passaggio (swing).
- Gli amministratori VMware, gli amministratori di rete (compresi i clienti e i fornitori WAN) e i proprietari delle applicazioni devono essere coinvolti, anche se non è pianificato alcun impatto su uno specifico sistema o una specifica apparecchiatura di rete.

## Link correlati
{: #hcxclient-migrations-related}

* [Glossario di componenti e termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparazione dell'ambiente di installazione ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Distribuzione client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Rete di servizi in loco HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Monitoraggio di parametri e componenti](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
