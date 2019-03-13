---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Informazioni su Gateway dei servizi edge NSX
{: #nsx_overview}

La soluzione Gateway dei servizi edge (ESG) VMware NSX è un'estensione delle offerte VMware Cloud Foundation on {{site.data.keyword.cloud}} e vCenter Server on {{site.data.keyword.cloud_notm}} attualmente disponibili su {{site.data.keyword.cloud_notm}}. L'architettura della soluzione per Cloud Foundation e vCenter Server indica in dettaglio i componenti della soluzione e la configurazione di alto livello di ogni componente nella progettazione.

Per ulteriori informazioni sulla progettazione di Cloud Foundation e vCenter Server, vedi [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Panoramica di Gateway dei servizi edge NSX
{: #nsx_overview-nsx-esg}

Il gateway dei servizi edge NSX collega reti stub isolate alle reti condivise (uplink) fornendo servizi gateway comuni come DHCP (Dynamic Host Configuration Protocol), VPN (Virtual Private Network), NAT (Network Address Translation), instradamento dinamico e bilanciamento del carico. Le distribuzioni comuni di Edge NSX includono zone demilitarizzate (DMZ), extranet VPN e ambienti cloud a più tenant in cui l'Edge NSX crea limiti virtuali per ogni tenant, carico di lavoro o componente di gestione. All'interno del gateway dei servizi edge NSX sono disponibili le seguenti funzioni.

Tabella 1. Funzioni disponibili con il gateway dei servizi edge NSX

| Funzione | Descrizione |
|:------- |:----------- |
| Instradamento servizi edge NSX | Fornisce le informazioni di inoltro necessarie tra i domini di trasmissione di livello 2, consentendoti di ridurre i domini di trasmissione di livello 2 e di migliorare l'efficienza e la scalabilità della rete. NSX estende questa intelligenza al punto in cui risiedono i carichi di lavoro per effettuare l'instradamento est-ovest. Ciò consente una comunicazione più diretta tra le macchine virtuali senza la costosa o tempestiva necessità di estendere i punti di connessione. Allo stesso tempo, NSX fornisce anche la connettività nord-sud, consentendo ai tenant di accedere alle reti pubbliche. |
| Firewall | Le regole supportate del firewall includono la configurazione a 5 tuple di IP con intervalli di IP e porte per l'ispezione stateful per tutti i protocolli. |
| NAT | Fornisce controlli separati per gli indirizzi IP di origine e destinazione è la conversione delle porte. |
| DHCP | Fornisce la configurazione di pool di IP, gateway, server DNS e domini di ricerca. |
| VPN Site-to-Site | Utilizza le impostazioni del protocollo IPSec standardizzate per interagire con tutti i principali fornitori di VPN. |
| L2VPN | Estende le reti L2 sulle topologie L3. |
| SSL VPN-Plus |  SSL VPN-Plus consente agli utenti remoti di connettersi in modo sicuro alle reti private dietro un gateway Edge NSX. |
| Bilanciamento del carico | Fornisce indirizzi IP virtuali e gruppi di server semplici e dinamicamente configurabili. |
| Alta disponibilità | Assicura un Edge NSX attivo sulla rete nel caso in cui la macchina virtuale Edge NSX primaria non sia disponibile. |

## Link correlati
{: #nsx_overview-related}

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
