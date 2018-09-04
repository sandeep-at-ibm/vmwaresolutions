---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-11"

---

{:tip: .tip}

# Ordine di nuovi cluster vSphere

Per distribuire una piattaforma virtualizzata VMware altamente personalizzabile, ordina un cluster VMware vSphere su {{site.data.keyword.cloud}}. Utilizza questa procedura per definire un nuovo cluster VMware vSphere.

Questa procedura ti guida attraverso la selezione dei componenti VMware, le impostazioni di Bare Metal Server {{site.data.keyword.cloud_notm}}, le impostazioni di archiviazione e le scelte di rete per creare un nuovo cluster. Dopo aver effettuato l'ordine, la configurazione del cluster viene acquisita in modo che tu possa tornare indietro e continuare a ridimensionare il cluster in base alle tue esigenze. Una volta completato l'ordine, puoi configurare manualmente il cluster VMware in base ai tuoi requisiti.

## Requisiti

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Gestione di account utente e impostazioni](../vmonic/useraccount.html).
*  Hai esaminato i requisiti e le considerazioni in [Requisiti e pianificazione per i cluster vSphere](vs_planning.html).

## Impostazioni di sistema

Quando ordini un nuovo cluster vSphere, devi specificare le seguenti impostazioni di sistema.

### Nome cluster

Il nome del cluster deve essere univoco all'interno del tuo account.

## Impostazioni di licenza

Seleziona i componenti VMware da ordinare con il tuo cluster e specifica l'opzione di licenza per i componenti.

### (Solo per i Business Partner IBM) Bundle di componenti

Se sei un Business Partner IBM, puoi selezionare un bundle di licenze per i componenti quando ordini un nuovo cluster vSphere. Sono disponibili i seguenti bundle:

Tabella 1. Bundle di componenti dei Business Partner IBM per i cluster vSphere

| Bundle | Componenti                   |
|:------------------------- |:----------------------- |
| Standard con gestione | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Avanzata                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Avanzata con rete | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Avanzata con rete e gestione | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

Nel tuo ordine, puoi includere anche i seguenti componenti VMware:
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

**Nota:** per i Business Partner IBM, l'opzione BYOL (Bring Your Own License) non è disponibile.

### (Solo per i non Business Partner) Singoli componenti

Se non sei un Business Partner, puoi selezionare i seguenti componenti VMware in modo flessibile per il tuo cluster vSphere:
* VMware vSphere Enterprise Plus
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

**Nota:** il componente VMware vSAN non è disponibile quando ordini VMware vSphere Enterprise Plus 6.0. Se hai intenzione di utilizzare la tua propria licenza per VMware vSphere Enterprise Plus 6.0, viene aperto un ticket dell'infrastruttura {{site.data.keyword.cloud_notm}} per tuo conto. Il ticket richiede che le licenze vSphere dei {{site.data.keyword.baremetal_short}} ordinati vengano sostituite con le licenze da te fornite.

### Opzioni di licenza

Per la licenza dei componenti VMware selezionati, hai le seguenti opzioni:
* **Includi licenza con l'acquisto**: in questo caso, una nuova licenza per il componente VMware viene acquistata per tuo conto. Viene generata una licenza VMware combinata in modo da soddisfare la dimensione cluster dell'ordine.
* **Licenza fornita dall'utente**: in questo caso, utilizzi la tua propria licenza per il componente VMware.

Se scegli di acquistare una qualsiasi licenza, ad eccezione di vSphere Enterprise Plus e vCenter Server, e ordini più server ESXi, viene aperto automaticamente un ticket {{site.data.keyword.cloud_notm}} per tuo conto per combinare le chiavi di licenza. Sei responsabile di controllare il ticket per garantire di utilizzare solo le chiavi di licenza generate dal team DevOps.

**Importante**: l'utilizzo di singole chiavi di licenza insieme alle chiavi di licenza combinate non soddisfa i requisiti di pagamento per le licenze di cui avrai bisogno.

## Impostazioni di Bare Metal Server

### Ubicazione data center

Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui deve essere ospitato il cluster.

**Nota:** se selezioni un componente vSAN, l'elenco di ubicazioni viene filtrato in base alla disponibilità SSD.

### Modello CPU e RAM

Specifica il modello di CPU e la RAM per il Bare Metal Server.

Tabella 2. Opzioni per i {{site.data.keyword.baremetal_short}} personalizzati

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 core totali, 2,1 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

Le opzioni disponibili variano a seconda che tu abbia selezionato o meno il componente VMware vSAN.

### Numero di server Bare Metal

