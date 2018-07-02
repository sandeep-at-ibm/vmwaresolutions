---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Panoramica di FortiGate Security Appliance on IBM Cloud

Il servizio FortiGate Security Appliance on {{site.data.keyword.cloud}} distribuisce una coppia di dispositivi FortiGate Security Appliance (FSA) della serie 300 in una modalità altamente disponibile per fornire servizi di firewall, instradamento, NAT e VPN per proteggere ogni server e macchina virtuale sulla VLAN pubblica delle tue istanze.

Puoi gestire questo servizio utilizzando il client web FortiOS o l'interfaccia della riga di comando tramite SSH.

**Disponibilità**: questo servizio è disponibile solo per le istanze distribuite nelle release della V1.8 o successive.

## Componenti di FortiGate Security Appliance on IBM Cloud

Quando ordini il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} per la tua istanza, una coppia HA di dispositivi FortiGate Security Appliance della serie 300 viene distribuita sulla VLAN pubblica predefinita dell'istanza o cluster originale. Tutto il traffico verso la VLAN pubblica della tua istanza viene instradato tramite FortiGate Security Appliance.

**Nota:** se ordini cluster aggiuntivi, le VLAN pubbliche per questi cluster appena aggiunti non avranno la coppia HA di dispositivi di sicurezza.

## Considerazioni sull'istallazione di FortiGate Security Appliance on IBM Cloud

Esamina le seguenti considerazioni prima di installare il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* Assicurati che l'account {{site.data.keyword.cloud_notm}} che stai utilizzando abbia l'autorizzazione **Firewall hardware**. Questa autorizzazione è necessaria per modificare o visualizzare i log e le impostazioni del firewall per il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} della tua istanza.
* Se vuoi aggiungere il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} a un'istanza distribuita, assicurati che non vi siano altri firewall dall'infrastruttura {{site.data.keyword.cloud_notm}} già attivi sulla VLAN pubblica dell'istanza.
* L'installazione del servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} aggiungerà una nuova VLAN pubblica.
* Durante la distribuzione del servizio, la tua istanza potrebbe non essere in grado di accedere temporaneamente a Internet.
* Dopo aver installato correttamente il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, puoi gestire e configurare le regole del firewall per FSA dalla console FortiGate. Devi assicurarti che le regole del firewall FSA siano definite per consentire le comunicazioni HTTPS in uscita (porta TCP 443) che vengono avviate dai componenti di gestione come la macchina virtuale IBM CloudDriver o Zerto Virtual Manager per comunicare con il database di gestione esterno in {{site.data.keyword.cloud_notm}} tramite Internet. Le comunicazioni HTTPS in uscita (porta TCP 443) hanno origine dall'indirizzo IP pubblico del gateway dei servizi edge (ESG) VMware NSX dei servizi di gestione nella tua istanza.
* Se distribuisci una coppia di dispositivi FortiGate Security Appliance come parte di una nuova istanza, i dispositivi FortiGate Security Appliance vengono configurati per consentire solo le comunicazioni in uscita richieste dalla tua istanza alla rete pubblica e negare tutte le altre comunicazioni.
* Se distribuisci una coppia di dispositivi FortiGate Security Appliance come parte di un'istanza esistente, i dispositivi FortiGate Security Appliance vengono configurati con una regola esplicita per consentire tutte le comunicazioni di gestione in uscita richieste dalla tua istanza alla rete pubblica. Inoltre, i dispositivi FortiGate Security Appliance sono configurati con una regola aggiuntiva per consentire tutte le altre comunicazioni in modo che il traffico dell'applicazione esistente non venga interrotto. Devi gestire attentamente la configurazione di FortiGate Security Appliance per consentire solo le comunicazioni necessarie e negare tutte le altre comunicazioni.

## Considerazioni sulla rimozione di FortiGate Security Appliance on IBM Cloud

Esamina le seguenti considerazioni prima di rimuovere il servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* La rimozione del servizio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} rimuoverà la VLAN pubblica che è stata aggiunta.
* Durante la rimozione del servizio, la tua istanza potrebbe non essere in grado di accedere temporaneamente a Internet.
* Tutte le regole FortiGate per consentire, esaminare, bloccare e instradare il traffico NAT vengono rimosse insieme al servizio Fortinet. Se hai delle regole NAT, devi riconfigurarle.

## Link correlati

* [Ordine di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_ordering.html)
* [Gestione di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](managingfsa.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web Fortinet](https://www.fortinet.com/){:new_window}
* [Libreria di documenti Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
