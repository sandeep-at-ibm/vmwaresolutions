---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Glossario di componenti e termini HCX
{: #hcxclient-components}

HCX consiste in un lato cloud (destinazione/ambiente VCD) e uno o più client (origine). Deve essere distribuita un'istanza di HCX per ogni vCenter, anche se i vCenter dove
viene distribuito HCX sono collegati nello stesso dominio SSO sul lato client o cloud. Le configurazioni supportate da HCX sono uno-a-uno,
uno-a-molti, molti-a-uno e molti-a-molti.

## Lato di destinazione e lato client
{: #hcxclient-components-cloud-client-side}

HCX ha il concetto di lato cloud (destinazione/ambiente VCD) e lato client (origine).

- Lato di destinazione - HCX Cloud Manager è predistribuito e configurato con i profili di rete e calcolo pronti per la creazione della rete di servizi.  
- Lato client - qualsiasi istanza vSphere che soddisfa i prerequisiti per l'installazione e il funzionamento. Il lato client di HCX è il master che controlla l'istanza slave lato cloud tramite il suo snap-in di IU (interfaccia utente) client web vCenter.

## HCX Manager
{: #hcxclient-components-hcx-manager}

- Lato cloud -.HCX Cloud Manager è configurato per essere in ascolto per il traffico di controllo, gestione e registrazione lato client in entrata.
- Lato client - HCX Enterprise Manager è un file immagine OVA specifico per il lato client che fornisce la funzionalità IU per la gestione e il funzionamento di HCX. HCX Manager lato client è responsabile della registrazione presso HCX Manager lato cloud e la creazione di un piano di gestione tra il lato client e quello cloud. È inoltre responsabile della distribuzione di una rete di servizi sul lato client e dell'indicazione al lato cloud di procedere alla stessa operazione.

## Componenti della rete di servizi
{: #hcxclient-components-fleet}

I componenti della rete di servizi HCX sono responsabili della creazione dei piani di dati e controllo tra il lato client e quello cloud. Distribuita come VM (Virtual Machine) in coppie con mirroring, la rete di servizi consiste nei seguenti componenti:

- Interconnect Appliance (HCX-IX) - il dispositivo di interconnessione crea dei tunnel crittografati che supportano il traffico (migrazione in blocco) di replica e vMotion.
- WAN Optimizer Appliance (HCX-WAN) - HCX include un dispositivo di ottimizzazione Silver Peak™ WAN distribuito facoltativamente. Viene distribuito come un dispositivo VM. Quando viene distribuito, il traffico di tunnel CGW viene reindirizzato per passare attraverso l'ottimizzatore WAN. Poiché l'ottimizzatore WAN riduce considerevolmente il traffico attraverso la WAN (quello osservato di norma è
da 3:1 a 6:1) aumentando al tempo stesso l'affidabilità della connessione, si consiglia di distribuire sempre l'ottimizzatore WAN con CGW. L'ulteriore vantaggio offerto dalla distribuzione dell'ottimizzatore WAN si estende alla limitazione della larghezza di banda della WAN consumata dal traffico di migrazione di VM. L'interfaccia di gestione dell'ottimizzatore WAN non è configurata per impostazione predefinita.
- Network Extension (HCX-NE) - fornisce le funzionalità di estensione di rete di livello 2, consentendo le migrazioni tra l'ubicazione in loco e l'ambiente vSphere con la necessità di riassegnare l'IP delle macchine virtuali.
- Host ESXi proxy - Ogni volta che HCX-IX è configurato per stabilire una connessione al sito HCX lato cloud, nel vCenter è presente un host ESXi proxy esternamente a qualsiasi cluster. Questo host ESXi ha lo stesso indirizzo IP vMotion e di gestione del dispositivo HCX-IX corrispondente. Ciò consente un funzionamento dell'ambiente vSphere
sia sul lato client che su quello cloud come se stesse eseguendo un vMotion locale. Questo metodo offre i seguenti vantaggi:
  - Gli intervalli IP di gestione sull'uno o sull'altro lato possono essere in sovrapposizione senza alcuna perdita di funzionalità.
  - Il lato cloud non ha alcuna visibilità vSphere nel lato client, il che lo rende più sicuro.

## Portali utente HCX
{: #hcxclient-components-hcx-user-portals}

- IU web client – il portale web client HCX è l'IU principale per HCX. Una volta installato, HCX Manager lato client viene visualizzato come uno snap-in all'IU web vCenter. Controlla la registrazione HCX cloud remota (accoppiamento di siti), la distribuzione dei componenti della flotta, l'estensione di rete e la migrazione di VM verso e dal cloud.
- IU lato cloud – l'IU HCX lato cloud è accessibile tramite l'URL di registrazione pubblico fornito per la registrazione client HCX. Per impostazione predefinita, utilizza le credenziali di amministratore vCenter lato cloud `administrator@vsphere.local`. Viene di norma utilizzato per eseguire l'upgrade dell'installazione e la modifica di qualche configurazione di rete.

## Link correlati
{: #hcxclient-components-related}

* [Requisiti di accesso alla porta per VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [Preparazione dell'ambiente di installazione](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Distribuzione client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Rete di servizi in loco HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrazioni VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitoraggio di parametri e componenti](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
