---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Caveonix console, Caveonix RiskForesight license, login Caveonix console

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestione di Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix}

## Accesso alla console Caveonix RiskForesight
{: #managingcaveonix-access-console}

Per gestire il servizio Caveonix RiskForesight on {{site.data.keyword.cloud}}, devi accedere alla console Caveonix RiskForesight completando la seguente procedura:

1. Utilizza la VPN dell'infrastruttura IBM Cloud o un server jump per consentire l'accesso all'indirizzo IP della VM (Virtual Machine) Caveonix RiskForesight. Puoi trovare l'indirizzo IP nella pagina dei dettagli del servizio per Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} nella console {{site.data.keyword.vmwaresolutions_short}}. Per essere specifici:
   1. Crea una password VPN dal portale clienti dell'infrastruttura {{site.data.keyword.cloud_notm}}.
   2. Accedi al portale VPN del data center utilizzando le credenziali VPN dell'infrastruttura {{site.data.keyword.cloud_notm}}.
   3. Aggiungi l'associazione di indirizzo IP e nome host nel file `hosts` dal tuo computer locale. Utilizza il seguente formato:

      ```javascript
      RiskForesight_VM_IP_Address      RiskForesight_FQDN
      ```
2. Per accedere alla console Caveonix RiskForesight, fai clic su **Visualizza console di RiskForesight** nella pagina dei dettagli del servizio per Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} ed esegui quindi l'accesso utilizzando le credenziali elencate nella stessa pagina dei dettagli del servizio.

## Applicazione di aggiornamenti a Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix-update}

Sei responsabile di mantenere Caveonix RiskForesight aggiornato alla versione più recente. Puoi scaricare gli aggiornamenti richiesti dal [portale del provider di servizi Caveonix](https://support.caveonix.com).

## Aggiornamento delle licenze Caveonix RiskForesight

La licenza Caveonix RiskForesight è valida per un anno. Puoi aggiornare la licenza Caveonix RiskForesight quando scade utilizzando la seguente procedura:
1. Ordina una nuova licenza Caveonix RiskForesight e copiala nella console di Caveonix RiskForesight. Per ulteriori informazioni, vedi [Procedura per ordinare licenze Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure).
2. Elimina la licenza scaduta dalla tabella **Licenze Caveonix RiskForesight** nella console {{site.data.keyword.vmwaresolutions_short}}. Per ulteriori informazioni, vedi [Procedura per eliminare licenze Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete).

## Link correlati
{: #managingcaveonix-related}

* [Panoramica di Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Ordine di Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
