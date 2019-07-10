---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

keywords: user account, user permissions, VRF account

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requisiti per l'account dell'infrastruttura IBM Cloud
{: #cloud-infra-acct-req}

Per utilizzare {{site.data.keyword.vmwaresolutions_full}} per effettuare l'ordine di istanze, devi disporre di un account dell'infrastruttura {{site.data.keyword.cloud_notm}}. Il costo dei componenti ordinati nelle tue istanze viene addebitato su tale account {{site.data.keyword.cloud_notm}}.

## Autorizzazioni per l'account dell'infrastruttura IBM Cloud
{: #cloud-infra-acct-req-permissions}

L'account dell'infrastruttura {{site.data.keyword.cloud_notm}} che utilizzi deve disporre di determinate autorizzazioni per poter ordinare i componenti nelle tue istanze ed eseguire operazioni per tuo conto. I requisiti di autorizzazione sono applicabili a tutti i tipi di istanze e servizi che ordini dalla console {{site.data.keyword.vmwaresolutions_short}}.

Gli utenti autorizzati possono verificare e aggiornare le autorizzazioni per un account dell'infrastruttura {{site.data.keyword.cloud_notm}} nel {{site.data.keyword.slportal}}. Per ulteriori informazioni, consulta [Modifica delle autorizzazioni del portale clienti di un utente](/docs/customer-portal?topic=customer-portal-customerportal_accuserprof#cp_editusercpperm){:new_window}.

Tabella 1. Autorizzazioni richieste per l'account dell'infrastruttura {{site.data.keyword.cloud_notm}}

| Autorizzazione         | Dettagli                                 |
|:------------------ |:--------------------------------------- |
| Aggiungi server | Questa autorizzazione è necessaria per le seguenti operazioni: per ordinare {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} su cui viene eseguito VMware ESXi e per il provisioning di server virtuali orari che vengono utilizzati per operazioni di configurazione, manutenzione e supporto delle istanze. |
| Annulla server | Questa autorizzazione è necessaria per rilasciare e recuperare i {{site.data.keyword.baremetal_short}} su cui viene eseguito VMware ESXi. Se elimini la tua istanza, i componenti ordinati vengono automaticamente rilasciati nella sequenza di dipendenze corretta. |
| Visualizza i dettagli di Virtual Server | Questa autorizzazione è necessaria per recuperare i dettagli di provisioning del server, che sono richiesti per la convalida degli ordini e la configurazione automatizzata. |
| Aggiungi archiviazione | Questa autorizzazione è necessaria per ordinare l'archiviazione di backup e l'archiviazione condivisa per l'istanza. |
| Gestisci archiviazione | Questa autorizzazione è necessaria per gestire l'archiviazione di backup e l'archiviazione condivisa per l'istanza. |
| Hardware Firewall | Questa autorizzazione è necessaria per modificare o visualizzare i file di log e le impostazioni del firewall per il servizio Fortinet on {{site.data.keyword.cloud_notm}}, se installato sull'istanza. |
| Aggiungi calcolo con la porta di rete pubblica | Questa autorizzazione è necessaria per ordinare hardware e VSI (Virtual Server Instance) con porte di rete pubblica. |
| Aggiungi indirizzi IP | Questa autorizzazione è necessaria per ordinare intervalli di sottoreti private portatili per tuo conto, necessari per gestire le VM (Virtual Machine) eseguite in un cluster vSphere. Quando vengono aggiunti più servizi alla tua istanza, gli indirizzi IP privati portatili vengono assegnati ai server VMware ESXi per isolare e assegnare la larghezza di banda. |
| Aggiungi ticket | Questa autorizzazione è necessaria per aprire ticket di servizio per tuo conto. I ticket possono essere creati per le seguenti operazioni: per avviare le operazioni di ripristino e avviare automaticamente i processi di risoluzione dei problemi quando vengono rilevati dei problemi. |
| Modifica ticket | Questa autorizzazione è necessaria per modificare i ticket di servizio creati per tuo conto. |
| Visualizza ticket | Questa autorizzazione è necessaria per monitorare i ticket di servizio relativi ai componenti della tua istanza per ritardi e problemi di provisioning dell'infrastruttura {{site.data.keyword.cloud_notm}}. |
| Visualizza dettagli hardware | Questa autorizzazione è necessaria per recuperare i dettagli hardware, che sono richiesti per la convalida degli ordini e la configurazione automatizzata. |
| Riavvia/Controlla | Questa autorizzazione è necessaria per spegnere l'hardware durante il processo di annullamento dell'hardware quando elimini un'istanza. |
| Visualizza licenze | Questa autorizzazione è necessaria per recuperare e convalidare le licenze utilizzate dalla tua istanza. |
| Visualizza password | Questa autorizzazione è necessaria per poter amministrare le VSI ordinate. |
| Gestisci monitoraggio server | Questa autorizzazione non è necessaria per effettuare un ordine ma è richiesta per recuperare e convalidare lo stato di monitoraggio dei {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} su cui sono in esecuzione i server VMware ESXi nella tua istanza. |

## VRF con endpoint del servizio abilitati
{: #cloud-infra-acct-req-vrf-se}

Il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} deve essere un account VRF (Virtual Routing and Forwarding). Se il tuo account è non VRF, devi eseguire la conversione a un account VRF. Ti consigliamo inoltre di abilitare il tuo account VRF per l'utilizzo degli endpoint del servizio.

Per ulteriori informazioni, vedi:
* [Panoramica di VRF on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Abilitazione del tuo account per l'utilizzo degli endpoint del servizio](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## Link correlati
{: #cloud-infra-acct-req-related}

* [Requisiti per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [Panoramica di VRF on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
