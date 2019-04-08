---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica su KMIP for VMware
{: #kmip-overview}

Questa architettura della soluzione descrive l'architettura KMIP on VMware per la protezione delle tue istanze VMware on {{site.data.keyword.cloud_notm}}. Sono disponibili molte opzioni di codifica dell'archiviazione per proteggere il tuo carico di lavoro VMware. KMIP for VMware lavora con le codifiche vSphere e vSAN native VMware per fornire una gestione della codifica dell'archiviazione semplificata insieme alla sicurezza e alla flessibilità delle chiavi gestite dal cliente di {{site.data.keyword.cloud_notm}} Key Protect.

Questa soluzione viene considerata come un componente extra e un'estensione delle offerte della soluzione vCenter Server e VMware Cloud Foundation su {{site.data.keyword.cloud_notm}}. Di conseguenza, questo documento non copre la configurazione esistente di queste soluzioni della fondazione su {{site.data.keyword.cloud_notm}}. Per avere ulteriori informazioni sull'architettura della soluzione della fondazione, fai riferimento alla nostra architettura della soluzione [VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Vantaggi principali
{: #kmip-overview-benefits}

Sebbene siano disponibili molte soluzioni di codifica dell'archiviazione per il tuo carico di lavoro VMware, KMIP for VMware offre i seguenti vantaggi:

* Integrazione con le codifiche VMware vSAN e vSphere, entrambe implementate al livello dell'hypervisor invece che al livello della VM (Virtual Machine) o dell'archiviazione. Questo approccio consente una gestione e una trasparenza facili per la tua applicazione e soluzione di archiviazione.
* Un server di gestione delle chiavi completamente gestito e disponibile in molte regioni multizona (MZR) {{site.data.keyword.cloud_notm}}.
* L'integrazione del tuo cluster VMware con {{site.data.keyword.cloud_notm}} Key Protect ti fornisce delle chiavi completamente gestite dal cliente che puoi revocare in qualsiasi momento.

## Link correlati
{: #kmip-overview-related}

* [Progettazione della soluzione](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [Implementazione e gestione](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-implementation)
