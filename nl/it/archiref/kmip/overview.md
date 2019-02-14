---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica su KMIP for VMware

Questa architettura della soluzione descrive l'architettura KMIP on VMware per la protezione delle tue istanze VMware on {{site.data.keyword.cloud_notm}}. Sono disponibili molte opzioni di crittografia dell'archiviazione per proteggere il tuo carico di lavoro VMware. KMIP for VMware lavora con le crittografie vSphere e vSAN native VMware per fornire una gestione della crittografia dell'archiviazione semplificata insieme alla sicurezza e alla flessibilità delle chiavi gestite dal cliente di {{site.data.keyword.cloud_notm}} Key Protect.

**Nota**: in questa release, KMIP for VMware on {{site.data.keyword.cloud_notm}} è limitato solo alla crittografia vSphere.

Questa soluzione viene considerata come un componente extra e un'estensione delle offerte della soluzione vCenter Server e VMware Cloud Foundation su {{site.data.keyword.cloud_notm}}. Di conseguenza, questo documento non copre la configurazione esistente di queste soluzioni della fondazione su {{site.data.keyword.cloud_notm}}. Per avere ulteriori informazioni sull'architettura della soluzione della fondazione, fai riferimento alla nostra architettura della soluzione [VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html).

## Vantaggi principali

Sebbene siano disponibili molte soluzioni di crittografia dell'archiviazione per il tuo carico di lavoro VMware, KMIP for VMware offre i seguenti vantaggi:

* Integrazione con le crittografie VMware vSAN e vSphere, entrambe implementate al livello dell'hypervisor invece che al livello della macchina virtuale o dell'archiviazione. Questo approccio consente una gestione e una trasparenza facili per la tua applicazione e soluzione di archiviazione.
* Un server di gestione delle chiavi completamente gestito e disponibile in molte regioni multizona (MZR) IBM Cloud.
* L'integrazione del tuo cluster VMware con IBM Cloud Key Protect ti fornisce delle chiavi completamente gestite dal cliente che puoi revocare in qualsiasi momento.

### Link correlati

* [Progettazione della soluzione](/docs/services/vmwaresolutions/archiref/kmip/design.html)
* [Implementazione e gestione](/docs/services/vmwaresolutions/archiref/kmip/implementation.html)
