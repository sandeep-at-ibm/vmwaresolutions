---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Informazioni su IBM Cloud for VMware Solutions

{{site.data.keyword.vmwaresolutions_full}} ti consente di integrare o migrare in modo rapido e uniforme i carichi di lavoro VMware in loco su {{site.data.keyword.cloud_notm}} utilizzando l'infrastruttura {{site.data.keyword.cloud_notm}} scalabile, sicura e ad alte prestazioni e la tecnologia di virtualizzazione ibrida VMware leader del settore.

{{site.data.keyword.vmwaresolutions_short}} ti permette di distribuire facilmente i tuoi ambienti virtuali VMware e di gestire le risorse dell'infrastruttura su {{site.data.keyword.cloud_notm}}. Allo stesso tempo, puoi ancora utilizzare la tua console dei prodotti VMware nativa per gestire i carichi di lavoro VMware.

## Vantaggi di IBM Cloud for VMware Solutions

{{site.data.keyword.vmwaresolutions_short}} fornisce i seguenti vantaggi principali:
* **Portata globale**: ti consente di espandere lo spazio occupato dal tuo cloud ibrido fino a 30 {{site.data.keyword.CloudDataCents_notm}} di classe aziendale in tutto il mondo.
* **Integrazione senza problemi**: consente una perfetta integrazione tra il cloud ibrido e l'infrastruttura {{site.data.keyword.cloud_notm}}.
* **Provisioning rapido**: automatizza la distribuzione e la configurazione dell'ambiente VMware, consentendoti di distribuire rapidamente un ambiente VMware di classe aziendale con server virtuali e {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}} su richiesta.
* **Semplificazione**: ti consente di utilizzare una piattaforma cloud VMware senza la necessità di identificare, acquisire, distribuire e gestire l'infrastruttura fisica sottostante (calcolo, archiviazione e rete) e le licenze software.
* **Flessibilità di espansione e contrazione**: ti consente di espandere e contrarre facilmente i tuoi carichi di lavoro VMware in base alle tue esigenze aziendali.
* **Singola console di gestione**: fornisce un'unica console per la distribuzione, l'accesso e la gestione degli ambienti VMware su {{site.data.keyword.cloud_notm}}.

## Offerte di distribuzione

{{site.data.keyword.vmwaresolutions_short}} offre scelte di distribuzione standardizzate e personalizzabili degli ambienti virtuali VMware. Sono offerti i seguenti tipi di distribuzione:
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**: l'offerta vCenter Server ti consente di distribuire un ambiente virtuale VMware utilizzando risorse di calcolo, archiviazione e rete personalizzate per soddisfare al meglio le tue esigenze aziendali.
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle**: l'offerta vCenter Server with Hybridity è un cloud privato ospitato che consente di estendere in modo semplice e rapido la tua infrastruttura in loco nel cloud. L'ambiente VMware è basato sulle licenze Software Defined Data Center VMware fornite da IBM e comprende VMware Hybrid Cloud Extension (HCX). Utilizzando HCX, puoi connettere in modo sicuro un ambiente vSphere 5.0+ in loco con i siti IBM Cloud per un'ibridità dell'infrastruttura senza interruzioni e una reale mobilità dell'applicazione.
* **VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}**: l'offerta Cloud Foundation fornisce un ambiente virtuale VMware unificato utilizzando le risorse di calcolo, archiviazione e rete {{site.data.keyword.cloud_notm}} standard dedicate alla distribuzione di ciascun utente.
* **VMware vSphere on {{site.data.keyword.cloud_notm}}**: l'offerta vSphere on {{site.data.keyword.cloud_notm}} fornisce un servizio di virtualizzazione personalizzabile che combina {{site.data.keyword.baremetal_short}}, componenti hardware e licenze compatibili con VMware per creare il tuo proprio ambiente VMware ospitato su IBM.
* **NetApp ONTAP Select**: l'offerta NetApp ONTAP Select ti consente di distribuire un cluster di archiviazione definita dal software che risponda alle tue esigenze di un'applicazione di archiviazione dedicata e altamente disponibile basata su NetApp ONTAP Select.
* **VMware Federal on {{site.data.keyword.cloud_notm}}**: l'offerta VMware Federal on {{site.data.keyword.cloud_notm}} fornisce supporto per ordinare un'istanza vCenter Server di base oltre a fornire l'opzione per proteggere le istanze distribuite, rimuovere le informazioni sensibili e la connessione di gestione aperta per l'accesso in corso all'istanza per le funzioni di gestione.

