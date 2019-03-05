---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Estensione di rete e migrazione della macchina virtuale
{: #vcshcx-stretching}

## Estensione di rete
{: #vcshcx-network-stretching}

### Concetti e prassi ottimali per l'estensione di rete
{: #vcshcx-stretching-best-practices-network}

La rete lato client è collegata alla VXLAN lato cloud da una sofisticata VPN multitunnel che consiste in tecnologia HCX proprietaria. Non è basata su NSX ma funziona con NSX e ne estende la capacità. Questo processo è controllato dall'IU (interfaccia utente) web vCenter lato client e automatizza la distribuzione e l'attivazione di entrambi gli endpoint sul lato client e su quello cloud.La selezione della rete da estendere viene eseguito singolarmente o in batch.

Inoltre, come parte del flusso di lavoro di estensione di rete, NSX sul lato cloud è tenuto a creare una VXLAN che viene quindi connessa a un'interfaccia creta sul dispositivo L3 lato cloud specificato (DLR o ESG lasciato in uno stato di non connesso) e il dispositivo L2C lato cloud.

Quando migri una specifica applicazione, tutte le reti utilizzate dalle macchine virtuali (VM, Virtual Machine) applicabili di norma devono essere estese fino all'istanza {{site.data.keyword.cloud}}.

Perché di norma e non sempre? Può essere vantaggioso disconnettere del traffico specifico dal lato client dopo la migrazione della VM. Un esempio sono i client di backup guest VM, che possono causare un elevato utilizzo della larghezza di banda quando sono spostati al cloud. Il client di backup in-guest non è necessario quando la VM viene migrata e viene selezionato automaticamente da un backup a livello di blocco più moderno sul lato cloud.

Invece di accedere a ciascuna VM per disattivare la pianificazione di backup del client in-guest, la mancata connessione dell'adattatore di rete di backup del client (se viene utilizzata la rete di backup) causa una mancata riuscita del backup  Questa è una situazione temporanea finché non sarà possibile raggiungere tutte le VM post-migrazione per disabilitare il client di backup in-guest.

La larghezza di banda di una singola L2C è teoricamente di 4 Gbps, tuttavia, questo può essere il limite per tutte le rete estese in una singola coppia L2C e non può essere raggiunto da una singola rete estesa. Una singola rete estesa può raggiungere ~1 Gbps, a condizione che la larghezza di banda sottostante assegnata sia sufficiente e che la latenza sia bassa (<~10 ms).

### Procedura per estendere una rete
{: #vcshcx-stretching-process-stretch}

Per estendere una rete (VLAN o VXLAN) con HCX, completa la seguente procedura dall'IU web vCenter lato client.

1. Per la selezione singola di gruppi di porta, vai alla scheda **Networks** nell'IU web vCenter, fai clic con il pulsante destro del mouse sulla rete da estendere e seleziona **Hybridity Actions-> Extend Networks to the Cloud**.
2. Seleziona il dispositivo L3 lato cloud a cui stabilire la connessione e il dispositivo L2C che verrà utilizzato. Immetti il gateway predefinito e la maschera di subnet correnti in formato CIDR.
3. Fai clic su **Stretch** nella parte inferiore dello schermo per avviare il flusso di lavoro di estensione della rete.

Lo stato di avanzamento della rete viene monitorato nel riquadro delle attività client di vCenter.

### Opzione Proximity Routing (Instradamento di prossimità)
{: #vcshcx-stretching-prox-routing}

Senza alcun tipo di ottimizzazione dell'instradamento, le reti estese eseguono l'instradamento nuovamente verso il lato client per qualsiasi accesso L3. Questo effetto, detto "tromboning", introduce un pattern di traffico inefficiente poiché i pacchetti devono muoversi avanti e indietro tra il client (origine) e il cloud anche per i casi in cui sia la VM di origine che quella di destinazione si trovano all'interno del cloud. La funzione Proximity Routing di HCX è stata progettata per risolvere questo problema e l'uscita di dati di traffico locale.

## vMotion
{: #vcshcx-stretching-vmotion}

La funzionalità vMotion in HCX estende la funzionalità di vSphere vMotion di operare su diverse versioni di vSphere e separare i domini SSO e diversi tipi di connettività di rete in internet. HCX presume che la rete che utilizza per stabilire connessioni non sia protetta e sposta sempre il traffico servendosi di tunnel crittografati, indipendentemente dal tipo di connettività.

### Concetti e prassi ottimali per vMotion
{: #vcshcx-stretching-best-practices-vmotion}

HCX è essenzialmente un proxy bidirezionale di vMotion. Ogni istanza di HCX emula un singolo host ESXi nel data center vSphere, al di fuori di qualsiasi cluster che sia esso stesso in posizione “frontale” per il componente della flotta gateway cloud (CGW). È presente un host proxy per ogni sito HCX collegato al sito attualmente visualizzato. Quando viene avviato un vMotion su un host remoto, l'host ESXi locale eseguirà il vMotion di tale VM all'host ESXi proxy locale in posizione frontale per il CGW per sta anche mantenendo un tunnel crittografato con il CGW sul lato remoto.

Al tempo stesso, viene avviato un vMotion dal proxy ESXi remoto all'host ESXi fisico vSphere di destinazione, quando riceve dati dal CGW di origine attraverso il tunnel. Quando si utilizza vMotion, a differenza dell'opzione di migrazione in blocco, viene eseguita solo una singola operazione di migrazione di VM per volta. Per tale motivo, per notevoli quantità di VM da migrare, se ne consiglia l'utilizzo solo laddove il tempo di inattività non è un'opzione oppure il riavvio della VM comporta un rischio. Tuttavia, come per vMotion standard, la VM può essere attiva durante il processo.

È stato osservato che un singolo vMotion raggiungerà circa ~1,7 Gbps sulla LAN e da 300 a 400 Mbps sulla WAN tramite l'ottimizzatore WAN. Questo non significa che 1,7 Gbps sulla LAN equivalgono a 400 Mbps sulla LAN ma si tratta semplicemente dei valori massimi osservati per l'ambiente. L'ambiente su cui è stata fatta questa osservazione consisteva di una rete vMotion LAN da 10 GB e un uplink internet da 1GB, condivisa con il traffico web di produzione.

Utilizza vMotion laddove:
- L'arresto o l'avvio della VM è problematico oppure il tempo di attività può essere lungo e il suo arresto introdurrebbe dei rischi.
- Qualsiasi applicazione di tipo cluster che richiede UUID disco, come ad esempio i cluster Oracle RAC. vMotion non modifica gli UUID disco sulla destinazione.
- Desideri spostare una singola VM il più velocemente possibile.
- La migrazione pianificata non è richiesta.

### Operazione
{: #vcshcx-stretching-operation}

Utilizza il portale di snap-in dell'IU web HCX o i menu di estensione contestuali del client web vSphere per avviare un vMotion tra cloud. In entrambi i casi, viene aperta la stessa procedura guidata di migrazione. Per i menu contestuali, solo una singola VM è selezionata per le operazioni di migrazione. Per il portale, possono essere selezionate più VM.

La migrazione inversa delle VM è possibile solo dal portale dell'IU web che utilizza la casella di spunta **Reverse migration** nella procedura guidata HCX Migration.

## Migrazione in blocco
{: #vcshcx-stretching-bulk-mig}

### Concetti e prassi ottimali per la migrazione in blocco
{: #vcshcx-stretching-best-practices-bulk-mig}

La funzionalità di migrazione in blocco di HCX utilizza la replica vSphere per migrare i dati del disco durante la ricreazione della VM sull'istanza HCX vSphere di destinazione. Una migrazione di una VM comporta il seguente flusso di lavoro:
- Creazione di una nuova VM sul lato di destinazione e sui relativi dischi virtuali corrispondenti.
- Replica dei dati VM sulla nuova VM. La replica viene avviata non appena la procedura guidata viene completata, indipendentemente dalla pianificazione di commutazione.
- Spegnimento della VM originale.
- Durante il periodo di spegnimento, si verifica la replica finale di qualsiasi modifica di dati.
- Accensione della nuova VM sul lato di destinazione.
- Rinominazione e spostamento della VM originale nella cartella sul cloud.

Sono di seguito indicati i vantaggi offerti dalla migrazione in blocco su vMotion:
- Migrazione di molte VM contemporaneamente.
- Un utilizzo della larghezza di banda più congruente. vMotion può generare delle fluttuazioni nell'utilizzo della larghezza di banda visibili come picchi e depressioni negli strumenti di monitoraggio di rete o nel'IU di ottimizzazione WAN.
- Utilizza la migrazione in blocco per ottenere un utilizzo complessivo maggiore di una capacità di larghezza di banda di rete rispetto a quella di cui è capace un singolo vMotion.
- Pianifica la migrazione in blocco per passare alle VM appena migrate durante una finestra di interruzione pianificata.
- Puoi consentire la migrazione di VM che attualmente stanno utilizzando delle funzioni di CPU virtuale che sono diverse dal lato cloud, laddove vMotion non riesce.

Sono di seguito indicati gli svantaggi comportati dalla migrazione in blocco su vMotion:
- La migrazione delle singole VM è molto più lenta che con vMotion.
- La VM è soggetta a un tempo di inattività per un breve lasso di tempo mentre la nuova VM clone viene attivata sul lato di destinazione.
- Le VM che dipendono dall'ordinamento dei dischi e dagli UUID disco (Oracle RAC) possono avere dei problemi e avere dei dischi che vengono visualizzati differentemente quando gli UID vengono modificati, cosa che potrebbe modificare i percorsi del sistema operativi ai dispositivi di disco virtuale.

## Prassi ottimali dei tipi di migrazione
{: #vcshcx-stretching-mig-type-best-practices}

### Cluster di dischi condivisi
{: #vcshcx-stretching-shared-disk-clusters}

I cluster Oracle RAC, MS Exchange e MS-SQL sono esempi di applicazioni in cui due o più VM partecipano a un cluster che richiede un disco condiviso tra tutte le VM o tutti i nodi cluster. L'indicatore multiwriter VMware deve essere abilitato su tutti i nodi VM per i dischi che fanno parte del cluster di applicazioni (dischi virtuali non del sistema operativo). Le VM con l'indicatore multiwriter abilitato per qualsiasi disco virtuale non sono supportate.

Migrazione di un cluster abilitato al disco virtuale multiwriter:
- Utilizza vMotion come disco VM originale e le associazioni UUID vengono mantenute.
- Il cluster rimane attivo in uno stato degradato (nodo singolo) durante la migrazione.
- Il cluster subisce un tempo di inattività prima dell'avvio della migrazione e dopo il completamento della migrazione per riassemblare la configurazione multiwriter nei nodi VM del cluster.

Completa la seguente procedura per migrare un cluster abilitato al disco multiwriter:
1. Disattiva il cluster e tutti i nodi in base alla prassi ottimale per l'applicazione.
2. Annota l'ordine dei dischi, se l'applicazione lo richiede, in ogni VM del nodo per i dischi virtuali configurati multiwriter.
3. Per Oracle e qualsiasi altra applicazione che utilizza la funzione UUID di disco virtuale, accedi a uno specifico ESXi ed esegui il comando `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` per ottenere l'UUID di ciascun file disco virtuale che richiede l'indicatore multiwriter impostato per il cluster.
  Ciò è necessario se la prassi ottimale allinea gli ordini dei dischi con il modo in cui il percorso viene visualizzato nel sistema operativo. vMotion può riordinare i dischi (disk1, disk2, disk3) ma gli UUID rimangono gli stessi.
  Utilizza le informazioni di associazione di UUID e disco annotate per ricreare l'ordine di denominazione dei dischi. ID SCSI quando la migrazione viene completata, se necessario. L'applicazione dovrebbe funzionare in entrambi i modi. Ciò viene utilizzato nei casi in cui un'istanza Oracle abbia molti dischi virtuali associati per la risoluzione dei problemi dell'applicazione.
4. Rimuovi i dischi virtuali da tutti i nodi VM cluster, fatta eccezione per quello ritenuto primario.
5. Rimuovi l'indicatore multiwriter dal nodo cluster VM primario che dovrebbe essere, al momento, il solo a possedere i dischi del cluster.
6. Riattiva il nodo cluster primario, se necessario, per un tempo di inattività minimo.
7. Migra tutti i nodi cluster con vMotion. Migrare prima il cluster primario e tutti gli altri nodi vengono migrati quando sono spenti.
8. Quando il disco primario proprietario del nodo completa la migrazione, spegnilo.
9. Se necessario, riassocia l'ordine dei dischi con i corretti UUID disco e ID SCSI. La riassociazione non è necessaria perché l'applicazione funzioni.
10. Riabilita l'indicatore multiwriter sul nodo primario.
11. Avvia il nodo primario e verifica il funzionamento.
12. Associa il disco/ abilita l'indicatore multiwriter su tutte le altre VM del nodo cluster ed eseguine l'accensione.
13. Verifica il funzionamento degli altri nodi del cluster.

### VM generali
{: #vcshcx-stretching-general-vms}

Una volta creata la fiducia nel funzionamento di HCX, è necessario utilizzare la migrazione in blocco. La migrazione in blocco è necessaria quando sono interessate delle applicazioni ridondanti. Ad esempio, i server web e laddove devono essere migrate molte centinaia o migliaia di VM.

### VM che utilizzano NAS collegato direttamente
{: #vcshcx-stretching-vms-direct-nas}

NFS viene di solito utilizzato per condividere i dati tra molti server, come ad esempio il contenuto di server web. iSCSI può essere utilizzato nei nodi VM formati da un cluster di applicazioni come ad esempio email o RDBMS ed è di norma più sensibile alla latenza di NFS.

In entrambi i casi, se è possibile tenere bassa la latenza a {{site.data.keyword.CloudDataCent_notm}} (< ~7 ms per iSCSI e qualunque cosa l'applicazione tolleri per NFS) e si consente il funzionamento dell'applicazione con una larghezza di banda di ~1 Gbps o meno, la rete NAS può essere estesa con HCX in un'ubicazione {{site.data.keyword.cloud_notm}}. Dopo l'esecuzione di tale operazione, le VM possono essere migrate/sottoposte a vMotion con HCX normalmente.

Dopo la migrazione, è possibile eseguire il mirroring del volumi iSCSI con il sistema operativo a un'altra soluzione di archiviazione cloud locale e i dati NFS possono essere replicati a qualsiasi soluzione nel cloud. Le considerazioni sono:
- Latenza (iSCSI o tolleranza dell'applicazione per NFS)
- Larghezza di banda (~1 Gbps per ogni rete estesa)
- Larghezza di banda di collegamento sottostante

Seguendo il ciclo di vita della migrazione, assicurati di eseguire dei test con le applicazioni di sviluppo o preparazione prima di provare con la produzione. QoS può essere adottato per il traffico tunnel sottostante (udp 500 / 4500) tra i dispositivi HCX L2C che portano reti L2 estese sensibili alla latenza.

## Passaggio (swing) di rete
{: #vcshcx-stretching-network-swing}

Se l'obiettivo è l'evacuazione del data center in {{site.data.keyword.cloud_notm}}, il penultimo passo prima della rimozione di HCX è il passaggio (swing) di rete. Il passaggio (swing) di rete consegue una migrazione della subnet di rete che ospita le VM migrate dal data center di origine su una rete di sovrapposizione NSX all'interno di {{site.data.keyword.cloud_notm}}.

Il passaggio (swing) di rete comporta quanto segue:
- Verifica che la rete venga evacuata da tutti i carichi di lavoro e che qualsiasi dispositivo collegato in rete non VM venga spostato a un'altra rete, migrato funzionalmente al cloud o dichiarato obsoleto.
- Verifica che qualsiasi topologia NSX o topologia di rete che supporta {{site.data.keyword.cloud_notm}} sia completata per supportare il passaggio (swing) di rete. Ad esempio, i firewall e i protocolli di instradamento dinamico.
- Esegui un flusso di lavoro di rete di annullamento dell'estensione HCX nell'IU e seleziona il dispositivo NSX di instradamento appropriato per prendere il controllo del gateway predefinito delle reti non estese.
- Esegui qualsiasi modifica di instradamento esterna, che può includere: l'inserimento di instradamento modificato per le reti che erano state migrate, la rimozione degli instradamenti al sito di origine per la rete migrata e la garanzia dell'instradamento a tale subnet migrata nella WAN per le applicazioni non migrate, se necessario.
- Una verifica da parte del proprietario dell'applicazione delle applicazioni migrate da tutti i punti di accesso possibili: internet, intranet e VPN.

Considerazioni relative al passaggio (swing) di rete di una specifica applicazione che ha tutte le VM completamente migrate al cloud:
se stai utilizzando un vyatta sul lato della rete privata per inserire instradamenti nel tuo cluster MPLS e un tunnel ai dispositivi di instradamento edge su MPLS per evitare lo spazio IP {{site.data.keyword.cloud_notm}}. Hai il tuo account impostato con un VRF {{site.data.keyword.cloud_notm}}. Alcune delle applicazioni si trovano dietro un vIP (virtual IP) con un carico bilanciato di rete. Questi vIP si trovano sulla tua subnet di proprietà che si trova su un F5 virtuale dietro vyatta. Mentre il rendere noto un instradamento più specifico in MPLS per le reti di cui viene eseguito il passaggio (swing) a {{site.data.keyword.cloud_notm}} tramite HCX funziona correttamente per altre reti, non funziona per i singoli vIP quando viene inserito un instradamento /32.

Soluzione: è prassi comune che i fornitori WAN escludano mediante filtro gli instradamenti /32 resi noti. Collabora con il fornitore WAN per consentirlo.

Sono di seguito riportate delle considerazioni e delle implicazioni:
- Le applicazioni che condividono subnet, vLAN e VXLAN devono essere spostate insieme.
- Le applicazioni dietro un programma di bilanciamento del carico che utilizza un IP instradabile interno possono richiedere delle modifiche dell'instradamento se non possono essere spostate insieme oppure se non è desiderabile farlo. Ad esempio, se c'è un rischio percepito eccessivo dal coinvolgimento di troppe applicazioni in un singolo passaggio (swing).
- Gli amministratori VMware, gli amministratori di rete (compresi i clienti/fornitori WAN) e i proprietari delle applicazioni devono essere coinvolti. Anche se non è previsto che le modifiche si ripercuotano su uno specifico sistema o una specifica apparecchiatura di rete.

## Link correlati
{: #vcshcx-stretching-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html) 
