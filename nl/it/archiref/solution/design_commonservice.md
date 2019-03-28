---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Progettazione di servizi comuni
{: #design_commonservice}

I servizi comuni forniscono i servizi che vengono utilizzati da altri servizi nella piattaforma di gestione cloud. I servizi comuni della soluzione includono servizi di identità e accesso, servizi DNS, servizi NTP, servizi SMTP e servizi di autorità di certificazione.

## Servizi di identità e accesso
{: #design_commonservice-identity-access}

In questa progettazione, Microsoft Active Directory (AD) viene utilizzato per la gestione delle identità. La progettazione distribuisce una o due VM (Virtual Machine) Windows Active Directory come parte dell'automazione della distribuzione di Cloud Foundation e vCenter Server. vCenter viene configurato per utilizzare l'autenticazione AD.

### Microsoft Active Directory
{: #design_commonservice-msad}

Per impostazione predefinita, una singola VSI di Active Directory viene distribuita sull'infrastruttura {{site.data.keyword.cloud}}. La progettazione offre inoltre la possibilità di distribuire due server Microsoft Active Directory altamente disponibili come VM di Windows Server dedicate nel cluster di gestione.

Se scegli questa opzione, sei responsabile di fornire licenze e attivazione Microsoft.
{:note}

Active Directory serve per autenticare gli accessi per gestire solo l'istanza VMware e non per ospitare gli utenti dei carichi di lavoro nelle istanze distribuite. Il nome di dominio root dell'insieme di strutture del server Active Directory corrisponde al nome di dominio DNS da te specificato. Questo nome di dominio è specificato solo per l'istanza primaria di Cloud Foundation e vCenter Server se sono collegate più istanze. Per le istanze collegate, ciascuna istanza contiene un server Active Directory che si trova nell'anello di replica root dell'insieme di strutture. Anche i file di zona DNS vengono replicati sui server Active Directory.

### Dominio SSO vSphere
{: #design_commonservice-vsphere-sso}

Il dominio SSO (Single Sign On) vSphere viene utilizzato come meccanismo di autenticazione iniziale per una singola istanza o più istanze collegate. Il dominio SSO serve anche per connettere un'istanza VMware o più istanze collegate al server Microsoft Active Directory. Viene applicata la seguente configurazione SSO:  
* Viene utilizzato sempre il dominio SSO di `vsphere.local`
* Per le istanze VMware collegate a un'istanza esistente, il PSC viene unito al dominio SSO dell'istanza esistente
* Il nome del sito SSO è uguale al nome dell'istanza

## DNS (Domain name Service)
{: #design_commonservice-dns}

Il DNS (Domain name Service) in questa progettazione è solo per i componenti di infrastruttura e gestione cloud.

### VMware vCenter Server
{: #design_commonservice-vcenter}

La distribuzione di vCenter Server utilizza i server Active Directory distribuiti come server DNS per l'istanza. Tutti i componenti distribuiti (vCenter, PSC, NSX e host ESXi) sono configurati in modo da puntare al server Active Directory come proprio server DNS predefinito. Puoi personalizzare la configurazione della zona DNS se la tua configurazione non interferisce con quella dei componenti distribuiti.

Questa progettazione integra i servizi DNS sui server Active Directory tramite la seguente configurazione:
* Puoi specificare la struttura del dominio. Il nome di dominio può essere un numero qualsiasi di livelli (fino al massimo che i componenti di vCenter Server possono gestire). Il livello più basso è il dominio secondario per l'istanza.
   * Il nome di dominio DNS che specifichi viene utilizzato come nome di dominio dell'insieme di strutture root di Active Directory. Ad esempio, se il nome del dominio DNS è `cloud.ibm.com`, il nome di dominio root dell'insieme di strutture di Active Directory sarà anche `cloud.ibm.com`. Questo nome di dominio DNS e Active Directory è uguale per tutte le istanze vCenter Server collegate.
   * Inoltre, puoi specificare un nome di dominio secondario per l'istanza. Il nome del dominio secondario deve essere univoco tra tutte le istanze vCenter Server collegate.
* I server DNS di Active Directory sono configurati per essere autorevoli sia per lo spazio del dominio che del dominio secondario DNS.
* I server DNS di Active Directory sono configurati per puntare ai server DNS di {{site.data.keyword.cloud_notm}} per tutte le altre zone.
* Qualsiasi istanza da integrare a un'istanza di destinazione esistente deve utilizzare lo stesso nome di dominio dell'istanza primaria.

### VMware Cloud Foundation
{: #design_commonservice-cf}

La distribuzione di Cloud Foundation utilizza l'automazione VMware Cloud Foundation, che utilizza il proprio server DNS che risiede all'interno del componente VM di SDDC Manager. I componenti Cloud Foundation gestiti da SDDC Manager, inclusi vCenter, PSC, NSX e host ESXi, sono configurati per utilizzare l'indirizzo IP della VM di SDDC Manager come loro DNS predefinito in base alla progettazione.

Poiché SDDC Manager genera e mantiene i nomi host per i componenti che gestisce, non si consiglia di manomettere direttamente il suo file di zona DNS per aggiungere e rimuovere gli host.

Questa progettazione integra i servizi DNS sui server Active Directory con la VM di SDDC Manager nella seguente configurazione:
* Puoi specificare la struttura del dominio. Il nome di dominio può essere un numero qualsiasi di livelli (fino al massimo che i componenti di Cloud Foundation gestiranno).
* Il livello più basso è il dominio secondario di cui è autorevole l'SDDC Manager.
* Il nome di dominio DNS che specifichi verrà utilizzato come nome di dominio dell'insieme di strutture root di Active Directory. Ad esempio, se il nome del dominio DNS è `cloud.ibm.com`, la root dell'insieme di strutture del dominio Active Directory sarà `cloud.ibm.com`. Questo dominio DNS e Active Directory è uguale per tutte le istanze Cloud Foundation collegate.
* Inoltre, puoi specificare un nome di dominio secondario per l'istanza. Il nome del dominio secondario deve essere univoco tra tutte le istanze Cloud Foundation collegate.  
* La configurazione DNS di SDDC Manager viene modificata in modo che punti ai server Active Directory per tutte le zone tranne che per la zona di cui è responsabile.
* I server DNS di Active Directory sono configurati per essere autorevoli per lo spazio del dominio DNS al di sopra del dominio secondario delle istanze SDDC Manager e Cloud Foundation.
* I server DNS di Active Directory sono configurati per puntare all'indirizzo IP di SDDC Manager per la delega del dominio secondario della zona di cui è autorevole l'SDDC Manager.
* I server DNS di Active Directory sono configurati per puntare ai server DNS di {{site.data.keyword.cloud_notm}} per tutte le altre zone.
* Qualsiasi istanza secondaria da integrare alla prima istanza o all'istanza di destinazione deve utilizzare la stessa struttura dei nomi DNS sul dominio secondario di SDDC Manager.

## Servizi NTP
{: #design_commonservice-ntp}

Questa progettazione utilizza i server NTP dell'infrastruttura {{site.data.keyword.cloud_notm}}. Tutti i componenti distribuiti sono configurati per utilizzare questi server NTP. Per il corretto funzionamento dei certificati e dell'autenticazione di Active Directory, è fondamentale che tutti i componenti all'interno della progettazione utilizzino lo stesso server NTP.

Figura 1. Servizi NTP

![Servizi NTP](commonservice_ntp.svg "In questa progettazione, tutti i componenti di un'istanza utilizzano lo stesso server NTP dell'infrastruttura {{site.data.keyword.cloud_notm}} tramite il servizio NTP.")

## Servizi CA (Certificate Authority)
{: #design_commonservice-cas}

Per impostazione predefinita, VMware vSphere utilizza i certificati TLS firmati da VMware Certificate Authority (VMCA), che risiede sul dispositivo VMware PSC (Platform Services Controller). Questi certificati non sono considerati attendibili dai dispositivi o dai browser dell'utente finale. È buona norma per la sicurezza sostituire i certificati rivolti all'utente con certificati firmati da un'autorità di certificazione (CA) di terze parti o di livello aziendale. I certificati per la comunicazione machine-to-machine possono rimanere come certificati firmati da VMCA, tuttavia, si consiglia di seguire le procedure ottimali per la tua organizzazione, che in genere implicano l'utilizzo di una CA aziendale identificata.

Puoi utilizzare i server Windows AD in questa progettazione per creare certificati firmati dall'istanza locale. Tuttavia, puoi anche scegliere di configurare i servizi CA, laddove necessario.

## Link correlati
{: #design_commonservice-related}

* [Progettazione dell'infrastruttura fisica](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure)
* [Progettazione dell'infrastruttura virtuale](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure)
* [Progettazione della gestione dell'infrastruttura](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_infrastructuremgmt)
