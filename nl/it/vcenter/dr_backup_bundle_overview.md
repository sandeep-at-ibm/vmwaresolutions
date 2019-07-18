---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

keywords: single-node trial, data protection DR, tech specs data protection DR

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview}

Single-node Trial for Data Protection and Disaster Recovery ti consente di eseguire un test drive di {{site.data.keyword.cloud}} per migrare e recuperare i carichi di lavoro VMware su {{site.data.keyword.cloud_notm}}. Inoltre, Single-node Trial for Data Protection and Disaster Recovery include i servizi Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX on {{site.data.keyword.cloud_notm}} e Zerto on {{site.data.keyword.cloud_notm}}.

Single-node Trial è una versione di prova di VMware vCenter Server on {{site.data.keyword.cloud_notm}} che fornisce la piattaforma VMware a singolo tenant che può essere gestita utilizzando gli stessi strumenti degli ambienti in loco. Puoi sfruttare la velocità e le funzionalità di ridimensionamento del cloud mantenendo allo stesso tempo il medesimo livello di controllo e di visibilità fornito in loco.

La versione di prova è progettata per la migrazione di un massimo di 20 semplici carichi di lavoro di sviluppo o test utilizzando vCenter Server on {{site.data.keyword.cloud_notm}} con Hybridity Bundle. L'automazione installerà e configurerà VMware HCX in {{site.data.keyword.cloud_notm}}, fornirà una chiave di attivazione HCX in loco e installerà Veeam on {{site.data.keyword.cloud_notm}} e Zerto on {{site.data.keyword.cloud_notm}} nel giro di poche ore. Puoi eseguire il backup e la replica di 20 macchine virtuali (VM) con Veeam on {{site.data.keyword.cloud_notm}} e Zerto on {{site.data.keyword.cloud_notm}}. 

Single-node Trial for Data Protection and Disaster Recovery è solo per una prova di utilizzo PoC (proof of concept). Non eseguire i carichi di lavoro di produzione su questo ambiente. Le funzioni di gestione come l'aggiunta o la rimozione degli host e dei cluster, l'ordine di ulteriori servizi di componenti aggiuntivi e l'applicazione degli aggiornamenti non sono supportate.
{:important}

Una volta distribuita la tua istanza Single-node Trial, puoi utilizzare [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:external} da [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:external} per assistenza con la tua istanza. Inoltre, [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:external} può aiutarti ad accelerare la modernizzazione dell'applicazione attraverso le più recenti pratiche native cloud.

Questa versione di prova è destinata ad essere utilizzata per un massimo di 90 giorni. Gli addebiti ricorrenti mensili sono fatturati in base alla tua pianificazione di fatturazione e non quando viene ordinata l'istanza. Se l'istanza non viene annullata l'ultimo giorno del tuo ciclo di fatturazione, o prima, ti viene addebitato il mese successivo. Una versione di prova di 90 giorni potrebbe comportare quattro mesi di addebito, a meno che l'annullamento non venga completato prima dell'inizio del quarto mese.
{:note}

Al termine della versione di prova, puoi eliminare questo ambiente ed eseguire il provisioning di un nuovo ambiente che soddisfi le tue esigenze di capacità.

## Specifiche tecniche per le istanze Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview-tech-specs}

I seguenti componenti sono inclusi nella tua istanza Single-node Trial for Data Protection and Disaster Recovery.

La disponibilità e il prezzo delle configurazioni hardware standardizzate possono variare in base al {{site.data.keyword.CloudDataCent_notm}} selezionato per la distribuzione.
{:note}

