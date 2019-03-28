---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di HyTrust KeyControl on IBM Cloud
{: #htkc_considerations}

Il servizio HyTrust KeyControl on {{site.data.keyword.cloud}} semplifica la gestione dei carichi di lavoro crittografati. Questo servizio automatizza e semplifica il ciclo di vita delle chiavi di crittografia, che include l'archiviazione, la distribuzione, la rotazione e la revoca delle chiavi. Utilizzando la crittografia conforme a FIPS 140-2, le aziende possono gestire facilmente le chiavi di crittografia in scala.

Questo servizio è disponibile solo per le istanze che eseguono vSphere 6.5 e che sono distribuite o aggiornate alla V2.5 o successive. La versione HyTrust KeyControl corrente installata è la 4.2.
{:note}

## Specifiche tecniche per HyTrust KeyControl on IBM Cloud
{: #htkc_considerations-specs}

Nel servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}} vengono ordinati e inclusi i seguenti componenti:

### Dispositivo HyTrust KeyControl
{: #htkc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* Disco: 20 GB VMDK residente su vSAN in cluster convergente
* Rete: posizionata su rete trasferibile privata supportata dalla VLAN specificata per la gestione

### Alta disponibilità (HA)
{: #htkc_considerations-ha}

Per impostazione predefinita, vengono distribuiti due dispositivi KeyControl in una configurazione in cluster attiva-attiva.

Facoltativamente, puoi specificare di distribuire due dispositivi KeyControl in una configurazione senza cluster autonoma.

### Licenze e tariffe
{: #htkc_considerations-licenses}

Viene ordinata una licenza di HyTrust KeyControl per ogni installazione dell'istanza.

## Considerazioni sulla rimozione di HyTrust KeyControl on IBM Cloud
{: #htkc_considerations-remove}

Prima di rimuovere il servizio HyTrust KeyControl on {{site.data.keyword.cloud_notm}}, assicurati di disaccoppiare tutti i client dall'utilizzo di KeyContol. Dopo aver rimosso il servizio, è possibile che le chiavi vengano eliminate e potresti non avere più accesso alle tue VM.

## Link correlati
{: #htkc_considerations-related}

* [Ordine di HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_ordering)
* [Gestione di HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sito web HyTrust](https://www.hytrust.com/)
