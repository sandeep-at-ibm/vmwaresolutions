---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di Zerto on IBM Cloud
{: #addingzertodr}

Il servizio Zerto on {{site.data.keyword.cloud}} integra le funzionalità di replica e ripristino di emergenza nelle offerte di distribuzione per proteggere e recuperare i dati nel tuo ambiente virtuale VMware su {{site.data.keyword.cloud_notm}}.

## Prima di iniziare
{: #addingzertodr-req}

* Assicurati che il tuo account {{site.data.keyword.cloud_notm}} sia un account fatturabile e che sia collegato all'account dell'infrastruttura {{site.data.keyword.cloud_notm}} in cui è distribuita la tua istanza. Per ulteriori informazioni, vedi [Fatturazione per la replica Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).
* Questo servizio è disponibile solo per le istanze distribuite nella V1.2 o successive. La versione corrente di Zerto installata è la 6.5 aggiornamento 3.

## Specifiche tecniche per Zerto on IBM Cloud
{: #addingzertodr-specs}

Nel servizio Zerto on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

I componenti Zerto Virtual Replication Appliance (VRA) vengono distribuiti solo nel cluster predefinito.
{:note}

### VSI (Virtual Service Instance)
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

* VSI
  * Un indirizzo IP primario privato
  * Uplink di rete privata da 1 Gbps
* VRA (Virtual Replication Appliance)
  * Una sottorete portatile privata per la distribuzione VRA

### Licenze e tariffe
{: #addingzertodr-specs-licenses}

Licenza di Zerto Replication V6.5 aggiornamento 3

## Link correlati
{: #addingzertodr-related}

* [Ordine di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sito web zerto.com](https://www.zerto.com){: external}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){: external}