### Bare Metal Server
{: #dr_backup_bundle_overview-bare-metal}

Processore Skylake Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz con 384 GB di RAM per un massimo di 20 VM

#### Overcommit della CPU
{: #dr_backup_bundle_overview-cpu}

Overcommit della CPU 16:1 per la gestione di vCenter Server, HCX e 20 VM del carico di lavoro del cliente

#### Overcommit della RAM
{: #dr_backup_bundle_overview-ram}

* Overcommit della RAM 1.22:1 per una distribuzione del cliente di 20 VM del carico di lavoro con 8 GB ciascuna
* 1:1 (nessun overcommit) per una distribuzione del cliente di nove VM del carico di lavoro con 8 GB ciascuna

### Archiviazione NFS
{: #dr_backup_bundle_overview-nfs-storage}

* 2 TB per la gestione
* 1 TB per il carico di lavoro del cliente (per 20 VM del cliente)

### Specifiche di rete per le istanze Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview-networking-specs}

Vengono ordinati i seguenti componenti di rete:
*  Doppi uplink di rete privata e pubblica da 10 Gbps
*  Tre VLAN (Virtual LAN): una VLAN pubblica e due VLAN private
*  Una VXLAN (Virtual eXtensible LAN) con DLR (Distributed Logical Router) per la potenziale comunicazione est-ovest tra carichi di lavoro locali connessi alle reti di livello 2 (L2). La VXLAN viene distribuita come topologia di instradamento di esempio, che puoi modificare, compilare o rimuovere. Puoi anche aggiungere zone di sicurezza collegando altre VXLAN a nuove interfacce logiche sul DLR.
*  Due gateway dei servizi edge VMware NSX:
  * Un gateway dei servizi edge (ESG) VMware NSX sicuro dei servizi di gestione per il traffico di gestione HTTPS in uscita, distribuito da IBM come parte della tipologia di rete di gestione. Questo ESG viene utilizzato dalle VM di gestione IBM per comunicare con specifici componenti di gestione IBM esterni correlati all'automazione.

    Non puoi accedere a questo ESG e non puoi usarlo. Se lo modifichi, potresti non essere in grado di gestire l'istanza Single-node Trial for Data Protection and Disaster Recovery dalla console {{site.data.keyword.vmwaresolutions_short}}. Inoltre, tieni presente che l'utilizzo di un firewall o la disabilitazione delle comunicazioni ESG ai componenti di gestione IBM esterni causerà l'inutilizzabilità di {{site.data.keyword.vmwaresolutions_short}}.
    {:important}
  * Un gateway dei servizi edge VMware NSX sicuro gestito dal cliente per il traffico del carico di lavoro HTTPS in uscita e in entrata, distribuito da IBM come template che puoi modificare per fornire l'accesso VPN o l'accesso pubblico.

### VSI (Virtual Server Instance)
{: #dr_backup_bundle_overview-vsi}

Vengono ordinate le seguenti VSI (Virtual Server Instance):

* Una VSI per IBM CloudBuilder, che viene annullata al termine della distribuzione dell'istanza.
* Viene distribuita una VSI di Microsoft Windows Server per Microsoft Active Directory (AD) che può essere consultata. La VSI funziona come DNS per l'istanza in cui sono registrati gli host e le VM.
* Una VSI per Zerto su {{site.data.keyword.cloud_notm}} - Zerto Virtual Manager.
* Una VSI con Veeam Backup and Replication 9.5 OS Add-on e Veeam Availability Suite 9.5.

### Licenze fornite da IBM e tariffe
{: #dr_backup_bundle_overview-license-and-fee}

Le seguenti licenze sono incluse con il tuo ordine dell'istanza Single-node Trial for Data Protection and Disaster Recovery.

* Il vCenter Server con le licenze Hybridity Bundle:
  * VMware vSphere Enterprise Plus 6.7u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Le istanze Single-node Trial for Data Protection and Disaster Recovery non supportano l'opzione BYOL (Bring Your Own License).
{:note}

## Specifiche tecniche per VMware HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-tech-specs}

Single-node Trial for Data Protection and Disaster Recovery include HCX on {{site.data.keyword.cloud_notm}}. Nel servizio HCX on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

Le istanze HCX in loco includono solo la licenza e l'attivazione.
{:note}

### Una coppia attivo/passivo di gateway dei servizi edge (ESG) VMware NSX per la gestione HCX
{: #dr_backup_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo di gestione HCX - VM (Virtual Machine)
{: #dr_backup_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: 60 GB VMDK

Ulteriori dispositivi HCX vengono distribuiti durante la configurazione in base alle esigenze di connettività L2, ottimizzazione WAN e connessioni gateway.

### Specifiche di rete per HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-networking-specs}

* Una sottorete portatile pubblica con 16 indirizzi IP
* Due sottoreti portatili private con 64 indirizzi IP
* Otto indirizzi IP dalla sottorete vMotion portatile privata

## Specifiche tecniche per Veeam on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-veeam-tech-specs}

Single-node Trial for Data Protection and  Disaster Recovery include Veeam on {{site.data.keyword.cloud_notm}}. Nel servizio Veeam on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

* Licenza di 25 pacchetti di Veeam Availability Suite
* 4000 GB di archiviazione
* Prestazioni dell'archiviazione di 0,25 IOPS/GB
* Windows Server 2016 Standard Edition (64 bit)
* Core 4 x 2,0 GHz
* 8 GB di RAM
* Uplink di rete privata da 1 Gbps
* Disco da 100 GB (SAN)

## Specifiche tecniche per Zerto on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-zerto-tech-specs}

Single-node Trial for Data Protection and Disaster Recovery include Zerto on {{site.data.keyword.cloud_notm}}. Nel servizio Zerto on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

* Licenza Zerto Virtual Replication V6.5u3
* Una VSI (Virtual Service Instance) - Zerto Virtual Manager
* Core 2 x 2,0 GHz
* 4 GB di RAM
* Windows Server 2016 Standard Edition (64 bit)
* Disco da 100 GB (SAN)

## Specifiche tecniche per IBM Cloud Automation Manager
{: #dr_backup_bundle_overview-cam-tech-specs}

{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 viene installato utilizzando la topologia di sviluppo/test su tutte le istanze Single-node Trial for Data Protection and Disaster Recovery. Per ulteriori informazioni su {{site.data.keyword.cloud_notm}} Automation Manager, vedi [{{site.data.keyword.cloud_notm}} Automation Manager documentation](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: external}.

## Link correlati
{: #dr_backup_bundle_overview-related}

* [Risorse VMware HCX](https://hcx.vmware.com/#/docs){:external}
* [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)
