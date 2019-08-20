---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: vmware solutions shared, get started shared, tech specs shared

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica su IBM Cloud for VMware Solutions Shared
{: #shared_overview}

{{site.data.keyword.vmwaresolutions_full}} Shared viene fornito come un'offerta sperimentale.
{:note}

Con i data center virtuali VMware, puoi migrare o distribuire velocemente e uniformemente i carichi di lavoro VMware al cloud sulla tua infrastruttura VMware gestita professionalmente. IBM fornisce una piattaforma di calcolo cloud VMware on-demand self-service con vCloud Director in esecuzione su {{site.data.keyword.cloud_notm}}. Questa offerta a pagamento a consumo IaaS (Infrastructure-as-a-Service) consente agli utenti di utilizzare vCPU, archiviazione, vRAM, rete e IP specifici, se necessario.

{{site.data.keyword.vmwaresolutions_short}} ha tre tipi di servizio di sottoscrizione "IaaS (Infrastructure-as-a-Service)":
- Data center virtuale riservato multitenant
- Data center virtuale a pagamento a consumo multitenant
- Data center virtuale dedicato a singolo tenant

I clienti gestiscono il ciclo di vita dei data center virtuali utilizzando l'offerta {{site.data.keyword.vmwaresolutions_short}}. Le seguenti funzioni sono supportate, con l'IU web o l'API pubblica:
- Creazione del data center virtuale
- Elasticità del data center virtuale
- Eliminazione del data center virtuale
- Aggiunta e rimozione di servizi VMware
- Licenza di Windows su richiesta
- Licenza di Red Hat su richiesta

Tutte e tre le offerte di data center virtuale di {{site.data.keyword.cloud_notm}} vengono fornite con cinque indirizzi IP pubblici su un gateway dei servizi edge NSX con ingresso illimitato sulla rete pubblica.

I data center virtuali comportano degli addebiti per i seguenti componenti:
- Assegnazioni di archiviazione con prezzi a livelli basati sulle prestazioni di archiviazione
- Utilizzo di CPU virtuale
- Utilizzo di memoria virtuale
- Uscita (egress) sulla rete pubblica
- Licenze del sistema operativo commerciali utilizzate
- Servizi VMware facoltativi

## Architettura di IBM Cloud for VMware Solutions Shared
{: #shared_overview-archi}

Il seguente grafico illustra l'architettura di alto livello e i componenti della distribuzione di {{site.data.keyword.vmwaresolutions_short}} Shared.

![{{site.data.keyword.vmwaresolutions_short}} Shared - Architettura](../images/vclouddirector-architecture-public.svg "{{site.data.keyword.vmwaresolutions_short}} Shared - Architettura")

### VMware vCloud Director
{: #shared_overview-vcloud-dir}

Questo livello rappresenta l'interfaccia di gestione. VMware® vCloud Director fornisce l'accesso basato sul ruolo a un portale tenant basato sul web che consente ai membri di un'organizzazione di interagire con le risorse dell'organizzazione per creare e utilizzare le vApp e le VM (macchine virtuali).

### Organizzazione
{: #shared_overview-org}

Un'organizzazione è un'unità di gestione per una raccolta di utenti, gruppi e risorse di calcolo. Gli utenti si autenticano al livello dell'organizzazione, fornendo le credenziali stabilite da un amministratore dell'organizzazione quando l'utente è stato creato o importato. Gli amministratori dell'organizzazione gestiscono gli utenti, i gruppi e i cataloghi dell'organizzazione.

### Utenti e politiche
{: #shared_overview-users-policies}

Un'organizzazione può contenere un numero arbitrario di utenti e gruppi. Gli utenti possono essere creati localmente dall'amministratore dell'organizzazione o importati da un servizio di directory come LDAP. Le autorizzazioni all'interno di un'organizzazione sono controllate tramite l'assegnazione di diritti e ruoli agli utenti e ai gruppi.

### Cataloghi 
{: #shared_overview-cat}

Le organizzazioni utilizzano i cataloghi per archiviare i template vApp e i file multimediali. I membri di un'organizzazione che hanno accesso a un catalogo possono utilizzare i file multimediali e i template vApp del catalogo per creare le proprie vApp. Gli amministratori delle organizzazioni possono copiare le voci dai cataloghi pubblici nel loro catalogo dell'organizzazione.

### Data center virtuali
{: #shared_overview-vc}

Un data center virtuale dell'organizzazione fornisce le risorse a un'organizzazione. I data center virtuali forniscono un ambiente in cui i sistemi virtuali possono essere archiviati, distribuiti e gestiti. Forniscono inoltre l'archiviazione per i supporti DVD e CD virtuali. Un'organizzazione può avere più data center virtuali.

![{{site.data.keyword.cloud_notm}} per l'architettura di data center virtuali](../images/virtual-datacenter-architecture-public.svg "{{site.data.keyword.cloud_notm}} per l'architettura di data center virtuali")

## Specifiche tecniche per IBM Cloud for VMware Solutions Shared
{: #shared_overview-specs}

Sono inclusi i seguenti componenti in {{site.data.keyword.cloud_notm}}:

### Calcolo
{: #shared_overview-specs-comp}

L'elaborazione di calcolo viene assegnata ai data center virtuali in incrementi di CPU virtuale (vCPU). Ogni incremento di vCPU rappresenta un singolo core da 2.0 GHz. La memoria di calcolo viene assegnata in incrementi di GB.

### Rete
{: #shared_overview-specs-net}

Per impostazione predefinita, ogni data center virtuale viene fornito configurato con un gateway edge con cinque indirizzi IP pubblici e un indirizzo IP del servizio privato. Il gateway edge è configurabile dal cliente e può essere personalizzato.

Gli indirizzi pubblici possono essere utilizzati per le vApp pubbliche per il traffico internet pubblico in entrata e in uscita.

L'indirizzo del servizio può essere utilizzato per accedere ai servizi dell'infrastruttura IBM Cloud sulla rete privata interna IBM Cloud, inclusi i seguenti servizi:
- NTP
- Aggiornamenti e licenze del sistema operativo Windows
- Aggiornamenti e licenze del sistema operativo Red Hat
- Cloud Object Storage

### Archiviazione
{: #shared_overview-specs-storage}

Quando crei o distribuisci vApp o VM, viene selezionata una politica di archiviazione. Esistono quattro diversi livelli di archiviazione disponibili, a seconda delle prestazioni di archiviazione necessarie:

- NFS Platinum: il livello di archiviazione con una velocità effettiva massima di 10 IOPS/GB, le prestazioni più elevate
- NFS Gold: livello di archiviazione con una velocità effettiva massima di 4 IOPS/GB
- NFS Silver: livello di archiviazione con una velocità effettiva massima di 2 IOPS/GB
- NFS Bronze: livello di archiviazione con una velocità effettiva massima di 0.25 IOPS/GB

## Link correlati
{: #shared_overview-related}

* [Ordinazione di Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Ordinazione di Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [Gestione di {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-74C9E10D-9197-43B0-B469-126FFBCB5121.html){:external}
