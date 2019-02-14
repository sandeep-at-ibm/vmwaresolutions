---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Panoramica dell'architettura generale

Le seguenti informazioni forniscono ulteriori dettagli sull'architettura di rete utilizzata in questa architettura di riferimento. Si articola nelle seguenti sezioni:
* **Panoramica di VMware vCenter Server on {{site.data.keyword.cloud}}** – Descrive i punti salienti della piattaforma vCenter Server.
* **Panoramica della rete** – Fornisce informazioni sui componenti di rete utilizzati in questa architettura di riferimento:
  - **Rete di {{site.data.keyword.cloud_notm}}** – {{site.data.keyword.cloud_notm}} fornisce la rete fisica ed è completamente gestito da {{site.data.keyword.cloud_notm}}. Esamina le caratteristiche chiave della rete di {{site.data.keyword.cloud_notm}} per comprendere i flussi di rete tra siti in loco e non in loco e tra carichi di lavoro ospitati in servizi differenti.
  - **NSX-V** – La rete di vCenter Server è sviluppata sulla rete {{site.data.keyword.cloud_notm}} con una sovrapposizione fornita da VMware NSX-V. Questa sovrapposizione segmenta il traffico dalla rete sottostante di {{site.data.keyword.cloud_notm}} consentendo un maggior controllo e una maggiore configurabilità, incluso BYOIP (Bring Your Own IP).
  - **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} utilizza Calico come proprio plug-in CNI (Container Network Interface).
  - **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} utilizza Calico come proprio plug-in CNI (Container Network Interface).

* **Integrazione** – Descrive l'architettura dei componenti di rete per consentire i flussi e l'indirizzamento del traffico di rete richiesti:
  - Assegnazione di indirizzi IP
  - Flussi di traffico di rete

## Panoramica di vCenter Server

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle è un cloud privato ospitato che consente di estendere in modo semplice e rapido la tua infrastruttura in loco nel cloud per un'ibridità dell'infrastruttura senza interruzioni e sicura e una reale mobilità dell'applicazione.

vCenter Server Hybridity Bundle è distribuito su un minimo di quattro {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, offre l'archiviazione dedicata tramite una VSAN (virtual storage area network) e include la configurazione e la distribuzione automatica di un'infrastruttura di rete definita dal software di facile gestione (NSX-V). vCenter Server Hybridity Bundle è un'architettura di riferimento distribuita attraverso l'automazione, che garantisce la coerenza, le prestazioni e la conformità. In molti casi, puoi eseguire il provisioning dell'intero ambiente in meno di un giorno e l'infrastruttura bare metal può ridimensionare rapidamente ed elasticamente la capacità di calcolo e di archiviazione a seconda delle necessità.

Sono disponibili molte opzioni per valorizzare ed estendere vCenter Server Hybridity Bundle. Le offerte di servizi di {{site.data.keyword.cloud_notm}} non includono solo le opzioni di archiviazione come componente aggiuntivo e varie opzioni di connettività WAN pubblica e privata, ma coprono anche aree come la sicurezza della piattaforma, la sicurezza della rete, il bilanciamento del carico del traffico per il backup e il ripristino di emergenza.

I servizi di sicurezza della piattaforma includono HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, che fornisce sicurezza automatizzata e supporto di conformità, consentendo una migliore visibilità e controllo sul tuo ambiente cloud e sugli amministratori. HyTrust DataControl on {{site.data.keyword.cloud_notm}} fornisce la protezione dei dati con una potente crittografia e la gestione delle chiavi scalabili per proteggere i tuoi carichi di lavoro in tutto il loro ciclo di vita. {{site.data.keyword.cloud_notm}} Secure Virtualization semplifica la conformità e protegge i tuoi dati con la crittografia, le politiche di fencing virtuale e i controlli di accesso basati sul ruolo, mentre KMIP for VMware on {{site.data.keyword.cloud_notm}} offre la gestione del ciclo di vita della chiave di crittografia che gestisce le chiavi di crittografia utilizzate dai servizi {{site.data.keyword.cloud_notm}} o dalle applicazioni integrate del cliente.

Le opzioni di sicurezza di rete sono il FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} che fornisce una coppia altamente disponibili di dispositivi FortiGate Security Appliance per analizzare il traffico di rete e proteggere la tua infrastruttura virtuale e il FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, che distribuisce una coppia altamente disponibile di VM FortiGate su {{site.data.keyword.cloud_notm}} per ridurre il rischio implementando i controlli di sicurezza critici all'interno della tua infrastruttura virtuale. Ulteriori offerte per la sicurezza della rete sono in sviluppo.

L'offerta del servizio del programma di bilanciamento del carico di rete F5 on {{site.data.keyword.cloud_notm}} ottimizza le prestazioni le prestazioni e garantisce la disponibilità e la sicurezza delle tue applicazioni più critiche con la suite F5 BIG-IP.

L'offerta di backup e ripristino di emergenza da IBM, Veeam e Zerto fornisce sicurezza e operatività continua se si verifica un'emergenza. IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} è una soluzione di protezione e disponibilità dei dati per gli ambienti virtuali. Veeam on {{site.data.keyword.cloud_notm}} consente la disponibilità per Always-On Enterprise™ con backup, ripristino e replica integrati su {{site.data.keyword.cloud_notm}}. Zerto on {{site.data.keyword.cloud_notm}} fornisce ai clienti in loco e {{site.data.keyword.cloud_notm}} una soluzione di ripristino di emergenza sicura, flessibile e scalabile.

vCenter Server Hybridity Bundle non è un servizio gestito, anche se puoi aggiungere servizi gestiti da IBM per scaricare le operazioni quotidiane e la manutenzione dei livelli di virtualizzazione, sistemi operativi guest o applicazioni. Il team {{site.data.keyword.cloud_notm}} Professional Services è anche disponibile per aiutarti ad accelerare il tuo viaggio verso il cloud con servizi di migrazione, implementazione, pianificazione e incorporazione.

Le opzioni di integrazione della piattaforma di vCenter Server Hybridity Bundle non sono limitate alle opzioni disponibili da VMware come vRealize Suite o vSphere with Operations Management, ma si estendono a più offerte di servizi di {{site.data.keyword.cloud_notm}} quali [vCenter Server e {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks/vcsiks-intro.html) e [vCenter Server e {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp/vcsicp-intro.html), che utilizzano Terraform open source per gestire e fornire l'IaC (Infrastructure as Code).

Il vasto portafoglio di servizi e opzioni di integrazione di più offerte disponibili per vCenter Server Hybridity Bundle forniscono una piattaforma realmente ibrida che rende l'ibridità un servizio possibile.

### Link correlati

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
