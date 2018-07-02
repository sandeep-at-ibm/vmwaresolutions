---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Panoramica di VMware HCX on IBM Cloud

Il servizio HCX on {{site.data.keyword.cloud}} può estendere senza problemi le reti dei data center in loco in {{site.data.keyword.cloud_notm}}, il che consente la migrazione delle macchine virtuali (VM) da e verso {{site.data.keyword.cloud_notm}} senza alcuna conversione o modifica.

**Disponibilità**: questo servizio è disponibile solo per le istanze VMware vCenter Server on IBM Cloud with Hybridity Bundle distribuite nelle release della V2.3 e successive.

Puoi aggiornare la tua istanza vCenter Server esistente a un'istanza vCenter Server with Hybridity Bundle. Per ulteriori informazioni sull'aggiornamento della tua istanza e sulla distribuzione del servizio HCX on {{site.data.keyword.cloud_notm}}, vedi [Aggiornamento all'istanza vCenter Server with Hybridity Bundle](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html#upgrading-to-the-vcenter-server-with-hybridity-bundle-instance).

**Nota:** un'istanza vCenter Server con HCX on {{site.data.keyword.cloud_notm}} è limitata a tre connessioni simultanee dai siti in loco.

## Considerazioni sull'istallazione di HCX on IBM Cloud

Esamina le seguenti considerazioni prima di tentare l'installazione di HCX on {{site.data.keyword.cloud_notm}}.

### Requisiti sul numero di server ESXi

Il servizio HCX on {{site.data.keyword.cloud_notm}} non può essere installato in un'istanza per la quale il cluster predefinito ha più di 51 server ESXi. Poiché HCX on {{site.data.keyword.cloud_notm}} richiede otto indirizzi IP nella sottorete vMotion dal cluster predefinito, se il numero di server ESXi supera 51, nessun indirizzo IP nella sottorete vMotion è disponibile per HCX on {{site.data.keyword.cloud_notm}}.

### Requisiti sulle regole del firewall

Prima di installare il servizio HCX on {{site.data.keyword.cloud_notm}}, devi aggiungere una regola firewall a qualsiasi firewall esistente per consentire tutto il traffico HTTPS in uscita in modo che il dispositivo virtuale HCX Manager possa registrarsi. Al termine dell'installazione di HCX Manager, puoi rimuovere la regola del firewall. Inoltre, devi configurare le regole del firewall per consentire a HCX di funzionare correttamente. Per ulteriori informazioni, vedi *Appendix A - Port Access Requirements* in [HCX on {{site.data.keyword.cloud_notm}} Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

## Considerazioni sulla rimozione di HCX on IBM Cloud

Esamina le seguenti considerazioni prima di rimuovere il servizio HCX on {{site.data.keyword.cloud_notm}}:
* Assicurati che le interconnessioni e le reti estese tra il sito di origine in loco e i siti di destinazione {{site.data.keyword.cloud_notm}} siano rimossi. Per rimuovere le interconnessioni e le reti estese, utilizza l'interfaccia utente HCX nel client web VMware vSphere installato in loco.
* Assicurati che gli accoppiamenti di siti tra il sito di origine in loco e i siti di destinazione {{site.data.keyword.cloud_notm}} siano rimossi. Per rimuovere gli accoppiamenti di siti, utilizza l'interfaccia utente HCX nel client web VMware vSphere installato in loco.
* La rimozione di HCX on {{site.data.keyword.cloud_notm}} è automatizzata. Per la corretta rimozione di questo servizio vengono completate le seguenti procedure:
   * Disattiva la licenza HCX ordinata per HCX Manager lato client.
   * Elimina HCX Manager.
   * Rilascia gli indirizzi IP vMotion che erano riservati per HCX.
   * Rimuovi i pool di risorse relativi a HCX, se vuoti.
   * Rimuovi le cartelle relative a HCX, se vuote.
   * Elimina i dispositivi edge di gestione HCX.

## Link correlati

* [Ordine di HCX on {{site.data.keyword.cloud_notm}}](hcx_ordering.html)
* [Gestione di HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Glossario dei termini HCX](hcx_glossary.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Panoramica di VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentazione di VMware Hybrid Cloud Extension](https://hcx.vmware.com/#vm-documentation)
