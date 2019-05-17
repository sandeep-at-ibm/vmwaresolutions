---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

subcollection: vmware-solutions


---

# Glossario di componenti e termini HCX
{: #vcshcx-components}

HCX consiste in un lato cloud (destinazione) e uno o più client
(origine). Deve essere distribuita un'istanza di HCX per ogni vCenter, anche se i vCenter dove
viene distribuito HCX sono collegati nello stesso dominio SSO sul lato client o cloud. Le configurazioni supportate da HCX sono uno-a-uno,
uno-a-molti, molti-a-uno e molti-a-molti.

## Lato cloud e lato client
{: #vcshcx-components-cloud-client-side}

HCX ha il concetto di lato cloud (destinazione) e lato client (origine).
- Lato cloud - vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. Il
lato cloud di HCX è l'istanza slave di una relazione client-cloud HCX. È controllata dal lato client.
- Lato client - qualsiasi istanza vSphere che soddisfa i prerequisiti per l'installazione e il funzionamento. Il lato client di HCX è il master che controlla l'istanza slave lato cloud tramite il suo snap-in di IU (interfaccia utente) client web vCenter.

## HCX Manager
{: #vcshcx-components-hcx-manager}

- HCX Manager lato cloud è la prima parte di un'installazione HCX
distribuita sul lato cloud dall'automazione {{site.data.keyword.vmwaresolutions_short}}.
Inizialmente è un singolo file immagine OVA distribuito specifico per il lato cloud insieme a un programma di bilanciamento del carico-firewall edge NSX configurato specificamente per il ruolo HCX. HCX Manager è configurato per essere in ascolto per il traffico di controllo, gestione e registrazione lato client in entrata.
- HCX Manager lato client è un file immagine OVA specifico per il lato client che fornisce la funzionalità IU per la gestione e il funzionamento di HCX. HCX Manager lato client è responsabile della registrazione presso HCX Manager lato cloud e la creazione di un piano di gestione tra il lato client e quello cloud. È inoltre responsabile della distribuzione dei componenti della flotta sul lato client e dell'indicazione al lato cloud di procedere alla stessa operazione.

## Componenti della flotta
{: #vcshcx-components-fleet}

I componenti della flotta HCX sono responsabili della creazione dei piani di dati e controllo tra il lato client e quello cloud. Distribuita come VM (Virtual Machine) in coppie con mirroring, la flotta consiste nei seguenti componenti:

- CGW (Cloud Gateway) - il Cloud Gateway è un componente facoltativo
responsabile della creazione di tunnel crittografati che supportano il traffico (migrazione in blocco) di replica e vMotion. Esiste solo una singola coppia per ogni sito HCX collegato.
- L2C (Layer 2 Concentrator) - il Layer 2 Concentrator è un componente facoltativo responsabile della creazione di tunnel crittografati per il piano di dati e di controllo corrispondente al traffico L2 (Layer 2) esteso. Ogni coppia L2C può gestire fino a 4096 delle reti estese. Ulteriori coppie L2C vengono distribuite come necessario. La capacità di larghezza di banda è limitata a ~4 Gbps e pertanto, se la capacità di larghezza di banda esterna è superiore ai 4 Gbps, l'utilizzo di ulteriori coppie L2C consente un maggiore utilizzo della rete sottostante.
- Ottimizzatore WAN - HCX include un dispositivo di ottimizzazione WAN Silver Peak™ distribuito facoltativamente. Viene distribuito come un dispositivo VM. Quando viene distribuito, il traffico di tunnel CGW viene reindirizzato per passare attraverso l'ottimizzatore WAN.
Poiché l'ottimizzatore WAN riduce considerevolmente il traffico attraverso la WAN (quello osservato di norma è
da 3:1 a 6:1) aumentando al tempo stesso l'affidabilità della connessione, si consiglia di distribuire sempre l'ottimizzatore WAN con CGW. L'ulteriore vantaggio offerto dalla distribuzione dell'ottimizzatore WAN si estende alla limitazione della larghezza di banda della WAN consumata dal traffico di migrazione di VM. L'interfaccia di gestione dell'ottimizzatore WAN non è configurata per impostazione predefinita.
- Host ESXi proxy - Ogni volta che CGW è configurato per stabilire una connessione al sito HCX lato cloud, nel vCenter è presente un host ESXi proxy esternamente a qualsiasi cluster. Questo host ESXi ha lo stesso indirizzo IP vMotion e di gestione del dispositivo CGW corrispondente. Ciò consente un funzionamento dell'ambiente vSphere
sia sul lato client che su quello cloud come se stesse eseguendo un vMotion locale. Questo metodo offre i seguenti vantaggi:
    - Gli intervalli IP di gestione sull'uno o sull'altro lato possono essere in sovrapposizione senza alcuna perdita di funzionalità.
    - Il lato cloud non ha alcuna visibilità vSphere nel lato client, il che lo rende più sicuro.

## Portali utente HCX
{: #vcshcx-components-hcx-user-portals}

- IU web client – il portale web client HCX è l'IU principale per HCX. Una volta installato, HCX Manager lato client viene visualizzato come uno snap-in all'IU web vCenter. Controlla la registrazione HCX cloud remota (accoppiamento di siti), la distribuzione dei componenti della flotta, l'estensione di rete e la migrazione di VM verso e dal cloud.

- IU lato cloud – l'IU HCX lato cloud è accessibile tramite l'URL di registrazione pubblico fornito per la registrazione client HCX. Per impostazione predefinita, utilizza l'accesso SSO vSphere lato cloud (` administrator@vsphere.local`). Viene di norma utilizzato per eseguire l'upgrade dell'installazione e la modifica di qualche configurazione di rete. Viene utilizzato anche per creare VM (Virtual Machine) all'interno di HCX.

- IU di gestione del dispositivo di HCX Manager client/cloud – Accesso all'IU di gestione del dispositivo per il lato cloud o quello client tramite l'indirizzo IP privato VM come visualizzato in vCenter `https://<hcxmanager_IP>:9443`. L'ID (di norma “admin”) e la password sono forniti tramite il portale {{site.data.keyword.vmwaresolutions_short}}. L'IU di gestione viene utilizzata per avviare e arrestare i servizi di HCX Manager, configurare il monitoraggio dei log, la configurazione di rete di base, gli upgrade manuali, la raccolta di log di supporto quando l'IU web non funziona, la registrazione presso i componenti vSphere (vCenter, PSC e NSX Manager) e la gestione dei certificati.

## Link correlati
{: #vcshcx-components-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro) 