Il numero di server ESXi che vuoi aggiungere al cluster vSphere. Tutti i server ESXi hanno la stessa configurazione.
* Se hai selezionato il componente VMware NSX, è richiesto un minimo di tre server.
* Se hai selezionato il componente VMware vSAN, è richiesto un minimo di quattro server.

## Impostazioni di archiviazione

Per gli ordini senza vSAN, i server ESXi vengono ordinati con chassis da 12 dischi, con due dischi per il sistema operativo (SO) ESXi.

Per gli ordini con vSAN, i server ESXi vengono ordinati con chassis da 12 dischi e quattro dischi ordinati: due per il SO ESXi e due riservati per la memorizzazione nella cache. Queste impostazioni sono configurate per impostazione predefinita e non possono essere modificate. Puoi ordinare dischi con più capacità selezionando **Tipo e dimensioni del disco per i dischi vSAN** e **Numero di dischi vSAN**.

Se hai selezionato il componente VMware vSAN per il cluster, specifica le seguenti impostazioni.

### Tipo e dimensioni del disco per i dischi vSAN

Questa opzione è disponibile solo se hai selezionato il componente VMware vSAN.

Sono disponibili i seguenti tipi di dischi:
* SED SSD da 960 GB
* SED SSD da 1,9 TB
* SED SSD da 3,8 TB (le unità SED SSD da 3,8 TB saranno supportate una volta rese generalmente disponibili in un data center)

### Numero di dischi vSAN

Questa opzione è disponibile solo se hai selezionato il componente VMware vSAN. Le opzioni di quantità dei dischi includono 2, 4, 6 e 8.

## Impostazioni dell'interfaccia di rete

Quando ordini un nuovo cluster vSphere, devi specificare le seguenti impostazioni dell'interfaccia di rete.

### Prefisso nome host

Il nome host è utilizzato per tutti gli ordini di server bare metal. Si consiglia di utilizzare il nome host per tutte le macchine virtuali di gestione, come vCenter Server e NSX.

Il prefisso del nome host deve rispettare i seguenti requisiti:
* Il nome deve iniziare e terminare con un carattere alfanumerico.
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* La lunghezza massima è di 10 caratteri.

### Etichetta dominio secondario

L'etichetta del dominio secondario deve rispettare i seguenti requisiti:
*  Sono consentiti solo caratteri alfanumerici e trattini (-).
*  L'etichetta del dominio secondario deve iniziare e terminare con un carattere alfanumerico.
*  La lunghezza massima dell'etichetta del dominio secondario è di 10 caratteri.
*  L'etichetta del dominio secondario deve essere univoca all'interno del tuo account.

### Nome dominio

Il nome dominio viene utilizzato per tutti i {{site.data.keyword.baremetal_short}} e deve rispettare i seguenti requisiti:
* Il nome deve essere composto da due o più stringhe separate da un punto (.)
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Ogni stringa deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico e l'ultima stringa può contenere solo caratteri alfabetici.
* La lunghezza dell'ultima stringa deve essere compresa tra 2 e 24 caratteri.
* La lunghezza delle altre stringhe deve essere compresa tra 1 e 63 caratteri.
* La lunghezza massima del nome del dominio è di 189 caratteri.

### VLAN

Le impostazioni di rete si basano sulla tua selezione di **Ordina nuove VLAN** o **Seleziona VLAN esistenti**.

Per l'ordine del tuo cluster sono richieste una VLAN pubblica e due VLAN private. Le due VLAN private sono collegate a ogni Bare Metal Server.

#### Ordina nuove VLAN
Seleziona questa opzione per ordinare una nuova VLAN pubblica e due nuove VLAN private.

#### Seleziona VLAN esistenti  
A seconda del {{site.data.keyword.CloudDataCent_notm}} che hai selezionato, potrebbero essere disponibili VLAN pubbliche e private esistenti.

  Se scegli di riutilizzare VLAN pubbliche e private esistenti, specifica le VLAN e le sottoreti:
  * La **VLAN pubblica** serve per l'accesso alla rete pubblica.
  * La **VLAN privata** serve per la connettività tra i data center e i servizi in {{site.data.keyword.cloud_notm}}.
  * La **VLAN privata secondaria** serve per le funzioni di VMware come vSAN.
  * La **Sottorete primaria** è assegnata agli host fisici per l'accesso alla rete pubblica.
  * La **Sottorete privata primaria** è assegnata agli host fisici per il traffico di gestione.

**Importante:**
* Assicurati che la configurazione del firewall sulle VLAN selezionate non blocchi il traffico dei dati di gestione.
* Assicurati che tutte le VLAN selezionate si trovino nello stesso pod. I server ESXi non possono essere forniti su VLAN con pod misti.

#### Coppia FortiGate Physical Appliance 300 Series HA

