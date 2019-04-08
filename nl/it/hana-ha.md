---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, high availability, highly available, SPOF, VLANs, HA, DR, disaster recovery, SAP NetWeaver

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Supporto per l'alta disponibilità di IBM Cloud 
{: #ha}

IaaS (Infrastructure as a service) di {{site.data.keyword.cloud}} ti offre una ambiente di calcolo solido con una distribuzione del sistema operativo (SO) facoltativa in primo piano che supporta le soluzioni di elevata disponibilità (HA). La soluzione si basa sulla versione SO supportata, che viene trattata in [SAP Note 2414097 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}. La soluzione HA è limitata alle licenze SO ordinate fornite con la tua distribuzione o alle licenze di terze parti, i, quali BYOL (bring your own license). Assicurati di discutere i dettagli HA con il supporto {{site.data.keyword.cloud_notm}} prima di eseguire la distribuzione. 

I sistemi operativi supportati e distribuiti da {{site.data.keyword.cloud_notm}} per SAP sono 
* Linux [Red Hat Enterprise Linux (RHEL) o SUSE Enterprise Linux Server (SLES)] supporta le soluzioni HA SAP NetWeaver e SAP HANA. Esistono delle limitazioni minori nell'ambiente {{site.data.keyword.cloud_notm}}, che vengono trattate in [Panoramica delle configurazioni di elevata disponibilità SAP NetWeaver](#overview-configs). 
* Microsoft Windows supporta solo le soluzioni HA SAP NetWeaver (a causa delle limitazioni del database SAP HANA). 

## Panoramica delle configurazioni di elevata disponibilità SAP NetWeaver 
{: #overview-configs}

Esistono molti documenti che forniscono una guida approfondita sulla pianificazione e l'installazione di un ambiente HA per i servizi SAP. I documenti includono informazioni su failover, replica, ridimensionamento incrementale e ripristino di emergenza (DR). Vengono forniti i riferimenti ad alcuni documenti quando appropriato. 

Tutti i sistemi operativi e le distribuzioni supportati da {{site.data.keyword.cloud_notm}} per una distribuzione SAP (Windows, Linux RHEL e SLES) sono forniti con estensioni specifiche e software di elevata di disponibilità. I seguenti sono i sistemi operativi e le distribuzioni supportati. 

* [New Failover Clustering Improvements in Windows Server 2012 and Its Benefits for SAP NetWeaver High Availability ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window} fornisce una descrizione in base al Microsoft Windows Server Failover Clustering (WFSC) sul sistema operativo Windows con SAP NetWeaver. 

* Esistono due guide di riferimento per la distribuzione di SAP NetWeaver in un ambiente HA basato su Linux con Linux Pacemaker: 
  * SUSE SAP NetWeaver High Availability Cluster 7.40 Setup Guide
  * Deploying Highly Available SAP NetWeaver-based Servers Using Red Hat Enterprise Linux HA add-on with Pacemaker

* [Building High Availability for SAP NetWeaver and SAP HANA on Linux ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} è un documento di procedure consigliate SAP e fornisce una descrizione tecnica approfondita con una forte attenzione su SAP HANA. 

* [SAP NetWeaver High Availability and Business Continuity in Virtual Environments with VMware and Hyper-V on Microsoft Windows ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window} copre gli aspetti della virtualizzazione se stai pianificando di implementare HA su server virtualizzati. 

Per ulteriori prodotti di elevata disponibilità certificati dai partner SAP per gli scenari di elevata disponibilità, vedi [High Availability Partner Information ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window}. Per i database non HANA SAP sono disponibili ulteriori informazioni sul failover HA e sulle configurazioni DR, nella tua documentazione del database. 

Tieni presente che l'accesso condiviso all'archiviazione NFS (Network File System)/CIFS (Common Internet File System) o all'archiviazione LUNS (logical unique number storage) basata su iSCSI, normalmente necessità di supportare il failover del sistema. L'archiviazione locale, combinata con un metodo di replica, normalmente necessita di supportare una configurazione simile a DR. Come con le installazioni in loco, controlla i requisiti di prestazioni e latenza del prodotto database quando pianifichi la tua distribuzione. 

## Ulteriori guide 
{: #extra-guide}

[Quorum-based storage](#quorum) e [Network considerations](#network) forniscono delle indicazioni che devi prendere in considerazione durante la tua distribuzione. Oltre alle considerazioni esposte in questi scenari, l'installazione di SAP NetWeaver e del relativo sistema database in un ambiente HA non è diversa da altre installazioni in loco. 

### Quorum-based storage
{: #quorum}

A causa delle limitazioni sulla sicurezza dell'ambiente {{site.data.keyword.cloud_notm}} IBM Cloud, l'accesso basato sulla rete per la gestione remota dei dispositivi tramite IPMI (Intelligent Platform Management Interface) non è disponibile. Gli ambienti cluster normalmente utilizzano i componenti basati su IPMI per “l'isolamento dei nodi del cluster” per garantire sempre un quorum. In assenza di un dispositivo abilitato IPMI, vengono utilizzati i dispositivi di archiviazione condivisa. In un ambiente {{site.data.keyword.cloud_notm}}, i dispositivi di archiviazione condivisa vengono implementati distribuendo un LUN iSCSI ai tuoi server come un dispositivo quorum. Ad esempio, un FSW (File Share Witness) su un cluster Microsoft e per SDB (storage-based death) per Stonith di Linux Pacemaker. 
* Fai clic [qui ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window} per ulteriori informazioni sui concetti cluster dell'elevata disponibilità di Linux. 
* Fai clic [qui ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window} per ulteriori informazioni sulla configurazione e gestione dei server di quorum per Windows Server 2012 e Windows Server 2012 R2. 

{{site.data.keyword.cloud_notm}} Storage dispone di funzionalità HA integrate, per cui un singolo LUN iSCSI condiviso non vuole introdurre un singolo punto di errore (SPOF) perché il tuo layout di rete è ridondante. Tuttavia, le specifiche del tuo prodotto cluster potrebbero richiedere più dispositivi quorum. 

### Network considerations
{: #network}

Un'installazione basata su {{site.data.keyword.cloud_notm}} viene fornita con una delle seguenti configurazioni di rete: 
* Rete privata 
* Rete pubblica
* Reti pubbliche e private
* Due reti private (su richiesta speciale) 

Come per le installazioni in loco, possono essere ordinati ulteriori adattatori di rete a seconda delle limitazioni fisiche dell'hardware. La limitazione è la stessa delle installazioni in loco. L'ordinazione di adattatori di rete ridondanti durante le distribuzioni hardware aiuta ad evitare SPOF nella tua topologia di rete. Gli adattatori ridondanti sono impostati in una configurazione di failover con Link Aggregation Control Protocol (LACP). Per Linux, l'impostazione utilizza le interfacce di bonding e gli adattatori di teaming vengono utilizzati per Microsoft Windows. L'infrastruttura di switch {{site.data.keyword.cloud_notm}} a cui sono connessi questi adattatori è ridondante, per cui non viene introdotto alcun nuovo SPOF. L'infrastruttura ridondante può essere utilizzata dalle VLAN ordinate. 

A seconda dei requisiti di rete, come ad esempio gli scenari di replica in una configurazione DR, devi controllare l'ubicazione dei dispositivi connessi e tutti i requisiti di rete specifici per il prodotto in questione. In alcuni casi, la replica basata sull'archiviazione istantanea {{site.data.keyword.cloud_notm}} potrebbe soddisfare i tuoi requisiti. Consultati con il supporto {{site.data.keyword.cloud_notm}} per determinare quale soluzione si adatta meglio alle tue necessità del processo di business. 
