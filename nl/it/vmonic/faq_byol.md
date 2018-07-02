---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Domande frequenti sulla concessione di licenza e su BYOL

Trova le risposte alle domande frequenti sulla concessione di licenza, inclusa la funzione BYOL (Bring Your Own License) di {{site.data.keyword.vmwaresolutions_full}}.

## Che cos'è BYOL?

Bring Your Own License, o BYOL, è una funzione disponibile per le istanze VMware Cloud Foundation nelle release della V1.8 e successive e per i cluster vCenter Server e vSphere nelle release della V2.0 e successive. BYOL ti consente di utilizzare le tue proprie licenze di VMware per uno o più dei seguenti componenti software VMware quando ordini le istanze:
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Se scegli di utilizzare la tua propria licenza per un componente VMware e fornisci quindi una chiave di licenza valida, per questo componente non viene ordinata alcuna licenza da IBM e non vengono addebitati costi di licenza mensili sul tuo account dell'infrastruttura {{site.data.keyword.cloud}}.

**Nota:** la funzione BYOL non è disponibile per gli utenti Business Partner.

## Da dove posso gestire le licenze e i componenti ordinati tramite VMware vSphere on IBM Cloud?

Dopo aver effettuato un ordine per creare un nuovo cluster per VMware vSphere on {{site.data.keyword.cloud_notm}}, vengono forniti server ESXi, licenze VMware e altri componenti di rete che è possibile gestire dal {{site.data.keyword.slportal}}.

Dopo la distribuzione, vai alla console {{site.data.keyword.vmwaresolutions_short}} per ridimensionare il nuovo cluster utilizzando la configurazione salvata. Per ulteriori informazioni sul ridimensionamento, vedi [Ridimensionamento di cluster vSphere esistenti](../vsphere/vs_scalingexistingclusters.html).

## Quali edizioni di licenza e quantità di CPU sono necessarie per BYOL?

I seguenti requisiti si applicano alle edizioni della licenza per BYOL.

### Requisiti di BYOL per le istanze vCenter Server

Tabella 1. Requisiti minimi di edizioni della licenza e CPU per le istanze vCenter Server

  | Componente VMware | Edizione di licenza richiesta | CPU minima richiesta
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard                | N/A |
  | vSphere        | Enterprise Plus | 8 CPU |
  | vSAN           | Advanced o Enterprise | 8 CPU |
  | NSX            | Standard, Advanced o Enterprise | 8 CPU |

### Requisiti di BYOL per le istanze Cloud Foundation

Tabella 2. Requisiti minimi di edizioni della licenza e CPU per le istanze Cloud Foundation

  | Componente VMware | Edizione di licenza richiesta | CPU minima richiesta
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard | N/A |
  | vSphere        | Enterprise Plus | 8 CPU |
  | vSAN           | Advanced o Enterprise | 8 CPU |
  | NSX            | Enterprise | 8 CPU |

## Cosa succede se la chiave di licenza che ho fornito non è corretta?

Tutte le chiavi di licenza che fornisci vengono convalidate per garantire che siano corrette per i componenti VMware corrispondenti e che soddisfino i requisiti minimi di edizione e CPU dei componenti VMware. Se la convalida di una chiave di licenza ha esito negativo, ricevi una notifica e non puoi procedere con l'ordine dell'istanza.

## Posso fornire una chiave di licenza con più di 8 CPU?

Sì. Per ogni componente VMware è richiesta una licenza per CPU. Attualmente, tutti i server vCenter Server e Cloud Foundation hanno due CPU, pertanto sono necessarie due licenze per ciascun server. Si consiglia di fornire una chiave di licenza in grado di supportare l'istanza di base e qualsiasi nodo di espansione che vorrai aggiungere all'istanza in futuro.

## Posso fornire la licenza di SDDC Manager quando utilizzo la funzione BYOL?

No. Il nostro accordo con VMware ci richiede di accettare l'effettiva chiave di licenza di un cliente. Sebbene la distribuzione di Cloud Foundation includa le licenze di SDDC Manager, non ci sono file di chiavi di licenza di SDDC Manager che possiamo accettare e convalidare per BYOL. Pertanto, le licenze di SDDC Manager vengono addebitate da IBM per tutte le istanze. Le licenze di SDDC Manager rappresentano una parte molto piccola dei costi di licenza complessivi per un'istanza Cloud Foundation.

## Posso utilizza la funzione BYOL per alcuni componenti di VMware e acquistare licenze mensili per altri?

Sì. Puoi utilizzare la funzione BYOL o acquistare licenze per qualsiasi combinazione dei quattro componenti VMware. La console {{site.data.keyword.vmwaresolutions_short}} semplifica la selezione dell'opzione di licenza quando ordini l'istanza di vCenter Server o Cloud Foundation. L'opzione di licenza che scegli al momento dell'ordine dell'istanza iniziale si applica per tutta la durata di tale istanza.

## Per uno specifico componente VMware, posso utilizzare BYOL per alcune licenze e acquistare il resto delle licenze da IBM?

Sì. Se hai selezionato BYOL per un componente VMware specifico, quando crei un nuovo cluster hai l'opzione di immettere una nuova chiave BYOL, continuare a utilizzare una chiave BYOL esistente o acquistare la licenza fornita da IBM per tale cluster.  Attualmente, sono disponibili solo VMware vSphere Enterprise e VMware vSAN per la licenza in ciascun cluster.

## Posso utilizzare BYOL quando creo un nuovo cluster?

