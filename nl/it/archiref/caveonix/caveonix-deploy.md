---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modelli di distribuzione per Caveonix RiskForesight
{: #caveonix-deploy}

In questa sezione vengono descritti i modelli di distribuzione per Caveonix RiskForesight insieme al processo di installazione per l'installazione della soluzione.

Quando selezioni l'opzione {{site.data.keyword.vmwaresolutions_full}} RiskForesight, non devi seguire tutti i passi nella distribuzione poiché quelli iniziali sono automatizzati. Tuttavia, per una conoscenza completa della distribuzione e dell'architettura, e per coloro che vogliono eseguire un ridimensionamento incrementale della soluzione dopo la distribuzione iniziale, è richiesta una comprensione dettagliata.

L'installazione di RiskForesight consiste nei seguenti passi di livello superiore:

1. [Pianificazione iniziale e prerequisiti](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) – Comprensione e selezione di un'opzione di distribuzione, configurando DNS per fornire la risoluzione di FQDN/IP per i componenti dell'applicazione.
2. [Distribuzione della VM (Virtual Machine)](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) – Distribuzione delle VM (Virtual Machine) da un modello OVF. Sulla VM sono installati tutti i componenti dell'applicazione.
3. [Configurazione dell'applicazione](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) – Esecuzione dello script di configurazione Caveonix che configura il componente dell'applicazione su ciascuna delle VM.
4. [Impostazione dell'applicazione](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) – Impostazione del provider di servizi e di un tenant o un'organizzazione in modo che l'applicazione diventi accessibile per gli utenti.

L'installazione automatica esegue il provisioning di una singola VM e configura tutti i componenti dell'applicazione su tale VM.
{:note}

## Dimensionamento della distribuzione
{: #caveonix-deploy-sizing}

Il dimensionamento della distribuzione viene calcolato utilizzando i seguenti volumi.

Tabella 1. Volumi

|Tipo di dati	|Volume |
|---|---|
|Scansioni al giorno	|1 |
|Dati scansione (MB)	|20 |
|Dati log (MB)	|500 |
|Dati flusso (MB)	|200 |
|Dati asset (MB)	|46 |
|Archiviazione totale per ogni asset al giorno (MB)	|766 |
|Moltiplicatore di replica dati	|2 |
|Totale archiviazione indice per asset al giorno (MB)	|1532 |

Il moltiplicatore di replica dati è impostato su 2 poiché l'archivio indice (Elastic Search) utilizza per impostazione predefinita n+1 replica degli indici.
{:note}

Il numero di VM di ridimensionamento è calcolato dal numero di asset e dal numero di giorni di dati da indicizzare.

Tabella 2. Parametri della VM di ridimensionamento

|Numero di asset	|100	|500	|5000 |
|---|---|---|---|
|Giorni di dati	|30	|30	|30 |
|Totale archiviazione indice per asset al giorno (MB)	|1532	|1532	|1532 |
|Totale archiviazione indice per asset per 30 giorni (TB)	|4	|22	|219 |
|Dati supportati per il nodo di ridimensionamento (TB)	|0	|8	|8 |
|VM di ridimensionamento richieste	|0	|3	|27 |

La quantità di archiviazione richiesta è calcolata come segue:

Tabella 3. Parametri di archiviazione

|Numero di asset	|100	|500	|5000 |
|---|---|---|---|
|Conservazione dati a lungo termine (mesi)	|8	|8	|8 |
|Archiviazione totale per ogni asset al giorno (MB)	|766	|766	|766 |
|Giorni di dati	|30	|30	|30 |
|Conservazione dati a breve termine (TB)	|7	|33	|329 |
|Conservazione dati a lungo termine (TB)	|18	|88	|877 |

Da una prospettiva dei dati, i dati sono utilizzati nel seguente modo:

-	I dati di scansione sono utilizzati nella gestione della conformità
-	I dati di log sono utilizzati nella gestione dell'analisi
-	I dati di politica e flusso sono utilizzati nella gestione dei rischi e i dati di flusso sono disponibili solo da NSX Manager.

L'archiviazione dati ha tre livelli:

-	Replicata
-	A breve termine
-	A lungo termine

La seguente tabella fornisce un riepilogo delle distribuzioni:

Tabella 4. Riepilogo

|Modello di distribuzione	|“tutto-in-uno”	|Parzialmente distribuito	|Completamente distribuito |
|---|---|---|---|
|Numero di asset	|100	|500	|5000 |
|Dati online generati in 30 giorni (TB)	|4	|22	|219 |
|Conservazione dati nearline (90 giorni) (TB)	|7	|33	|329 |
|Conservazione dati offline (8 mesi) (TB)	|18	|88	|877 |
|Totale conservazione archivio dati (1 anno) (TB)	|28	|142	|1425 |
|VM di base	|1	|1	|20 |
|VM di ridimensionamento	|0	|3	|28 |
|Totale VM	|1	|4	|48 |

**Nota:**
quando rimuovi il servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, l'automazione {{site.data.keyword.vmwaresolutions_short}} elimina solo la singola VM Caveonix "tutta-in-uno" che era stata distribuita e la sottorete privata dedicata che era stata ordinata per essa. Pertanto:
* Se avevi ridimensionato la VM Caveonix VM in più VM, queste VM aggiuntive non vengono rimosse.
* Se avevi utilizzato gli indirizzi IP della sottorete privata dedicata sulle VM aggiuntive, a tali VM devono essere assegnati dei nuovi indirizzi IP perché continuino a funzionare.
* Se elimini l'istanza A di vCenter Server con il servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} installato, e avevi usato gli indirizzi IP sulla sottorete privata dedicata che era stata ordinata per il servizio nell'istanza B di vCenter Server, la sottorete privata dedicata viene annullata quando viene eseguita l'eliminazione dell'istanza A di vCenter Server.
