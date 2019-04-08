---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations}

Il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud}} distribuisce una coppia di dispositivi FortiGate Virtual Appliance al tuo ambiente, che può aiutarti a ridurre i rischi implementando controlli di sicurezza critici all'interno della tua infrastruttura virtuale.

Puoi installare più istanze di questo servizio a seconda delle necessità. Puoi gestire questo servizio utilizzando il client web FortiOS o l'interfaccia della riga di comando tramite SSH.

Questo servizio è disponibile solo per le istanze distribuite nelle release della V2.0 o successive. La versione del servizio corrente installata è la 6.0.3.
{:note}

## Specifiche tecniche per FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations-specs}


Nel servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### VM (Virtual Machine)
{: #fortinetvm_considerations-specs-vms}

* Tutte le opzioni includono una coppia di VM (Virtual Machine) ad alta disponibilità (HA)
* 2, 4 o 8 vCPU per VM (Virtual Machine) in base al tipo di sottoscrizione e alla dimensione della distribuzione
* 4, 6 o 12 GB di RAM per VM (Virtual Machine) in base al tipo di sottoscrizione e alla dimensione della distribuzione

### Alta disponibilità (HA)
{: #fortinetvm_considerations-specs-ha}

Due VM (Virtual Machine) sono distribuite e pronte per la configurazione HA o VRRP (Virtual Router Redundancy Protocol).

### Rete
{: #fortinetvm_considerations-specs-network}

L'accesso alla console FortiGate® viene fornito tramite una rete di gestione privata.

### Licenza e tariffe
{: #fortinetvm_considerations-specs-license}

Le tariffe della licenza per ogni VM (Virtual Machine) vengono applicate a ciascun ciclo di fatturazione in base alla dimensione della distribuzione selezionata e al modello di licenza di sottoscrizione mensile.

Non puoi modificare il livello di licenza dopo l'installazione del servizio. Per modificare il livello di licenza, devi rimuovere il servizio esistente e reinstallare il servizio utilizzando un'opzione di licenza diversa.
{:important}

## Considerazioni sull'istallazione di FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations-install}

Esamina le seguenti considerazioni prima di installare il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}:
* Le VM (Virtual Machine) FortiGate vengono distribuite solo nel cluster predefinito.
* Viene anche prenotato il 100% di CPU e RAM per le due VM FortiGate perché queste VM si trovano nel piano dati delle comunicazioni di rete ed è fondamentale che per loro siano ancora disponibili risorse.

  Per calcolare la prenotazione di CPU e RAM per una singola VM FortiGate, utilizza la seguente formula:
   * `Prenotazione CPU = velocità CPU del server ESXi * numero di vCPU`
   * `Prenotazione RAM = dimensione RAM`
* Quando distribuisci una coppia HA di dispositivi FortiGate Virtual Appliance nella tua istanza, vengono definite regole SNAT e firewall sul gateway dei servizi edge (ESG) NSX di gestione insieme a rotte statiche sui dispositivi FortiGate Virtual Appliance per consentire comunicazioni HTTPS in uscita dalla tua istanza alla rete pubblica per l'attivazione della licenza e per l'acquisizione di contenuti e politiche di sicurezza più recenti.
* Non puoi modificare il livello di licenza dopo l'installazione del servizio. Per modificare il livello di licenza, devi rimuovere il servizio esistente e quindi reinstallare il servizio selezionando un'opzione di licenza diversa.
* Per evitare errori con FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, devi soddisfare i seguenti requisiti:
   * Sono disponibili almeno due server ESXi attivi per le due VM FortiGate da distribuire con la regola di anti-affinità di mantenere le VM su server separati.
   * I due server ESXi attivi hanno sufficienti risorse disponibili in modo che una VM FortiGate possa essere ospitata su ciascun server ESXi con prenotazione del 100% di CPU e RAM.
   * VMware vSphere HA dispone di risorse sufficienti per ospitare due VM FortiGate con il 100% di CPU e RAM.

  A causa di questi requisiti, devi pianificare attentamente lo spazio necessario per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}. Se necessario, prima di ordinare FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, aggiungi 1-2 server ESXi alla tua istanza e/o riduci la prenotazione di CPU di vSphere HA per il failover.

## Esempio di ordine di FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations-example}

Ordini un'istanza **Small** di VMware vCenter Server con 2 server ESXi con la seguente configurazione: 16 core a 2,10 GHz ciascuno con 128 GB di RAM. Per FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, selezioni l'opzione **Large** (8 vCPU / 12 GB di RAM) per la dimensione di distribuzione e qualsiasi modello di licenza di sottoscrizione.

In questo caso, una singola VM FortiGate richiede, su ciascun server:
* 2,1 GHz * 8 vCPU = 16,8 GHz di CPU e
* 12 GB di RAM

In totale, si tratta di 33,6 GHz di CPU e 24 GB di RAM per due VM FortiGate.

Ogni server ESXi ha una capacità di 16 core * 2,1 GHz = 33,6 GHz, quindi soddisfiamo i primi due requisiti se entrambi i server sono attivi e ci sono almeno 16,8 GHz di CPU e 12 GB di RAM disponibili su ciascun server.

Tuttavia, per impostazione predefinita, vSphere HA riserva il 50% di CPU e RAM per il failover sulle istanze vCenter Server che sono state inizialmente distribuite con 2 server ESXi, quindi abbiamo solo:

`50% di 2 * 16 core * 2,1 GHz = 33,6 GHz disponibili`

Poiché esistono altri carichi di lavoro sui server ESXi, ad esempio, VMware vCenter Server, Controller VMware NSX o VMware NSX Edge, utilizzando queste risorse, il terzo requisito non viene soddisfatto. Questo perché abbiamo bisogno di 33.6 GHz di CPU e 24 GB di RAM per due VM FortiGate.

In questo caso, l'installazione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} potrebbe non riuscire, a meno che almeno un server ESXi venga aggiunto all'ambiente e le prenotazioni di failover di vSphere HA vengano aggiornate in modo appropriato per garantire che ci siano risorse sufficienti per due VM FortiGate.

Se sono necessarie risorse aggiuntive per eseguire il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, puoi aggiungere altri server ESXi prima di installare il servizio.

## Considerazioni sulla rimozione di FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations-remove}

Prima di rimuovere il servizio FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, assicurati che la configurazione dei dispositivi FortiGate Virtual Appliance esistenti sia stata rimossa correttamente. In particolare, il traffico di rete deve essere instradato attorno ai FortiGate Virtual Appliance anziché tramite i FortiGate Virtual Appliance. In caso contrario, il traffico di dati esistente all'interno del tuo ambiente potrebbe essere influenzato.

## Link correlati
{: #fortinetvm_considerations-related}

* [Ordine di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [Gestione di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web Fortinet](https://www.fortinet.com/){:new_window}
* [Libreria di documenti Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
