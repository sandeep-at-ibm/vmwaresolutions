---

copyright:

  years:  2016, 2017

lastupdated: "2017-08-28"

---

# Note sulla release per la V1.8
{: #relnotes_v18}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Servizio Fortinet on IBM Cloud

Il servizio Fortinet on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze Cloud Foundation e vCenter Server. Questo servizio distribuisce una coppia di dispositivi FortiGate Security Appliance (FSA) della serie 300 in una modalità altamente disponibile per fornire servizi di firewall, instradamento, NAT e VPN per proteggere ogni server e macchina virtuale sulla VLAN pubblica delle tue istanze. Puoi ordinare le istanze con il servizio Fortinet incluso al momento dell'ordine della tua istanza o aggiungere questo servizio alle tue istanze esistenti in un secondo momento utilizzando la pagina dei dettagli dell'istanza.

Dopo aver installato correttamente il servizio Fortinet, puoi gestire e configurare le regole del firewall per FSA dalla console FortiGate. Devi assicurarti che le regole del firewall FSA siano definite per consentire le comunicazioni HTTPS in uscita che vengono avviate dai componenti di gestione come la macchina virtuale IBM CloudDriver o Zerto Virtual Manager per comunicare con il database di gestione esterno su IBM Bluemix® tramite Internet. Le comunicazioni HTTPS in uscita hanno origine dall'indirizzo IP pubblico del gateway dei servizi edge (ESG) VMware NSX dei servizi di gestione nella tua istanza.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Panoramica di Fortinet on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Gestione di Fortinet on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)

## Servizio Veeam on IBM Cloud

Questa release introduce il servizio Veeam on {{site.data.keyword.cloud_notm}}, che può eseguire il backup sia dei componenti di gestione che dei carichi di lavoro. Il nuovo servizio sostituisce la precedente VSI Veeam che era stata integrata nelle release precedenti alla V1.8 per il backup dei soli componenti di gestione.

A causa di questa modifica, sebbene la VSI Veeam nelle istanze precedenti alla V1.8 continui a funzionare, i punti di backup per le istanze non sono più disponibili nella console {{site.data.keyword.vmwaresolutions_short}} e devi creare un ticket di supporto per ottenere assistenza con un ripristino.

Inoltre, la licenza della VSI Veeam nelle istanze precedenti alla V1.8 scade il 14 ottobre 2017. Pertanto, devi sostituire la VSI Veeam precedente con il nuovo servizio Veeam al più presto.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Panoramica di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## Aggiornamenti per le istanze VMware Cloud Foundation

### Utilizza le tue proprie licenze VMware (BYOL) quando ordini le istanze Cloud Foundation

A partire dalla release della V1.8, quando ordini un'istanza Cloud Foundation, ti vengono fornite due opzioni per la licenza dei componenti VMware dell'istanza, inclusi vSphere, vCenter Server, NSX e vSAN. Puoi scegliere di utilizzare nuove licenze che devono essere acquistate per tuo conto.

Puoi anche scegliere di utilizzare la tua propria licenza VMware per un componente, nel qual caso dovrai fornire le chiavi di licenza. In questo caso, il supporto per i componenti VMware per i quali fornisci le licenze verrà offerto da VMware, non dal supporto IBM.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Domande frequenti su BYOL](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_byol)

## Aggiornamenti per le istanze VMware vCenter Server

### Personalizza la CPU e la memoria della tua istanza

Insieme alle opzioni Small, Medium e Large precostruite e testate, è disponibile un'opzione di server personalizzabile. Puoi effettuare una selezione da un elenco di server compatibili con HCL VMware in base alle doppie CPU e al numero di core totali, oltre alla quantità di RAM. L'archiviazione locale non è personalizzabile.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Aggiunta e visualizzazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

### Supporto per aggiungere più di 7 condivisioni file NFS

 Puoi collegare fino a un massimo di 32 condivisioni file su tutti i server ESXi in un cluster.

 Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Aggiunta e visualizzazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

### Aggiornamenti ai data center

Per la distribuzione, sono disponibili i seguenti nuovi data center: **DAL-09, DAL-12, DAL-13 - Dallas**; **LON-04, LON-06 - Londra**; **SJC-04 - San Jose**; **WDC-06, WDC-07 - Washington, DC**

Per ulteriori informazioni, vedi [Requisiti e pianificazione per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)

## Miglioramenti dell'usabilità

Sono stati apportati miglioramenti in tutta l'interfaccia utente:
* Puoi conoscere i servizi e ordinare un'istanza nella pagina **Introduzione** dal riquadro di navigazione a sinistra.
* Utilizza il menu di overflow nella pagina dei dettagli dell'istanza per eliminare un'istanza nello stato **Pronto per l'utilizzo**.
* L'opzione per aggiornare la tua edizione della licenza NSX è ora disponibile nella scheda **Aggiorna e applica patch**. L'aggiornamento della licenza sostituisce tutte le licenze NSX esistenti nel tuo account IBM SoftLayer con la nuova licenza.
* La scheda **Backup e ripristino** nella pagina dei dettagli dell'istanza non è più disponibile.
* Puoi selezionare più servizi da distribuire all'inizio di un ordine. Oltre al servizio Zerto on {{site.data.keyword.cloud_notm}}, sono disponibili anche le opzioni per selezionare il servizio Veeam on {{site.data.keyword.cloud_notm}} e il servizio Fortinet on {{site.data.keyword.cloud_notm}}.
* La scheda **Servizi disponibili** nella scheda **Servizi** nella pagina dei dettagli dell'istanza è rinominata in **Aggiungi servizi**.
