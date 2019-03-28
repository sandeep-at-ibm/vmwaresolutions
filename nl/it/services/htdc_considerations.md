---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di HyTrust DataControl on IBM Cloud
{: #htdc_considerations}

Il servizio HyTrust DataControl on {{site.data.keyword.cloud}} offre una potente crittografia con gestione delle chiavi integrata per proteggere i carichi di lavoro per tutto il loro ciclo di vita. Il servizio fornisce la crittografia sia a livello di sistema operativo che a livello di dati. Ciò consente di crittografare e decrittografare qualsiasi directory, cartella o file all'interno di un carico di lavoro.

Questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alla V2.3 o successive. La versione HyTrust DataControl corrente installata è la 4.2.1.
{:note}

## Specifiche tecniche per HyTrust DataControl on IBM Cloud
{: #htdc_considerations-specs}

Nel servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Dispositivo HyTrust DataControl
{: #htdc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* Disco: 20 GB VMDK residente su vSAN in cluster convergente
* Rete: posizionata su rete trasferibile privata supportata dalla VLAN specificata per la gestione

### Alta disponibilità (HA)
{: #htdc_considerations-ha
}
Vengono distribuiti due dispositivi DataControl in una configurazione attiva-attiva.

### Licenze e tariffe
{: #htdc_considerations-licenses}

Licenza per host: viene ordinata una licenza HyTrust DataControl per ciascun host nell'ambiente.

## Considerazioni sulla rimozione di HyTrust DataControl on IBM Cloud
{: #htdc_considerations-remove}

Prima di rimuovere il servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}}, disaccoppia tutti client dall'utilizzo di DataControl. Dopo aver rimosso il servizio, è possibile che le chiavi vengano eliminate e potresti non avere più accesso alle tue VM.

## Link correlati
{: #htdc_considerations-related}

* [Ordine di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Gestione di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web HyTrust](https://www.hytrust.com/)
