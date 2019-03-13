---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requisiti e pianificazione per VMware vSphere on IBM Cloud
{: #vs_planning}

Esamina i seguenti requisiti prima di ordinare VMware vSphere on {{site.data.keyword.cloud}}. Pianifica i tuoi cluster VMware vSphere in base all'ubicazione del {{site.data.keyword.CloudDataCent_notm}} e ai requisiti di capacità del carico di lavoro.

Sei responsabile della configurazione dell'ambiente, dell'installazione e della configurazione dei vari componenti VMware dopo la distribuzione dei server ESXi. I seguenti esempi sono componenti VMware: VMware vCenter Server, VMware NSX e VMware vSAN.
{:note}

## Requisiti dell'account IBM Cloud
{: #vs_planning-account-req}

L'account {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti per l'account {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## Disponibilità dei data center IBM Cloud
{: #vs_planning-dc-availability}

La distribuzione di vSphere ha requisiti rigorosi sull'infrastruttura fisica. Pertanto, puoi distribuire i cluster solo nei {{site.data.keyword.CloudDataCents_notm}} che soddisfano i requisiti. Per la distribuzione di vSphere sono disponibili i seguenti {{site.data.keyword.CloudDataCent_notm}}.

Se selezioni un componente vSAN, l'elenco di ubicazioni viene filtrato in base alla disponibilità SSD (Solid-State Disk).
{:note}

Tabella 1. {{site.data.keyword.CloudDataCents_notm}} disponibili per i cluster vSphere

| {{site.data.keyword.CloudDataCent_notm}} | Ubicazione | Regione |
|:----------------------|:---------|:-------|
| AMS03 | Amsterdam | Europa |
| CHE01 | Chennai | Asia-Pacifico |
| DAL09 | Dallas | Nord America meridionale |
| DAL10 | Dallas | Nord America meridionale |
| DAL12 | Dallas | Nord America meridionale |
| DAL13 | Dallas | Nord America meridionale |
| FRA02 | Francoforte | Europa |
| FRA04 | Francoforte | Europa |
| FRA05 | Francoforte | Europa |
| HKG02 | Hong Kong | Asia-Pacifico |
| LON02 | Londra | Europa |
| LON04 | Londra | Europa |
| LON05 | Londra | Europa |
| LON06 | Londra | Europa |
| MEL01 | Melbourne | Asia-Pacifico |
| MEX01 | Queretaro | Nord America meridionale |
| MIL01 | Milano | Europa |
| MON01 | Montreal | Nord America orientale |
| OSL01 | Oslo | Europa |
| PAR01 | Parigi | Europa |
| SAO01 | San Paolo | Sud America |
| SEO01 | Seul | Asia-Pacifico |
| SJC03 | San Jose | Nord America occidentale |
| SJC04 | San Jose | Nord America occidentale |
| SNG01 | Singapore | Asia-Pacifico |
| SYD01 | Sydney | Asia-Pacifico |
| SYD04 | Sydney | Asia-Pacifico |
| TOK02 | Tokyo | Asia-Pacifico |
| TOR01 | Toronto | Nord America orientale |
| WDC04 | Washington, DC | Nord America orientale |
| WDC06 | Washington, DC | Nord America orientale |
| WDC07 | Washington, DC | Nord America orientale |

## Link correlati
{: #vs_planning-related}

* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ridimensionamento di cluster esistenti](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Ridimensionamento di cluster esistenti creati all'esterno della console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
