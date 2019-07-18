---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-21"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# ID utente IBM
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}} conserva un insieme di utenti nel tuo account utilizzabili dall'automazione {{site.data.keyword.cloud_notm}} quando esegui operazioni come l'aggiunta di host, cluster o archiviazione alla tua istanza VMware. Gli utenti nel tuo account possono essere utilizzati anche per l'installazione e la configurazione di servizi da parte dell'automazione dei servizi {{site.data.keyword.cloud_notm}}. Esamina le seguenti sezioni relative agli ID utente per l'automazione {{site.data.keyword.cloud_notm}}.

Le operazioni dell'istanza VMware hanno esito negativo se gli ID utente vengono eliminati, disabilitati oppure se le loro password vengono modificate.
{:important}

## ID utente vCenter e Platform Services Controller
{: #audit_user_ids-vcenter-psc}

A partire dalla V2.5, {{site.data.keyword.vmwaresolutions_short}} utilizza i seguenti ID utente per aggiungere un'origine di identità, integrata per impostazione predefinita, in vCenter.

| Utente     | ID utente      | Metodo | Descrizione |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Utilizzato per la configurazione di VMware, ad esempio la configurazione di VMware HA (High Availability) e la creazione degli switch distribuiti. Utilizzato nella post-distribuzione per accoppiare le istanze vCenter Server primarie e secondarie. |
| Cliente | customerroot | SSH    | Creato solo per l'utilizzo da parte del cliente. |
| IBM      | automation@``root_domain``<br/>(utente Active Directory) | HTTP | Utilizzato nella post-distribuzione per aggiungere e rimuovere gli host e i cluster e per distribuire e configurare le VM per i servizi aggiuntivi. |
| Cliente | Administrator@vsphere.local | HTTP | Creato solo per l'utilizzo da parte del cliente. |
{: caption="Tabella 1. ID utente vCenter e Platform Services Controller" caption-side="top"}

HTTP viene utilizzato per l'impostazione e la configurazione di vCenter, come pure per le operazioni VMware come l'aggiunta di host, cluster o archiviazione per la gestione delle risorse di vCenter.
{:note}

## ID utente NSX Manager
{: #audit_user_ids-nsx-mgr}

| Utente     | ID utente      | Descrizione |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(utente Active Directory) | Utilizzato nella post-distribuzione per gestire gli indirizzi IP NSX VTEP, per gestire la configurazione host e cluster quando vengono aggiunti e rimossi host e cluster e per gestire la configurazione ESG per i servizi aggiuntivi che richiedono l'accesso alla rete pubblica per la licenza, l'attivazione o la creazione di report sull'utilizzo. |
| Cliente | Amministratore        | Creato solo per l'utilizzo da parte del cliente. |
{: caption="Tabella 2. ID utente NSX Manager" caption-side="top"}

## ID utente host ESXi
{: #audit_user_ids-esxi}

| Utente     | ID utente      | Descrizione |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Utilizzato nella post-distribuzione per aggiungere altra archiviazione NFS, per configurare gli instradamenti a tale archiviazione e per eseguire tutto il codice di convalida del server. |
| Cliente | root         | Creato solo per l'utilizzo da parte del cliente. |
{: caption="Tabella 3. ID utente host ESXi" caption-side="top"}

## ID utente Microsoft Active Directory
{: #audit_user_ids-ad}

| Utente     | ID utente       | Descrizione |
|:---------|:------------- |:------------|
| IBM      | automation    | Utilizzato per aggiungere un host, per aggiungere una VM per il servizio e per configurare le voci Active Directory e DNS. |
| Cliente | Amministratore | Creato solo per l'utilizzo da parte del cliente. |
{: caption="Tabella 4. ID utente Active Directory" caption-side="top"}


## ID utente di servizio
{: #audit_user_ids-services}

| ID utente                                    | Descrizione |
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio F5 on {{site.data.keyword.cloud_notm}}. |
| prod-Caveonix-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}. |
| prod-Fortigate-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}. |
| prod-FortigateVM-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustCC-``shortID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustDC-``shortID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustKC-``shortID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}. |
| prod-KMIPAdapter-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}. |
| prod-ICP-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio {{site.data.keyword.cloud_notm}} Private Hosted. |
| prod-SPPlus-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. |
| prod-Veeam-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio Veeam on {{site.data.keyword.cloud_notm}}. |
| prod-HCX-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio VMware HCX on {{site.data.keyword.cloud_notm}}. |
| prod-Zerto-``dynamicID``-@``domainName`` | Utilizzato per l'installazione e la configurazione del servizio Zerto on {{site.data.keyword.cloud_notm}}. |
{: caption="Tabella 5. ID utente del servizio" caption-side="top"}

dove:

* ``dynamicID`` comprende gli 8-10 caratteri generati dinamicamente durante l'installazione del servizio.
* ``shortID`` comprende i cinque caratteri generati dinamicamente durante l'installazione del servizio.
* ``domainName`` è il nome di dominio della tua istanza.

## Link correlati
{: #audit_user_ids-related}

* [Considerazioni sulla modifica delle risorse vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Eventi di Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
