---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: planning vCenter Server, data center, vCenter Server data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requisiti e pianificazione per le istanze vCenter Server
{: #vc_planning}

Esamina i seguenti requisiti prima di ordinare le tue istanze VMware vCenter Server. Pianifica la tua istanza in base all'ubicazione del {{site.data.keyword.CloudDataCent}}, ai requisiti di capacità del tuo carico di lavoro e ai requisiti di servizi aggiuntivi.

## Requisiti dell'account IBM Cloud
{: #vc_planning-account-req}

L'account {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti per l'account {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).

## Disponibilità dei data center IBM Cloud
{: #vc_planning-dc-availability}

La distribuzione di vCenter Server ha requisiti rigorosi sull'infrastruttura fisica. Pertanto, puoi distribuire le istanze solo nei {{site.data.keyword.CloudDataCents_notm}} che soddisfano i requisiti. Per la distribuzione di vCenter Server sono disponibili i seguenti {{site.data.keyword.CloudDataCents_notm}}.

Cascade Lake {{site.data.keyword.baremetal_short}} sono disponibili in una regione multizona {{site.data.keyword.CloudDataCents_notm}}. Per ulteriori informazioni, vedi [Panoramica della regione multizona (o MZR, Multi-Zone Region)
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).
{:note}

| {{site.data.keyword.CloudDataCent_notm}} | Ubicazione | Regione | Opzioni server |
|:----------------------|:---------|:-------|:---------------|
| AMS01 | Amsterdam | Europa | Skylake, Certificato SAP, Broadwell |
| AMS03 | Amsterdam | Europa | Skylake, Certificato SAP, Broadwell |
| CHE01 | Chennai | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| DAL09 | Dallas | Nord America meridionale | Skylake, Certificato SAP, Broadwell |
| DAL10 | Dallas | Nord America meridionale | Skylake, Certificato SAP, Broadwell |
| DAL12 | Dallas | Nord America meridionale | Skylake, Certificato SAP, Broadwell |
| DAL13 | Dallas | Nord America meridionale | Skylake, Certificato SAP, Broadwell |
| FRA02 | Francoforte | Europa | Skylake, Certificato SAP, Broadwell |
| FRA04 | Francoforte | Europa | Skylake, Certificato SAP, Broadwell |
| FRA05 | Francoforte | Europa | Skylake, Certificato SAP, Broadwell |
| HKG02 | Hong Kong | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| LON02 | Londra | Europa | Skylake, Broadwell |
| LON04 | Londra | Europa | Skylake, Certificato SAP, Broadwell |
| LON05 | Londra | Europa | Skylake, Broadwell |
| LON06 | Londra | Europa | Skylake, Certificato SAP, Broadwell |
| MEL01 | Melbourne | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| MEX01 | Queretaro | Nord America meridionale | Skylake, Certificato SAP, Broadwell |
| MIL01 | Milano | Europa | Skylake, Certificato SAP, Broadwell |
| MON01 | Montreal | Nord America orientale | Skylake, Certificato SAP, Broadwell |
| OSL01 | Oslo | Europa | Skylake, Certificato SAP, Broadwell |
| PAR01 | Parigi | Europa | Skylake, Certificato SAP, Broadwell |
| SAO01 | San Paolo | Sud America | Skylake, Certificato SAP, Broadwell |
| SEO01 | Seul | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| SJC03 | San Jose | Nord America occidentale | Skylake, Broadwell |
| SJC04 | San Jose | Nord America occidentale | Skylake, Broadwell |
| SNG01 | Singapore | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| SYD01 | Sydney | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| SYD04 | Sydney | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| SYD05 | Sydney | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| TOK02 | Tokyo | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| TOK04 | Tokyo | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| TOK05 | Tokyo | Asia-Pacifico | Skylake, Certificato SAP, Broadwell |
| TOR01 | Toronto | Nord America orientale | Skylake, Certificato SAP, Broadwell |
| WDC04 | Washington, DC | Nord America orientale | Skylake, Certificato SAP, Broadwell |
| WDC06 | Washington, DC | Nord America orientale | Skylake, Certificato SAP, Broadwell |
| WDC07 | Washington, DC | Nord America orientale | Skylake, Certificato SAP, Broadwell |
{: caption="Tabella 1. {{site.data.keyword.CloudDataCents_notm}} disponibili per le istanze vCenter Server" caption-side="top"}

A seconda della disponibilità e della fornitura di inventario, i {{site.data.keyword.CloudDataCents_notm}} potrebbero visualizzare un indicatore di stato nella console {{site.data.keyword.vmwaresolutions_short}} per aiutarti a pianificare le tue distribuzioni.

| Stato | Dettagli sullo stato |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | Il {{site.data.keyword.CloudDataCent_notm}} non è attualmente disponibile. |
| Temporarily Out of Inventory  | Il {{site.data.keyword.CloudDataCent_notm}} al momento non ha disponibilità. |
| Limited Inventory             | Il {{site.data.keyword.CloudDataCent_notm}} ha una disponibilità limitata e l'ordine potrebbe non essere completato. |
{: caption="Tabella 2. Indicatori di stato per i {{site.data.keyword.CloudDataCents_notm}} quando ordini le istanze vCenter Server" caption-side="top"}

## Backup dei componenti di gestione
{: #vc_planning-backup-mgmt-components}

Sei responsabile del mantenimento e della verifica della disponibilità di tutti i componenti dell'istanza. Si consiglia vivamente di pianificare il backup o l'alta disponibilità di tutti i componenti di gestione. Per ulteriori informazioni, vedi [Backup dei componenti](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Servizi per le istanze vCenter Server
{: #vc_planning-addon-services}

Puoi ordinare servizi aggiuntivi per la tua istanza in base alle tue esigenze, ad esempio il ripristino di emergenza. Per ulteriori informazioni, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

I servizi sono supportati per il vCenter Server con istanze NSX-T.
{:note}

### Pianificazione per VMware HCX on IBM Cloud
{: #vc_planning-addon-services-hcx}

Il servizio VMware HCX on {{site.data.keyword.cloud_notm}} può estendere senza problemi le reti dei data center in loco in {{site.data.keyword.cloud_notm}}, il che consente la migrazione delle VM (Virtual Machine) da e verso {{site.data.keyword.cloud_notm}} senza alcuna conversione o modifica.

Quando distribuisci questo servizio, completa le seguenti impostazioni:
* Specifica il **Tipo di interconnessione HCX** selezionando una delle seguenti opzioni:
  * **Rete pubblica**: HCX crea una connessione crittografata tra i siti sulla rete pubblica.
  * **Rete privata**: HCX crea una connessione crittografata tra i siti sulla rete privata.
* Specifica il **Tipo di certificato endpoint pubblico**. Se selezioni **Certificato CA**, configura le seguenti impostazioni:
  * **Contenuto del certificato**: immetti il contenuto del certificato CA.
  * **Chiave privata**: immetti la chiave privata del certificato CA.
  * (Facoltativo) **Password**: immetti la password per la chiave privata, se è crittografata.
  * (Facoltativo) **Immettere nuovamente la password**: immetti di nuovo la password per la chiave privata.
  * (Facoltativo) **Nome host**: immetti il nome host da associare al nome comune (CN) del certificato CA. HCX on {{site.data.keyword.cloud_notm}} richiede che il certificato CA sia in un formato accettato da Edge NSX. Per ulteriori informazioni sui formati dei certificati Edge NSX, vedi [Importazione di certificati SSL](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}.

## Considerazioni sulla capacità
{: #vc_planning-capacity-considerations}

Per ulteriori informazioni relative alle considerazioni sulla capacità, vedi [Ridimensionamento della capacità](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Link correlati
{: #vc_planning-related}

* [Panoramica di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
