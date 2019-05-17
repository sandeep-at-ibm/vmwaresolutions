---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations}

Il servizio FortiGate Security Appliance on {{site.data.keyword.cloud}} distribuisce una coppia di dispositivi FortiGate Security Appliance (FSA) della serie 300 in una modalità altamente disponibile per fornire servizi di firewall, instradamento, NAT e VPN per proteggere ogni server e macchina virtuale sulla VLAN pubblica delle tue istanze.

Puoi gestire questo servizio utilizzando il client web FortiOS o l'interfaccia della riga di comando tramite SSH.

Questo servizio è disponibile solo per le istanze distribuite nelle release della V1.8 o successive.
{:note}

## Specifiche tecniche per FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-specs}

Nel servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Hardware
{: #fsa_considerations-hardware}

Dispositivo FortiGate Security Appliance della serie 300.

### Alta disponibilità (HA)
{: #fsa_considerations-ha}

Vengono distribuiti due dispositivi in una configurazione attiva-passiva.

### Rete
{: #fsa_considerations-networking}

* Dual 1 GbE associato su reti upstream e downstream
* Una nuova VLAN pubblica {{site.data.keyword.cloud_notm}} upstream
* Una VLAN pubblica {{site.data.keyword.cloud_notm}} downstream esistente

## Considerazioni sull'installazione di FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-install}

Esamina le seguenti considerazioni prima di installare il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* Assicurati che l'account {{site.data.keyword.cloud_notm}} che stai utilizzando abbia l'autorizzazione **Hardware Firewall**. Questa autorizzazione è necessaria per modificare o visualizzare i log e le impostazioni del firewall per il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} della tua istanza.
* Se vuoi aggiungere il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} a un'istanza distribuita, assicurati che nessun altro firewall dell'infrastruttura {{site.data.keyword.cloud_notm}} sia già attivo sulla VLAN pubblica dell'istanza.
* L'installazione del servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} aggiunge una nuova VLAN pubblica.
* Durante la distribuzione del servizio, la tua istanza potrebbe non essere in grado di accedere temporaneamente a Internet.
* Dopo aver installato correttamente il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, puoi gestire e configurare le regole del firewall per FSA dalla console FortiGate. Devi assicurarti che le regole del firewall FSA siano definite per consentire le comunicazioni HTTPS in uscita (porta TCP 443) che vengono avviate dai componenti di gestione come Zerto Virtual Manager per comunicare con il database di gestione esterno su {{site.data.keyword.cloud_notm}} tramite Internet. Le comunicazioni HTTPS in uscita (porta TCP 443) hanno origine dall'indirizzo IP pubblico del gateway dei servizi edge (ESG) VMware NSX dei servizi di gestione nella tua istanza.
* Devi gestire attentamente la configurazione di FortiGate Security Appliance per consentire solo le comunicazioni necessarie e negare tutte le altre comunicazioni.
* Se ordini cluster aggiuntivi, le VLAN pubbliche per questi cluster appena aggiunti non hanno la coppia HA di dispositivi di sicurezza.

## Considerazioni sulla rimozione di FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-remove}

Esamina le seguenti considerazioni prima di rimuovere il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* La rimozione del servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} rimuove la VLAN pubblica che è stata aggiunta.
* Durante la rimozione del servizio, la tua istanza potrebbe non essere in grado di accedere temporaneamente a Internet.
* Tutte le regole FortiGate per consentire, esaminare, bloccare e instradare il traffico NAT vengono rimosse insieme al servizio Fortinet. Se hai delle regole NAT, devi riconfigurarle.

## Link correlati
{: #fsa_considerations-related}

* [Ordine di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Gestione di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web Fortinet](https://www.fortinet.com/){:new_window}
* [Libreria di documenti Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:new_window}
