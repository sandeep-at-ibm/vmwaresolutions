---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: single-node trial, migration app modernization, tech specs migration app modernization

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di Single-node Trial for Migration and App Modernization
{: #cloud_modern_bundle_overview}

Single-node Trial for Migration and App Modernization ti consente di eseguire un test drive di {{site.data.keyword.cloud_notm}} per migrare i carichi di lavoro VMware in {{site.data.keyword.cloud}} e quindi modernizzare semplici carichi di lavoro utilizzando i contenitori.

Single-node Trial è una versione di prova di {{site.data.keyword.cloud_notm}} Private Hosted su VMware vCenter Server on {{site.data.keyword.cloud_notm}} che fornisce la piattaforma di gestione di Kubernetes per i contenitori e la piattaforma VMware a singolo tenant che può essere gestita utilizzando gli stessi strumenti degli ambienti in loco. Puoi sfruttare la velocità e le funzionalità di ridimensionamento del cloud mantenendo allo stesso tempo il medesimo livello di controllo e di visibilità fornito in loco.

La versione di prova è progettata per la migrazione di massimo 20 semplici carichi di lavoro di sviluppo o test utilizzando vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle e la containerizzazione di tali carichi di lavoro con la piattaforma di sviluppo di applicazioni {{site.data.keyword.cloud_notm}} Private Hosted basata su Kubernetes. L'automazione installerà e configurerà VMware HCX in {{site.data.keyword.cloud_notm}}, fornirà una chiave di attivazione HCX in loco e installerà e configurerà una piccola topologia di sviluppo/test di {{site.data.keyword.cloud_notm}} Private Hosted in poche ore.

Single-node Trial for Migration and App Modernization è solo per una prova di utilizzo. Non eseguire i carichi di lavoro di produzione su questo ambiente. Le funzioni di gestione come l'aggiunta e la rimozione di host e cluster, l'ordinazione di servizi aggiuntivi e l'applicazione di aggiornamenti non sono supportate.
{:important}

Per ottenere il massimo dall'istanza Single-node Trial, puoi utilizzare [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:external} da [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:external}, che può aiutarti a migrare i tuoi carichi di lavoro VMware in {{site.data.keyword.cloud_notm}}. Inoltre, [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:external} può aiutarti ad accelerare la modernizzazione dell'applicazione attraverso le più recenti pratiche native cloud.

Questa versione di prova è destinata ad essere utilizzata per un massimo di 90 giorni. Al termine della versione di prova, puoi eliminare questo ambiente ed eseguire il provisioning di un nuovo ambiente che soddisfi le tue esigenze di capacità.
{:note}

## Specifiche tecniche per le istanze Single-node Trial for Migration and App Modernization
{: #cloud_modern_bundle_overview-tech-specs}

I seguenti componenti sono inclusi nella tua istanza Single-node Trial for Migration and App Modernization.

La disponibilità e il prezzo delle configurazioni hardware standardizzate possono variare in base al {{site.data.keyword.CloudDataCent_notm}} selezionato per la distribuzione.
{:note}

### Bare Metal Server
{: #cloud_modern_bundle_overview-bare-metal}

Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz con 384 GB di RAM) per un massimo di 20 VM

#### Overcommit della CPU
{: #cloud_modern_bundle_overview-cpu}

* Overcommit della CPU 16:1 per la gestione di vCenter Server, HCX e 20 VM del carico di lavoro del cliente
* Overcommit della CPU 11:1 per {{site.data.keyword.cloud_notm}} Private

#### Overcommit della RAM
{: #cloud_modern_bundle_overview-ram}

* Overcommit della RAM 1.22:1 per una distribuzione del cliente di 20 VM del carico di lavoro con 8 GB ciascuna
* 1:1 (nessun overcommit) per una distribuzione del cliente di nove VM del carico di lavoro con 8 GB ciascuna

### Archiviazione NFS
{: #cloud_modern_bundle_overview-nfs-storage}

* 2 TB per la gestione
* 1 TB per il carico di lavoro del cliente (per 20 VM del cliente)
* 4 TB per {{site.data.keyword.cloud_notm}} Private Hosted

### Specifiche di rete per le istanze Single-node Trial for Migration and App Modernization
{: #cloud_modern_bundle_overview-networking-specs}

Vengono ordinati i seguenti componenti di rete:
*  Doppi uplink di rete privata e pubblica da 10 Gbps
*  Tre VLAN (Virtual LAN): una VLAN pubblica e due VLAN private
*  Una VXLAN (Virtual eXtensible LAN) con DLR (Distributed Logical Router) per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2). La VXLAN viene distribuita come topologia di instradamento di esempio, che puoi modificare, compilare o rimuovere. Puoi anche aggiungere zone di sicurezza collegando altre VXLAN a nuove interfacce logiche sul DLR.
*  Due gateway dei servizi edge VMware NSX:
  * Un gateway dei servizi edge (ESG) VMware NSX sicuro dei servizi di gestione per il traffico di gestione HTTPS in uscita, distribuito da IBM come parte della tipologia di rete di gestione. Questo ESG viene utilizzato dalle VM di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione.

    Non puoi accedere a questo ESG e non puoi usarlo. Se lo modifichi, potresti non essere in grado di gestire l'istanza Single-node Trial for Migration and App Modernization dalla console {{site.data.keyword.vmwaresolutions_short}}. Inoltre, tieni presente che l'utilizzo di un firewall o la disabilitazione delle comunicazioni ESG ai componenti di gestione IBM esterni causerà l'inutilizzabilità di {{site.data.keyword.vmwaresolutions_short}}.
    {:important}
  * Un gateway dei servizi edge VMware NSX sicuro gestito dal cliente per il traffico del carico di lavoro HTTPS in uscita e in entrata, distribuito da IBM come template che puoi modificare per fornire l'accesso VPN o l'accesso pubblico.

### VSI (Virtual Server Instance)
{: #cloud_modern_bundle_overview-vsi}

Vengono ordinate le seguenti VSI (Virtual Server Instance):

* Una VSI per IBM CloudBuilder, che viene annullata al termine della distribuzione dell'istanza.
* Viene distribuita una VSI di Microsoft Windows Server per Microsoft Active Directory (AD) che può essere consultata. La VSI funziona come DNS per l'istanza in cui sono registrati gli host e le VM.

### Licenze fornite da IBM e tariffe
{: #cloud_modern_bundle_overview-license-and-fee}

Con il tuo ordine dell'istanza Single-node Trial for Migration and App Modernization sono incluse le seguenti licenze.

* VMware vSphere Enterprise Plus 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Le istanze Single-node Trial for Migration and App Modernization non supportano l'opzione BYOL (Bring Your Own License).
{:note}

## Specifiche tecniche per VMware HCX on IBM Cloud
{: #cloud_modern_bundle_overview-hcx-tech-specs}

Single-node Trial for Migration and App Modernization include HCX on {{site.data.keyword.cloud_notm}}. Nel servizio HCX on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

Le istanze HCX in loco includono solo la licenza e l'attivazione.
{:note}

### Una coppia attivo/passivo di gateway dei servizi edge (ESG) VMware NSX per la gestione HCX
{: #cloud_modern_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo di gestione HCX - VM (Virtual Machine)
{: #cloud_modern_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: 60 GB VMDK

Ulteriori dispositivi HCX vengono distribuiti durante la configurazione in base alle esigenze di connettività L2, ottimizzazione WAN e connessioni gateway.

### Specifiche di rete per HCX on IBM Cloud
{: #cloud_modern_bundle_overview-hcx-networking-specs}

* Una sottorete portatile pubblica con 16 indirizzi IP
* Due sottoreti portatili private con 64 indirizzi IP
* Otto indirizzi IP dalla sottorete vMotion portatile privata

## Specifiche tecniche per IBM Cloud Private Hosted
{: #cloud_modern_bundle_overview-icp-tech-specs}

{{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 viene installato utilizzando la topologia di sviluppo/test su tutte le istanze Single-node Trial for Migration and App Modernization. Per ulteriori informazioni su {{site.data.keyword.cloud_notm}} Private Hosted, vedi [Panoramica su {{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview).

## Specifiche tecniche per IBM Cloud Automation Manager
{: #cloud_modern_bundle_overview-cam-tech-specs}

{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 viene installato utilizzando la topologia di sviluppo/test su tutte le istanze Single-node Trial for Migration and App Modernization. Per ulteriori informazioni su {{site.data.keyword.cloud_notm}} Automation Manager, vedi [{{site.data.keyword.cloud_notm}} Automation Manager documentation](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: external}.

## Link correlati
{: #cloud_modern_bundle_overview-related}

* [Guida di vCenter Server e {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Apri un ticket per {{site.data.keyword.cloud_notm}} privato](https://www.ibm.com/mysupport/s/?language=en_US){:external}
* [Risorse VMware HCX](https://hcx.vmware.com/#/docs){:external}
* [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
