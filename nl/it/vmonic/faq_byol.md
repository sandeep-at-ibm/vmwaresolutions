---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Domande frequenti sulla concessione di licenza e su BYOL
{: #faq_byol}

Trova le risposte alle domande frequenti sulla concessione di licenza, inclusa la funzione BYOL (Bring Your Own License) di {{site.data.keyword.vmwaresolutions_full}}.

## Che cos'è BYOL?
{: #faq_byol-def}
{: faq}

Bring Your Own License, o BYOL, è una funzione disponibile per le istanze VMware Cloud Foundation nella V1.8 e successive e per i cluster VMware vCenter Server e VMware vSphere nella V2.0 e successive. Con BYOL, puoi utilizzare le tue proprie licenze VMware per uno o più dei seguenti componenti software VMware:
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Se scegli di utilizzare la tua propria licenza per un componente VMware e fornisci quindi una chiave di licenza valida, per questo componente non viene ordinata alcuna licenza da IBM e non vengono addebitati costi di licenza mensili sul tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}}.

La funzione BYOL non è disponibile per gli utenti Business Partner.
{:note}

## Da dove posso gestire le licenze e i componenti ordinati tramite VMware vSphere on IBM Cloud?
{: #faq_byol-license-mgmt}
{: faq}

Dopo aver effettuato un ordine per creare un nuovo cluster per VMware vSphere on {{site.data.keyword.cloud_notm}}, vengono forniti server ESXi, licenze VMware e altri componenti di rete che è possibile gestire dal {{site.data.keyword.slportal}}.

Dopo la distribuzione, vai alla console {{site.data.keyword.vmwaresolutions_short}} per ridimensionare il nuovo cluster utilizzando la configurazione salvata. Per ulteriori informazioni, vedi [Ridimensionamento di cluster vSphere esistenti](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters).

## Quali edizioni di licenza e CPU sono richieste per BYOL?
{: #faq_byol-license-cpu-reqs}
{: faq}

I seguenti requisiti si applicano alle edizioni della licenza per BYOL.

### Requisiti di BYOL per le istanze vCenter Server
{: #faq_byol-vcs-reqs}

Tabella 1. Requisiti minimi di edizioni della licenza e CPU per le istanze vCenter Server

  | Componente VMware | Edizione di licenza richiesta | CPU minima richiesta
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard                | N/A |
  | vSphere        | Enterprise Plus | 8 CPU |
  | vSAN           | Advanced o Enterprise | 8 CPU |
  | NSX            | Standard, Advanced o Enterprise | 8 CPU |

### Requisiti di BYOL per le istanze Cloud Foundation
{: #faq_byol-cf-reqs}

Tabella 2. Requisiti minimi di edizioni della licenza e CPU per le istanze Cloud Foundation

  | Componente VMware | Edizione di licenza richiesta | CPU minima richiesta
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard | N/A |
  | vSphere        | Enterprise Plus | 8 CPU |
  | vSAN           | Advanced o Enterprise | 8 CPU |
  | NSX            | Enterprise | 8 CPU |

## Cosa succede se la chiave di licenza che ho fornito non è corretta?
{: #faq_byol-incorrect-license}
{: faq}

Tutte le chiavi di licenza che fornisci vengono convalidate per garantire che siano corrette per i componenti VMware corrispondenti e che soddisfino i requisiti minimi di edizione e CPU dei componenti VMware. Se la convalida di una chiave di licenza ha esito negativo, ricevi una notifica e non puoi procedere con l'ordine dell'istanza.

## Posso fornire una chiave di licenza con più di 8 CPU?
{: #faq_byol-license-key}
{: faq}

Sì. Per ogni componente VMware è richiesta una licenza per CPU. Attualmente, tutti i server vCenter Server e Cloud Foundation hanno due CPU. Pertanto, sono necessarie due licenze per ciascun server. Si consiglia di fornire una chiave di licenza in grado di supportare l'istanza di base e qualsiasi nodo di espansione che vorrai aggiungere all'istanza in futuro.

## Posso fornire la licenza di SDDC Manager se utilizzo la funzione BYOL?
{: #faq_byol-sddc}
{: faq}

No. Il nostro accordo con VMware ci richiede di accettare l'effettiva chiave di licenza di un cliente. Sebbene la distribuzione di Cloud Foundation includa le licenze di SDDC Manager, non possiamo accettare i file delle chiavi di licenza di SDDC Manager e convalidarli per BYOL. Pertanto, le licenze di SDDC Manager vengono addebitate da IBM per tutte le istanze. Le licenze di SDDC Manager rappresentano una piccola parte dei costi di licenza complessivi per un'istanza Cloud Foundation.

## Posso utilizza la funzione BYOL per alcuni componenti di VMware e acquistare licenze mensili per altri?
{: #faq_byol-mthly-license}
{: faq}

Sì. Puoi utilizzare la funzione BYOL o acquistare licenze per qualsiasi combinazione dei quattro componenti VMware. La console {{site.data.keyword.vmwaresolutions_short}} rende semplice la selezione dell'opzione di licenza quando ordini la tua istanza. L'opzione di licenza che scegli al momento dell'ordine dell'istanza iniziale si applica per tutta la durata di tale istanza.

## Per uno specifico componente VMware, posso utilizzare BYOL per alcune licenze e acquistare il resto delle licenze da IBM?
{: #faq_byol-purchase}
{: faq}

Sì. Se hai selezionato BYOL per uno specifico componente VMware, quando crei un cluster hai le seguenti opzioni:
* Immettere una nuova chiave BYOL
* Continuare a utilizzare una chiave BYOL esistente
* Acquistare la licenza fornita da IBM per tale cluster.

Attualmente, solo VMware vSphere Enterprise e VMware vSAN possono essere concessi in licenza per ciascun cluster.

## Posso utilizzare BYOL quando creo un cluster?
{: #faq_byol-cluster}
{: faq}

Sì. Quando crei un cluster, puoi utilizzare BYOL da licenze BYOL esistenti o immettere una nuova BYOL. Inoltre, puoi acquistare una licenza di sottoscrizione fornita da IBM quando crei un cluster.

Attualmente, solo VMware vSphere Enterprise e VMware vSAN possono essere concessi in licenza per ciascun cluster.

## Come gestisco le mie licenze BYOL?
{: #faq_byol-mgmt}
{: faq}

Puoi gestire le licenze BYOL utilizzando il client web VMware vSphere al termine della distribuzione dell'istanza.

## Quando aggiungo più server ESXi alla mia istanza in un secondo momento, l'istanza verifica se le mie licenze BYOL hanno una capacità sufficiente?
{: #faq_byol-add-esxi}
{: faq}

Sì. Quando aggiungi più server ESXi a un'istanza distribuita, la capacità delle tue licenze BYOL viene automaticamente controllata per verificare il numero di server ESXi specificato. Se la capacità non è sufficiente, i server ESXi non vengono aggiunti e ricevi una notifica dalla console.

## Come faccio a sapere di quanta capacità della licenza dispongo su un cluster con BYOL?
{: #faq_byol-capacity}
{: faq}

Per trovare il numero di CPU disponibili nella tua chiave di licenza, completa la seguente procedura:
1. Vai alla pagina **Risorse**.
2. Individua e fai clic sull'istanza.
3. Nella scheda **Infrastruttura**, fai clic sul cluster per il quale vuoi controllare la capacità della licenza.
   Il numero di CPU disponibili è elencato nella tabella **Licenza fornita dall'utente**.

## IBM fornisce supporto se seleziono l'opzione di licenza BYOL?
{: #faq_byol-support}
{: faq}

Il supporto IBM continua a essere il tuo punto di contatto per qualsiasi problema di configurazione dell'istanza. Tuttavia, se il problema segnalato riguarda un componente VMware BYOL, vieni indirizzato al supporto VMware.

## Perché i costi di licenza vSphere vengono visualizzati nell'elenco di stime dei prezzi se utilizzo BYOL? Mi verranno addebitati dei costi?
{: #faq_byol-vsphere}
{: faq}

I {{site.data.keyword.baremetal_short}} vengono forniti con VMware vSphere già installato e con le licenze vSphere già incluse. Se hai selezionato BYOL per vSphere, dopo la distribuzione dell'istanza viene avviato automaticamente un processo per rimuovere le licenze vSphere incluse. Quindi, i costi della licenza vengono accreditati sul tuo account {{site.data.keyword.cloud_notm}}. Non devi fare nulla in questo processo.

## Posso ancora utilizzare il processo manuale esistente per BYOL?
{: #faq_byol-manual-process}
{: faq}

Con l'introduzione della funzione BYOL, l'uso continuato del processo manuale non è consigliato. Se vuoi utilizzare BYOL, fornisci le tue proprie licenze quando ordini l'istanza.

## BYOL è supportato per altri prodotti VMware come VMware vRealize Automation, VMware vRealize Operations o VMware vRealize Log Insight?
{: #faq_byol-other-support}
{: faq}

No, perché questi prodotti VMware non fanno parte della distribuzione dell'istanza. Questi prodotti VMware potrebbero essere installati in aggiunta alla distribuzione iniziale, il che richiede ai client o ai loro agent di installare e concedere la licenza per questi prodotti.

## Posso ordinare l'archiviazione NFS con vCenter Server with Hybridity Bundle?
{: #faq_byol-nfs}
{: faq}

Per le istanze appena distribuite, è supportata solo l'archiviazione vSAN all-flash. L'offerta vCenter Server with Hybridity Bundle include le licenze vSAN Advanced o Enterprise.

Se hai un'istanza vCenter Server con l'archiviazione NFS, puoi aggiornare la tua istanza esistente a vCenter Server with Hybridity Bundle. Anche se durante l'aggiornamento viene ordinata la licenza vSAN Advanced, non dovrai fornire un cluster vSAN all-flash..

## Posso utilizzare BYOL con vCenter Server with Hybridity Bundle?
{: #faq_byol-hybridity}
{: faq}

Non puoi portare la tua licenza VMware (BYOL) in {{site.data.keyword.cloud_notm}}. vCenter Server with Hybridity Bundle richiede che tutte le licenze VMware siano fornite da IBM.

## Qual è la differenza tra la licenza di vCenter Server with Hybridity Bundle e la licenza di vCenter Server?
{: #faq_byol-hybridity-vcs}
{: faq}

Le singole licenze VMware disponibili in vCenter Server hanno un prezzo per CPU. Come con tutte le licenze VMware per CPU fornite da IBM, c'è un aumento di prezzo di 1,3x su tutti i server che hanno più di 16 core per CPU, ad esempio per Dual Intel Xeon Gold 6140.

vCenter Server with Hybridity Bundle è una serie prescritta di licenze ed edizioni VMware concesse in licenza per core e non per CPU. Pertanto, il prezzo della licenza per queste istanze non cambia.

## Quali componenti ed edizioni di licenza VMware fornita da IBM sono disponibili per vCenter Server with Hybridity Bundle?
{: #faq_byol-hybridity-avail}
{: faq}

Le nuove istanze di vCenter Server with Hybridity Bundle includono VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced o Enterprise, VMware vSAN Advanced o Enterprise e VMware Hybrid Cloud Extension (HCX).

Se hai un'istanza vCenter Server con l'edizione NSX Base, viene eseguito automaticamente l'aggiornamento a NSX Advanced quando ordini vCenter Server with Hybridity Bundle.

## Posso aggiornare l'edizione NSX Advanced inclusa in vCenter Server with Hybridity Bundle all'edizione NSX Enterprise?
{: #faq_byol-nsx-upgrade}
{: faq}

Anche se vCenter Server with Hybridity Bundle include NSX Advanced, puoi eseguire l'aggiornamento all'edizione NSX Enterprise dopo aver ordinato vCenter Server with Hybridity Bundle. Per farlo, usa la scheda **Aggiorna e applica patch** nella pagina dei dettagli dell'istanza della console {{site.data.keyword.vmwaresolutions_short}}.

## Link correlati
{: #faq_byol-related}

* [Accesso alla console](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
