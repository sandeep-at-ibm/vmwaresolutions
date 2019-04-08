---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, network connectivity, VLANs, external storage, high availability, highly available, disaster recovery, HA, DR, VLANs,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Elementi da considerare quando pianifichi il tuo scenario SAP
{: #considerations}

I sistemi SAP in uno scenario hanno requisiti specifici per la connettività, tra loro o con sistemi esterni. Devi anche pensare all'archiviazione esterna del tuo scenario e cosa fare se decidi di distribuire VMware al tuo server.

## Connettività di rete
{: #network_connectivity}

[La rete {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-about_ibmcloud_for_sap#ibm_cloud_network) fornisce una panoramica dell'approccio di {{site.data.keyword.cloud}} alla connettività di rete. I problemi con la connettività di rete possono causare ritardi significativi per il tuo progetto se non esegui la pianificazione in modo adeguato, indipendentemente da come pensi di utilizzare il tuo sistema.

In generale, hai due scelte di interfaccia per i tuoi server {{site.data.keyword.cloud_notm}} forniti con IaaS, la prima è un'interfaccia esterna con un IP pubblico. La seconda è un'interfaccia interna fornita con un “IP privato” conforme al Request for Comment (RFC) 1918. Puoi anche scegliere una sola interfaccia interna con un “IP privato.” L'IP esterno potrebbe essere più facile da utilizzare, ma esiste un rischio potenziale, anche se è installato e preconfigurato un firewall di base.

La seconda opzione accede alla VPN (Virtual Private Network) {{site.data.keyword.cloud_notm}} tramite il portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}} o distribuisce un dispositivo di sicurezza nel tuo scenario. I dispositivi di sicurezza sono offerti per i firewall, la conversione dell'indirizzo di rete, l'accesso VPN e altre funzioni di rete. Si consiglia che il tuo dipartimento di rete comunichi con il [supporto {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) dopo che è stato determinato il layout del tuo scenario e la connettività necessaria per livello dell'applicazione SAP.

### VLAN
{: #vlans}

Se vuoi separare tipi differenti di traffico di rete nel tuo scenario, puoi ordinare ulteriori LAN virtuali (VLAN). Tieni presente che le VLAN aggiuntive portano la segregazione del traffico, non aumentano le prestazioni. SAP generalmente consiglia di utilizzare reti da 10 Gb per il traffico tra i suoi server dell'applicazione e i database SAP HANA e per gli altri client SAP HANA, come SAP Business Intelligence. Se vuoi separare l'accesso amministrativo del tuo server SAP HANA da altri client, dovresti ordinare un'altra VLAN per il tuo scenario. Un'altra opzione è di separare il traffico tramite la rete privata e pubblica, poiché ulteriori uplink "fisici" non sono supportati da {{site.data.keyword.cloud_notm}}. Segui le raccomandazioni di SAP in [SAP HANA Tailored Data Center Integration (TDI) ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}.

L'accesso tramite la VPN, così come l'accesso da un jumpbox, consente l'accesso trasparente alle tue istanze SAP HANA da SAP HANA Studio.

## Archiviazione esterna
{: #external_storage}

In aggiunta all'archiviazione locale, potresti aver bisogno di ulteriore archiviazione per eseguire i backup. Per questi requisiti, puoi ordinare l'archiviazione blocchi o NAS (Network Attached Storage) come descritto in [Archiviazione](/docs/infrastructure/sap-hana?topic=sap-hana-iaas-overview#storage). Poiché gli ulteriori dati NFS (Network File System) e di archiviazione blocchi sono trasferiti tramite gli stessi adattatori fisici come tutto il restante traffico di rete, bisogna tenerne presente l'impatto.

Per l'archiviazione esterna, è importante calcolare i tuoi requisiti del progetto prima di decidere una soluzione di archiviazione. Se hai bisogno di ripristinare un sistema SAP HANA, gli IOPS della tua archiviazione hanno un'influenza significativa nella tua finestra di ripristino. Le finestre di backup non sono così critiche per SAP HANA poiché tutti i backup sono online indipendentemente da come configuri SAP HANA.

Ad esempio, utilizzando {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, puoi calcolare un ripristino approssimativo di 12 TB per SAP HANA a una massima velocità. Devi creare tre dispositivi di archiviazione fisici (LUN iSCSI archiviazione blocchi) perché la dimensione massima per dispositivo è 4 TB. Puoi creare uno stripe di questi tre dispositivi con il gestore del volume logico Linux e creare un dispositivo logico di 12 TB.

I 12 TB ti consentono 3x10 IOPS/GB, per un totale di 122,880 IOPS/GB a 16 KB. Questo ti fornisce un tempo di ripristino di 1.875 GB al secondo o un totale di meno di 2 ore. Poiché la misurazione degli IOPS è presa in una distribuzione 50/50 di lettura e scrittura, puoi considerare questi numeri come un limite inferiore delle prestazioni di ripristino. Si consiglia di eseguire i test di backup e ripristino se utilizzi una certa finestra di ripristino.

{{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, {{site.data.keyword.filestorage_full_notm}} o NAS possono essere utilizzati come spazio di backup o di archiviazione per ulteriori componenti software installati sul tuo server. L'archiviazione {{site.data.keyword.cloud_notm}} e NSA non può, tuttavia, essere utilizzata come archiviazione per SAP HANA perché queste opzioni non soddisfano i criteri KPI.

Per ulteriori informazioni, vedi [Getting started with {{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-GettingStarted#GettingStarted) e [Getting started with {{site.data.keyword.filestorage_full_notm}}](/docs/infrastructure/FileStorage?topic=FileStorage-GettingStarted#getting-started-with-file-storage).

## Scenari di elevata disponibilità e di ripristino di emergenza
{: #ha_dr}

L'ambiente {{site.data.keyword.cloud_notm}} non supporta alcuno scenario di elevata disponibilità (HA) preconfigurato. Tuttavia, ti consente di implementare le soluzioni HA per SAP HANA tramite le estensioni Red Hat Enterprise Linux HA, come un caso in loco.

La replica del sistema SAP HANA può essere configurata con un failover automatizzato da un server a una replica. Consulta la documentazione SAP sulla replica del sistema per determinare la modalità di replica che si adatta al meglio al tuo scenario dell'applicazione e al tuo livello di resilienza alle catastrofi. A seconda della modalità di replica, devono essere soddisfatti diversi KPI di rete. Consulta i consigli SAP sulla latenza e la velocità effettiva della rete per determinare la velocità effettiva richiesta e la latenza massima per la tua modalità dell'operazione scelta. La topologia di rete {{site.data.keyword.cloud_notm}} dovrebbe essere in grado di servire tutte le configurazioni richieste. Contatta il supporto {{site.data.keyword.cloud_notm}} per determinare la configurazione ottimale del tuo scenario se non sei sicuro o se vuoi che il tuo sito di ripristino di emergenza in un diverso data center archivi la resilienza alle catastrofi massima.

Tieni presente che gli ambienti con scaling incrementale SAP HANA (a più nodi) sono ancora in corso di valutazione. In altre parole, un nodo di standby per SAP HANA non è un'opzione corrente in un ambiente {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni sull'alta disponibilità e sul ripristino di emergenza, consulta [Supporto di elevata disponibilità {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha) e [Ripristino di emergenza (DR)](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

Per ulteriori informazioni sulla replica del sistema e la latenza e la velocità effettiva della rete, consulta
  * [How To Perform System Replication for SAP HANA ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html){: new_window}
  * [Network Required for SAP HANA System Replication ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html){: new_window}

Per ulteriori informazioni sulla configurazione delle estensioni cluster HA per il tuo sistema operativo Linux, consulta
  * [Automated SAP HANA System Replication with Pacemaker on RHEL Setup Guide ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://access.redhat.com/articles/1466063){: new_window}
  * [SAP HANA SR Performance Optimized Scenario ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf){: new_window}

## Distribuzioni server VMware ESXi
{: #vmware_server}

Tutti i server nell'offerta {{site.data.keyword.cloud_notm}} SAP HANA sono certificati per VMware ESX, che rende SAP HANA distribuibile nelle macchine virtuali (VM). Se un server viene ordinato con VMware ESX, viene distribuito con un'istanza ESX configurata di base e preinstallata; non viene distribuita alcuna VM. Tieni presente che sei responsabile della distribuzione del sistema operativo guest corretto in una distribuzione basata su ESX. Segui le istruzioni definite in SAP Note 2414820 per scegliere una versione del sistema operativo supportata da SAP HANA in {{site.data.keyword.cloud_notm}}.

Il processo di ridimensionamento di una distribuzione basata su ESX è diverso da quello di una distribuzione di un server bare metal. Segui i consigli in *Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*. Il sovraccarico del livello di virtualizzazione necessita di essere ricalcolato, seguendo le regole in *Architecture...and Considerations Guide*. Dopo che il sistema operativo guest è stato distribuito a una VM, assicurati che i KPI SAP HANA TDI siano rispettati. Controlla SAP Note 1943937 per i dettagli sulla verifica dell'ambiente per la conformità con i prerequisiti del supporto SAP. I prerequisiti devono essere completati per ogni VM distribuita a un server specifico.

Devono essere seguite molte altre regole definite da SAP per distribuire SAP HANA in un ambiente virtualizzato. Per la produzione, segui le limitazioni descritte in SAP Note 1995460. SAP Note 2024433 descrive le regole per più VM a un server.

Per maggiori informazioni, consulta la seguente documentazione:
  * [SAP Note 2414820 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/2414820){: new_window}
  * [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide* ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window}
  * [SAP Note 1943937 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/1943937){: new_window}
  * [SAP HANA Tailored Data Center Integration Frequently Asked Questions ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html){: new_window}
  * [SAP Note 1995460 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/1995460){: new_window}
  * [SAP Note 2024433 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/2024433){: new_window}
  * [SAP HANA Tailored Data Center Intgration (TDI) Overview ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}
