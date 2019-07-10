---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Monitoraggio di parametri e componenti
{: #hcxclient-monitoring}

## Utilizzo dell'ottimizzatore WAN per il monitoraggio
{: #hcxclient-monitoring-using-wan}

L'interfaccia di gestione per il dispositivo di ottimizzazione WAN Silver Peak distribuito come parte di HCX non è configurata. L'IU (interfaccia utente) web è uno strumento prezioso da utilizzare quando determini la tua velocità effettiva del traffico di base e limiti l'utilizzo della larghezza di banda di migrazione della rete.

Solo il traffico del tunnel WAN del gateway CGW HCX fluisce tramite il dispositivo ottimizzatore WAN. Non può pertanto monitorare il traffico L2 esteso.
{:note}

### Configurazione dell'IU
{: #hcxclient-monitoring-config-ui}

Al di fuori della configurazione di un indirizzo IP per l'interfaccia utente web,
non apportare modifiche alla configurazione del dispositivo dell'ottimizzatore WAN se non dietro indicazione dello staff di supporto {{site.data.keyword.IBM}} o VMware.

Per configurare l'IU web dell'ottimizzatore WAN:

1. Trova il dispositivo VM dell'ottimizzatore WAN nel client vCenter.
2. Apri una console alla VM che utilizza un client vCenter.
3. Nella console, fai clic su **F4** per configurare l'interfaccia di gestione.
4. Seleziona la configurazione di un IP statico.
5. Utilizza un indirizzo IP sul gateway predefinito e l'intervallo di IP portatili assegnato a {{site.data.keyword.cloud}} di gestione.
6. Fai clic su **Apply** nella schermata successiva per salvare.
7. Fai clic su edit settings per la VM dell'ottimizzatore WAN all'interno della console vCenter.
8. Seleziona **Connected at Power On** e **Connected for Network Adapter 1**.
9. Fai clic su **OK** per salvare.
10. Trova CGW-<xxx>-WANOPT in vCenter.
11. Modifica le impostazioni sulla VM.
12. Fai clic sulla casella di spunta per connettere l'adattatore di rete 1.
13. Fai clic su **OK**.
14. Vai all'indirizzo `https://<configured_WAN_OPT_IP>`.
15. Accedi con l'utente predefinito `admin` e la password `admin`.

Puoi ora utilizzare l'IU web dell'ottimizzatore WAN per monitorare le velocità di trasmissione e i rapporti di compressione e impostare le limitazioni della larghezza di banda.

### Limitazione della larghezza di banda della migrazione
{: #hcxclient-monitoring-mig-bandwidth}

Prima di migrare le VM, esegui una valutazione del collegamento di rete utilizzato. Lavora con gli ingegneri di rete per la rete che contiene l'istanza di origine di vSphere oppure esamina l'utilizzo del traffico settimanale e mensile. Limita la larghezza di banda disponibile per le migrazioni se tale traffico transita su un collegamento di importanza critica per la tua attività di business, soprattutto se tale collegamento è inferiore a 1 Gbps. Utilizza il lato con la larghezza di banda più limitata, che è di solito il lato client.

Esegui tale operazione quando distribuisci i componenti della flotta nell'IU client HCX, ma la post-distribuzione richiede che tu vada nell'IU dell'ottimizzatore WAN.

Le modifiche vanno perse se distribuisci CGW HCX dall'IU web HCX. Questo imposta i limiti di larghezza di banda solo per il traffico di migrazione. Il traffico L2 esteso non è interessato da questa impostazione.
{:note}

1. Accedi all'interfaccia Web dell'ottimizzatore WAN.
2. Dalla scheda **Configuration**, seleziona **Shaper** dal menu.
3. Nella casella **Max bandwidth**, imposta la larghezza di banda massima disponibile per il dispositivo dell'ottimizzatore WAN in Kbps. Non superare la larghezza di banda massima del collegamento WAN. Per impostare il valore in Mbps, moltiplica per 1.000. Per impostare il valore in Gbps, moltiplica per 1.000.000. Il valore predefinito è 10 Gbps (10.000.000 Kbps).
4. Fai clic su **Apply**.

Per la limitazione della larghezza di banda di L2 esteso, è possibile utilizzare
QoS per UDP 500 e 4500 per il traffico di tunnel tra i dispositivi L2C.

## Monitoraggio dei componenti HCX
{: #hcxclient-monitoring-hcx-comp}

Monitora i componenti HCX quali HCX Manager, il gateway cloud, l'ottimizzatore WAN e le operazioni di L2C (Layer 2 Concentrator) nei seguenti modi:

- Configura HCX Manager per inviare i log a un server syslog. Utilizza il programma di
utilità di gestione del dispositivo di HCX Manager per eseguire il comando `https://<hcxhostname or
IP>:9443`.
- Imposta un ping a una VM migrata prima del passaggio (swing) di rete per ciascuna rete L2 estesa.
- Monitora l'integrità della VM del componente HCX con VMware vRealize Operations
Manager o altri strumenti di monitoraggio di VM VMware.

## Utilizzo della larghezza di banda
{: #hcxclient-monitoring-band-use}

Utilizza i seguenti metodi per monitorare l'utilizzo della larghezza di banda e la latenza.

- Il traffico vMotion può essere eseguito più efficacemente utilizzando l'IU web dell'ottimizzatore WAN. L'ottimizzatore WAN
riduce notevolmente il traffico che passa sulla WAN e riduce la perdita di pacchetti inviando pacchetti ridondanti. Si è osservato che il tipico rapporto di larghezza di banda LAN-WAN utilizzato è circa 3:1 (350 Mbps LAN = 90-120Mbps WAN).
- La migrazione (in blocco) basata sulla replica delle VM all'interno di HCX produce uno spostamento delle VM con il thick provisioning. Mentre ciò non è desiderabile, l'IU dell'ottimizzatore WAN rivela un elevato rapporto tra utilizzo di LAN e WAN quando sposti dati del disco inutilizzati. Viceversa si osserva che, se vengono migrati dei dati non comprimibili, come ad esempio dei dati di DB e del contenuto multimediale, l'utilizzo della WAN è al suo massimo man mano che si approssima all'utilizzo della LAN.

Osservazioni:
- La migrazione vMotion di una VM all'interno di HCX non genera più velocità effettiva rispetto alla rete vMotion per un singolo host ESXi.
- Poiché la migrazione in blocco può avere più migrazioni in-flight simultaneamente, raggiunge un utilizzo della larghezza di banda
superiore a quello di una migrazione vMotion. Il rapporto osservato su un lato cliente con collegamento vMotion da 1 Gbps
agli host ESX era: Otto repliche = utilizzo della larghezza di banda di 1 vMotion.
- Lo spostamento di spazio vuoto su disco determina la visualizzazione di un elevato utilizzo della LAN con un rapporto elevato e, di conseguenza, un basso utilizzo della WAN. Nota: 1 Gbps sembra essere
il limite. In effetti, in questo specifico caso, la rete vMotion è capace solo di 1 Gbps, che è il collo di bottiglia.
- Migrazione vMotion di un DB Oracle da più TB. Con un collegamento WAN di 1 Gbps,
la limitazione è la rete vMotion di 1 Gbps.

## Traffico L2 (Layer 2) esteso
{: #hcxclient-monitoring-stretched-layer-2-traffic}

Il componente della flotta HCX L2C (Layer 2 Concentrator) ha una limitazione della larghezza di banda di circa 4 Gbps per tutto il traffico di rete L2 che l'attraversa. Le reti estese singolarmente hanno un limite di larghezza di banda di circa 1 Gbps o meno, a seconda del tipo di traffico. È possibile avere molte reti L2 estese in una singola coppia L2C (massimo teorico consentibile di
4096 reti per ogni coppia L2C). Mentre l'L2C è progettato per rilevare e proteggere piccoli flussi di traffico in modo che non siano sopraffatti dai flussi di grandi dimensioni nella stessa coppia L2C, può essere vantaggioso identificare se la situazione si sta verificando e attivare più L2C per aumentare la capacità di larghezza di banda complessiva.

La distribuzione di più L2C può anche essere vantaggiosa laddove esistano più percorsi tra il sito del cliente e {{site.data.keyword.cloud}}, come ad esempio un collegamento diretto e internet. Una singola rete non può essere resa ridondante né è possibile darle della larghezza di banda aumentata su più coppie L2C.

Monitora il traffico su tutte le interfacce che utilizzano la scheda Monitoring della VM L2C. Se la frequenza dati totale si sta avvicinando a 8 Gbps (4 Gbps input/output), prendi in considerazione l'aggiunta di un'altra coppia L2 e ridistribuisci le reti estese per un riequilibrio.

## Link correlati
{: #hcxclient-monitoring-related}

* [Glossario di componenti e termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparazione dell'ambiente di installazione](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Distribuzione client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Rete di servizi in loco HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrazioni VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
