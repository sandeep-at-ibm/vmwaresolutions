---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, {{site.data.keywords.baremetal_short}}, data centers, VPN,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Panoramica di SAP HANA on IBM Cloud IaaS
{: #iaas-overview}

Un ambiente Infrastructure-as-a-server (IaaS) è formato da molti componenti: data center, calcolo, connettività, archiviazione e rete.

## Data center

Con i data center in Nord e Sud America, Europa, Asia e Australia, puoi fornire risorse cloud dove (e quando) ti servono. Ogni data center è collegato alla rete privata globale di {{site.data.keyword.cloud_notm}}, rendendo i trasferimenti dei dati più veloci e efficienti ovunque nel mondo.

Per maggiori informazioni, consulta [Data Center ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

## Server bare metal

{{site.data.keyword.baremetal_long}} sono server fisici con funzionalità di personalizzazione limitate. I server sono dedicati al tuo utilizzo o dei tuoi clienti e non sono condivisi, neanche in parte, incluse le risorse del server, con altri clienti {{site.data.keyword.cloud_notm}} e sono forniti come un server fisico completo in esecuzione su un sistema operativo (SO) di tua scelta. I sistemi operativi per l'offerta SAP HANA sono Red Hat Enterprise Linux 7.4 per SAP HANA, SUSE Linux Enterprise Server 12 SP2 per SAP HANA e VMware Server Virtualization 6.5.

Poiché la personalizzazione è limitata sui server bare metal, sono ottenibili tempi di provisioning più veloci di 1 - 4 ore. Il provisioning rapido è utile quando stai tentando di ottenere un'applicazione dal mercato prima della concorrenza.

Ti viene offerto un array di combinazioni di RAM e CPU poiché i server certificati SAP hanno molte RAM e CPU preconfigurate. La combinazione *non può* essere modificata durante il processo d'ordine o tramite un ticket di supporto dopo la distribuzione dei server.

Per ulteriori informazioni, consulta [About bare metal servers](/docs/bare-metal?topic=bare-metal-about#about).

## Connettività di rete

La connettività VPN (Virtual private network) alla rete cloud virtuale {{site.data.keyword.cloud_notm}} viene concessa automaticamente quando viene configurato il tuo account {{site.data.keyword.cloud_notm}}. Per impostazione predefinita, il tuo server ha un indirizzo IP privato e pubblico. Se vuoi che il tuo server sia privato, puoi disattivare l'interfaccia pubblica dopo il provisioning del tuo server o ordinarlo come privato.

Mentre i requisiti della rete per SAP HANA (rete ridondante da 10 Gb) sono soddisfatti dall'offerta {{site.data.keyword.cloud_notm}}, potresti voler soddisfare la latenza e la velocità effettiva dei KPI (key performance indicator), a seconda del tuo scenario di applicazione. Per ulteriori informazioni sulla determinazione in quale data center posizionare il tuo server SAP HANA e sulla decisione della soluzione di connettività di rete migliore, consulta le considerazioni sulla [Connettività di rete](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#network_connectivity).

Per ulteriori informazioni, vedi [Introduzione a VPN (Virtual Private Networking)](/docs/infrastructure/iaas-vpn?topic=VPN-getting-started-with-virtual-private-networking-vpn-#getting-started-with-virtual-private-networking-vpn-) e il libro bianco [*SAP HANA Network Requirements* ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html){: new_window}.

## Archiviazione
{: #storage}

L'archiviazione locale viene fornita con il tuo {{site.data.keyword.baremetal_short}} e utilizza la LAN virtuale di rete privata (VLAN) {{site.data.keyword.cloud_notm}} per fornire la sicurezza a livello aziendale mentre non blocca l'accesso dell'amministratore. Per i server certificati SAP HANA, è progettata e configurata per soddisfare i KPI definiti da SAP per la velocità effettiva e la latenza in conformità ai criteri di certificazione SAP HANA. L'archiviazione locale ha la dimensione rilevante di diversi file system secondari come definito dalla SAP HANA Installation Guide (`data.log` e `shared`). Nessun ulteriore adattamento deve essere fatto dall'utente.

Esistono due tipi di archiviazione per {{site.data.keyword.cloud_notm}}-blocchi e file-tra cui scegliere per eseguire i backup e i ripristini di SAP HANA. Entrambi i tipi utilizzano le operazioni di input/output al secondo (IOPS), che sono utilizzate per determinare i bisogni di archiviazione. Gli IOPS sono misurati in base alla dimensione blocco di 16 KB con un mix 50/50 di lettura/scrittra. Per raggiungere il numero massimo di IOPS su un volume, devono essere utilizzate adeguate risorse di rete. Altre considerazioni includono l'utilizzo della rete privata all'esterno dell'archiviazione lato host e le messe a punto specifiche dell'applicazione (ad esempio, gli stack IP e le profondità della coda). Per ulteriori informazioni, vedi [Getting started with Block Storage](/docs/infrastructure/BlockStorage?topic=BlockStorage-GettingStarted#GettingStarted) e [Getting started with File Storage](/docs/infrastructure/FileStorage?topic=FileStorage-GettingStarted#getting-started-with-file-storage).

## Distribuzione e gestione

{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} sono distribuiti tramite l'API o il portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}} dopo che hai creato il tuo account cliente {{site.data.keyword.cloud_notm}}. I server possono essere gestiti tramite il portale del cliente, l'API o l'interfaccia della riga di comando (CLI). Per ulteriori informazioni, consulta [About bare metal servers](/docs/bare-metal?topic=bare-metal-about#about).

## Supporto

[Il supporto clienti {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) gestisce tutte le domande e i problemi di supporto che si verificano tramite varie fonti, incluso il supporto basato sul ticket, chat e telefono. Il supporto clienti offerto è gratuito per tutti i clienti {{site.data.keyword.cloud_notm}} e copre la maggior parte dei ticket inseriti ogni giorno. Per ulteriori informazioni, vedi [Getting Customer Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

Puoi anche continuare a creare i ticket tramite il supporto SAP correlato ai tuoi prodotti {{site.data.keyword.cloud_notm}} IaaS e SAP. Per ulteriori informazioni, consulta [SAP Support ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://support.sap.com/en/index.html){: new_window} e [SAP Note 2414820 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/2414820){: new_window}.

## Installazione di SAP HANA

Il tuo software SAP HANA deve essere installato da un programma di installazione SAP HANA certificato che ha completato il corso di certificazione di installazione SAP HANA. Per ulteriori informazioni, vedi [Who Can Install SAP HANA?![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.saphanacentral.com/p/who-can-install-sap-hana.html){: new_window}.
