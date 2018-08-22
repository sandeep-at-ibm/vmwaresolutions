---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# Panoramica di HyTrust DataControl on IBM Cloud

Il servizio HyTrust DataControl on {{site.data.keyword.cloud}} offre una potente crittografia con gestione delle chiavi integrata per proteggere i carichi di lavoro per tutto il loro ciclo di vita. Il servizio può fornire la crittografia sia a livello di sistema operativo che a livello di dati, il che significa che è possibile crittografare e decrittografare qualsiasi directory, cartella o file all'interno di un carico di lavoro.

**Disponibilità:** questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.3 o successive.

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

Prima di rimuovere il servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}}, assicurati di aver crittografato o eseguito il backup di tutti i dischi da DataControl. Dopo aver rimosso il servizio, le chiavi potrebbero essere eliminate e potresti essere bloccato dalle tue VM.

### Link correlati

* [Ordine di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gestione di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web HyTrust](https://www.hytrust.com/)
