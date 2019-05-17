---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-23"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di VMware HCX on IBM Cloud
{: #hcx_considerations}

Il servizio HCX on {{site.data.keyword.cloud}} estende senza problemi le reti dei data center in loco in {{site.data.keyword.cloud_notm}}, il che ti consente di migrare le VM (Virtual Machine) da e verso {{site.data.keyword.cloud_notm}} senza alcuna conversione o modifica.

Questo servizio è disponibile solo per le istanze VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle distribuite nella V2.3 e successive. La versione corrente di HCX on {{site.data.keyword.cloud_notm}} installata è la 3.5.1.
{:note}

Puoi aggiornare la tua istanza vCenter Server esistente a un'istanza vCenter Server with Hybridity Bundle. Per ulteriori informazioni sull'upgrade della tua istanza e sulla distribuzione del servizio HCX on {{site.data.keyword.cloud_notm}}, vedi [Procedura per eseguire l'upgrade a Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic#vc_upgrade-lic-procedure-upgrade-to-hybridity).

Un'istanza vCenter Server con HCX on {{site.data.keyword.cloud_notm}} è limitata a tre connessioni simultanee dai siti in loco.
{:note}

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
* [Glossario dei termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Panoramica di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentazione di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