## Servizi aggiuntivi

{{site.data.keyword.vmwaresolutions_short}} ti consente di aggiungere vari servizi al momento dell'ordine o dopo la distribuzione dell'istanza. Sono offerti i seguenti servizi:

### FortiGate Security Appliance on IBM Cloud

Questo servizio distribuisce una coppia HA di dispositivi FortiGate Security Appliance della serie 300 in grado di fornire servizi di firewall, instradamento, NAT e VPN per proteggere la connessione di rete pubblica al tuo ambiente.

Questo servizio è disponibile solo per le istanze distribuite nelle release della V1.8 o successive.

Per ulteriori informazioni, vedi [Gestione di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

Questo servizio distribuisce una coppia HA di dispositivi FortiGate Virtual Appliance che ti consente di ridurre i rischi implementando controlli di sicurezza critici all'interno della tua infrastruttura virtuale.

Questo servizio è disponibile solo per le istanze distribuite nelle release della V2.0 o successive.

Per ulteriori informazioni, vedi [Gestione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html).

### F5 on IBM Cloud

Questo servizio ottimizza le prestazioni e garantisce disponibilità e sicurezza per le applicazioni con F5 BIG-IP Virtual Edition (VE).

Questo servizio è disponibile solo per le istanze distribuite nelle release della V1.9 o successive.

Per ulteriori informazioni, vedi [Gestione di F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html).

### IBM Spectrum Protect Plus on IBM Cloud

Questo servizio fornisce una soluzione efficiente e scalabile per la protezione dei dati, il riutilizzo dei dati e il recupero dei dati per gli ambienti virtuali. Puoi implementarlo come soluzione autonoma o integrarlo con il tuo ambiente IBM Spectrum Protect&trade; Plus per scaricare copie per la governance di dati e archiviazione a lungo termine.

**Note**:
* Questo servizio è disponibile solo per le istanze che sono distribuite o aggiornate alle release della V2.2 o successive.
* er le istanze distribuite nelle release della V2.3 o successive, IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} fornisce il backup per la gestione automatica delle VM.
* Per le istanze distribuite nella V2.2, questo servizio fornisce la protezione dei dati solo per le VM del carico di lavoro.

Per ulteriori informazioni, vedi [Gestione di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html).

### Veeam on IBM Cloud

Questo servizio si integra perfettamente con il tuo ambiente VMware per aiutarti a gestire il backup e il ripristino di tutte le macchine virtuali (VM) nel tuo ambiente, compreso il backup e il ripristino dei componenti di gestione. Può fornire un obiettivo del punto di ripristino (RPO) inferiore a 15 minuti dopo la configurazione dei dati.

Questo servizio è configurato per eseguire il backup delle VM di gestione subito dopo la distribuzione della tua istanza.

Questo servizio è disponibile solo per le istanze distribuite nelle release della V1.8 o successive.

Per ulteriori informazioni, vedi [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html).

### Zerto on IBM Cloud

Questo servizio fornisce funzionalità di replica e ripristino di emergenza per proteggere i tuoi carichi di lavoro. Per ulteriori informazioni, vedi [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html).

### Servizi gestiti da IMI

Questi servizi consentono a IBM Integrated Managed Infrastructure (IMI) di offrire servizi di gestione remota dinamici per una vasta gamma di infrastrutture cloud.

Questi servizi sono disponibili solo per le istanze Cloud Foundation.

Per ulteriori informazioni, vedi [Richiesta di servizi gestiti da IMI](../services/managing_imi.html).

## Link correlati

* [Introduzione](../index.html)
* [Panoramica di Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Panoramica di vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [NetApp ONTAP Select](../netapp/np_netappoverview.html)