Puoi anche scegliere se includere la coppia FortiGate Physical Appliance 300 Series HA per proteggere il tuo ambiente cloud. Per ulteriori informazioni, vedi [Panoramica di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html).

## Riepilogo ordine

In base alle tue configurazioni, il costo stimato viene generato e visualizzato immediatamente nel riquadro **Riepilogo ordine** sulla destra. Fai clic su **Dettagli sui prezzi** per generare un documento PDF che fornisce i dettagli della stima.

## Procedura

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e poi su **VMware vSphere** nella sezione **Data center virtuali**.
2. Nella pagina **VMware vSphere on IBM Cloud**, fai clic su **Crea**.  
   Assicurati di essere nella scheda **Crea nuovo** e che **Nuovo cluster** sia visualizzato nell'elenco **Configurazioni cluster**.
3. Immetti il nome del cluster.
4. Seleziona i componenti VMware:
  * Se sei un Business Partner IBM, seleziona un bundle di licenze e qualsiasi ulteriore componente VMware disponibile.
  * Se non sei un Business Partner, seleziona il componente, l'eventuale edizione e specifica l'opzione di licenza.
  Se scegli di utilizzare l'opzione BYOL (Bring Your Own License) per VMware vSphere Enterprise Plus, viene aperto automaticamente un ticket {{site.data.keyword.cloud_notm}} per tuo conto per richiedere che le licenze vSphere predefinite sui tuoi {{site.data.keyword.baremetal_short}} ordinati vengano sostituite con le licenze da te fornite.   

    **Importante:** sei responsabile di tracciare il ticket in modo tale da sostituire la licenza vSphere sui server ESXi appena ordinati. In questo modo, l'infrastruttura {{site.data.keyword.cloud_notm}} concede l'annullamento del costo della licenza vSphere dell'infrastruttura {{site.data.keyword.cloud_notm}} fornita inizialmente. Per sostituire la tua licenza ESXi vSphere, vedi [Configure License Settings for an ESXi Host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}.

5. Completa le impostazioni di Bare Metal Server:
   1. Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare il cluster.
   2. Seleziona il modello CPU e la dimensione della RAM.
   3. Specifica il numero di server bare metal.
6. Se hai selezionato il componente **VMware vSAN**, completa le impostazioni di archiviazione vSAN selezionando il **Tipo e dimensioni del disco per i dischi vSAN** e il **Numero di dischi vSAN**.
7. Completa le impostazioni dell'interfaccia di rete:
   1. Immetti il prefisso del nome host, l'etichetta del dominio secondario e il nome del dominio.
   2. Seleziona l'interfaccia di rete che vuoi utilizzare.
    * Se vuoi ordinare nuove VLAN pubbliche e private, fai clic su **Ordina nuove VLAN**.
    * Se vuoi riutilizzare le VLAN pubbliche e private esistenti quando sono disponibili, fai clic su **Seleziona VLAN esistenti** e specifica le VLAN e, facoltativamente, le sottoreti.
    3. Specifica se applicare la coppia FortiGate Physical Appliance 300 Series HA per proteggere il tuo ambiente cloud.  
8. Nel riquadro **Riepilogo ordine**, verifica la configurazione del cluster e il costo stimato.
   * Per salvare la configurazione come template senza effettuare un ordine, fai clic su **Salva configurazione**.
   * Per effettuare l'ordine, assicurati che l'account da addebitare sia corretto, esamina e accetta i termini e infine fai clic su **Fornitura**.

   **Nota**: vengono installati solo i {{site.data.keyword.baremetal_short}}. Sei responsabile dell'installazione e della configurazione dei vari componenti dopo la distribuzione del cluster, come VMware vCenter, VMware NSX, VMware vSAN.

### Risultati

Se hai salvato la configurazione del cluster come template, ricevi una notifica dalla console che indica che la configurazione è stata salvata correttamente e puoi quindi trovare il template nell'elenco **Configurazioni cluster**.

Se hai effettuato un ordine, la distribuzione del cluster inizia automaticamente e ricevi un'e-mail di conferma che ti indica che l'ordine è in fase di elaborazione. Quando il cluster è pronto per l'uso, ti viene inviata una notifica via e-mail.

**Nota:** i cluster vSphere, a differenza delle istanze vCenter Server e Cloud Foundation, non vengono visualizzati nella pagina **Istanze distribuite**.

### Link correlati

* [Ordine di cluster vSphere in base alle configurazioni esistenti](vs_orderingbasedonexistingconfig.html)
* [Ridimensionamento di cluster esistenti](vs_scalingexistingclusters.html)
* [Ridimensionamento di cluster creati all'esterno della console](vs_orderingforclustersoutside.html)