Sì. Puoi utilizzare BYOL da licenze BYOL esistenti o immettere un nuovo BYOL quando crei un nuovo cluster. Avrai anche l'opzione di acquistare una licenza di sottoscrizione fornita da IBM durante la creazione di un nuovo cluster. Attualmente, sono disponibili solo VMware vSphere Enterprise e VMware vSAN per la licenza in ciascun cluster.

## Come posso gestire le mie licenze BYOL?

Puoi gestire le licenze BYOL utilizzando il client web VMware vSphere al termine della distribuzione dell'istanza.

## Quando aggiungo più server ESXi alla mia istanza in un secondo momento, l'istanza verifica se la capacità delle mie licenze BYOL è sufficiente?

Sì. Quando aggiungi più server ESXi a un'istanza distribuita, la capacità delle tue licenze BYOL viene automaticamente controllata per verificare il numero di server ESXi specificato. Se la capacità non è sufficiente, i server ESXi non vengono aggiunti e ricevi una notifica dalla console.

## Come faccio a sapere di quanta capacità della licenza dispongo su un cluster con BYOL?

Puoi trovare il numero di CPU disponibili nella tua chiave di licenza andando alla pagina **Istanze distribuite**, individuando e facendo clic sull'istanza e quindi, sulla scheda **Infrastruttura** facendo clic sul cluster di cui vuoi controllare la capacità della licenza. Il numero di CPU disponibili è elencato nella tabella **Licenza fornita dall'utente**.

## IBM fornisce supporto se seleziono l'opzione di licenza BYOL?

Il supporto IBM continua a essere il tuo punto di contatto per qualsiasi problema di configurazione dell'istanza. Tuttavia, se il problema segnalato riguarda un componente VMware BYOL, vieni indirizzato al supporto VMware.

## Perché i costi di licenza vSphere vengono visualizzati nell'elenco di stime dei prezzi se utilizzo BYOL? Mi verranno addebitati dei costi?

I {{site.data.keyword.baremetal_short}} vengono forniti con VMware vSphere già installato e con le licenze vSphere già incluse. Se hai selezionato BYOL per vSphere, dopo la distribuzione dell'istanza viene avviato automaticamente un processo per rimuovere le licenze vSphere incluse. Quindi i costi della licenza vengono accreditati sul tuo account {{site.data.keyword.cloud_notm}}. Non devi fare nulla in questo processo.

## Posso ancora utilizzare il processo manuale esistente per BYOL?

Con l'introduzione della funzione BYOL, l'uso continuato del processo manuale non è consigliato. Se vuoi utilizzare BYOL, fornisci le tue proprie licenze quando ordini l'istanza.

## BYOL è supportato per altri prodotti VMware come VMware vRealize Automation, VMware vRealize Operations o VMware vRealize Log Insight?

No, perché questi prodotti VMware non fanno parte della distribuzione dell'istanza. Questi prodotti VMware potrebbero essere installati insieme alla distribuzione iniziale, il che richiede ai clienti o ai loro agenti di effettuare l'installazione e concedere le licenze.

## Posso ordinare l'archiviazione NFS con vCenter Server with Hybridity Bundle?

Per le istanze appena distribuite, è supportata solo l'archiviazione vSAN all-flash. L'offerta vCenter Server with Hybridity Bundle include le licenze vSAN Advanced o Enterprise.

Se hai un'istanza vCenter Server con l'archiviazione NFS, puoi aggiornare la tua istanza esistente a vCenter Server with Hybridity Bundle. Anche se durante l'aggiornamento viene ordinata la licenza vSAN Advanced, non dovrai fornire un cluster vSAN all-flash..

## Posso utilizzare BYOL con vCenter Server with Hybridity Bundle?

Non puoi portare la tua licenza VMware (BYOL) in {{site.data.keyword.cloud_notm}}. vCenter Server with Hybridity Bundle richiede che tutte le licenze VMware siano fornite da IBM.

## Qual è la differenza tra la licenza di vCenter Server with Hybridity Bundle e la licenza di vCenter Server?

Le singole licenze VMware disponibili in vCenter Server hanno un prezzo per CPU. Come con tutte le licenze VMware per CPU fornite da IBM, c'è un aumento di prezzo di 1,3x su tutti i server che hanno più di 16 core per CPU, ad esempio per Dual Intel Xeon Gold 6140.

vCenter Server with Hybridity Bundle è una serie prescritta di licenze ed edizioni VMware concesse in licenza per core e non per CPU. Pertanto, il prezzo della licenza per queste istanze non cambia.

## Quali componenti ed edizioni di licenza VMware fornita da IBM sono disponibili per vCenter Server with Hybridity Bundle?

Le nuove istanze di vCenter Server with Hybridity Bundle includono VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced o Enterprise, VMware vSAN Advanced o Enterprise e VMware Hybrid Cloud Extension (HCX).

Se hai un'istanza vCenter Server con l'edizione NSX Base, verrà eseguito automaticamente l'aggiornamento a NSX Advanced quando ordini vCenter Server with Hybridity Bundle.

## Posso aggiornare l'edizione NSX Advanced inclusa in vCenter Server with Hybridity Bundle all'edizione NSX Enterprise?

Anche se vCenter Server with Hybridity Bundle include NSX Advanced, puoi eseguire l'aggiornamento all'edizione NSX Enterprise dopo aver ordinato vCenter Server with Hybridity Bundle. Per farlo, usa la scheda **Aggiorna e applica patch** nella pagina dei dettagli dell'istanza della console {{site.data.keyword.vmwaresolutions_short}}.

### Link correlati

* [Ordine di istanze Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Istanze Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Accesso alla console](loginmethod.html)
* [Come contattare il supporto IBM](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
