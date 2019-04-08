---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di Zerto on IBM Cloud
{: #addingzertodr}

Il servizio Zerto on {{site.data.keyword.cloud}} integra le funzionalità di replica e ripristino di emergenza nelle offerte di distribuzione per proteggere e recuperare i dati nel tuo ambiente virtuale VMware su {{site.data.keyword.cloud_notm}}.

Questo servizio è disponibile solo per le istanze distribuite nella V1.2 o successive. La versione corrente di Zerto installata è la 6.5 aggiornamento 3.
{:note}

## Specifiche tecniche per Zerto on IBM Cloud
{: #addingzertodr-specs}

Nel servizio Zerto on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

I componenti Zerto Virtual Replication Appliance (VRA) vengono distribuiti solo nel cluster predefinito.
{:note}

### VSI
{: #addingzertodr-specs-vsi}

* Una VSI (Virtual Service Instance) - Zerto Virtual Manager
* Core 2 x 2,0 GHz
* 4 GB di RAM
* Windows Server 2016 Standard Edition (64 bit)

### Archiviazione
{: #addingzertodr-specs-storage}

Disco da 100 GB (SAN)

### Rete
{: #addingzertodr-specs-network}

* Un indirizzo IP primario privato
* Uplink di rete privata da 1 Gbps

### Licenze e tariffe
{: #addingzertodr-specs-licenses}

Licenza di Zerto Replication V6.5 aggiornamento 3

## Link correlati
{: #addingzertodr-related}

* [Informazioni su {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-prod_overview)
* [Ordine di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Richiesta di servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sito web zerto.com](https://www.zerto.com){:new_window}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
