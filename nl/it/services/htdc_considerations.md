---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di HyTrust DataControl on IBM Cloud

Il servizio HyTrust DataControl on {{site.data.keyword.cloud}} offre una potente crittografia con gestione delle chiavi integrata per proteggere i carichi di lavoro per tutto il loro ciclo di vita. Il servizio fornisce la crittografia sia a livello di sistema operativo che a livello di dati. Ciò consente di crittografare e decrittografare qualsiasi directory, cartella o file all'interno di un carico di lavoro.

Questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alla V2.3 o successive. La versione HyTrust DataControl corrente installata è la 4.2.1.
{:note}

## Specifiche tecniche per HyTrust DataControl on IBM Cloud

Nel servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Dispositivo HyTrust DataControl
* CPU: 2 vCPU
* RAM: 8 GB
* Disco: 20 GB VMDK residente su vSAN in cluster convergente
* Rete: posizionata su rete trasferibile privata supportata dalla VLAN specificata per la gestione

### Alta disponibilità (HA)
Vengono distribuiti due dispositivi DataControl in una configurazione attiva-attiva.

### Licenze e tariffe

Licenza per host: viene ordinata una licenza HyTrust DataControl per ciascun host nell'ambiente.

## Considerazioni sulla rimozione di HyTrust DataControl on IBM Cloud

Prima di rimuovere il servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}}, disaccoppia tutti client dall'utilizzo di DataControl. Dopo aver rimosso il servizio, è possibile che le chiavi vengano eliminate e potresti non avere più accesso alle tue VM.

### Link correlati

* [Ordine di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_ordering.html)
* [Gestione di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managinghtdc.html)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Sito web HyTrust](https://www.hytrust.com/)
