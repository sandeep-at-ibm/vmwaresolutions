---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di HyTrust KeyControl on IBM Cloud

Il servizio HyTrust KeyControl on {{site.data.keyword.cloud}} semplifica la gestione dei carichi di lavoro crittografati. Questo servizio automatizza e semplifica il ciclo di vita delle chiavi di crittografia, che include l'archiviazione, la distribuzione, la rotazione e la revoca delle chiavi. Utilizzando la crittografia conforme a FIPS 140-2, le aziende possono gestire facilmente le chiavi di crittografia in scala.

Questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alla V2.5 o successive. La versione HyTrust KeyControl corrente installata è la 4.2.
{:note}

## Specifiche tecniche per HyTrust KeyControl on IBM Cloud

Nel servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Dispositivo HyTrust KeyControl

* CPU: 2 vCPU
* RAM: 8 GB
* Disco: 20 GB VMDK residente su vSAN in cluster convergente
* Rete: posizionata su rete trasferibile privata supportata dalla VLAN specificata per la gestione

### Alta disponibilità (HA)

Per impostazione predefinita, vengono distribuiti due dispositivi KeyControl in una configurazione in cluster attiva-attiva.

Facoltativamente, puoi specificare di distribuire due dispositivi KeyControl in una configurazione senza cluster autonoma.

### Licenze e tariffe

Viene ordinata una licenza di HyTrust KeyControl per ogni installazione dell'istanza.

## Considerazioni sulla rimozione di HyTrust KeyControl on IBM Cloud

Prima di rimuovere il servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}, assicurati di disaccoppiare tutti i client dall'utilizzo di KeyContol. Dopo aver rimosso il servizio, è possibile che le chiavi vengano eliminate e potresti non avere più accesso alle tue VM.

### Link correlati

* [Ordine di HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_ordering.html)
* [Gestione di HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managinghtkc.html)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Sito web HyTrust](https://www.hytrust.com/)
