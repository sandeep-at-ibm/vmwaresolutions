---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: VMware HCX, HCX, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di VMware HCX on IBM Cloud
{: #hcx_considerations}

Il servizio HCX on {{site.data.keyword.cloud}} estende senza problemi le reti dei data center in loco in {{site.data.keyword.cloud_notm}}, il che ti consente di migrare le VM (Virtual Machine) da e verso {{site.data.keyword.cloud_notm}} senza alcuna conversione o modifica. HCX crea un livello di astrazione che abilita la mobilità dell'applicazione e l'ibridità dell'infrastruttura tramite le reti estese in modo sicuro. Puoi semplicemente modernizzare il tuo ambiente VMware da vSphere 5.1 all'ultima versione vSphere senza eseguire il refactoring o modificare la tua applicazione esistente, poiché HCX abilita questa trasformazione senza interruzioni. HCX ti consente di utilizzare i tuoi intervalli di sottoreti di IP in {{site.data.keyword.cloud_notm}} garantendo la coerenza degli IP tramite una distribuzione ibrida, fornendo anche sicurezza di livello elevato con le crittografie Suite B end-to-end.

HCX on {{site.data.keyword.cloud_notm}} ti richiede di utilizzare NSX Advanced o Enterprise tramite {{site.data.keyword.cloud_notm}} o una versione equivalente utilizzando BYOL (Bring Your Own License). È richiesto un impegno a termine di 12 mesi quando ordini il servizio VMware HCX on {{site.data.keyword.cloud_notm}}. L'addebito è basato su 12 mesi consecutivi dopo la distribuzione iniziale di HCX. Tutti i nodi aggiuntivi sono inclusi all'interno della data di scadenza del provisioning iniziale. Dopo la scadenza dell'impegno a termine di 12 mesi, puoi installare e disinstallare il servizio HCX on {{site.data.keyword.cloud_notm}} e puoi aggiungere e rimuovere gli host e i cluster senza limitazioni. Gli addebiti sul tuo account verranno poi fatti su una base mensile e puoi recedere in qualsiasi momento.

La data di scadenza dell'impegno a termine di 12 mesi è disponibile sulla pagina dei dettagli di HCX on {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni sulla visualizzazione dei dettagli del servizio, vedi [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

Un'istanza vCenter Server con HCX on {{site.data.keyword.cloud_notm}} è limitata a tre connessioni simultanee dai siti in loco.

HCX on {{site.data.keyword.cloud_notm}} è supportato sulle seguenti piattaforme:

* vSphere 5.1 (riga di comando solo per vCenter 5.1 utilizzando l'API)
* vSphere 5.5 (IU client web supportata su vCenter 5.5u3 e successive.)
* vSphere 6.0
* vSphere 6.5 (vDS deve essere a un livello 6.0)
* vSphere 6.7

## Specifiche tecniche per HCX on IBM Cloud
{: #hcx_considerations-specs}

Nel servizio HCX on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti.

Le istanze HCX in loco includono solo la licenza e l'attivazione.
{:note}

### Una coppia attivo/passivo di gateway dei servizi edge (ESG) VMware NSX per la gestione HCX
{: #hcx_considerations-nsx}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo di gestione HCX - VM (Virtual Machine)
{: #hcx_considerations-vm}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: 60 GB VMDK

Ulteriori dispositivi HCX vengono distribuiti durante la configurazione in base alle esigenze di connettività L2, ottimizzazione WAN e connessioni gateway.

### Rete
{: #hcx_considerations-networking}

* Una sottorete portatile pubblica con 16 indirizzi IP
* Due sottoreti portatili private con 64 indirizzi IP
* Otto indirizzi IP dalla sottorete vMotion portatile privata

## Considerazioni sull'installazione di HCX on IBM Cloud
{: #hcx_considerations-install}

Esamina le seguenti considerazioni prima di tentare l'installazione di HCX on {{site.data.keyword.cloud_notm}}.

### Requisiti sul numero di server ESXi
{: #hcx_considerations-esxi-servers}

Il servizio HCX on {{site.data.keyword.cloud_notm}} non può essere installato in un'istanza per la quale il cluster predefinito ha più di 51 server ESXi. Poiché HCX on {{site.data.keyword.cloud_notm}} richiede otto indirizzi IP nella sottorete vMotion dal cluster predefinito, se il numero di server ESXi supera 51, nessun indirizzo IP nella sottorete vMotion è disponibile per HCX on {{site.data.keyword.cloud_notm}}.

### Requisiti sulle regole del firewall
{: #hcx_considerations-firewall}

Prima di installare il servizio HCX on {{site.data.keyword.cloud_notm}}, devi aggiungere una regola firewall a qualsiasi firewall esistente per consentire tutto il traffico HTTPS in uscita in modo che il dispositivo virtuale HCX Manager possa registrarsi. Al termine dell'installazione di HCX Manager, puoi rimuovere la regola del firewall. Inoltre, devi configurare le regole del firewall per consentire a HCX di funzionare correttamente. Per ulteriori informazioni, vedi [Requisiti di accesso alla porta di VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req#hcx-archi-port-req).

## Considerazioni sulla rimozione di HCX on IBM Cloud
{: #hcx_considerations-delete}

Esamina le seguenti considerazioni prima di rimuovere il servizio HCX on {{site.data.keyword.cloud_notm}}:
* Assicurati che le interconnessioni e le reti estese tra il sito di origine in loco e i siti di destinazione {{site.data.keyword.cloud_notm}} siano rimossi. Per rimuovere le interconnessioni e le reti estese, utilizza l'interfaccia utente HCX nel client web VMware vSphere installato in loco.
* Assicurati che gli accoppiamenti di siti tra il sito di origine in loco e i siti di destinazione {{site.data.keyword.cloud_notm}} siano rimossi. Per rimuovere gli accoppiamenti di siti, utilizza l'interfaccia utente HCX nel client web VMware vSphere installato in loco.
* La rimozione di HCX on {{site.data.keyword.cloud_notm}} è automatizzata. Per la corretta rimozione di questo servizio vengono completate le seguenti procedure:
   * La licenza HCX ordinata per HCX Manager lato cloud viene disattivata.
   * HCX Manager viene eliminato.
   * Gli indirizzi IP vMotion che erano riservati per HCX vengono rilasciati.
   * Se vuoti, i pool della risorsa correlata a HCX vengono rimossi.
   * Se vuote, le cartelle correlate a HCX vengono rimosse.
   * I dispositivi edge di gestione HCX vengono eliminati.

## Link correlati
{: #hcx_considerations-related}

* [Ordine di HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)
* [Gestione di HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [VMware HCX on IBM Cloud guided demo: Learn how to migrate a VM by using HCX](https://www.ibm.com/cloud/garage/dte/producttour/vmware-hcx-ibm-cloud-guided-demo-learn-how-migrate-vm-using-hcx){:external}
* [Glossario dei termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Panoramica di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}
* [Documentazione di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
