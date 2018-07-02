---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-05"

---

# Requisiti e pianificazione per le istanze Cloud Foundation

Esamina i seguenti requisiti prima di ordinare le tue istanze VMware Cloud Foundation. Pianifica la tua istanza in base all'ubicazione del {{site.data.keyword.CloudDataCent}}, ai requisiti di capacità del tuo carico di lavoro e ai requisiti di servizi aggiuntivi.

## Requisiti dell'account IBM Cloud

L'account {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti dell'account {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilità dei data center IBM Cloud

La distribuzione di Cloud Foundation ha requisiti rigorosi sull'infrastruttura fisica. Pertanto, puoi distribuire le istanze solo nei {{site.data.keyword.CloudDataCents_notm}} che soddisfano i requisiti. Per la distribuzione di Cloud Foundation sono disponibili i seguenti {{site.data.keyword.CloudDataCents_notm}}:

Tabella 1. {{site.data.keyword.CloudDataCents_notm}} e configurazioni di Bare Metal Server {{site.data.keyword.cloud_notm}} disponibili per le istanze Cloud Foundation

| {{site.data.keyword.CloudDataCent_notm}} | Ubicazione | Regione | Configurazioni server |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europa | Personalizzato |
| CHE01 | Chennai | Asia Pacifico | Personalizzato |
| DAL09 | Dallas | Nord America meridionale | Personalizzato |
| DAL10 | Dallas | Nord America meridionale | Personalizzato, Small, Large |
| DAL12 | Dallas | Nord America meridionale | Personalizzato |
| DAL13 | Dallas | Nord America meridionale | Personalizzato |
| FRA02 | Francoforte | Europa | Personalizzato, Large |
| FRA04 | Francoforte | Europa | Personalizzato |
| HKG02 | Hong Kong | Asia Pacifico | Personalizzato |
| LON02 | Londra | Europa | Personalizzato |
| LON04 | Londra | Europa | Personalizzato |
| LON06 | Londra | Europa | Personalizzato, Small, Large |
| MEL01 | Melbourne | Asia Pacifico | Personalizzato |
| MEX01 | Queretaro | Nord America meridionale | Personalizzato |
| MIL01 | Milano | Europa | Personalizzato |
| MON01 | Montreal | Nord America orientale | Personalizzato |
| OSL01 | Oslo | Europa | Personalizzato |
| PAR01 | Parigi | Europa | Personalizzato |
| SAO01 | San Paolo | Sud America | Personalizzato |
| SEO01 | Seul | Asia Pacifico | Personalizzato |
| SJC03 | San Jose | Nord America occidentale | Personalizzato |
| SJC04 | San Jose | Nord America occidentale | Personalizzato |
| SNG01 | Singapore | Asia Pacifico | Personalizzato |
| SYD01 | Sydney | Asia Pacifico | Personalizzato |
| SYD04 | Sydney | Asia Pacifico | Personalizzato |
| TOK02 | Tokyo | Asia Pacifico | Personalizzato |
| TOR01 | Toronto | Nord America orientale | Personalizzato, Small, Large |
| WDC04 | Washington, DC | Nord America orientale | Personalizzato, Small, Large |
| WDC06 | Washington, DC | Nord America orientale | Personalizzato |
| WDC07 | Washington, DC | Nord America orientale | Personalizzato |

A seconda della disponibilità e della fornitura di inventario, i {{site.data.keyword.CloudDataCents_notm}} potrebbero visualizzare un indicatore di stato nella console {{site.data.keyword.vmwaresolutions_short}} per aiutarti a pianificare le tue distribuzioni.

Tabella 2. Indicatori di stato per i {{site.data.keyword.CloudDataCents_notm}} quando ordini le istanze Cloud Foundation

| Stato | Dettagli sullo stato |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | Il {{site.data.keyword.CloudDataCent_notm}} non è attualmente disponibile. |
| Temporarily Out of Inventory  | Il {{site.data.keyword.CloudDataCent_notm}} non ha disponibilità in questo momento. |
| Limited Inventory             | Il {{site.data.keyword.CloudDataCent_notm}} ha una disponibilità limitata e l'ordine potrebbe non essere completato. |

## Servizi per le istanze Cloud Foundation

Puoi ordinare servizi aggiuntivi per la tua istanza in base alle tue esigenze, ad esempio il ripristino di emergenza. Per ulteriori informazioni, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](sd_addingremovingservices.html).

<!-- ## Capacity considerations

For capacity information and considerations, see the _Bill of Materials_ document on the [Virtualization reference architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page. -->

## Link correlati

* [Panoramica di Cloud Foundation](sd_cloudfoundationoverview.html)
* [Ordine di istanze Cloud Foundation](sd_orderinginstance.html)
* [Espansione e contrazione della capacità per le istanze Cloud Foundation](sd_addingremovingservers.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](sd_addingremovingservices.html)
